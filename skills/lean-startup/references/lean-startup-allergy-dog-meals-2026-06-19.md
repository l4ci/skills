# Lean Startup Experiment: Vet-Approved Meal Plans for Allergy-Prone Dogs

> _Illustrative example output for the `lean-startup` skill. This venture is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Idea:** A subscription app delivering vet-approved, rotation-based meal plans for dogs with food allergies.
- **Customer:** First-time owners of allergy-prone breeds (e.g. French Bulldogs, Labradors, Golden Retrievers) whose dog has itching, ear infections, or GI flare-ups they suspect are food-driven.
- **Date:** 2026-06-19
- **Context:** Pre-launch solo founder. Nothing built but a logo. Budget ~$3,000 and three weekends to test. No product, no list, no customers.

---

## 1. Leap-of-faith assumptions

What must be true for this venture to work. Each is written to be falsifiable.

| # | Assumption | Type |
|---|---|---|
| A1 | First-time owners of allergy-prone dogs **recognize** food allergy as their problem and are actively looking for a solution (not just living with the symptoms). | Value (problem) |
| A2 | These owners will **pay a subscription** (~$45–70/mo) for a vet-approved plan rather than DIY an elimination diet or buy off-the-shelf "limited ingredient" kibble. | **Value hypothesis** |
| A3 | A meal *plan* (guidance + curated ingredient/product list) delivers enough value on its own, or owners need the **food physically delivered** for the plan to matter. | Value (solution shape) |
| A4 | "Vet-approved" is **credible and operable** at a price point that works: a real vet will sign off on plans at a cost that fits a $45–70 subscription. | Value (supply/trust) |
| A5 | New customers can be **acquired profitably** through breed-specific communities, vet referrals, or paid social at a CAC well below lifetime value. | **Growth hypothesis** |
| A6 | Subscribers **stay** long enough to recoup CAC: once symptoms improve, they don't churn back to cheaper kibble. | Growth (retention) |

The two primary leap-of-faith assumptions are **A2 (value)** and **A5 (growth)**. The rest are the scaffolding they rest on.

---

## 2. Riskiest assumption

**Chosen to test first: A2: owners will pay a subscription for a vet-approved allergy meal plan.**

### Why it beat the others

Four analyst lenses were run in parallel over the assumption set; their ranked verdicts reconciled to A2.

| Lens | Top pick | Reasoning (condensed) |
|---|---|---|
| Most uncertain | A2 | Zero evidence either way. The founder has never charged anyone. Symptom severity ≠ willingness to open a wallet for *this* form factor. |
| Most fatal if false | A2 / A5 (tie) | If owners won't pay, nothing downstream matters: no retention, no growth, no vet supply to worry about. A5 is equally fatal but is *downstream*: you can't measure CAC payback before you know there's a sale to be had. |
| Hidden sub-assumptions | A2 | A2 silently assumes (a) the problem is felt acutely, (b) DIY/kibble are seen as inadequate, and (c) "vet-approved" justifies a premium. A passing payment test partially validates all three at once. |
| What a skeptical investor attacks | A2 | "Pet owners *say* they'd do anything for their dog, then buy the $1.50/lb bag. Show me money changing hands before symptoms even improve." |

**Reconciliation.** A5 (growth) is genuinely co-fatal, but it is **sequenced after** A2: you cannot compute CAC-to-payback for a product no one has agreed to buy. A1 (problem awareness) and A4 (vet credibility) are real but cheaper to retire and partly fold into a payment test. **A2 is both the most uncertain and the most fatal testable-now assumption.** It goes first.

A trap avoided: the *easy* test here is "do people click and join a waitlist?": that measures curiosity, not willingness to pay. The riskiest-first discipline forces a money test, not an interest test.

---

## 3. Experiment design

### The MVP

A **smoke-test landing page + pre-sale**, not a product. No app, no kitchen, no logistics.

- One landing page describing the plan, the "vet-approved" promise, and three breed-specific examples.
- A single, real **pre-order button** at **$59/mo, charged today** (first month upfront, "founding owner" framing), via a Stripe checkout. The page states honestly that onboarding starts in ~3 weeks (gives the founder a Wizard-of-Oz window to fulfill the first plans by hand if anyone buys).
- Full refund offered to anyone who asks. The point is the *act of paying*, with a real card, not locking in revenue.

### Behavior observed

The specific behavior: **a visitor enters card details and completes a real $59 charge**: not an email signup, not a "notify me," not a survey "yes I'd pay." Money must move.

### Traffic source (kept honest)

~$600 of the budget into tightly targeted paid social and two breed-specific Facebook/Reddit communities (with mod permission), aimed only at owners describing allergy symptoms. Goal: **~400 qualified visitors** to the page over two weekends.

### Actionable metric + pre-committed threshold

**Metric:** paid pre-order conversion rate = completed $59 charges ÷ qualified visitors. (A cohort conversion metric tied directly to A2, not total visits, not signups, not "reach.")

| | Threshold (set **before** running) |
|---|---|
| **PASS** | **≥ 4%** of qualified visitors complete a real paid pre-order (≈16+ of 400). |
| **FAIL** | **< 1.5%** paid conversion. |
| **Ambiguous** | 1.5%–4%: treat as weak signal; redesign offer and re-run, do not greenlight. |

Rationale for the line: at $59/mo and a plausible CAC, 4%+ paid conversion from cold-but-qualified traffic indicates a real, monetizable pull. Below 1.5% indicates the problem isn't felt acutely enough to pay *this* way. A waitlist email is explicitly **rejected as a vanity metric**: it would rise reassuringly and prove nothing about A2.

---

## 4. Results and learning

> _Invented results, for illustration._

| Measure | Result |
|---|---|
| Qualified visitors | 418 |
| Email "notify me" signups | 96 (23%): the vanity number; ignored for the decision |
| **Completed $59 paid pre-orders** | **9** |
| **Paid conversion rate** | **9 / 418 = 2.2%** |
| Refund requests | 1 |

**Against the threshold: AMBIGUOUS (2.2%, between the 1.5% fail and 4% pass lines).**

### What was learned about A2

- People **will** pay: 9 strangers charged $59 on a card for a non-existent product. The willingness-to-pay is non-zero and real, which kills the harshest investor objection outright.
- But it's **not yet at the bar** for a subscription business. 2.2% is a weak pull, not a strong one.
- The richest signal came from the 9 buyers and a follow-up call with 6 of them: **all six wanted the food delivered, not a plan to shop themselves.** The plan-only framing was the friction. Several said versions of "I don't have time to source novel-protein ingredients, that's the whole reason I'd pay you."
- This is direct evidence on **A3**: the "guidance/meal-*plan*" form factor is weaker than "**done-for-you delivered food**." A2 didn't fail on price; it under-performed on **product shape**.

---

## 5. Decision: pivot or persevere

**Decision: PIVOT, a zoom-in / product pivot on the solution, keeping the customer and the problem.**

The pre-committed threshold was not met (2.2% < 4%), so "persevere on the current plan" is off the table by the rules set in advance. But the evidence isn't "no one will pay", it's "they'll pay for a *different shape* of the same thing." That is a textbook **zoom-in pivot**: the feature owners actually want (delivered food) becomes the whole product; the standalone "meal plan" recedes to onboarding.

- **Assumption that changes:** A3, the value sits in **done-for-you delivered allergy food**, not in a plan the owner executes.
- **What is kept (validated learning preserved):** the customer segment (first-time allergy-breed owners), the problem (food-driven symptoms), the price anchor (~$59 is not the blocker), and the proof that real money moves.

### Next hypothesis the next loop tests

> **A2′ (revised value hypothesis):** First-time allergy-breed owners will pre-pay ~$59/mo for **vet-approved allergy meals delivered to the door**, at ≥4% paid conversion from the same qualified traffic.

Next MVP: same landing page, reframed to "delivered vet-approved allergy meals," fulfilled **concierge / Wizard-of-Oz** by hand for the first cohort (founder personally sources and ships ~5–10 boxes). This retires A2′ and begins probing A4 (vet sign-off cost) on real orders. **A5 (growth) is still untested and remains the next major risk after A2′**: CAC-to-payback cannot be judged until the delivered offer clears its bar.

---

## 6. Loop log

| Loop | Hypothesis tested | Experiment | Result vs. threshold | Decision |
|---|---|---|---|---|
| 1 | **A2**: owners pay $59/mo for a vet-approved meal *plan* | Smoke-test landing page + real $59 pre-sale, 418 qualified visitors | 2.2% paid conversion (pass ≥4%, fail <1.5%) → **ambiguous/below bar** | **Pivot (zoom-in):** value is in delivered food, not a plan |
| 2 | **A2′**: owners pay $59/mo for vet-approved allergy meals *delivered* | (planned) Reframed page + Wizard-of-Oz hand-fulfilled first cohort |: |: |

---

## 7. Caveats

- **One experiment tests one assumption.** Loop 1 tested A2 (willingness to pay for the *plan* form factor): it did not validate growth (A5), retention (A6), vet-supply economics (A4), or unit economics. The venture is not validated; one corner of it was probed.
- **A passed test reduces risk; it does not prove success.** Even had A2 passed at 4%+, that would mean "people will pay," not "this is a business." Growth and retention remain the larger unknowns.
- **Learning is only valid because the metric was actionable and the threshold was pre-committed.** The 4%/1.5% lines were set before traffic ran, so 2.2% couldn't be rationalized into a "win." The 96 email signups (23%) were named a vanity metric in advance and excluded from the decision, without that discipline, this loop would have been mis-read as a success.
- **The pivot is a hypothesis, not a conclusion.** "Delivered beats plan" rests on 9 buyers and 6 calls, a strong directional signal, but Loop 2 must confirm it with money at the committed bar before any build.
- All figures here are illustrative for documentation purposes and were not researched.
