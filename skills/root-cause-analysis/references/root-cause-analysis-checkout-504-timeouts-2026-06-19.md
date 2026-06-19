# Root-cause analysis: Checkout API 504 timeouts

> _Illustrative example output for the `root-cause-analysis` skill. The checkout incident is fictional; every figure, log line, query, and timestamp below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Effect (fish head):** Checkout API returns 504 timeouts on ~3% of requests, only during the 12:00–14:00 traffic peak, since the Tuesday deploy on the 9th.
- **Context:** Software/service domain. A new recommendations sidecar shipped in that Tuesday deploy. Latency dashboards, deploy logs, and DB slow-query logs available. No infra capacity change.
- **Date:** 2026-06-19
- **Category set:** The 6 Ms (People, Machine, Method, Material, Measurement, Environment), chosen over the service 4 Ps because the effect is a concrete technical failure in a running system with identifiable components, logs, and a code change, not a process or policy defect.
- **Framework:** Ishikawa fishbone scans every cause category so nothing is missed; the 5 Whys drills the strongest candidates to a cause that, if removed, stops recurrence.

---

## 1. Verdict

**Root cause (confirmed by evidence):** The recommendations sidecar deployed on the 9th opens a **new database connection per request against the same Postgres primary** and holds it for the full duration of a synchronous, uncached recommendations query. Under peak load (12:00–14:00) this exhausts the shared connection pool; checkout requests then queue waiting for a connection and breach the 5-second gateway timeout, returning 504. Off-peak, the pool is never saturated, so the effect disappears, which is exactly why it is intermittent and time-bound.

**Lead countermeasure:** Give the sidecar its own bounded connection pool (or a read replica), cap its pool well below the primary's headroom, and make the recommendations call asynchronous and time-boxed so it can never hold a checkout-path connection. Removing the shared-pool contention is what stops recurrence.

A second, **contributing** cause is verified: checkout's call to the sidecar is **on the synchronous critical path with no timeout or fallback**, so a slow sidecar drags checkout down instead of degrading gracefully. This worsens the blast radius but is not the origin; it is addressed as a resilience countermeasure.

---

## 2. The fishbone

Every category was scanned by a finder before any chain was drilled. Each candidate is marked **[evidenced]** or **[speculative]**, with rank and confidence.

### Machine (equipment, systems): *strongest category*

| # | Candidate cause | Mechanism | Evidence | Mark | Conf |
|---|---|---|---|---|---|
| M1 | Sidecar opens a new connection per request to the **shared** Postgres primary, exhausting the pool at peak | Each held connection subtracts from the fixed pool; checkout waits on a free connection and times out | `pg_stat_activity` peaks at 100/100 connections 12:05–13:50 daily since the 9th; `active` count from the sidecar service user ~40, was 0 before | [evidenced] | High |
| M2 | Pool max (100) is undersized for combined checkout + sidecar load | Even bounded, two services on one pool exceed it at peak | Pool config unchanged for 8 months; checkout alone peaked at ~70 connections pre-deploy | [evidenced] | Med |
| M3 | Gateway/LB idle timeout misconfigured, cutting healthy long requests | A too-low timeout would 504 slow-but-succeeding requests | Gateway timeout 5s, unchanged before/after the 9th; rejected as origin | [evidenced] | Low |

### Method (how the work is done)

| # | Candidate cause | Mechanism | Evidence | Mark | Conf |
|---|---|---|---|---|---|
| Me1 | Sidecar call is **synchronous on checkout's critical path, no timeout, no fallback** | Slow sidecar blocks the checkout response thread until the gateway gives up | Trace spans show checkout waiting on `recommendations.fetch` for 4.8s+ in every 504 sample | [evidenced] | High |
| Me2 | Recommendations query is **uncached**, recomputed per request | No cache means every checkout pays full DB cost; load scales 1:1 with traffic | Sidecar has no cache layer in config; slow-query log shows the same query 9k times/hour | [evidenced] | Med |
| Me3 | Deploy shipped without a load test at peak-equivalent traffic | A staging load test would have surfaced pool exhaustion pre-prod | CI logs show unit + smoke tests only; no load stage | [evidenced] | Med |

### Measurement (how the effect is observed)

| # | Candidate cause | Mechanism | Evidence | Mark | Conf |
|---|---|---|---|---|---|
| Ms1 | 504s under-counted by the dashboard (gateway-level errors not in app metrics) | Real rate may exceed 3%; would change urgency, not cause | App error metric excludes gateway 504s; LB logs show ~3.1%: confirms, not refutes | [evidenced] | Low |
| Ms2 | "Timeout" conflates gateway 504 with app 500s | Misdiagnosis risk if categories are mixed | LB and app logs separated; 504s cleanly attributable to gateway timeout | [evidenced] | Low |

### Material (inputs, dependencies)

| # | Candidate cause | Mechanism | Evidence | Mark | Conf |
|---|---|---|---|---|---|
| Ma1 | New sidecar container image pulls a heavier Postgres driver with different pooling defaults | Driver default could open more connections than expected | Image diff shows added driver; defaults to one connection per request unless pooled: supports M1 | [evidenced] | Med |
| Ma2 | Recommendations model data table grew, slowing the query | A larger scan would lengthen each held connection | Table row count steady; query plan unchanged: rejected | [evidenced] | Low |

### People (who does the work)

| # | Candidate cause | Mechanism | Evidence | Mark | Conf |
|---|---|---|---|---|---|
| P1 | Sidecar author unaware checkout shares the same DB primary | Knowledge gap led to the shared-pool design | Plausible from PR review comments asking "which DB?"; a system gap, not blame | [speculative] | Med |
| P2 | Peak-hours on-call rotation thinner, slower mitigation | Affects recovery time, not the cause | No bearing on why 504s start; rejected as cause | [speculative] | Low |

### Environment (conditions around the work)

| # | Candidate cause | Mechanism | Evidence | Mark | Conf |
|---|---|---|---|---|---|
| E1 | 12:00–14:00 lunch-hour traffic peak is the **trigger condition** | Peak load is what pushes the shared pool to exhaustion; not a cause alone | Traffic ~2.3x baseline 12:00–14:00; 504s start/stop exactly with the peak window | [evidenced] | High |
| E2 | Seasonal/marketing event raised baseline traffic the same week | Coincident load increase could confound the deploy correlation | No campaign in the window; week-over-week baseline flat: rejected as confound | [evidenced] | Med |

**Pooled strongest candidates carried to drilling:** M1 (shared-pool exhaustion), Me1 (synchronous no-timeout call), Me2 (uncached query), with E1 as the trigger condition. M2 and Ma1 fold into the M1 chain.

---

## 3. Why-chains

### Chain A: M1: shared-pool exhaustion (root candidate)

1. **Why do checkout requests 504 at peak?** Because they wait longer than 5s for a database connection and the gateway times out.
2. **Why do they wait for a connection?** Because the Postgres connection pool is fully allocated (100/100) during the 12:00–14:00 window.
3. **Why is the pool fully allocated now but not before the 9th?** Because the new recommendations sidecar consumes ~40 connections it did not consume before, on top of checkout's ~70 at peak.
4. **Why does the sidecar consume so many?** Because it opens a connection per request and holds it for the whole synchronous recommendations query, against the **same primary** checkout uses: no separate pool, no replica.
   - **Branch 4a (Material/Ma1):** Why one-per-request? Because the bundled driver defaults to unpooled connections and the sidecar never configured a bounded pool.
5. **Why was a shared, unbounded pool design shipped?** Because there is **no pre-deploy check that a new service's DB connection budget fits within the shared pool's headroom**, and no peak-load test stage in CI (Me3) to surface it.

**Root reached:** a sidecar design that draws unbounded connections from checkout's shared pool, shipped without a connection-budget or load gate. Removing the shared-pool contention (own pool/replica + bounded cap + async call) prevents recurrence. Actionable; stops here rather than at "traffic is high."

### Chain B: Me1: synchronous call with no timeout/fallback (contributing candidate)

1. **Why does a slow sidecar cause a checkout 504?** Because checkout calls it synchronously and blocks on the response.
2. **Why does it block?** Because the call has no client-side timeout and no fallback path.
3. **Why no timeout/fallback?** Because recommendations were treated as required-inline rather than a best-effort enhancement.
4. **Why treated as required?** Because the integration spec did not classify recommendations as non-critical, so the default (block-and-wait) applied.

**Root of this branch:** a missing resilience contract (timeout + fallback + criticality classification) on a non-critical dependency. This **worsens** every slow-sidecar event but is not why the sidecar is slow, contributing, not root.

### Chain C: Me2: uncached query (contributing candidate)

1. **Why is each recommendations call expensive?** Because the query is recomputed per request.
2. **Why recomputed?** No cache layer.
3. **Why no cache?** The sidecar shipped as an MVP; caching was deferred.

**Root of this branch:** deferred caching. Caching shortens how long each connection is held, easing pool pressure, it **mitigates** the M1 mechanism but does not remove the shared-pool design. Contributing.

---

## 4. Verification

| Claimed cause | Timeline | Removal | Data | Mechanism | Verdict |
|---|---|---|---|---|---|
| **M1: shared-pool exhaustion** | 504s begin the day of the 9th deploy, none in the 30 days prior; sidecar connections appear in `pg_stat_activity` starting the 9th | Staging repro: capping the sidecar to its own 20-connection pool eliminated checkout connection-waits under replayed peak load; 504s → 0 | Pool at 100/100 only in the 12:00–14:00 window; sidecar service user accounts for the new ~40 | Held connections directly subtract from a fixed pool; queued checkout requests exceed the 5s gateway timeout | **PASS: root cause (confirmed)** |
| **Me1: sync call, no timeout** | Pre-dates the deploy (always synchronous): so not the *origin* of the new 504s | Adding a 400ms timeout + fallback in staging let checkout return 200 with no recs even while the sidecar was slow | Every 504 trace shows checkout blocked on `recommendations.fetch` | Blocking on a slow dependency propagates its latency | **PASS as contributing** (enables/worsens; not origin) |
| **Me2: uncached query** | Pre-dates as a property of the new sidecar; not independently the trigger | Adding a 60s cache in staging cut sidecar connection-hold time ~70%, raising the load needed to exhaust the pool | 9k identical queries/hour in slow-query log | Longer holds = fewer free connections | **PASS as contributing** (mitigates, not removes) |
| **E1: peak traffic** | Correlates perfectly with the 504 window | Cannot remove (traffic is the business); reducing it is not a fix | Traffic 2.3x baseline 12:00–14:00 | Load is the *trigger*, not the defect | **Trigger condition, not a cause to remove** |
| M3 gateway timeout, Ma2 table growth, E2 campaign confound, P2 on-call | n/a | n/a | Each refuted by data above |: | **Rejected** |

**Correlation vs. causation:** Peak traffic (E1) correlates perfectly with the 504s, but it is the trigger, not the cause: the same traffic ran fine before the 9th. The deploy (M1) both precedes the effect and passes the removal test in staging, which is what promotes it from correlation to confirmed cause.

**Root vs. contributing:** M1 is the single **root** (remove it, recurrence stops). Me1 and Me2 are **contributing** (they enlarge the blast radius and the load-to-failure margin, but the 504s originate in the shared-pool design). E1 is a trigger condition, not a removable cause.

---

## 5. Countermeasures

Ranked by impact on the effect × feasibility. Each names the cause it removes and the post-action check.

1. **Isolate the sidecar's database access (removes root M1).** Give the sidecar its own bounded connection pool capped well under the primary's headroom, and prefer a read replica for recommendations so checkout's pool is never shared. **Verify:** at peak, `pg_stat_activity` for the checkout pool stays below saturation and the 504 rate falls to baseline (~0%) for a full week including lunch peaks. *Impact 5 / Feasibility 4.*
2. **Make the recommendations call async, time-boxed, with a fallback (removes contributing Me1).** Cap the call at ~400ms; on timeout, return checkout without recommendations rather than failing. **Verify:** induce sidecar latency in staging and confirm checkout returns 200 with no recs and no 504. *Impact 4 / Feasibility 5.*
3. **Cache recommendations results (reduces contributing Me2).** Short-TTL cache to cut per-request connection-hold time and DB load. **Verify:** slow-query volume drops sharply; connection-hold duration falls in tracing. *Impact 3 / Feasibility 4, mitigation, not a cure.*
4. **Add a peak-load test stage and a DB connection-budget gate to CI (removes the systemic root behind Chain A step 5).** No new service ships without proving its connection budget fits the shared pool under peak-equivalent load. **Verify:** the gate rejects a deliberately over-provisioned test service. *Impact 4 / Feasibility 3, prevents the next variant.*
5. **Stopgap only, raise the pool max / scale the primary (symptom relief).** Buys headroom now but leaves the unbounded-shared-pool design intact; the problem returns as traffic grows. **Label:** stopgap, not a fix; do not close the incident on this alone. *Impact 2 / Feasibility 5.*

---

## 6. Caveats

- A fishbone **enumerates** possible causes; it does not prove any. The confidence here comes from the verification stage, not the breadth of the scan.
- The 5 Whys is a structured guess until tested. M1 is called **confirmed** because the staging removal test reproduced and then eliminated the effect; the contributing causes passed weaker tests and are labeled accordingly.
- The analysis is only as good as the available data. The 3% figure depends on LB logs being complete; if 504s are under-counted (Ms1), severity rises but the cause is unchanged.
- Removing the verified root (M1) stops **this** recurrence, peak-hour 504s from shared-pool exhaustion. It does not immunize against every future variant (e.g., a different new service repeating the same pattern), which is exactly what countermeasure 4's CI gate is meant to catch.
- "Operator unaware of the shared DB" (P1) is recorded as a **system** gap, not blame: the fix is the connection-budget gate, not a reprimand. A missing guardrail let a reasonable engineer ship the design.
- All figures, logs, and timestamps in this report are illustrative for documentation purposes and were not researched.
