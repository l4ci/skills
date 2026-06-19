# Balanced Scorecard: Northwind Insurance (Personal Lines)

> _Illustrative example output for the `balanced-scorecard` skill. Northwind Insurance is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Organization / unit:** Northwind Insurance, Personal Lines division (auto and home), division level.
- **Strategy being translated:** Win on retention rather than new-business volume. Make renewals effortless and claims fast, so loyal low-risk customers stay and lifetime value rises.
- **Date:** 2026-06-19
- **Framework:** Kaplan & Norton Balanced Scorecard, four perspectives (Financial, Customer, Internal Process, Learning & Growth) wired bottom-up by a cause-effect strategy map, balancing leading drivers against lagging results.
- **Time horizon for targets:** 12 months. Already tracked: loss ratio, renewal rate. Not yet tracked: claims-cycle time, staff capability.

---

## 1. The strategy in one paragraph

Northwind Personal Lines is choosing **customer intimacy through retention** over a new-business arms race. The bet: acquiring a policyholder costs far more than keeping one, and the customers worth keeping are the loyal, low-risk renewers who quietly subsidise the book. The strategy wins by removing the two moments where good customers leave, a renewal that feels like a chore or a price shock, and a claim that drags. Make renewal effortless (proactive, pre-filled, fairly priced) and make claims fast (settled in days, not weeks), and low-risk customers stay longer, the book's average risk improves, acquisition spend falls per retained dollar, and lifetime value compounds. The scorecard must therefore measure not just whether retention held (lagging) but whether the two drivers, renewal friction and claims speed, and the capabilities under them are actually moving (leading).

---

## 2. Scorecard table

| Perspective | Objectives | Measures (L = leading / G = lagging) | Targets (12-month) | Initiatives |
|---|---|---|---|---|
| **Financial** | Grow lifetime value of the retained book; improve underwriting profit; shift the cost base from acquisition to retention | Customer lifetime value, avg (G); Combined operating ratio (G); Acquisition cost as % of premium (G/L) | CLV +12% (to ~$2,950); COR 96% → 93%; Acquisition cost 18% → 13% of premium | Reallocate marketing budget from prospecting to win-back/loyalty; LTV-based pricing model |
| **Customer** | Retain low-risk policyholders; make renewal effortless; make claims feel fast and fair | Renewal rate, low-risk segment (G); Renewal effort score / CES (L); Claims NPS (G); Net Promoter Score (G) | Low-risk renewal 84% → 90%; CES ≤ 2.0 (1–7, lower=easier); Claims NPS +25 → +45; NPS +18 → +35 | Proactive pre-filled renewal offers; transparent loyalty-priced renewals; claims status notifications |
| **Internal Process** | Cut claims-cycle time; remove renewal friction; price renewals to retain good risks | Claims-cycle time, FNOL→settlement (L); Straight-through renewal rate (L); Touchless-claims share (L) | Cycle time 14 → 6 days; STP renewals 35% → 70%; Touchless claims 20% → 45% | Automated claims triage & fast-track lane; renewal auto-population from policy data; loyalty-pricing rules engine |
| **Learning & Growth** | Build claims-handler capability & authority; equip staff with point-of-work data; align incentives to retention | Adjuster skill-coverage vs. need (L); Systems coverage: staff with claims data at point of work (L); Strategy-alignment / incentive-shift score (L); Adjuster retention (G) | Skill coverage 60% → 85%; Systems coverage 55% → 90%; Alignment score 3.1 → 4.2 (of 5); Adjuster retention 82% → 90% | Adjuster certification & raised settlement authority; unified claims/policy desktop; rebase bonuses on retention not volume |

---

## 3. Strategy map (read bottom-up)

```
                       FINANCIAL
            ┌──────────────────────────────┐
            │  ↑ Lifetime value of book     │
            │  ↑ Underwriting profit (COR)  │
            │  ↓ Acquisition cost % premium │
            └──────────────▲───────────────┘
                           │ produces
                        CUSTOMER
            ┌──────────────────────────────┐
            │  ↑ Low-risk renewal rate      │
            │  ↓ Renewal effort (CES)       │
            │  ↑ Claims NPS / overall NPS   │
            └──────────────▲───────────────┘
                           │ delivers
                    INTERNAL PROCESS
            ┌──────────────────────────────┐
            │  ↓ Claims-cycle time          │
            │  ↑ Straight-through renewals  │
            │  ↑ Touchless-claims share     │
            └──────────────▲───────────────┘
                           │ enables
                   LEARNING & GROWTH
            ┌──────────────────────────────┐
            │  ↑ Adjuster capability        │
            │  ↑ Point-of-work data coverage│
            │  ↑ Retention-aligned incentives│
            └──────────────────────────────┘
```

**The chain as explicit hypotheses (bottom-up):**

1. **L&G → Process.** *If* adjusters are certified and hold higher settlement authority, *and* they have policy + claims data on one desktop, *and* their bonuses reward retention not volume, *then* claims-cycle time falls, more claims go touchless, and renewals auto-populate without manual rework.
2. **Process → Customer.** *If* claims settle in 6 days instead of 14 and renewals arrive pre-filled and loyalty-priced, *then* renewal effort drops, claims feel fast and fair, and low-risk customers renew rather than shop.
3. **Customer → Financial.** *If* low-risk renewal climbs to 90% and NPS rises, *then* the retained book's lifetime value grows, the loss ratio improves (good risks stay), and the division spends less acquiring replacements: lifting underwriting profit and cutting acquisition cost as a share of premium.

Each arrow is a bet Northwind can test against evidence over the year. The map, not the KPI list, is the strategy.

---

## 4. Per-perspective detail

### 4.1 Financial

**Guiding question:** *"To succeed financially, how should we appear to our shareholders?"*

Northwind is a mature book, so the financial frame is margin, return, and cost discipline, not top-line growth. The strategy explicitly *forgoes* new-business volume, so a revenue-growth objective would contradict it; the financial story is that a retained, lower-risk book is more profitable per dollar than a churning one.

| Objective | Measures | Target | Rationale (line from strategy) |
|---|---|---|---|
| Grow lifetime value of the retained book | CLV, avg (G) | +12% to ~$2,950 | The whole strategy is an LTV bet: keeping low-risk renewers longer is the financial payoff. Enabled below by the Customer retention objective. |
| Improve underwriting profit | Combined operating ratio (G) | 96% → 93% | Retaining *low-risk* customers improves the book's loss ratio; faster claims also cut leakage and litigation cost. Paid off by Customer + Process. |
| Shift cost base acquisition → retention | Acquisition cost as % of premium (G/L) | 18% → 13% | If retention rises, fewer replacements must be bought; spend moves from prospecting to loyalty. Leading where it signals the budget reallocation is happening. |

**Initiatives:** reallocate marketing from prospecting to win-back/loyalty; build an LTV-based pricing model so renewal prices reflect a customer's full retained value, not a single year's rate.

**Confidence:** High on the objectives (they follow directly from the strategy). Medium on the CLV target: the +12% rests on an assumed retention-to-LTV elasticity that Northwind has not yet measured.

### 4.2 Customer

**Guiding question:** *"To achieve our vision, how should we appear to our customers?"*

The value proposition is **customer intimacy** for the low-risk segment: effortless renewal and fast, fair claims. The measures must track *that* choice, effort and claims experience, not product breadth or price-leadership, which belong to other strategies.

| Objective | Measures | Target | Rationale |
|---|---|---|---|
| Retain low-risk policyholders | Low-risk-segment renewal rate (G) | 84% → 90% | This is the strategy's headline outcome. Note: division-wide renewal rate is *already tracked* but is the wrong cut: it blends in the high-risk churn the strategy is happy to lose. Segment it. |
| Make renewal effortless | Renewal effort score / CES (L) | ≤ 2.0 (1–7, lower=easier) | "Effortless renewal" must be measured as felt effort, the leading driver of the renewal-rate lag. Enabled by straight-through renewals below. |
| Make claims feel fast and fair | Claims NPS (G); overall NPS (G) | Claims NPS +25 → +45; NPS +18 → +35 | A slow claim is the moment a loyal customer leaves; claims experience is the second retention driver. Enabled by claims-cycle time below. |

**Initiatives:** proactive, pre-filled renewal offers sent before the customer has to act; transparent loyalty pricing so renewers aren't punished relative to new joiners; real-time claims status notifications.

**Confidence:** High on the objectives. Medium on CES and Claims-NPS *targets*: Northwind does not yet collect either, so the starting points are estimates and the targets are directional until a baseline lands (see Caveats).

### 4.3 Internal Process

**Guiding question:** *"To satisfy our shareholders and customers, which business processes must we excel at?"*

Given the value proposition, two processes carry the strategy: **claims handling** and **renewal processing**. A third, **loyalty pricing**: sits across both. The reference framework warns against measuring only current operations; here the operations *are* the strategy, but the loyalty-pricing rules engine is the closest thing to an innovation-process objective and is included deliberately.

| Objective | Measures | Target | Rationale |
|---|---|---|---|
| Cut claims-cycle time | Cycle time, FNOL→settlement (L) | 14 → 6 days | The single biggest lever on the claims-experience objective above. *Not currently tracked*: instrumenting this is itself an initiative. |
| Remove renewal friction | Straight-through (touchless) renewal rate (L) | 35% → 70% | Friction the customer feels (CES) is produced here; auto-population is what makes renewal effortless. |
| Price renewals to retain good risks | Touchless-claims share (L) as a proxy for automation maturity; rules-engine coverage | Touchless claims 20% → 45% | Loyalty pricing is what lets a low-risk renewer be offered a fair price without manual underwriting: directly serves the Financial cost-shift and Customer retention. |

**Initiatives:** automated claims triage with a fast-track lane for low-complexity claims; renewal auto-population from existing policy data; a loyalty-pricing rules engine.

**Confidence:** High that these are the right processes. Low-to-medium on the cycle-time *baseline*: the 14-day figure is an estimate because the measure isn't instrumented yet; the 6-day target should be re-grounded once the baseline exists.

### 4.4 Learning & Growth

**Guiding question:** *"To achieve our vision, how will we sustain our ability to change and improve?"*

The foundation, and the perspective Northwind currently measures *not at all* ("nothing on staff capability"). Three groups: **people** (adjuster capability and retention), **systems** (claims data at point of work), **climate** (incentives aligned to retention rather than volume). These are the most leading measures on the board and the first that get cut, which is exactly why a retention strategy that skips them stalls.

| Objective | Measures | Target | Rationale |
|---|---|---|---|
| Build claims-handler capability & authority | Adjuster skill-coverage vs. need (L); adjuster retention (G) | Coverage 60% → 85%; retention 82% → 90% | Fast claims require adjusters who can settle without escalation; capability + authority is the root enabler of cycle-time. |
| Equip staff with point-of-work data | Systems coverage: % staff with claims+policy data on one desktop (L) | 55% → 90% | An adjuster toggling between systems is the hidden tax on cycle-time and on renewal auto-population. |
| Align incentives to retention | Strategy-alignment / incentive-shift score (L) | 3.1 → 4.2 (of 5) | If frontline bonuses still reward new-business volume, the strategy is contradicted at the point of contact. This is the climate objective. |

**Initiatives:** adjuster certification programme with raised settlement-authority tiers; a unified claims/policy desktop; rebase frontline bonuses on retention and claims-NPS rather than policy count.

**Confidence:** High on the objectives' relevance. Medium on targets: no baseline existed before this scorecard, so all four starting figures are first estimates to be confirmed by survey/audit in month one.

---

## 5. Balance and the vital few

**Leading vs. lagging mix.** The scorecard is deliberately front-loaded with leading drivers, because the strategy's whole point is to act *before* retention shows up in the financials:

- **Financial:** 0 leading / 3 lagging (results only, correct for this perspective).
- **Customer:** 1 leading (CES) / 3 lagging.
- **Internal Process:** 3 leading / 0 lagging.
- **Learning & Growth:** 3 leading / 1 lagging.

Net: **7 leading, 7 lagging.** The lagging measures cluster where they belong (Financial, Customer outcomes); the leading measures cluster in Process and L&G, where management still has leverage this quarter. This is the opposite of Northwind's status quo, which tracked only two lagging financial/outcome measures (loss ratio, renewal rate), a textbook rear-view-mirror scorecard.

**Measure count per perspective:** Financial 3, Customer 4, Internal Process 3, Learning & Growth 4, **14 total**, comfortably inside Kaplan & Norton's ~20 ceiling and the "vital few" discipline.

**What was pruned, and why:**

- *Division-wide renewal rate* (the existing metric), kept conceptually but **replaced** by the low-risk-segment cut. The blended rate rewards retaining high-risk churners the strategy wants to lose.
- *Quote-to-bind conversion, new-business count, market share*, cut. They measure the new-business volume game this strategy explicitly declines to play; leaving them on the board would pull the org back toward the old strategy.
- *Premium growth*, cut as a primary measure; a retention strategy can grow premium while shrinking policy count, so the raw figure would mislead.
- *Generic employee-satisfaction survey*, narrowed to adjuster retention + alignment score, the two staff measures that actually drive this strategy, rather than a catch-all engagement number.

---

## 6. Broken links and gaps

- **Loyalty pricing has a thin enabler below it.** "Price renewals to retain good risks" (Process) depends on an LTV-based pricing model (Financial initiative) and a rules engine, but **no Learning & Growth objective covers pricing/actuarial capability or the data to compute per-customer LTV.** Risk: the pricing objective floats with no capability driving it. *Implication: likely a missing L&G objective, "actuarial/data capability for customer-level LTV pricing."* Flag for the next cycle.
- **Adjuster retention (L&G, lagging) has no explicit payoff link drawn.** It enables capability, but its arrow into cycle-time is indirect (experienced adjusters settle faster). Keep it, but treat it as a second-order enabler, not a headline.
- **No customer-acquisition objective anywhere, and that is correct.** A reader expecting an acquisition measure should note its absence is intentional: the strategy chose retention over volume. The only acquisition-adjacent measure (acquisition cost % of premium) appears as a *cost* the strategy aims to shrink, not a growth target. No broken link; a deliberate exclusion.
- **Every Process and Customer driver traces cleanly upward.** No orphan process improvements (a faster claim → claims NPS → retention → LTV; touchless renewal → CES → retention → LTV). No process objective lacks a customer/financial payoff.

---

## 7. Caveats

- **The scorecard is only as sound as the strategy.** Northwind's strategy is unusually clear (a named value proposition, a named target segment, a stated way to win), so the objectives trace cleanly. Had it stayed "improve retention," half this map would be guesswork.
- **Three measures are not yet instrumented**: claims-cycle time, renewal CES, and all of Learning & Growth. Their baselines (14 days, CES ~3.5, ~55–60% coverage) are **estimates**, and their 12-month targets are directional until month-one measurement replaces the estimates. Treat the first quarter partly as a baselining quarter.
- **The map shows hypothesized cause and effect, not proven causation.** Each arrow, faster claims → higher retention → higher LTV, is a bet. The retention-to-LTV elasticity behind the +12% CLV target is assumed, not measured. Revisit the map as evidence accumulates; if cycle-time falls but retention doesn't follow, the hypothesis (not just the execution) is wrong.
- **Segment, don't blend.** The single highest-leverage methodological point: read renewal rate, CLV, and loss ratio on the *low-risk segment*, not division-wide. Blended figures will mask whether the strategy is working on the customers it targets.
- **All figures here are illustrative for documentation purposes and were not researched.**
