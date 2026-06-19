# Analysis of Competing Hypotheses: Q2 Enterprise Churn Spike

> _Illustrative example output for the `analysis-of-competing-hypotheses` skill. The company, its churn data, and every figure, name, and claim below are fictional and invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Question:** What is the primary cause of the 40% jump in enterprise churn in Q2?
- **Role:** VP of Customer Success, who must decide where to put retention budget this quarter.
- **Date:** 2026-06-19
- **Method:** Heuer's Analysis of Competing Hypotheses, rank by fewest weighted inconsistencies (disconfirmation), not by most supporting evidence.

---

## 1. Bottom line

Across five hypotheses scored against eleven evidence items, the field ranks:

| Rank | Hypothesis | Inconsistency score | Relative likelihood |
|---|---|---|---|
| 1 | **H4: Onboarding/CS coverage gap** (the Q1 reorg thinned coverage on mid-tier enterprise accounts) | **2** | **~45%** |
| 2 | H1: Competitor price cut pulled price-sensitive accounts | 5 | ~22% |
| 3 | H2: The May 3 outage broke trust on already-shaky accounts | 6 | ~18% |
| 4 | H5: No single cause; churn is the lagged sum of small frictions | 7 | ~10% |
| 5 | H3: Product gap: a missing feature competitors shipped | 9 | ~5% |

**Headline confidence: moderate.** The leading hypothesis (H4) wins because the least evidence is *inconsistent* with it: not because it has the most checkmarks. But the verdict turns on two linchpin items (E6, E9); if either is wrong or mismeasured, H1 and H4 become a near-tie. The honest read for the VP: **put the marginal retention dollar on restoring CS coverage to the mid-tier segment, not on price-matching or an outage apology campaign, but instrument E6 and E9 before committing the full budget.**

---

## 2. The matrix

Evidence rows × hypothesis columns. **C** consistent, **I** inconsistent, **N/A** no bearing; doubled (**CC** / **II**) for strength. The bottom row is the weighted inconsistency tally (II = 2, I = 1, scaled by evidence credibility: high ×1.0, medium ×0.6, low ×0.3). Lowest tally = most likely.

| Evidence (type, weight) | H1 price | H2 outage | H3 product | H4 CS gap | H5 diffuse | Diagnostic? |
|---|---|---|---|---|---|---|
| **E1**: Competitor cut list price ~18% in April (report, high) | CC | N/A | C | N/A | C | yes |
| **E2**: Major outage May 3, 4h, status-page confirmed (fact, high) | N/A | CC | N/A | N/A | C | yes |
| **E3**: Exit surveys: "didn't feel supported / slow responses" is the top theme, 52% (observation, med) | I | C | I | CC | C | **yes: linchpin-adjacent** |
| **E4**: Exit surveys: only 11% cite price (observation, med) | II | N/A | N/A | C | C | yes |
| **E5**: Support-ticket backlog doubled Feb→Apr; median first-response 6h→19h (fact, high) | N/A | C | N/A | CC | C | yes |
| **E6**: Churn concentrated in mid-tier ($25–75k ARR) accounts; top-tier and SMB flat (fact, high) | I | I | I | CC | I | **yes: LINCHPIN** |
| **E7**: NPS unchanged until June (i.e. lagged the churn) (observation, med) | C | I | C | C | CC | yes |
| **E8**: No competitor shipped a notable feature in the window; roadmap parity held (report, med) | C | C | II | C | C | yes |
| **E9**: Q1 reorg reassigned CSMs; mid-tier book grew from ~30 to ~55 accounts per CSM (fact, high) | N/A | N/A | N/A | CC | C | **yes: LINCHPIN** |
| **E10**: Churned accounts were disproportionately month-to-month / up-for-renewal in Q2 (fact, med) | C | C | C | C | C | **no: consistent with all** |
| **E11**: No abnormal spike in product-bug tickets or feature-request volume (absence, med) | C | C | II | C | C | yes |
| **Weighted inconsistency score** | **5.0** | **6.0** | **9.0** | **2.0** | **7.0** | |

E10 is **non-diagnostic** (consistent with every hypothesis: renewal-window accounts churn under any cause) and is excluded from the tally though kept for context.

---

## 3. Why this ranking

ACH rejects hypotheses by what is *inconsistent* with them, not by counting support.

**H4, CS coverage gap (winner, score 2).** Almost nothing in the evidence contradicts it. The two items that drive its low score are positively *strongly* consistent: E9 (the reorg roughly doubled mid-tier CSM book size in Q1, immediately before the Q2 spike) and E6 (churn is concentrated in exactly the mid-tier segment that lost coverage, while top-tier, which kept dedicated CSMs, stayed flat). E3 (top exit theme is "didn't feel supported") and E5 (response times tripled) corroborate. Its only friction is E7 (NPS lagged), a mild inconsistency it shares with most hypotheses. H4 is not the hypothesis with the most C marks, it is the one the evidence repeatedly fails to disprove.

**H1, competitor price cut (score 5).** Rejected from the top spot by E4 (only 11% of churned accounts cite price, strongly inconsistent, II) and E6 (a pure price effect would hit SMB and price-sensitive top-tier too, not concentrate in mid-tier, inconsistent). The April price cut (E1) is real and consistent with H1, but "consistent" is cheap: it is also consistent with the diffuse hypothesis. The price cut is a *backdrop*, not the *driver*.

**H2, May 3 outage (score 6).** The outage is real (E2) and consistent. But H2 is sunk by timing and distribution: E6 (an outage hits all tiers equally, not just mid-tier) and E7 (an outage-driven exodus would show an NPS dip in May, not June). The outage plausibly *tipped* a few already-disengaged accounts but cannot carry a 40% jump.

**H5, diffuse / no single cause (score 7).** The "everything a little" story is consistent with almost everything (that is its weakness, not its strength, high consistency, low diagnosticity). It is pushed down by E6: a diffuse cause should produce diffuse churn across tiers, but the churn is sharply segment-concentrated. Concentration is the signature of a *specific* cause.

**H3, product/feature gap (score 9, rejected).** Strongly disconfirmed. E8 (no competitor shipped a notable feature; parity held, II), E11 (no abnormal feature-request or bug volume, II), and E3/E6 all point away from product. There is no evidentiary footprint of a product cause.

---

## 4. Linchpins and fragility

The conclusion is **less robust than the 2-vs-5 gap suggests**, because it leans on two high-weight items:

- **E6 (segment concentration of churn).** This single fact does the most work in the entire matrix: it is inconsistent with H1, H2, H3, and H5, and strongly consistent with H4. If E6 is wrong, e.g. the "mid-tier concentration" is an artifact of how renewal cohorts happened to fall in Q2 rather than a true segment effect, then H1 and H4 collapse toward a tie (H4 → ~4, H1 → ~4). **This is the item to verify first.**
- **E9 (reorg doubled mid-tier book size).** The causal hinge from "coverage thinned" to "this segment churned." If the book-size increase was smaller than reported, or pre-dated the coverage-quality drop, H4's mechanism weakens even if E6 holds.

**Deception / planted-evidence check:** none of the hard facts (E2, E5, E6, E9) come from a party with an incentive to mislead, they are internal operational data. The softest items are the exit surveys (E3, E4), which suffer ordinary self-report bias: churned buyers may rationalize ("support was bad") over admitting price sensitivity. We stress-tested by assuming E4 is understated and price is actually ~30% of true motivation: even then H1 only climbs to ~3.5, still behind H4, because E6's segment concentration is the binding constraint, not the exit-survey theme split. **A single deception does not flip the answer; a mismeasured E6 does.**

**Hypothesis-gap check:** one candidate was added during reconciliation and is worth flagging as a watch-item rather than a column, *"a specific large logo's internal mandate (M&A, budget freeze) cascaded to several of its business units counted as separate accounts."* If the 40% is driven by a handful of related logos rather than a segment-wide pattern, the entire framing changes. The account-level breakdown behind E6 should be inspected for this before acting.

---

## 5. Indicators to watch

Concrete future observations that would *change* the ranking, tripwires, not a one-time verdict:

- **Raises H1 (price):** churn begins appearing in SMB and top-tier, not just mid-tier; win/loss notes start citing the competitor's pricing; a price-match pilot measurably reduces save-rate loss. → reallocate toward commercial/pricing.
- **Raises H2 (outage):** a *second* incident produces an immediate, measurable churn bump in all tiers within weeks; June NPS damage traces specifically to reliability comments. → invest in reliability + proactive incident comms.
- **Raises H4 further (confirms winner):** restoring mid-tier CSM ratios (or a pooled-CS pilot) cuts the mid-tier churn rate within one renewal cycle; first-response time recovery (E5 reversing) tracks with retention. → this is the budget bet.
- **Raises H3 (product):** feature-request volume spikes on a specific capability; competitors ship a differentiator; exit theme shifts toward "missing X." → loop in product, not CS.
- **Raises the gap hypothesis (concentrated logos):** the E6 breakdown shows churn driven by <5 related parent accounts. → this is account management / a save play, not a segment program.

---

## 6. Gaps and confidence

- **Overall confidence: moderate.** H4 is the clear leader on inconsistency, but its margin over H1 is hostage to two linchpins (E6, E9). Verify those before committing the full retention budget; a one-week cohort analysis would firm or break the call.
- **Missing evidence:** (1) account-level churn breakdown to confirm E6 is a true segment effect and not a renewal-cohort or concentrated-logo artifact; (2) a controlled read on price sensitivity beyond self-report (E4), e.g. did churned accounts that received a retention discount actually stay; (3) CSM-level retention deltas to directly tie coverage ratio (E9) to churn (E6).
- **Too close to call:** H1 vs H4 *conditional on E6 being wrong*. As scored, they are clearly separated; the separation is only as solid as E6.
- **Decision implication for the VP:** the most likely cause is operational (coverage), not commercial (price) or technical (outage/product). The expected-value move is to **restore mid-tier CS coverage and response times**, instrument E6/E9 in parallel, and hold a small reserve to pivot to price-matching only if the SMB/top-tier churn indicator trips.

---

*All figures here are illustrative for documentation purposes and were not researched. ACH reports the whole field of hypotheses and the evidence that would change the verdict, it adjudicates what is most likely true given current evidence, not what is certain.*
