# RICE: Q3 Activation Backlog

> _Illustrative example output for the `rice-prioritization` skill. This backlog and company are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Goal (what Impact moves):** Lift **quarterly activations**: new users who complete their first project.
- **Planning horizon:** One quarter (Q3 2026).
- **Date:** 2026-06-19
- **Framework:** RICE = (Reach × Impact × Confidence) / Effort, from Intercom. A rate, not a total, it rewards value per unit of effort, so cheap wins can outrank large bets that are still worth making. The ranking is only as good as the calibration below.

### Calibration (locked before scoring)

| Dimension | Setting |
|---|---|
| **Reach window + source** | Users **per quarter** who hit the relevant step, from the signup-to-activation funnel analytics. Baseline funnel volume ≈ **10,000 signups/quarter**. |
| **Impact scale** | Per-user effect on first-project completion: 3 massive · 2 high · 1 medium · 0.5 low · 0.25 minimal. |
| **Confidence** | 100% solid data · 80% some data + judgment · 50% moonshot. Below 50% → validate, do not score. |
| **Effort unit** | **Person-months**, whole-team (product + design + eng), on a 6-person eng team. |

*Gate note:* **SSO/SAML is already committed** to an enterprise deal closing this quarter. It is scored for transparency but its place on the roadmap is fixed by the commitment, not by its RICE rank: see the Recommendation.

---

## 1. Verdict

Build the **in-app onboarding checklist first**: it is the clear winner, reaching nearly the entire signup cohort with a direct, evidenced lift on first-project completion at low cost, and its lead is **robust** to plausible swings in Confidence and Effort. **CSV bulk import** and **dark mode** follow as the next tier, but their order is a **close call** that flips on small Effort changes. **Mobile push, SSO, and usage-based billing** sit at the bottom on activation grounds. SSO ships regardless on its contractual commitment; mobile push and billing are **validate-before-committing** bets resting on 50% Confidence and should not consume Q3 build time until tested.

---

## 2. The RICE table

Sorted by score, highest first. Score = (Reach × Impact × Confidence) / Effort.

| Rank | Initiative | Reach (users/qtr) | Impact | Confidence | Effort (pm) | **Score** |
|---|---|---|---|---|---|---|
| 1 | In-app onboarding checklist | 10,000 | 1 | 80% | 1.5 | **5,333** |
| 2 | CSV bulk import | 2,500 | 1 | 80% | 1.0 | **2,000** |
| 3 | Dark mode | 8,000 | 0.25 | 80% | 1.0 | **1,600** |
| 4 | Mobile push notifications | 4,000 | 0.5 | 50% | 3.0 | **333** |
| 5 | SSO/SAML login *(committed)* | 600 | 1 | 100% | 2.0 | **300** |
| 6 | Usage-based billing tier | 1,200 | 0.5 | 50% | 4.0 | **75** |

---

## 3. Per-item detail

### 1. In-app onboarding checklist: score 5,333 (rank 1)

- **Reach: 10,000/qtr.** Every new signup sees the checklist; it sits on the main funnel path. Source: full signup volume from funnel analytics.
- **Impact, 1 (medium).** Funnel data shows the largest single drop-off is between signup and first-project start. A guided checklist targets exactly this step; medium rather than high because guidance nudges but does not guarantee completion.
- **Confidence, 80%.** Strong directional evidence (the drop-off is measured), but the size of the lift is judgment, no prior checklist to benchmark against in-product.
- **Effort, 1.5 pm.** Frontend checklist component, event wiring to existing funnel steps, copy. No backend or data-model change.
- **Biggest uncertainty:** Impact size. Could be high (2) if the drop-off is pure friction, or low (0.5) if users stall on intent, not confusion. Either way it stays rank 1 (see sensitivity).
- **Flag:** None. Highest-confidence high-reach item on the list.

### 2. CSV bulk import: score 2,000 (rank 2)

- **Reach, 2,500/qtr.** Subset of signups arriving with existing data to migrate (teams switching tools). Source: funnel segment + sales-qualified import requests.
- **Impact, 1 (medium).** For a user with data to bring, the first project *is* the import; removing manual entry directly unblocks activation for that segment.
- **Confidence, 80%.** Support tickets and lost-deal notes name manual entry as a blocker; the count of affected users is estimated, not exact.
- **Effort, 1.0 pm.** Parser, column-mapping UI, validation. Bounded, well-understood work.
- **Biggest uncertainty:** Reach. If "users with data to migrate" is closer to 4,000, this pulls level with the checklist's tier; if 1,500, it slips behind dark mode.
- **Flag:** None.

### 3. Dark mode: score 1,600 (rank 3)

- **Reach, 8,000/qtr.** Most active users would encounter the setting. Source: estimate from share of sessions on devices/hours where dark mode is requested.
- **Impact, 0.25 (minimal).** A satisfaction and retention feature, not an activation driver. It barely touches first-project completion, the minimal multiplier is doing honest work here.
- **Confidence, 80%.** High confidence it ships cleanly and is wanted; the activation impact is low *and* well-understood to be low.
- **Effort, 1.0 pm.** Theming tokens already exist; mostly a styling pass.
- **Biggest uncertainty:** Impact relevance to *this* goal. Against a retention goal it would rank far higher; against activation it is near the floor. Its rank here is high mostly on cheap, broad reach.
- **Flag:** None, but note its rank is an artifact of low Effort × wide Reach, not of activation value. See caveats.

### 4. Mobile push notifications: score 333 (rank 4)

- **Reach, 4,000/qtr.** Signups on mobile or who install the app. Source: platform-mix estimate; soft.
- **Impact, 0.5 (low).** Re-engagement nudges can pull stalled users back to finish a first project, but the effect on *initial* activation is indirect.
- **Confidence, 50% (moonshot).** No in-product push data; lift is assumed from category norms, not measured here.
- **Effort, 3.0 pm.** Push infrastructure, device-token handling, opt-in flow, per-platform work.
- **Biggest uncertainty:** Confidence, sits right at the 50% floor. The whole score rests on an unvalidated re-engagement assumption.
- **Flag:** **Validate before committing.** Cheapest test: a lightweight email/in-app nudge to stalled signups to measure whether *any* re-engagement channel lifts completion before paying for push infrastructure.

### 5. SSO/SAML login: score 300 (rank 5, committed)

- **Reach, 600/qtr.** Users behind enterprise SSO. Small relative to the self-serve funnel. Source: seat count on the pending deal + existing enterprise accounts.
- **Impact, 1 (medium).** For those users, SSO is a hard gate to even reaching first project; medium on activation for the segment it touches.
- **Confidence, 100%.** Scope is fully specified by the contract; the requirement and the user count are known.
- **Effort, 2.0 pm.** SAML integration, provisioning, testing against the customer's IdP.
- **Biggest uncertainty:** None material, the scope is contractually pinned. Its low *RICE rank* simply reflects narrow activation reach, not low value.
- **Flag:** **Committed.** Builds this quarter regardless of rank; the deal closing depends on it. RICE does not get a vote here.

### 6. Usage-based billing tier: score 75 (rank 6)

- **Reach, 1,200/qtr.** Users who would hit a usage threshold in-quarter. Source: estimate from current usage distribution.
- **Impact, 0.5 (low).** A monetization lever, not an activation one; touches first-project completion only weakly, if at all.
- **Confidence, 50% (moonshot).** Revenue intuition, no pricing-test data; effect on activation is largely assumed.
- **Effort, 4.0 pm.** Metering, billing-system changes, plan migration, edge cases. The heaviest item on the list.
- **Biggest uncertainty:** Goal fit. Against a *revenue* goal this could be a top item; against *activation* it is mis-aimed and the score says so.
- **Flag:** **Validate before committing**: and reconsider against the right goal. If the real objective is revenue, re-score it on that goal rather than activation.

---

## 4. Sensitivity note

Confidence (a multiplier that can halve a score) and Effort (a denominator that can double one) swing the ranking hardest. Varying both within plausible ranges:

- **Rank 1 is robust.** The onboarding checklist leads by ~2.7× over rank 2. Even at its pessimistic case (Impact 0.5, Effort 2.0 pm) it scores ~2,000, still tied for the top tier. No plausible swing dislodges it. **Commit to it.**
- **Ranks 2–3 are a fragile, near-tie pair.** Import (2,000) vs. dark mode (1,600) are 25% apart and both rest on soft Reach estimates. Import's Reach moving from 2,500 to ~3,200, *or* dark mode's Effort slipping from 1.0 to 1.3 pm, locks import ahead comfortably; the reverse swaps them. **Treat 2 and 3 as one block to sequence by dependency and team fit, not by the 400-point gap.**
- **The bottom three are stable in their tier but built on sand.** Mobile push and billing both sit at 50% Confidence, their *scores* won't climb without new evidence, so no Effort revision rescues them. SSO's rank is fixed by reach, not fragility; its position is irrelevant because the commitment overrides it.
- **Effort is the lever to watch.** Import and dark mode are the two cheapest items; if either is underestimated (the most common bias), its score is inflated and the rank-2/3 call flips. Re-estimate both as if committing before sequencing them.

---

## 5. Recommendation

**Q3 roadmap order (activation goal, one-quarter horizon):**

1. **Onboarding checklist**: start here. Robust rank 1, direct hit on the largest funnel drop-off, low cost. The single highest-value activation move available.
2. **SSO/SAML, in parallel, on the contract clock.** Its RICE rank (5) is overridden by the committed deal. Slot it by the closing date, not the score; it consumes ~2 pm of the 6-person team regardless.
3. **CSV bulk import** *or* **dark mode**: the rank-2/3 block. Sequence by which is dependency-free and ready: import has the stronger activation case (medium vs. minimal Impact), so prefer it unless its Reach estimate proves soft. Dark mode is a cheap satisfaction win whose high RICE rank is an artifact of broad reach × low effort, *not* activation value, take it as a fast follow, not an activation bet.

**Validate before building (do not consume Q3 capacity yet):**
- **Mobile push**: run a cheap nudge test (email/in-app) to confirm re-engagement lifts completion at all before funding push infrastructure.
- **Usage-based billing**: re-score against a *revenue* goal; it is mis-aimed at activation. If revenue is the real objective, it belongs in a different prioritization pass.

**What would re-order the list:** a measured Reach for CSV import (settles the 2/3 block); any activation-lift data for push (could pull it out of the validate bucket); and an explicit second goal (revenue) that would relocate billing and likely dark mode.

---

## 6. Caveats

- **Every input is an estimate, not a measurement.** Reach figures are best guesses dressed as numbers; the precision of "10,000/qtr" is illusory. Confidence is the only thing absorbing that softness.
- **The score is a rate, and rates reward cheap wins.** Dark mode out-ranking SSO and billing reflects effort-efficiency, not strategic importance, a large, worthy bet can be starved by the formula. Read the rank, then sanity-check it against strategy.
- **Confidence guards against wishful thinking but cannot manufacture evidence.** The two 50% items are bets; their low scores are a prompt to go test, not a verdict that they are bad ideas.
- **An underestimated Effort silently inflates a score.** The rank-2/3 call hinges on 1.0 pm estimates being honest. If they creep, the order changes.
- **Near-ties are ties in sequence, not a mandate.** The 400-point gap between import and dark mode is noise; do not over-read it.
- **A commitment legitimately overrides the score.** SSO is the worked example of this: rank 5 by RICE, rank "this quarter, non-negotiable" by contract.
- All figures here are illustrative for documentation purposes and were not researched.
