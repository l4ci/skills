# Value Proposition Canvas: PantryPilot

> _Illustrative example output for the `value-proposition-canvas` skill. PantryPilot is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Value proposition:** PantryPilot, a meal-planning app that auto-generates grocery lists from saved recipes and syncs them to delivery services.
- **Customer segment:** Dual-income parents of young kids who cook on weeknights and dislike planning.
- **Stage / context:** Early stage. 20 user interviews completed. The live decision: build the delivery-sync feature or pivot.
- **Date:** 2026-06-19
- **Scope note:** This canvas tests **problem-solution fit**: whether the value map addresses the profile on paper. It does not establish product-market fit (needs market evidence) or business-model fit (needs the Business Model Canvas).

---

## 1. Verdict

**Partial fit.** PantryPilot's core engine, auto-generating a grocery list from saved recipes, lands squarely on the segment's single most important job ("get a workable weeknight dinner on the table without spending the evening deciding") and on their two most severe pains (the daily "what's for dinner" decision tax and the mid-week scramble of a forgotten ingredient). That is a real problem-solution match on the items that matter most.

The **delivery-sync feature, the thing the team is deciding whether to build, does not sit on a top-ranked customer item.** It targets a mid-ranked pain (the chore of the grocery run) for a segment that, by the interviews, mostly already has a grocery routine that works and is price-sensitive about delivery fees. It is at risk of being effort poured into a pain the customer does not rank highest.

- **Strongest match:** recipe-to-list automation against the decision-fatigue job and pain. **Hit.**
- **Biggest miss:** the app does nothing for the segment's top *gain*, feeling like a competent, calm parent rather than a short-order cook, which no current feature produces.

**Fit level reached: problem-solution fit, partial.** On the planning half, strong. On the delivery-sync half, unproven and pointed at a lower-ranked item.

---

## 2. Customer Profile

Described from 20 interviews (early-stage, thin but directional evidence). The ranking is the spine of the report; the value map is judged against it.

### Customer Jobs (ranked by importance to the customer)

| Rank | Job | Type | Evidence | Fact / Assumption | Conf |
|---|---|---|---|---|---|
| 1 | Get a workable dinner on the table on a weeknight without spending the evening deciding what it is | Functional + Emotional | 18/20 interviews named the daily "what do we eat" decision as the worst part of the week | Fact | High |
| 2 | Feed the kids something they will actually eat and that isn't junk | Functional + Social | 15/20 mentioned the tension between healthy and "what the 4-year-old will tolerate" | Fact | High |
| 3 | Not run out of a needed ingredient mid-recipe | Functional | 12/20 described a recent "missing one thing" failure | Fact | Med |
| 4 | Keep the weekly food spend predictable | Functional (buyer-of-value) | 9/20 raised budget unprompted; sharper among the single-car households | Fact | Med |
| 5 | Spend less of the week on the grocery run itself | Functional | 7/20 found the shopping trip tedious; most had an existing routine they tolerated | Fact | Med |
| 6 | Feel like a capable parent, not a frazzled one | Emotional + Social | Surfaced indirectly ("I just want to feel on top of it") in ~10 interviews | Assumption | Med |

**Note on Job 1 vs Job 6:** the functional job (get dinner decided) and the emotional job (feel competent) are entangled: the interviews suggest the *emotional* relief is what they actually buy, but the functional task is what they can articulate. The value map currently serves the functional layer only.

### Pains (ranked by severity)

| Rank | Pain | Kind | Evidence | Fact / Assumption | Conf |
|---|---|---|---|---|---|
| 1 | Daily decision fatigue: the 5pm "what's for dinner" dread, every single day | Emotional / recurring | Named first by 18/20; described as "the worst 20 minutes of the day" | Fact | High |
| 2 | Mid-week ingredient gap: start cooking, discover a missing item, improvise or abandon | Functional | 12/20 had a recent instance; high frustration | Fact | Med |
| 3 | Wasted food and money from over-buying or buying without a plan | Functional / financial | 11/20 mentioned throwing out produce | Fact | Med |
| 4 | Repetitive menus: "we eat the same six things" guilt | Emotional / social | 10/20 expressed boredom and mild guilt | Fact | Med |
| 5 | The grocery run is a time-sink | Functional / ancillary | 7/20; but most had absorbed it into a routine, not acute | Fact | Med |
| 6 | Delivery fees feel like a tax for the price-sensitive | Financial | 6/20 had tried delivery and dropped it over cost | Fact | Med |

### Gains (ranked by relevance)

| Rank | Gain | Kind | Evidence | Fact / Assumption | Conf |
|---|---|---|---|---|---|
| 1 | The dinner decision is just *made for them*: they show up and cook | Desired | The most-wished-for outcome across interviews; "I just want to be told" | Fact | High |
| 2 | Quiet confidence that the week's meals are handled and healthy-ish | Desired / emotional | The competence gain behind Job 6; inferred, not stated outright | Assumption | Med |
| 3 | Reliable lists: what they need to buy is correct and complete | Expected | Treated as table stakes; absence would be a dealbreaker | Fact | High |
| 4 | Some variety without extra effort | Desired | 10/20 wanted "new but easy" | Fact | Med |
| 5 | Spend stays inside a rough budget | Expected | Raised by the budget-conscious subset | Fact | Med |
| 6 | Groceries arrive without a store trip | Nice-to-have | Appealing in the abstract, but ranked below cost concerns | Assumption | Low |

---

## 3. Value Map

The offering, each item tied to the profile item it is meant to serve. Built after the profile, mapped onto it.

### Products & Services

| Item | Targets (profile item) | Evidence | Fact / Assumption | Conf |
|---|---|---|---|---|
| Recipe save / library (save recipes from web, photos, manual entry) | Job 1, Job 4 (variety) | Built and in use by beta testers | Fact | High |
| Auto-generated, de-duplicated grocery list from selected recipes | Job 1, Job 3, Pain 2 | Core feature, working in beta | Fact | High |
| Weekly meal-plan view (assign recipes to days) | Job 1, Pain 1 | Built | Fact | High |
| Delivery-sync (push the list to Instacart/grocer carts) | Job 5, Pain 5 | **Not built: the decision under review** | Assumption | Low |

Essential to the proposition: the recipe library and the auto-list. The meal-plan view supports them. Delivery-sync is the contested, not-yet-essential add-on.

### Pain Relievers

| Reliever | Pain addressed | How | Fact / Assumption | Conf |
|---|---|---|---|---|
| One-tap "plan my week" from saved recipes | Pain 1 (decision fatigue) | Reduces the daily decision to a weekly one, then to zero on the night | Assumption (effect untested at scale) | Med |
| Consolidated, de-duplicated shopping list | Pain 2 (ingredient gap) | Eliminates the "forgot one thing" failure if the list is followed | Fact (works in beta) | Med |
| Quantity roll-up across recipes | Pain 3 (waste) | Reduces over-buying by buying to the plan | Assumption | Low |
| Delivery-sync auto-fills the cart | Pain 5 (grocery run time) | Removes manual cart entry | Assumption | Low |

### Gain Creators

| Creator | Gain produced | How | Fact / Assumption | Conf |
|---|---|---|---|---|
| "Plan my week" suggestion engine | Gain 1 (decision made for them) | Proposes a full week the user can accept as-is | Assumption (suggestion quality unproven) | Med |
| Accurate consolidated list | Gain 3 (reliable lists) | Delivers the expected gain | Fact | Med |
| Recipe discovery / rotation prompts | Gain 4 (variety without effort) | Surfaces new-but-easy recipes | Assumption | Low |
| Delivery hand-off | Gain 6 (no store trip) | Groceries arrive | Assumption | Low |

---

## 4. Fit Assessment

### Fit-check table (top customer items vs. the value map)

| Customer side (ranked) | Value side | Fit? |
|---|---|---|
| **Job 1**: dinner decided without an evening of deciding | "Plan my week" + meal-plan view + auto-list | **Hit** |
| **Job 2**: feed kids something they'll eat and isn't junk | *Nothing targets kid-acceptance or nutrition filtering* | **Miss** |
| **Job 3**: don't run out mid-recipe | Consolidated de-duplicated list | **Hit** |
| **Pain 1**: daily decision fatigue | One-tap plan-my-week | **Hit (effect still assumed)** |
| **Pain 2**: mid-week ingredient gap | Consolidated list | **Hit** |
| **Pain 3**: food/money waste | Quantity roll-up | **Partial** (assumed effect) |
| **Gain 1**: the decision is made for them | Suggestion engine | **Partial** (depends entirely on suggestion quality) |
| **Gain 2**: quiet confidence / feel competent | *Nothing produces this* | **Miss** |
| **Gain 3**: reliable lists | Accurate consolidated list | **Hit** |

### Top items the map misses

- **Job 2 / Gain 2: the kid-acceptance and competence layer.** The single biggest gap. Two top-three customer items (a top job and the #2 gain) have **no product, reliever, or creator** pointing at them. The app plans meals but is indifferent to whether the 4-year-old eats them or whether the parent feels capable. This is the gap to close, and it is more central than delivery-sync.
- **Gain 1 is only a partial hit** because it rides entirely on suggestion quality, which is unproven. A bad suggestion engine converts the strongest gain into a churn driver.

### Irrelevant relievers and creators (effort where the customer doesn't rank highly)

- **Delivery-sync (reliever + creator).** Targets Pain 5 (grocery-run time, ranked 5th) and Gain 6 (no store trip, ranked last, low confidence). It addresses a mid-to-low pain for a price-sensitive segment that dropped delivery over fees (Pain 6). **This is effort aimed below the waterline.** Per the framework: cut it or justify it. The decision the team is weighing, *build delivery-sync or pivot*, resolves toward **not building it now**: it is the canvas's clearest example of a feature chasing a lower-ranked item while two top items go unaddressed.
- **Recipe discovery / rotation prompts.** Targets Gain 4 (variety, ranked 4th). Reasonable, but secondary, not where the next build effort belongs.

---

## 5. Riskiest Assumptions to Test

Ranked by how badly a wrong answer breaks the fit, tied to the build-or-pivot decision.

1. **That the "plan my week" suggestion engine produces plans parents accept as-is.** (Assumption, Med confidence.) Gain 1 and Pain 1, the whole strong half of the fit, collapse if suggestions are mediocre. **Test first:** put the current engine in front of 8–10 of the interviewed parents for two real weeks; measure accept-as-is rate vs. heavy editing. This gates everything.
2. **That "feel like a competent parent" (Gain 2 / Job 6) is what they actually buy.** (Assumption, Med.) If true, the roadmap should pivot toward the competence/kid-acceptance layer, the current miss, not delivery. **Test:** structured re-interviews probing the emotional job directly; watch whether retention tracks "felt in control" more than "saved time."
3. **That delivery-sync is wanted enough to justify the build.** (Assumption, Low.) The interviews already lean *no* (price sensitivity, existing routines). **Test:** a fake-door / concept test before any engineering, if it under-clicks, the pivot is decided cheaply.

**Decision implication:** the canvas points to **pivot the next build away from delivery-sync and toward Job 2 / Gain 2** (kid-acceptance, nutrition filtering, the competence layer), after validating the suggestion engine (Assumption 1). Delivery-sync should be a fake-door test, not a build.

---

## 6. Caveats

- The canvas tests **problem-solution fit on paper**, not whether the market will respond. Product-market fit needs real in-market behavior; business-model fit needs the Business Model Canvas to test viability (delivery margins, suggestion-engine cost, willingness to pay). Neither is claimed here.
- The customer side rests on **20 early-stage interviews**: directional, not statistically grounded. The emotional items (Gain 2, Job 6) are inferred and marked as assumptions; they are the most consequential to validate.
- Assumptions marked as such are **untested**. The strong half of the fit (the planning engine) is itself partly assumed, its effect at scale is unproven.
- A good fit on this canvas is a **promising hypothesis, not a validated one**. The ranking is the customer's, evidenced where possible; treating any assumption here as a fact is how this canvas would mislead.
- All figures and quotes are illustrative for documentation purposes and were not researched.
