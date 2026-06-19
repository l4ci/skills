# Reference-Class Forecast: Monolith-to-Microservices Migration

> _Illustrative example output for the `reference-class-forecasting` skill. The migration project below is fictional; every figure, name, and claim is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Prediction:** Number of months from kickoff until the last service is extracted from the monolith and the monolith is decommissioned.
- **Case:** A 12-engineer SaaS company breaking a 6-year-old Rails monolith into ~15 services. No prior microservices experience on the team. Runs alongside normal feature work.
- **Inside-view estimate:** 9 months (the current roadmap).
- **Decision it feeds:** Whether to commit a 9-month roadmap with hiring, customer, and board commitments hung off it, and how much schedule buffer to reserve.
- **Date:** 2026-06-19

---

## 1. The forecast

**Most likely 21 months, plausibly 15 to 34 months**, for a full extraction-and-decommission, at the stated scope and team size, running alongside feature work.

The outside view lands a little over **2x** the 9-month roadmap. The roadmap is not a stretch goal that occasionally slips; it sits below the 10th percentile of how this class of project actually finishes. No case in the reference class resembling this one finished in 9 months while also carrying normal feature load.

| | Outside-view forecast | Inside-view estimate |
|---|---|---|
| Central (P50) | **21 months** | 9 months |
| Optimistic (P10) | 15 months |: |
| Pessimistic (P90) | 34 months |: |
| Position vs. class | at the class median, lightly adjusted | below the class P10 |

---

## 2. The base rate

**Reference class (chosen):** *Single-team monolith decompositions*: an established product company breaking one large, mature monolith (4+ years old) into roughly 8–25 services, executed by an in-house team of 8–25 engineers with no prior at-scale microservices delivery, while the product stays live and feature work continues.

**Inclusion criteria (auditable):**

- Existing revenue-generating monolith, not a greenfield rewrite.
- Migration runs concurrently with normal feature delivery (not a frozen-roadmap rewrite).
- In-house team of 8–25 engineers; no dedicated, pre-experienced platform org.
- Target end state: monolith fully decommissioned, not merely "strangler started."
- Outcome measured as **realized** elapsed months to decommission, not the originally planned figure.

**The distribution** (n = 23 documented cases; see caveats):

| Percentile | Months to full decommission |
|---|---|
| P10 | 15 |
| P25 | 18 |
| **P50 (base rate)** | **22** |
| P75 | 28 |
| P90 | 34 |
| Never finished* | 4 of 23 (~17%) |

\*Four cases stalled: the strangler pattern reached "most traffic moved" and the residual monolith was never killed (it became a permanent service). These are counted as right-censored at the point work stopped; excluding them entirely would bias the class optimistic, so the median above already treats them as "≥ their last observed month."

**The base rate is ~22 months to full decommission, with a roughly 1-in-6 chance the monolith never fully dies.** Note the second number: for this class, "how long" and "does it finish at all" are the same question, and the roadmap implicitly assumes a clean finish that ~17% of the class never reached.

---

## 3. The planning-fallacy gap

| | Months |
|---|---|
| Inside-view estimate (roadmap) | 9 |
| Outside-view forecast (P50) | 21 |
| **Gap** | **+12 months (~133% uplift)** |

The roadmap is not slightly optimistic; it is off by more than a factor of two and sits below where 90% of comparable projects finished. This gap is the most valuable output of the exercise: it is the optimism that would otherwise have been built silently into board, hiring, and customer commitments.

The mechanism is textbook planning fallacy. The 9-month figure was built from the **inside view**: summing the estimated effort to extract ~15 services and dividing by team capacity. That arithmetic sees the plan but not the things that derailed every comparable effort: the shared database that resists splitting, the dual-write/consistency work nobody scoped, the half of the team's time that feature work silently consumes, and the long tail of "almost decommissioned" that drags for quarters.

---

## 4. Adjustments

Start at the base rate (22 months). Apply only adjustments that survived all three critics. Each names its evidence and its size.

### Adjustments applied

| Adjustment | Direction | Size | Evidence |
|---|---|---|---|
| Scope at the low-middle of class (~15 services, not 25) | faster | −1 month | Class spans 8–25 services; 15 is near the median, so only a small pull below P50 |

Net: **22 − 1 = ~21 months central.**

That is the entire defensible adjustment. The case is squarely a typical member of its class, so the forecast sits essentially at the base rate.

### Adjustments rejected (and why)

| Tempting adjustment | Claimed direction | Why rejected |
|---|---|---|
| "Our team is strong and ships fast" | faster | Not evidence. Every case in the class believed this; team quality is already priced into the class median, which is composed of teams that also rated themselves capable. No *documented*, class-relative differentiator was offered. |
| "Modern tooling (managed K8s, service mesh, IaC) is better than the older cases" | faster | The tooling improved for the whole class over time; the recent cases in the distribution already use it and still land at ~22 months. Tooling moved the floor for everyone, not this case relative to peers. |
| "No prior microservices experience: adjust slower" | slower | Already in the class definition (the class is *teams without prior at-scale experience*). Adjusting again would double-count. |
| "We'll freeze features for the migration" | faster | The case explicitly states migration runs *alongside* normal feature work, so this does not apply. (If the company genuinely froze the roadmap, that would move it toward the frozen-rewrite class, ~30% faster: but that is a different decision, not an adjustment to this one.) |
| "We'll staff it as the top priority" | faster | Intention, not a structural change. The cases that slipped also intended to prioritize it; feature pressure reasserts itself. No evidence this case has a mechanism the slipped cases lacked. |

**Critic verdict:** Every adjustment the inside view wanted pointed the same direction: faster, which is the planning fallacy reasserting itself rather than analysis. The regression critic's default held: the case is more average than it feels, and only the single, modest scope adjustment cleared all three reviewers.

---

## 5. The contingency implication

Plan to the outside view, not the roadmap.

- **Commit to ~21 months, not 9.** Hang board, hiring, and customer commitments off the P50, not the inside-view figure. If a 9-month narrative is unavoidable externally, define the 9-month milestone as a *partial* checkpoint ("first N services extracted, X% of traffic moved"), never as "monolith decommissioned."
- **Reserve a buffer to P90, ~34 months,** for any commitment whose failure is expensive (a contract clause, a deprecation deadline, a dependent migration). A buffer sized to the inside view is a buffer to nothing.
- **Pre-commit a decommission kill-criterion.** Given the ~17% "never finished" rate, decide *now* what triggers a hard push to kill the residual monolith (e.g., "if >85% traffic is migrated by month 18, freeze new feature work on the monolith and fund a decommission sprint"). The default failure of this class is not lateness, it is a half-strangled monolith that lives forever.
- **Protect migration capacity explicitly.** The single largest driver of the gap is feature work quietly eating migration time. Ring-fence a fixed fraction of team capacity (or a sub-team) for extraction, and track it, because the inside view assumes a capacity that day-to-day priorities erode.

---

## 6. Confidence and limits

- **Sample size and quality:** ~23 documented cases. Moderate confidence in the central estimate, lower in the tails. Real cases under-report the messy decommission tail (write-ups stop at "we migrated to microservices," not at "we finally killed the last monolith endpoint"), so the true median may be *later* than 22 months, not earlier, the survivorship bias here runs against optimism.
- **Sensitivity to the reference class:** The forecast is robust to the class choice. The narrow class (Rails-specific, 10–15 engineers) gave a similar ~20-month median on fewer cases; the broad class (any monolith decomposition, any team size) gave ~18 months but with much higher spread and less relevance. The mechanism class (projects gated on splitting a shared database) was the *worst*, median ~26 months, suggesting the shared-data dependency, if this monolith has one, is the variable most likely to push the case above 21.
- **What would sharpen this forecast:** (1) Whether the monolith has a single shared database that all ~15 services must split, the strongest documented driver of class variance. (2) The actual, measured fraction of team capacity that will be protected for migration vs. consumed by features. (3) A Fermi (inside-view) build-up of the same project, to reconcile against this outside view; the gap between the two is itself diagnostic.
- All figures here are illustrative for documentation purposes and were not researched.
