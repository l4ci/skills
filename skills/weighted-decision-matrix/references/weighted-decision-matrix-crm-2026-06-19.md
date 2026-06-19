# Weighted decision matrix: CRM selection

> _Illustrative example output for the `weighted-decision-matrix` skill. This CRM evaluation is fictional; every figure, price, and capability claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Decision:** Which CRM to adopt for a 12-person sales team.
- **Options:** Salesforce (Sales Cloud), HubSpot (Sales Hub), Pipedrive.
- **Date:** 2026-06-19
- **Framework:** Weighted scoring model. Criteria and weights were fixed *before* any option was scored; each option was scored independently on a 1-to-5 scale, then ranked by weighted total, then stress-tested by varying the weights. The matrix informs the choice; it does not make it.

## Calibrated criteria, weights, and scale

Weights (set from the decision-maker's stated priorities, sum to 100%) and the one-line definition that anchors each criterion:

| Criterion | Weight | What it means (scored 1–5) |
|---|---|---|
| Total cost of ownership | 30% | All-in annual cost for 12 seats: licences, required add-ons, onboarding, admin time. **5** = comfortably under the $40k ceiling; **1** = breaks the budget. |
| Ease of adoption | 25% | How fast a non-technical sales team reaches daily fluency without a dedicated admin. **5** = self-serve in days; **1** = needs paid consultants and months. |
| Integration with our stack | 20% | Native, no-glue integration with Gmail and Slack. **5** = first-class native both; **1** = manual export or paid third-party connector. |
| Reporting depth | 15% | Pipeline analytics, custom dashboards, forecasting. **5** = deep custom reporting out of the box; **1** = basic lists only. |
| Scalability | 10% | Headroom to grow past 12 seats and add teams/process without replatforming. **5** = scales to hundreds of seats cleanly; **1** = outgrown within a year. |

**Scale:** 1-to-5, used for every cell. No option was dropped at calibration: all three quote a 12-seat plan that *can* be configured under $40k/year, so none failed the hard budget constraint outright (though Salesforce only clears it on its mid tier; see its detail).

---

## 1. Verdict

**Adopt Pipedrive.** It tops the ranking at **4.30**, ahead of **HubSpot (3.90)** and well ahead of **Salesforce (3.15)**. The result is **robust but not unconditional**: Pipedrive wins on the two heaviest criteria (cost and ease of adoption, together 55% of the weight), and the sensitivity check shows it keeps the lead across every plausible reweighting *except* one, if reporting depth and scalability together climb above roughly 40% of the decision (they sit at 25% now), HubSpot overtakes it. So the verdict reduces to a sharp question: **is this a "get a lean team selling fast and cheap" decision, or a "build the analytics-and-scale backbone for the next five years" decision?** On the priorities as weighted, it is the former, and Pipedrive wins.

Salesforce is not a close call, it ranks third under every weighting tested, but it is the only option that wins outright on reporting and scalability, which is why it would return to contention if those weights were much higher (or if the seat count were heading for the hundreds).

---

## 2. The scored matrix

Criteria as rows (with weight), options as columns, every cell scored 1–5, weighted total at the bottom.

| Criterion | Weight | Salesforce | HubSpot | Pipedrive |
|---|---|---|---|---|
| Total cost of ownership | 30% | 2 | 3 | 5 |
| Ease of adoption | 25% | 2 | 4 | 5 |
| Integration with our stack | 20% | 4 | 5 | 4 |
| Reporting depth | 15% | 5 | 4 | 3 |
| Scalability | 10% | 5 | 4 | 3 |
| **Weighted total** | **100%** | **3.15** | **3.90** | **4.30** |
| **Rank** | | **3** | **2** | **1** |

Arithmetic:
- **Salesforce:** 0.30(2) + 0.25(2) + 0.20(4) + 0.15(5) + 0.10(5) = 0.60 + 0.50 + 0.80 + 0.75 + 0.50 = **3.15**
- **HubSpot:** 0.30(3) + 0.25(4) + 0.20(5) + 0.15(4) + 0.10(4) = 0.90 + 1.00 + 1.00 + 0.60 + 0.40 = **3.90**
- **Pipedrive:** 0.30(5) + 0.25(5) + 0.20(4) + 0.15(3) + 0.10(3) = 1.50 + 1.25 + 0.80 + 0.45 + 0.30 = **4.30**

---

## 3. Per-option detail

### Pipedrive: total 4.30, rank 1 (confidence: medium-high)

| Criterion | Score | Rationale |
|---|---|---|
| Total cost | 5 | ~$23k/year all-in for 12 seats on the Professional tier, including onboarding; the largest margin under the $40k ceiling. |
| Ease of adoption | 5 | Built for small sales teams; reps reach daily fluency in days with no dedicated admin. Lowest training overhead of the three. |
| Integration | 4 | Native Gmail sync is first-class; Slack is supported but via the marketplace app rather than as deeply native as HubSpot's. |
| Reporting depth | 3 | Solid pipeline and activity reports and basic forecasting; custom dashboards are shallower than the rivals. |
| Scalability | 3 | Comfortable to ~50 seats and a couple of teams; the ceiling for complex multi-team process and heavy automation is the lowest here. |

- **Strongest:** cost and ease of adoption: it wins both, the two heaviest criteria, outright.
- **Weakest:** reporting depth and scalability, the only two criteria where it scores below both rivals. These are exactly the axes that would matter most if the team were scaling fast or analytics-led.
- **Confidence medium-high.** Cost and adoption scores rest on the quoted 12-seat plan and the product's well-established fit for small teams. The reporting/scalability 3s are a judgment that they are *adequate-not-leading* for this team size, not a measured limit.

### HubSpot: total 3.90, rank 2 (confidence: high)

| Criterion | Score | Rationale |
|---|---|---|
| Total cost | 3 | ~$33k/year for 12 Sales Hub Professional seats plus required onboarding; clears the ceiling but with the least headroom of the qualifying options, and add-ons escalate fast. |
| Ease of adoption | 4 | Clean UI and strong in-app guidance; faster than Salesforce, a step behind Pipedrive, and tempting feature sprawl can slow a lean team. |
| Integration | 5 | Best-in-class native Gmail and Slack integration; no third-party connector needed. The clear winner on the integration criterion. |
| Reporting depth | 4 | Strong custom dashboards and forecasting out of the box; deepest reporting short of Salesforce. |
| Scalability | 4 | Scales well into the low hundreds of seats and across teams without replatforming. |

- **Strongest:** integration (the only 5 on that row): it is the one option that fully satisfies the Gmail+Slack must-have natively.
- **Weakest:** cost, its 3 is what keeps it 0.40 behind Pipedrive; it is roughly $10k/year more expensive for this team.
- **Confidence high.** Scores rest on published per-seat pricing and well-documented native integrations; little is assumed.

### Salesforce: total 3.15, rank 3 (confidence: high)

| Criterion | Score | Rationale |
|---|---|---|
| Total cost | 2 | ~$38–42k/year for 12 seats once required add-ons and admin time are counted; sits at or over the $40k ceiling and effectively assumes a part-time admin. |
| Ease of adoption | 2 | Powerful but heavy; a 12-person team realistically needs paid setup help and weeks of ramp. Steepest learning curve of the three. |
| Integration | 4 | Native Gmail and Slack (Salesforce owns Slack), strong but configuration-heavy to get clean for a small team. |
| Reporting depth | 5 | Deepest analytics, custom reports, and forecasting of any option: the reference 5 for this criterion. |
| Scalability | 5 | Effectively unlimited headroom; the safest choice if the team were heading for hundreds of seats. |

- **Strongest:** reporting depth and scalability: it wins both outright. This is a genuine, enterprise-grade strength.
- **Weakest:** cost and ease of adoption, it scores lowest on the two heaviest criteria, which is why it ranks third despite leading on reporting and scale.
- **Confidence high.** The pattern (expensive, heavy, deep, scalable) is well established; the cost score straddling the budget line is the main judgment call.

---

## 4. Sensitivity note

The base ranking is **Pipedrive 4.30 > HubSpot 3.90 > Salesforce 3.15**. The decisive separation is on the two heaviest criteria: Pipedrive's 5/5 on cost and adoption (55% of the weight) builds a lead that its weaker reporting/scalability cannot erase at the current weights.

**Varying the heaviest weight (cost, 30%).** Push cost down to 20% (and spread the freed 10 points across reporting and scalability): Pipedrive 4.05, HubSpot 3.95, Salesforce 3.45, Pipedrive still leads, but the gap narrows to 0.10, effectively a tie with HubSpot. Push cost *up* to 40%: Pipedrive widens to ~4.55 and the lead is decisive. So a cost-conscious decision-maker only strengthens the verdict; a cost-indifferent one brings HubSpot level.

**The flip case, analytics/scale priority.** The only reweighting that overturns Pipedrive is loading the reporting + scalability pair. At the current 25% combined they are second-order. **Break-even: Pipedrive and HubSpot swap once reporting + scalability together exceed roughly 40% of the decision** (e.g. reporting 25%, scalability 15%, with cost cut to 20% and adoption to 20%): HubSpot ~3.95 vs Pipedrive ~3.80. Past that point Salesforce also climbs sharply, at reporting 30% / scalability 20% it reaches ~3.9 and contends. In other words: **HubSpot wins the moment analytics-and-scale outweighs cost-and-speed; Salesforce only wins if they dominate.**

**Decisive criteria:** total cost and ease of adoption separate Pipedrive from the field; reporting depth and scalability are the only criteria on which the ranking can be flipped. Integration, where HubSpot leads, is too evenly scored (4/5/4) to move the result on its own.

**Verdict on robustness:** the winner is **robust to cost reweighting** (the most likely place a small business would push) but **fragile to a large reporting/scalability reweighting**. Pipedrive vs HubSpot is closer than the 0.40 gap suggests once you stop trusting the cost weight; Pipedrive vs Salesforce is not close under any tested weighting.

---

## 5. Recommendation

**Adopt Pipedrive**, on the priorities as weighted: a 12-person team with a $40k ceiling that needs people selling quickly, where cost and time-to-fluency outrank deep analytics. It wins the two criteria that carry the most weight and clears the budget with the most room, and it satisfies the Gmail+Slack must-have (native Gmail, marketplace Slack) well enough to not fail the hard constraint.

**Take HubSpot instead if any of these is true:**
- Native Slack integration is a hard requirement rather than a nice-to-have (HubSpot is the only outright 5 there).
- Reporting depth and scalability together are worth more than ~40% of the decision, i.e. you are buying the analytics-and-growth backbone, not just a deal tracker. This is the single reweighting that flips the result.
- The team is expected to roughly double within a year, making Pipedrive's lower scalability ceiling a near-term constraint.

**What would change the recommendation:**
- **A reweight** lifting reporting + scalability past ~40% → HubSpot. Lifting them to dominate → Salesforce.
- **A missing criterion.** This matrix has no row for *vendor lock-in / data portability*, *AI/automation features*, or *customer support quality*. If any of those is decisive for you, add it before trusting the ranking, the arithmetic can only weigh what is in the table.
- **A hard constraint** not captured here (e.g. a mandated security certification only one vendor holds) legitimately overrides the score.

---

## 6. Caveats

- **Scores are judgment anchored to a stated scale, not measurement.** A cell is "this vendor, on this criterion, is roughly a 4 against our anchors," not a benchmarked figure.
- **The Pipedrive–HubSpot gap is real but not large.** 4.30 vs 3.90 separates them, but it inverts under a credible reweighting; treat it as "Pipedrive on cost-and-speed priorities, HubSpot on analytics-and-scale priorities," not as a decisive numeric win.
- **Weights encode whose priorities the decision serves.** Cost at 30% and adoption at 25% reflect a budget-conscious small team. A different decision-maker (a VP of Sales building for scale) would legitimately weight differently and could get a different winner, that is disclosed in the sensitivity section, not hidden.
- **An omitted criterion is invisible.** Lock-in, AI features, and support are not scored; if one matters, the clean arithmetic above is answering an incomplete question.
- **The matrix informs the call; it does not make it.** A hard requirement (native Slack, a security cert, a mandated integration) or a strategic must-do can rightly override the top score.
- **All figures here are illustrative for documentation purposes and were not researched.**
