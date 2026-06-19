---
name: fermi-estimation
description: Use when the user needs a defensible quantitative estimate of something with no data at hand, and wants a reasoned order-of-magnitude answer rather than a blind guess or a refusal. Runs Fermi estimation: defines the target quantity precisely, decomposes it in parallel into a chain of sub-factors each estimable to within an order of magnitude, estimates each factor as a range with its basis, multiplies the chain and propagates the uncertainty, then cross-checks the result against independent decompositions and known bounds and names the factor that dominates the error. Triggers include "Fermi estimate", "back of the envelope", "order of magnitude", "ballpark", "how many / how much / how big roughly", "estimate the market size", "we don't have data but need a number".
---

# fermi-estimation

An agentic, parallel implementation of Fermi estimation, named for the physicist Enrico Fermi, who produced accurate order-of-magnitude answers to seemingly unanswerable questions ("how many piano tuners are there in Chicago?") with no data, by decomposing them into factors he could each estimate roughly. It rests on a statistical gift: when you break a quantity into a chain of independent estimated factors, the individual over- and under-estimates tend to cancel, so a product of rough guesses is far more accurate than a single rough guess at the whole. This defeats both the blind guess (a number from nowhere) and the refusal ("we can't estimate that, we have no data").

## When to use

The user needs a number and has little or no direct data: market sizing, capacity and load estimates, cost or effort ballparks, "how big could this be", "how many of X are there", feasibility sanity checks. Triggers: "Fermi estimate", "back-of-the-envelope", "order of magnitude", "ballpark this", "rough estimate", "how many / how much, roughly".

Reach for it when a rough-but-reasoned answer now beats a precise answer never, and when you want the estimate to be *auditable*: every assumption visible, so a reader can challenge any single factor rather than the opaque whole. It is the inside-view complement to [reference-class-forecasting](../reference-class-forecasting/): Fermi builds the estimate up from components; reference-class anchors it on how similar cases actually turned out. Running both and reconciling them is a strong cross-check. It also feeds a [weighted-decision-matrix](../weighted-decision-matrix/) when an option needs a quantified payoff.

Do **not** use it when precise data exists and is cheap to get (just get it), nor when the question is not really quantitative (use [analysis-of-competing-hypotheses](../analysis-of-competing-hypotheses/) for "which explanation", or [scenario-planning](../scenario-planning/) for "what futures").

## Inputs

- **QUANTITY** (required): the thing to estimate, stated with its units. If it is vague ("how big is the market"), sharpen it first: market for what product, which buyers, which geography, annual revenue or unit volume, what year. A Fermi estimate of a fuzzy target is worthless precision.
- **PRECISION NEEDED** (optional): how tight the answer must be to be useful: order of magnitude (the Fermi default), within 2-3×, or better. Drives how hard to work the decomposition. Defaults to order of magnitude.
- **KNOWN ANCHORS** (optional): any real numbers the user already has (a measured figure, a comparable, a published statistic). Used as anchors and as sanity bounds.

## Orchestration map

```
Stage 1  Frame the quantity      ── 1 agent ── pin down exactly what, in what units, and the estimation approach
Stage 2  Decompose               ── N decomposer subagents IN PARALLEL ── independent factor breakdowns; pick the cleanest
Stage 3  Estimate each factor    ── 1 subagent PER LEAF FACTOR IN PARALLEL ── low / best / high, with the basis
Stage 4  Combine + propagate     ── 1 agent, needs all factors ── compute the chain; produce a point and an uncertainty band
Stage 5  Cross-check + bound     ── 3 critic subagents IN PARALLEL ── second path; sanity bounds; dominant-factor sensitivity
Stage 6  Report                  ── 1 agent ── the estimate with its band, the decomposition, what dominates the error
```

Tell each subagent that its final message is the return value, meaning structured data rather than prose for a human. Estimator subagents should use whatever retrieval the runtime offers to anchor a factor on a real figure; where no figure exists, reason from anchors and state the range honestly rather than inventing a precise number.

---

## Stage 1: Frame the quantity

A Fermi estimate is only as good as the question. Pin down:

- **Exactly what** is being counted or measured, with no ambiguity about scope (which population, which geography, which timeframe, stocks vs flows).
- **The units**, explicitly. Annual vs total, per-user vs absolute, revenue vs volume. Most blown estimates are unit errors, not arithmetic errors.
- **The estimation approach.** Decide whether to build it **bottom-up** (sum or multiply up from atomic units: users × frequency × price) or **top-down** (start from a large known total and carve it down by fractions). Note which; Stage 2 will often try both as a cross-check.

Output: the sharpened quantity with units, and the chosen approach(es).

## Stage 2: Decompose (PARALLEL)

The structure you pick anchors everything after it, so do not commit to the first tree that comes to mind. Dispatch three to five decomposer subagents, each asked to break the QUANTITY into a chain or tree of sub-factors by a *different route*:

- A **bottom-up** path: the smallest atomic unit, multiplied up (e.g. households × pets-per-household × vet-visits-per-pet × spend-per-visit).
- A **top-down** path: a large known total, carved down by fractions (e.g. national GDP × share-of-services × share-captured).
- A **proxy** path: route through an easier-to-estimate correlate and a conversion ratio (e.g. estimate via number of employees, or via a comparable country scaled by population).
- A **dimensional** path: build from rates and capacities (throughput × time × utilization).

Each decomposer returns its factor chain, with every leaf factor being something estimable to within an order of magnitude. A good decomposition bottoms out in factors that are either knowable from common sense, lookup-able, or anchorable to something familiar.

Then **select and reconcile.** Pick the cleanest chain, the one whose leaves are most independently estimable and least likely to hide a correlated error, as the primary. Keep a second, structurally *different* chain as the independent cross-check for Stage 5 (two paths that agree are far more trustworthy than one). Note any factor that appears in both, since a shared factor means a shared error.

Output: the primary factor chain F1…Fk (with the arithmetic that combines them) and a reserved second chain.

## Stage 3: Estimate each factor (PARALLEL)

Dispatch **one subagent per leaf factor** (batch several per agent if the chain is long). Each agent estimates its single factor as a **range, not a point**:

- A **low**, a **best**, and a **high** value, ideally a 90% credible interval (the agent should be 90% sure the true value falls inside [low, high]).
- The **basis**: the anchor or reasoning behind the numbers, a looked-up statistic, a personal-experience anchor, a comparable, a physical limit. Name it, so the factor can be challenged.
- A **confidence** flag: how solid is this factor, and is it a lookup-able fact (tighten it with retrieval) or a genuine guess (keep the range wide)?

Estimate each factor independently, so one agent's optimism doesn't infect another's. Anchor on a real number wherever one exists; only reason from analogy where it doesn't. Output per agent: low / best / high, basis, and confidence for its factor.

## Stage 4: Combine and propagate uncertainty

Assemble the factors and compute the chain. Two moves matter:

**1. Compute the central estimate.** Combine the best values through the chain's arithmetic (multiply the multiplicative factors, sum the additive ones). State it to **one or two significant figures only**: a Fermi estimate that reads "2,847,193" is lying about its precision; write "~3 million".

**2. Propagate the range.** Carry the uncertainty through, don't drop it. For a product of factors, combine the low values and the high values to get a low and high bound on the answer (a rough but honest band); where you want to be sharper, combine the relative uncertainties in log space, since multiplicative errors compound geometrically. Report the answer as a band, "between ~1M and ~10M, best estimate ~3M", not a false point.

Render the calculation as a table so it is auditable:

| Factor | Low | Best | High | Basis |
|---|---|---|---|---|
| F1 — households (M) | 120 | 130 | 140 | census anchor |
| F2 — fraction with a pet | 0.5 | 0.6 | 0.7 | survey, rough |
| F3 — vet visits / yr | 1 | 2 | 4 | guess, wide |
| … | | | | |
| **Result** | **~?** | **~?** | **~?** | product |

## Stage 5: Cross-check and sanity-bound (PARALLEL)

A single chain can be confidently wrong. Dispatch three critic subagents, each attacking the Stage 4 result a different way:

- **The second-path critic:** run the reserved alternate decomposition from Stage 2 to its own answer, independently. If the two paths land within the same order of magnitude, confidence rises sharply. If they diverge, that gap is the real uncertainty, and the reconciliation (which factor differs, and which path to trust) is the finding.
- **The bounds critic:** sanity-check the answer against hard ceilings and floors. Does it exceed a known total it logically cannot (more users than people, more spend than GDP)? Is it absurdly small against a known comparable? An estimate that violates a bound has a broken factor; find it.
- **The sensitivity critic:** identify the **dominant factor**: the one whose uncertainty swamps all the others. In a product, the factor with the widest relative range controls the answer's precision; tightening any other factor is wasted effort. Name it, and say what single measurement would most shrink the band.

Each critic returns its finding. Reconcile: state the cross-checked estimate, widen or narrow the band based on whether the paths agreed, and surface the dominant uncertainty.

## Stage 6: Report

Lead with the number and its honesty, then show the work.

1. **The estimate.** The answer to one or two significant figures, with its uncertainty band, "~3 million, plausibly 1 to 10 million". Never a false-precision point.
2. **The decomposition.** The Stage 4 table, so every factor is visible and any single one can be challenged.
3. **What it rests on.** The two or three load-bearing factors, and the basis for each, especially any that are guesses rather than looked-up figures.
4. **The dominant uncertainty.** The one factor that controls the band's width (from Stage 5), and the single piece of data that would most tighten the estimate.
5. **Cross-check.** Whether an independent decomposition agreed, and against which known bounds the answer was checked.
6. **Confidence and caveats.** How much to trust the order of magnitude, and what would change it.

---

## Principles

- **Decompose the unknown into the knowable.** Never guess the whole; guess the pieces. Independent errors cancel and a transparent chain can be audited factor by factor.
- **Ranges, not points.** Every factor and the final answer carry an uncertainty band. A Fermi answer is an order-of-magnitude claim: one or two significant figures, and more digits than the method earns is a lie about precision.
- **Hunt the dominant factor.** In a product, one factor's uncertainty usually swamps the rest. It is the only one worth more effort, and what the whole estimate's precision depends on.
- **Two paths beat one.** An independent second decomposition is the cheapest, strongest check available. A single chain, however careful, can be confidently wrong.
