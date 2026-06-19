---
name: reference-class-forecasting
description: Use when the user must forecast a duration, cost, success rate, or outcome and is tempted to estimate from the specifics of their own case, which systematically underestimates and over-optimizes. Runs reference-class forecasting (the outside view): defines the prediction, builds in parallel a class of similar past cases, constructs the empirical distribution of how that class actually turned out, anchors the forecast on that base rate, then adjusts for the case's true distinctiveness under adversarial checks for optimism and regression to the mean. Triggers include "reference class forecasting", "outside view", "base rate", "planning fallacy", "how long will this really take", "are we being too optimistic", "how do projects like this usually go".
---

# reference-class-forecasting

An agentic, parallel implementation of reference-class forecasting — the forecasting discipline grounded in Daniel Kahneman and Amos Tversky's distinction between the *inside view* and the *outside view*, and operationalized for real planning by Bent Flyvbjerg, who used it to expose the chronic cost and schedule overruns of large projects. The method treats your case not as a unique story to be reasoned about from its details, but as one instance of a class of similar past cases whose actual outcomes are the most reliable anchor you have.

It is built to defeat the **planning fallacy**: when people forecast from the inside view — the specific plan, the specific team, the reasons this time will go smoothly — they systematically underestimate time and cost and overstate success, because the inside view sees the plan but not the unknown unknowns that derailed every comparable effort. The outside view corrects this by starting from the base rate: how did projects *like this* actually turn out, before you adjust for anything special about yours.

The skill runs six stages. Building the reference class in Stage 2 and the case-adjustment checks in Stage 4 fan out across parallel subagents. The stages between are sequential because each depends on the class and distribution the previous stage produced.

## When to use

The user must predict a quantity or outcome for a case that belongs to a recognizable class of similar efforts: how long a project will take, what it will cost, whether a launch will hit its target, what adoption or conversion to expect, the odds a venture succeeds. Triggers: "outside view", "base rate", "reference class", "planning fallacy", "how long will this really take", "are we being too optimistic", "how do things like this usually go".

Reach for it specifically when the inside-view estimate feels confident and you suspect that confidence is the problem — when there is a track record of similar cases to learn from, and a strong pull to believe this one is different. It is the outside-view complement to [fermi-estimation](../fermi-estimation/): Fermi builds an estimate up from the specifics of this case (the inside view); reference-class anchors it on how the class actually performed. Run both and reconcile the gap. It also strengthens a [pre-mortem](../pre-mortem/) (the base rate of failure is the reason to take the pre-mortem seriously) and feeds [scenario-planning](../scenario-planning/).

Do **not** use it when the case is genuinely without precedent (no class exists to anchor on — though be very skeptical of "unprecedented", which is usually optimism in disguise), nor for adjudicating which explanation is true (use [analysis-of-competing-hypotheses](../analysis-of-competing-hypotheses/)).

## Inputs

- **PREDICTION** (required): what is to be forecast, stated as a specific measurable outcome for a specific case — "how many months until this platform migration is live", "the final cost of this office build", "the first-year retention of this product". Name the target variable and its units.
- **THE CASE** (required): enough about the specific case to find its peers and judge its distinctiveness — what it is, its scale, its context, what makes the user think it is typical or atypical.
- **INSIDE-VIEW ESTIMATE** (optional): the estimate the user has already formed from the case's specifics, if any. Used to measure the planning-fallacy gap, not to anchor the forecast.

## Orchestration map

```
Stage 1  Frame the prediction    ── 1 agent ── pin the target variable, units, and the case
Stage 2  Build the reference class ── N proposer subagents IN PARALLEL ── candidate classes; reconcile to one with criteria
Stage 3  Build the distribution   ── 1 agent (uses retrieval) ── gather class outcomes; construct the base-rate distribution
Stage 4  Locate the case + adjust ── 3 critic subagents IN PARALLEL ── place the case; constrain the adjustment
Stage 5  Forecast                 ── 1 agent ── outside-view forecast as a distribution, every adjustment justified
Stage 6  Report                   ── 1 agent ── base rate, the gap vs inside view, the forecast, the contingency
```

Tell each subagent that its final message is the return value, meaning structured data rather than prose for a human. The subagents that build the class and its distribution should use whatever retrieval the runtime offers to find real comparable cases and their outcomes. If no retrieval is available, the agent should build the class from documented knowledge and state plainly that the distribution is approximate.

---

## Stage 1: Frame the prediction

Pin the forecast precisely, because the reference class must match it:

- **The target variable** and its units — months to completion, total cost in dollars, percentage retained at twelve months, probability of hitting the stated goal. A vague target ("will it go well") cannot be forecast from a distribution.
- **The case**, stated at the level of generality that will let you find its peers — specific enough to be the right kind of thing, general enough that comparables exist.
- **The decision the forecast feeds**, so the report can target the right precision and the right contingency question.

Output: the sharpened prediction (variable, units, case) and the decision it informs.

## Stage 2: Build the reference class (PARALLEL)

This is the move that makes or breaks the method, and it carries a genuine tension: the class must be **similar enough** that its outcomes are relevant to your case, yet **broad enough** that it contains enough cases to form a stable distribution. Too narrow ("projects exactly like ours") and you have a class of one and are back to the inside view; too broad ("all projects") and the base rate is noise.

Dispatch three to five proposer subagents in parallel, each constructing a candidate reference class from a different framing:

- **The narrow-and-similar class** — cases as close to this one as possible (same type, scale, domain). High relevance, but check it has enough members to count.
- **The broad-and-numerous class** — a wider category with many members and a stable base rate, accepting some loss of similarity.
- **The mechanism class** — cases that share the *causal structure* that drives the outcome (the same kind of dependency, the same kind of coordination problem), even if they look different on the surface.
- **The outcome class** — cases defined by sharing the failure mode or the success condition that matters for this forecast (e.g. "migrations that depended on a third-party API").

Each proposer returns its candidate class, the inclusion criteria, and an estimate of how many real cases it contains.

Then **reconcile** to a single working class (or two, kept as a sensitivity check): pick the framing that best balances similarity against sample size, write explicit inclusion criteria so membership is auditable, and state honestly how many cases it holds and therefore how stable its distribution will be.

Output: the chosen reference class with its inclusion criteria and expected sample size.

## Stage 3: Build the distribution

Gather the outcomes of the class members and turn them into the base rate. Using retrieval where available:

- Collect the actual outcome of the target variable for as many class members as you can find — the *realized* duration, cost, or success rate, not the originally planned figure (the planned figures are exactly the inside-view estimates the method exists to correct).
- Construct the empirical **distribution**: at minimum the median and the range; better, the key percentiles (e.g. P10 / P50 / P90). For a yes/no outcome, the base rate is simply the historical success frequency.
- Note the data quality: how many cases, how reliable the outcomes, any survivorship bias (failed cases that left no record will skew the class optimistic).

The median of this distribution is the **base rate** — the single most important number in the forecast, and the anchor everything else adjusts from. Output: the distribution (median, range, percentiles) with its sample size and quality caveats.

## Stage 4: Locate the case and adjust (PARALLEL)

The case is not the median by default, but it is much closer to the median than the inside view will want to admit. The job here is to place the case in the distribution and make only the adjustments the evidence actually warrants. Dispatch three critic subagents in parallel, each guarding against a different way the adjustment goes wrong:

- **The placement analyst** — argue where in the distribution this case genuinely sits, with evidence. Is there a *specific, documented* reason it should beat the median (a materially stronger team, a smaller scope, a removed dependency)? Each proposed adjustment off the base rate must name its evidence and its size; "we're good at this" is not evidence.
- **The regression critic** — push the case back toward the mean. Extreme inputs produce less-extreme outcomes; the reasons this case feels exceptional are partly noise that will regress. This critic's default is that the case is more average than it looks, and the burden of proof is on any adjustment away from the median.
- **The optimism critic** — check the direction of every adjustment. If all the proposed corrections happen to point toward "faster, cheaper, more likely to succeed", that is the planning fallacy reasserting itself, not analysis. This critic also tests the "this time is different" claims: are they genuinely unprecedented, or did every case in the class believe the same thing?

Each critic returns its finding. Reconcile into a single, justified position in the distribution: start at the base rate, apply only the adjustments that survived all three critics, and keep them small — a defensible reference-class forecast usually lands much nearer the base rate than the inside view ever would.

## Stage 5: Forecast

Produce the outside-view forecast as a **distribution, not a point**:

- A central estimate anchored on the base rate and shifted only by the surviving adjustments.
- An interval carried over from the class distribution (the class's spread is your case's uncertainty; do not report tighter than the class warrants).
- For each adjustment made off the base rate, a one-line justification and its evidence, so the whole move from base rate to forecast is auditable.

State the base rate explicitly alongside the adjusted forecast, so a reader can see exactly how far you departed from the class and why.

## Stage 6: Report

Write the forecast for the decision. Lead with the outside view, then show the work.

1. **The forecast.** The central estimate with its interval, stated as a range — "most likely 14 months, plausibly 11–22" — never a false-precision point.
2. **The base rate.** The reference class's median and distribution, and the class itself with its inclusion criteria, so the anchor is auditable.
3. **The planning-fallacy gap.** If an inside-view estimate was given, the difference between it and the outside-view forecast, stated bluntly. This gap is usually the most valuable output: it quantifies the optimism that would otherwise have gone into the plan.
4. **Adjustments.** Every shift made off the base rate, with its evidence — and, just as important, the tempting adjustments that were *rejected* and why.
5. **The contingency implication.** What the forecast means for the plan: the schedule buffer, the cost reserve, or the uplift to apply so the plan is calibrated to how the class actually performs, not to how the inside view hopes.
6. **Confidence and limits.** The sample size and data quality behind the base rate, the sensitivity to the reference-class choice, and what would sharpen the forecast.

---

## Principles

- **Anchor on the base rate, adjust second.** The class's historical outcome is the forecast's foundation; the specifics of your case are an adjustment to it, not the starting point. The inside view reverses this — it reasons from the specifics and never reaches the base rate at all. Start outside, then come in.
- **Your case is less special than it feels.** Almost every adjustment people want to make is in the optimistic direction, and almost every "this time is different" was also believed by the cases that went the usual way. Keep adjustments small, evidenced, and skeptically reviewed.
- **The realized outcome, never the plan.** Build the distribution from how class members *actually* turned out, not from what they originally projected. The original projections are the very inside-view estimates the method is designed to correct.
- **Mind the class width tradeoff.** A class too narrow has no statistical power; a class too broad is irrelevant. The skill is choosing a class similar enough to matter and broad enough to count, and stating the tradeoff you struck.
- **Regression to the mean is the default.** Extreme cases produce less-extreme outcomes. Unless there is documented, case-specific reason to sit away from the median, expect the median.
- **Forecast a distribution.** The class's spread is your uncertainty. Reporting a single number throws away the most honest thing the method gives you; report a range and the contingency it implies.
- **The gap is the gift.** The distance between the inside-view estimate and the outside-view forecast is often the single most useful number produced — it is the optimism that would otherwise have been built silently into the plan.
