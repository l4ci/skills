# Key Assumptions Check: German Market Entry

> _Illustrative example output for the `key-assumptions-check` skill. This SaaS company and its expansion plan are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Subject:** A bootstrapped B2B SaaS plan to reach €2M ARR in Germany within 12 months by porting the US self-serve playbook.
- **Role:** The founders and the board, deciding whether to fund the expansion.
- **Date:** 2026-06-19
- **Context:** Bootstrapped (no outside runway buffer); the decision feeds a €600k hiring-and-marketing budget request to the board.

The claim under check, verbatim:

> "We'll hit €2M ARR in Germany within 12 months by porting our US self-serve playbook, because German SMBs have the same buying behavior and our main US rival won't follow us there for at least a year."

---

## 1. Bottom line

**The foundation is weak: the plan rests on three load-bearing assumptions that are each low-confidence and high-impact, and at least two of them are key uncertainties dressed up as premises.** The headline "€2M in 12 months" is not itself an assumption, it is the output of a stack of them. Strip the stack and the number has nothing holding it up.

The two assumptions that most threaten the conclusion if wrong:

1. **"German SMBs buy self-serve the way US SMBs do."** This is the keystone. The entire reason for porting the playbook unchanged is that the buyer is the same. If German SMBs prefer assisted/sales-led purchasing, longer evaluation, or invoiced billing over card-on-file, all common in the DACH market, the self-serve funnel underperforms and the playbook does not transfer. This is asserted, not evidenced.
2. **"The US rival won't follow for at least a year."** A timing bet on a competitor's choice, with no stated basis. If they enter in month 4 instead of month 13, the unit economics that justify the €600k change underneath the plan.

Of eleven assumptions surfaced, **three are solid, three are caveated, and five are unsupported**: and the unsupported five are exactly the ones carrying the conclusion. Recommend the board fund a **staged probe**, not the full €600k, until the keystone assumption is tested with real German pipeline.

---

## 2. Assumption register

Confidence (high/med/low) against impact-if-wrong. The cell that matters most is low-confidence + high-impact (the linchpin zone).

| # | Assumption (testable proposition) | Confidence | Basis | If wrong, impact | Class |
|---|---|---|---|---|---|
| A1 | German SMBs complete a self-serve purchase (card, no sales call) at conversion rates within ~20% of the US funnel | **low** | analogy to the US market; no German data | self-serve motion underperforms → core revenue path breaks (**high**) | **unsupported** |
| A2 | The main US rival does not launch a German GTM motion within the next 12 months | **low** | assertion; no signal cited | price/CAC pressure arrives mid-build → economics collapse (**high**) | **unsupported** |
| A3 | The existing US product is usable by German SMBs without localization beyond UI translation (no invoicing, no German-law data handling, no EUR/SEPA billing) | **low** | optimism; not validated | onboarding stalls at payment/legal steps (**high**) | **unsupported** |
| A4 | €2M ARR is reachable from a standing start in 12 months at the planned spend | **low** | back-solved from the goal, not bottom-up | the headline target itself is unfounded (**high**) | **unsupported** |
| A5 | €600k funds a full year of the German motion to the €2M milestone | **med** | internal budget model | underfunded mid-year; bootstrapped = no bridge (**high**) | **caveated** |
| A6 | Paid-acquisition CAC in Germany is comparable to the US (within ~30%) | **low** | assumed parity | marketing spend buys far less pipeline (**high**) | **unsupported** |
| A7 | German-market SaaS demand for this category exists at the assumed volume | **med** | category exists in US/UK; DACH adoption lags but is real | TAM thinner than modeled → ceiling below €2M (**med**) | **caveated** |
| A8 | The team can hire German-speaking GTM/support staff inside the 12-month window | **med** | recruiter conversations; tight but plausible | ramp delayed a quarter (**med**) | **caveated** |
| A9 | GDPR and German consumer/B2B contract law impose no blocking requirement the product can't meet | **high** | product already serves EU customers from the US | rework, not a blocker (**low**) | **solid** |
| A10 | The product is genuinely valued (US retention proves real demand for the core) | **high** | US net revenue retention track record | n/a: this one holds (**low**) | **solid** |
| A11 | The company's English-language brand carries no weight in Germany at launch (start from zero awareness) | **high** | reasonable default for a new market | already priced in; conservative (**low**) | **solid** |

---

## 3. Linchpins

The assumptions the conclusion hangs on. If one flips, does the plan survive in modified form, or collapse?

**L1: A1: German SMBs buy self-serve like US SMBs.** *Collapses.* This is the load-bearing wall. The plan's only stated mechanism is "port the playbook unchanged," and that mechanism is valid only if the buyer is the same. DACH SMB buying skews toward assisted sales, longer cycles, and invoice/SEPA billing more than the US, a well-known regional pattern the plan treats as absent. If A1 is false, the self-serve funnel doesn't just convert worse, the entire go-to-market model is the wrong one. **Confidence it holds: low.** This is the first thing to test, before any spend.

**L2, A2: the US rival stays out for ≥12 months.** *Collapses the economics, not the motion.* The plan can still run if the rival enters, but the CAC and pricing assumptions underneath the €2M target were set in a no-competition window. A mid-year entry compresses margins and lengthens payback exactly when the bootstrapped company has no bridge. **Confidence it holds: low**: it is a guess about an actor's choice with no cited signal.

**L3, A4: €2M is reachable in 12 months at this spend.** *Is the conclusion, restated.* A4 is not really a premise; it is the headline wearing a premise's clothes (see §5 reversal). It survives only if A1, A6, and A7 all hold. It has no independent support, it was back-solved from the goal. **Confidence it holds: low.**

A1 → A6 → A4 form a single dependency chain: same buyer ⇒ same acquisition cost ⇒ same revenue path. **The chain is only as strong as A1, and A1 is untested.**

---

## 4. Unsupported assumptions, with action

Each unsupported assumption is a task, not a verdict. The next step is to verify it, hedge it, or rework the plan without it.

- **A1 (keystone), German self-serve buying behavior.**
  *Verify:* Run a 6–8 week German-language landing-page + paid-traffic test before committing GTM headcount. Measure visit→signup→paid conversion against the US baseline. Interview 15–20 German SMB buyers on how they actually purchase tools in this category.
  *Hedge if unverifiable:* budget for an assisted/sales-assisted motion as the default, treat pure self-serve as the upside case.
  *Rework without it:* if German buying differs, the "port unchanged" plan is void, re-plan as a localized, possibly sales-led entry with a different target and timeline.

- **A2, rival's timing.**
  *Verify:* Check the rival's job postings (DACH/EU roles), domain/trademark filings, partner-channel chatter, and any EU pricing pages, cheap signals of an imminent move.
  *Hedge:* stress-test the model with the rival entering in month 4; if the plan only works in the no-competition case, it is fragile by construction.

- **A3, product readiness without localization.**
  *Verify:* Map the German onboarding path end-to-end (signup → billing → invoice → support) and find where it breaks today. EUR/SEPA billing and proper German VAT invoices are the usual stoppers.
  *Hedge:* scope a minimum-localization build into the budget rather than assuming UI translation suffices.

- **A4, €2M in 12 months.**
  *Rework:* rebuild the target bottom-up from the tested A1 conversion rate and the verified A6 CAC. A goal back-solved from ambition is not a forecast. Present the board a range, not a point.

- **A6, German CAC parity.**
  *Verify:* the same paid-traffic test that checks A1 yields a real German CAC. Until then, model with a CAC band (e.g. US ×1.0 to ×2.0) and show the €2M math at each end.

---

## 5. Caveats to carry

Conditions to staple to the caveated assumptions so the analysis travels with its own fine print:

- **A5, €600k is sufficient *only if* the motion is self-serve and CAC lands near the US figure.** If A1/A6 push toward an assisted motion or higher CAC, €600k under-funds the year, and there is no outside runway to bridge. The budget number is contingent on the very assumptions in question.
- **A7, DACH category demand is real *but lags*.** Plausible that the ceiling sits below €2M in year one even if everything else works; treat €2M as the top of a range, not the base case.
- **A8, hiring fits the window *only if* started immediately and the assisted-motion scenario doesn't suddenly require more headcount.** A localization-heavy pivot (A1 false) changes the hiring plan.

---

## 6. Indicators to monitor

Tripwires that an assumption is starting to break, watch these and re-run the check if one fires:

- **A1:** German signup→paid conversion running below ~60% of the US rate after the first 1,000 visits. → keystone wobbling; pause spend.
- **A2:** rival posts DACH GTM/sales roles, registers a `.de` domain, or publishes EUR pricing. → the no-competition window is closing.
- **A3:** support tickets or drop-off clustering at the billing/invoice step. → localization gap is live, not hypothetical.
- **A4/A6:** blended German CAC trending >1.5× the US figure by month 3. → the €2M math no longer closes at €600k.
- **A8:** key German-speaking GTM/support roles still open at month 3. → ramp slipping; revisit the 12-month timeline.

---

## 7. Caveats on this check

- KAC tests *assumptions*, it does not verify them. Every "unsupported" classification above is a flag to go get data, not a conclusion that the assumption is false.
- Confidence ratings are judgment, not measurement, made with no German-market retrieval in this illustrative run, which is itself the reason A1, A2, and A6 sit at low confidence rather than being resolved here.
- The register aims at near-exhaustiveness but the most dangerous assumption is the one no proposer surfaced. The completeness pass flagged one such candidate folded in as A11 (zero brand awareness at launch); the board should still ask "what are we treating as a fact that was never written down?"
- All figures here are illustrative for documentation purposes and were not researched.
