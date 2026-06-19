# Pre-mortem: Stripe Billing migration

> _Illustrative example output for the `pre-mortem` skill. The migration plan, team, and customer base are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Plan reviewed:** Migrate all 40,000 subscription customers from the in-house billing engine to Stripe Billing over Q3, cutting over in a single weekend, then decommissioning the old engine.
- **Imagined horizon:** The Monday after the October renewal run.
- **Definition of failure used:** Any customer charged the wrong amount or not at all, or a renewal that silently fails. Goal is zero billing interruptions.
- **Constraints:** Team of 4 engineers; hard deadline before the October renewal spike.
- **Date:** 2026-06-19
- **Method:** Prospective-hindsight pre-mortem (Gary Klein). Six failure-finder lenses run in parallel, a blind-spot pass, then reconciliation and scoring by likelihood × impact.

---

## 1. Executive summary

The plan is one large irreversible step taken under a hard deadline by a small team, against the most unforgiving definition of failure possible, *any* customer mischarged. That combination is the core risk: a single-weekend big-bang cutover removes every opportunity to catch a defect before it touches real money, and the October renewal spike is the worst possible week to discover one. The overall posture is **high risk, concentrated in the cutover itself**, with most failure modes tracing back to the same root: no incremental proof that the new system charges correctly at scale before it owns all 40,000 customers.

The risks that most threaten the plan:

1. **Silent renewal failures at cutover (severity 25, critical).** Subscriptions migrate with wrong renewal dates, proration, or trial state, and a slice of customers simply never gets charged, invisible until revenue is reconciled weeks later.
2. **Data-mapping errors between the in-house schema and Stripe's model (severity 20, critical).** The old engine's plan, discount, and tax representations do not map cleanly onto Stripe objects; edge cases (annual-to-monthly switchers, grandfathered plans, paused accounts) migrate wrong.
3. **No realistic dry run at full scale (severity 20, critical).** The team validates on a sample, not on a full mirror of production, so the failures that only appear at 40,000-customer scale and real card declines surface live.
4. **Four engineers, hard deadline, key-person concentration (severity 16, high).** The one person who understands the old engine's billing quirks is a single point of failure, and the deadline leaves no slack for the reconciliation work to overrun.
5. **No clean rollback once the old engine is decommissioned (severity 16, high).** "Decommission" is planned for right after cutover; if a defect surfaces in week two there is nothing to fall back to.

The blind spot every lens nearly missed is **dunning and failed-payment recovery**: see Section 5.

---

## 2. Risk register

Severity = likelihood × impact (1–25). Bands: 20–25 critical, 12–19 high, 6–11 medium, 1–5 low.

| # | Risk | Lik | Imp | Sev | Band | Lenses that raised it |
|---|---|---|---|---|---|---|
| R1 | Silent renewal failures at cutover (customers never charged) | 5 | 5 | **25** | Critical | Execution, Assumptions, Second-order |
| R2 | Data-mapping errors: old schema → Stripe objects | 4 | 5 | **20** | Critical | Execution, Assumptions |
| R3 | No full-scale dry run; defects surface live | 4 | 5 | **20** | Critical | Execution, Timeline |
| R4 | Key-person + 4-engineer concentration under hard deadline | 4 | 4 | **16** | High | Timeline, People |
| R5 | No rollback after old engine decommissioned | 4 | 4 | **16** | High | Assumptions, Timeline |
| R6 | Dunning / failed-payment recovery not migrated (blind spot) | 4 | 4 | **16** | High | Blind-spot pass |
| R7 | Webhook / downstream integration drift (provisioning, entitlements, accounting) | 3 | 4 | 12 | High | Execution, Second-order |
| R8 | Stripe rate limits / API throughput during bulk migration | 3 | 4 | 12 | High | Execution, External |
| R9 | Tax and compliance handling differs (VAT, sales-tax nexus) | 3 | 4 | 12 | High | Assumptions, External |
| R10 | Customer trust shock from billing emails / receipts changing | 3 | 3 | 9 | Medium | People, Second-order |
| R11 | Stripe pricing / fee structure erodes margin post-migration | 2 | 3 | 6 | Medium | External |
| R12 | PCI / card-data handoff during migration mishandled | 2 | 4 | 8 | Medium | External, Execution |
| R13 | Stripe outage during the cutover weekend | 1 | 5 | 5 | Low | External |

---

## 3. Detailed entries (critical and high risks)

### R1: Silent renewal failures at cutover (severity 25, critical)

**Mechanism.** Over the cutover weekend, 40,000 subscriptions are created in Stripe with `current_period_end` dates, billing anchors, and proration computed from the old engine's export. A subset: annual customers mid-cycle, accounts that recently changed plans, those with credit balances, get an anchor date that is off by a cycle or set in the past. Stripe either skips their next invoice or generates one immediately for the wrong amount. Because nothing errors loudly, the gap only shows when October revenue lands ~8–15% below forecast and finance asks why.

**Early warning signs.** A dry-run reconciliation where the count of invoices Stripe *would* generate in the next 30 days does not equal the count of renewals the old engine *would* have run. Any non-zero set of subscriptions with a billing anchor in the past. Mismatch between summed expected MRR pre- and post-migration.

**Mitigation (targets likelihood and impact).** Before decommissioning anything, run a **shadow billing period**: keep the old engine authoritative for one full renewal cycle while Stripe runs in test/no-charge mode, then diff every invoice Stripe would have raised against what the old engine actually charged. Block cutover until that diff is zero or every exception is explained.

**Leading indicator.** Daily count of subscriptions whose next Stripe invoice date ≠ old-engine next-renewal date. Must reach zero before go-live.

**Contingency.** If discovered post-cutover, freeze automatic collection, identify the affected cohort by the invoice-date diff, and re-issue correct invoices manually with a proactive customer email before any second charge fires.

**Suggested owner.** Billing engineer (old-engine owner) paired with finance for the reconciliation diff.

---

### R2: Data-mapping errors: old schema → Stripe objects (severity 20, critical)

**Mechanism.** The in-house engine encodes plans, add-ons, percentage and fixed discounts, grandfathered legacy pricing, and tax flags in a schema shaped by years of product changes. The migration script maps these onto Stripe Products, Prices, Coupons, and tax behaviors. The common cases map fine; the long tail does not, a grandfathered "$9 forever" plan becomes the current $14 price, a stacked discount collapses to one coupon, a paused account migrates as active. Thousands of customers are individually small but collectively a mispriced cohort.

**Early warning signs.** Any customer whose post-migration recurring amount differs from their last actual charge without an intended price change. Coupons that fail to attach. A count of "unmapped" or "defaulted" records in the migration log that is greater than zero and waved through.

**Mitigation (targets likelihood).** Build a **per-customer price assertion**: for every account, assert `migrated_next_amount == last_charged_amount` (adjusting only for known, intended changes). Treat every mismatch as a blocking defect, not a rounding note. Enumerate the long-tail plan types explicitly rather than trusting a generic mapper.

**Leading indicator.** Number of accounts failing the amount assertion. Trend must hit zero before go-live.

**Contingency.** Maintain the old engine's price-per-customer table as the source of truth; on any post-cutover dispute, the old value wins and Stripe is corrected to match.

**Suggested owner.** Billing engineer, with product confirming intended price changes.

---

### R3: No realistic full-scale dry run (severity 20, critical)

**Mechanism.** With four engineers and a hard deadline, validation happens on a few hundred sample customers in Stripe's test mode. The behaviors that only appear at scale, API rate limiting during bulk create, real card declines, webhook backlogs, race conditions between migration and live traffic, are never exercised. They appear for the first time on the live cutover weekend, when there is no time to fix them.

**Early warning signs.** The test plan describes a "sample," not a "full production mirror." No load test against Stripe's bulk-create throughput. No rehearsal that includes real-cardinality webhook volume.

**Mitigation (targets likelihood and impact).** Run a **full-scale rehearsal**: all 40,000 customers migrated into a Stripe sandbox/test environment, timed end-to-end, with synthetic card declines injected. The rehearsal must reproduce the cutover runbook exactly, including the reconciliation diff (R1) and amount assertion (R2). Cutover is approved only after one clean rehearsal.

**Leading indicator.** Rehearsal completion time vs. the cutover-weekend window, plus the rehearsal's defect count.

**Contingency.** If a clean rehearsal is not achieved before the deadline, **do not cut over**: see R5; the fallback is to delay past the October spike rather than ship an unrehearsed migration.

**Suggested owner.** Tech lead.

---

### R4: Key-person and team-size concentration under a hard deadline (severity 16, high)

**Mechanism.** Only one of the four engineers truly understands the old engine's billing edge cases. The deadline allows no slack, so when that person is the bottleneck on R1/R2 reconciliation, or is simply out sick during cutover week, the work either stalls or proceeds without the one reviewer who would catch a quirk. Scope that was "tidy up later" gets shipped as-is.

**Early warning signs.** Reconciliation tasks consistently routed to one named person. No second engineer able to explain the grandfathered-plan logic. The schedule has zero buffer days before the October spike.

**Mitigation (targets likelihood and impact).** Deliberately **pair on the edge-case logic** so at least two engineers can validate the reconciliation, and front-load a written map of the old engine's known quirks. Protect a buffer by treating the migration as needing to finish a full cycle *before* October, not during it.

**Leading indicator.** Bus factor on the reconciliation work (target ≥ 2). Days of schedule buffer remaining (target > 0).

**Contingency.** If the key person is unavailable at cutover, invoke the delay decision rather than cutting over without them.

**Suggested owner.** Engineering manager.

---

### R5: No clean rollback once the old engine is decommissioned (severity 16, high)

**Mechanism.** The plan decommissions the old engine right after the cutover weekend. A defect that only shows up in week two, a mispriced cohort, a renewal-date class that fires later in the month, has nothing to fall back to. The team is forced to fix forward under live revenue pressure, which is how a contained billing bug becomes a mass mischarge.

**Early warning signs.** The runbook has a "decommission" step in the same window as cutover. No defined rollback procedure. No agreed observation period during which the old engine stays warm.

**Mitigation (targets impact).** **Do not decommission for at least one full renewal cycle.** Keep the old engine in warm standby with its data intact and a documented, rehearsed rollback path. Decommission only after one clean live renewal run proves Stripe is authoritative.

**Leading indicator.** Days the old engine remains in warm standby post-cutover (target ≥ one full cycle). Existence of a rehearsed rollback runbook (yes/no).

**Contingency.** If a defect class is found in the standby window, roll renewals back to the old engine for the affected cohort while Stripe is corrected.

**Suggested owner.** Tech lead.

---

### R6: Dunning and failed-payment recovery not migrated (severity 16, high): **the blind spot**

See Section 5 for the full write-up; carried here for completeness in the register.

**Mechanism.** Failed-payment retry schedules, grace periods, and the in-flight state of customers already in dunning are not part of the migration scope. At cutover, customers mid-recovery either get dropped (subscription cancelled prematurely) or double-dunned (both systems chase them).

**Mitigation.** Explicitly migrate dunning state and configure Stripe Smart Retries to match the old grace-period policy before cutover.

**Leading indicator.** Count of customers in an active dunning/retry state at cutover that lack a corresponding Stripe retry schedule (target zero).

**Suggested owner.** Billing engineer with support/finance input.

---

### R7: Webhook and downstream integration drift (severity 12, high)

**Mechanism.** Feature entitlements, seat provisioning, and accounting exports all listen to the old engine's events. After cutover they must listen to Stripe webhooks instead. If even one consumer is missed or its event shape differs, customers pay correctly but lose access, or revenue stops flowing to the books.

**Early warning signs.** No inventory of every system that consumes a billing event. No webhook signature/verification test. Accounting reconciliation not included in the cutover checklist.

**Mitigation (targets likelihood).** Build a complete **consumer inventory** of everything downstream of billing events and repoint each to Stripe webhooks with a verified handler before cutover; run an end-to-end test that a Stripe payment grants entitlement and reaches accounting.

**Leading indicator.** Number of downstream consumers not yet verified against Stripe events (target zero).

**Contingency.** Bridge layer that translates Stripe webhooks into the old event format for any consumer not yet migrated, retired once each is repointed.

**Suggested owner.** Backend/integrations engineer.

---

### R8: Stripe rate limits and throughput during bulk migration (severity 12, high)

**Mechanism.** Creating 40,000 customers, subscriptions, and payment methods in one weekend hits Stripe's API rate limits. The migration job throttles, retries, or partially completes; a naive retry creates duplicates (double subscriptions, double charges).

**Early warning signs.** No idempotency keys in the migration script. No measured throughput from the rehearsal (R3). Migration job has no resumable checkpointing.

**Mitigation (targets likelihood and impact).** Use **idempotency keys on every create call**, batch within Stripe's documented limits, and make the job resumable from a checkpoint. Confirm throughput in the full-scale rehearsal.

**Leading indicator.** Rehearsal throughput (records/min) vs. the weekend window; duplicate-object count after a forced mid-run retry (target zero).

**Contingency.** Duplicate-detection sweep post-migration that cancels any second subscription before its first charge.

**Suggested owner.** Tech lead.

---

### R9: Tax and compliance handling differs (severity 12, high)

**Mechanism.** The old engine computes VAT and sales tax with its own logic and nexus assumptions. Stripe Tax applies its own rules. Customers in tax jurisdictions are charged a different total than before, or tax is collected where it should not be, creating both customer disputes and a compliance exposure.

**Early warning signs.** Tax totals in the per-customer assertion (R2) differ from last actual charge. No sign-off from finance on the Stripe Tax configuration. Cross-border customers not explicitly tested.

**Mitigation (targets likelihood).** Include tax in the per-customer amount assertion and get **finance sign-off on the Stripe Tax config** against the current jurisdictions before cutover.

**Leading indicator.** Count of customers whose tax-inclusive total changed without an intended reason (target zero).

**Contingency.** Hold automatic collection for any jurisdiction failing the assertion until its config is corrected.

**Suggested owner.** Finance, with billing engineer.

---

## 4. (reserved)

*Detailed entries above cover every critical and high risk. Medium and low risks are summarized in the register (Section 2) and the "not worried about" list (Section 6).*

---

## 5. The blind spot

**Dunning and failed-payment recovery (R6).** Five of the six lenses fixated on the *successful-charge* path: did the right customer get charged the right amount on the right date. None gave first-class attention to the customers whose payments *fail*, and at 40,000 subscribers, a meaningful slice are always mid-recovery: card declined, in a grace period, on retry attempt two of three.

The in-house engine holds in-flight state for those customers, when the next retry fires, how long until the subscription is cancelled, whether a customer has been emailed. That state is not a row that maps cleanly to a Stripe object; it is *process* state, and it is the easiest thing to forget in a migration scoped around "move the subscriptions." At cutover the failure splits two ways: customers mid-dunning get dropped (Stripe sees no active recovery and the old engine is gone, so the subscription lapses and a paying customer churns silently), or they get double-dunned (Stripe starts its own Smart Retry while residual old-engine emails still go out, so the customer is chased twice and loses trust).

This matters because it is invisible to the obvious tests. A reconciliation that checks "is everyone charged correctly" passes, these customers were *correctly not charged yet*. The defect only shows as elevated involuntary churn or a wave of "why am I being dunned twice" support tickets weeks later, exactly when the team has declared victory. It scores severity 16 (high) and deserves explicit scope: migrate dunning state, map the grace-period policy onto Stripe Smart Retries, and verify zero customers enter the new system with an orphaned recovery state.

---

## 6. What this pre-mortem is not worried about

- **A Stripe outage during the cutover weekend (R13).** Impact would be severe, but Stripe's billing infrastructure reliability makes a full outage in the specific window low-likelihood; the warm-standby rollback (R5) covers it anyway. Watch the status page, do not plan around it.
- **Stripe fees eroding margin (R11).** Real but slow and reversible; this is a finance-planning question, not a *zero-billing-interruption* failure. It does not belong in the critical path.
- **Customers reacting to changed receipt/email branding (R10).** Worth a heads-up email and template review, but a cosmetic change does not meet the definition of failure (wrong or missing charge). Kept at medium.
- **PCI / card-data handoff (R12).** Genuinely sensitive, but the standard path (Stripe-hosted card collection or a PAN import via Stripe's documented secure process, never card data touching the team's servers) is well-trodden; the risk is low *provided the team does not invent its own handoff*. Flagged so it is not improvised.
- **Choosing Stripe at all.** Out of scope. This pre-mortem stress-tests the *migration*, not the vendor decision.

---

## 7. Caveats

- A pre-mortem surfaces *plausible* failures, not certainties. Every likelihood and impact here is structured judgment, not measured data; the scores order attention, they do not predict outcomes.
- The analysis is only as good as the definition of failure it was given. Here that definition, *any customer charged wrong or not at all*, is deliberately strict, which is why so much weight lands on reconciliation and the irreversibility of the big-bang cutover. A looser definition would reshuffle the register.
- It will not catch a true unknown unknown. The blind-spot pass widens coverage but cannot guarantee completeness.
- Cross-lens agreement (the right-most register column) is a severity signal, not proof; three lenses converging on R1 means it is hard to miss, not that it is certain.
- Use this to decide **what to watch and what to harden**: the leading indicators are the operational output, not as a verdict on whether to proceed. On balance the plan is defensible *if* the cutover is de-risked: a full-scale rehearsal (R3), a shadow billing cycle (R1), per-customer amount assertions (R2), and no decommission until one clean live renewal (R5). The single biggest structural improvement would be to convert the single-weekend big-bang into a phased migration by cohort, so the first failure touches hundreds of customers, not all 40,000.
- All figures here are illustrative for documentation purposes and were not researched.
