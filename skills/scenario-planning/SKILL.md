---
name: scenario-planning
description: Use when the user wants scenario planning for an uncertain future: framing a focal question, finding critical uncertainties, building a 2x2 of plausible futures, and deriving strategy that holds across them. Gathers driving forces and selects the two critical uncertainties as axes, then fans out four scenario-builder subagents in parallel (one per quadrant) to develop named narratives, and synthesizes robust versus contingent strategy with the signposts to monitor. Triggers include "scenario planning", "scenario analysis", "2x2 scenarios", "critical uncertainties", "what if the future", "plan for uncertainty".
---

# scenario-planning

Builds several distinct, plausible futures for a focal question using the 2x2 critical-uncertainties method (Global Business Network / Royal Dutch Shell tradition; Peter Schwartz, *The Art of the Long View*, 1991). The goal is to prepare for an uncertain future, not to predict which one arrives.

The method, the axis-selection logic, what makes a good axis and a good scenario, how to write signposts, and the pitfalls live in [references/scenarios.md](references/scenarios.md). Load that file before starting and follow it exactly.

## When to use

The user faces a decision whose right answer depends on an uncertain future and wants to stress-test strategy against several of them rather than a single forecast. The unit of analysis is a focal question tied to a decision-maker and a horizon, not "the future" in the abstract. Scenario planning complements [pestel-analysis](../pestel-analysis/README.md), which is the natural source of driving forces (its high-impact, high-uncertainty watch list feeds Stage 1 directly), and [three-horizons](../three-horizons/README.md), which sequences moves over time once the scenarios are set. If the user has already run a PESTEL scan, take its forces as input rather than regathering them.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework and its terms keyed to it regardless of the output language.

## Inputs

- **FOCAL QUESTION** (required): the decision or strategic question, and the entity it concerns. Push for specificity: "what will our market look like" is too loose until tied to a decision-maker and a choice. Narrow it with a question or two if vague.
- **HORIZON** (optional): how far out to look. Default to a sensible multi-year horizon (five to fifteen years), far enough that today's certainties could break but not so far it turns to fiction.
- **CONTEXT** (optional): driving forces already known (for example from a prior PESTEL scan), and the decision the scenarios should inform.

## Orchestration map

```
Stage 1  Forces + Axes  ── gather driving forces, then SELECT 2 critical uncertainties ──┐
Stage 2  Scenarios      ── 4 scenario-builder subagents IN PARALLEL, one per quadrant ───┤
Stage 3  Synthesis      ── 1 agent, needs all 4 ─────────────────────────────────────────┘  (robust vs contingent, signposts)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval to ground forces and scenario logic in real, current developments.

## Stage 1: Force gathering and axis selection

Gather the driving forces first, then select the two axes. Both steps happen before any scenario is built.

**Gather the forces.** If a PESTEL scan or a force list is supplied in CONTEXT, use it. Otherwise cast wide across political, economic, social, technological, environmental, legal, and the relevant industry forces. You may fan out a few force-finder subagents by lens to gather concurrently, or do it in one pass; either way produce a single deduplicated list of driving forces that could shape the focal question.

**Rank and select (this stays with the orchestrator).** Score every force on two dimensions against the focal question, per the impact-x-uncertainty matrix in the reference file:

- **Impact**: how much the force would move the answer to the focal question.
- **Uncertainty**: how unpredictable its trajectory is over the horizon.

Sort the forces into the four cells. Set aside the **predetermined elements** (high impact, low uncertainty) as the shared backdrop every scenario inherits. From the **critical uncertainties** (high impact, high uncertainty) pick the two most decisive that are also independent of each other, and render each as an axis: a spectrum between two opposed, plausible poles. Run the independence and goodness tests in the reference file before committing; if the two axes are correlated, the 2x2 collapses into one future at four intensities.

Crossing the two axes defines the four quadrants. Name each quadrant's pole combination so Stage 2 knows exactly which world to build. Confirm the two axes with the user before fanning out, since everything downstream rests on this choice.

## Stage 2: Scenario building (PARALLEL, four scenarios)

Dispatch four scenario-builder subagents at once, one per quadrant of the 2x2. Give each the shared framing plus its quadrant's pole combination and the predetermined elements that every scenario shares.

**Shared framing (send to every builder):**

> Build one scenario for this focal question: **[FOCAL QUESTION]**, over **[HORIZON]**. Your scenario sits at this corner of the 2x2: **[AXIS A pole] x [AXIS B pole]**. Every scenario shares this backdrop of predetermined elements: **[predetermined elements]**. Develop a coherent, internally consistent world, not a bullet list. Return:
> - **Name**: a vivid, memorable name for this world
> - **The path here**: how the world got from today to this corner over the horizon, with the key turning points
> - **What it looks like**: the state of the world in this scenario, with the predetermined elements playing out inside it, grounded in real evidence where retrieval allows
> - **Implications for the focal question**: what this world means for the entity and its decision
> - **Distinctive signals**: the early, observable indicators that this world specifically is emerging (not the other three)
> - **Confidence**: high, medium, or low on the internal logic, lowered where evidence was thin
>
> Treat this as a plausible future to prepare for, not a prediction. Do not assign it a probability. Context: [CONTEXT]

Assign the four quadrants by their pole combinations. Collect all four structured scenarios before continuing, and re-dispatch any builder that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 4)

One agent turns the four scenarios into strategy:

1. **The scenario set at a glance.** The 2x2 with the four named scenarios in their quadrants, and a line on each. Check the set: are the four genuinely distinct worlds, or the same world at four intensities? If they collapse, the axes were wrong; flag it.
2. **Robust (resilient) moves.** The actions that make sense across all four scenarios. These are the core of the strategy because they carry no bet on which future arrives.
3. **Contingent moves.** Hedges and options tied to specific scenarios, each held ready rather than committed now, and each wired to the signpost that would trigger it.
4. **Signposts to monitor.** The early-warning dashboard: observable, discriminating, leading indicators that show which scenario is emerging. Pull the distinctive signals from each scenario and sharpen them into a watch list, noting which scenario each one points toward.
5. **Implications for the decision.** What the focal question's decision-maker should do now (the robust moves), what to prepare (the contingent moves), and what to watch (the signposts) as the future declares itself.

## Report structure

Write a thorough markdown report and save it to `scenario-planning-<topic-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The focal question, the entity, the horizon, the date, and a one-line note on the method and that scenarios are not forecasts.
2. **The 2x2 at a glance.** The two axes, the four named scenarios placed in their quadrants (a simple ascii 2x2 is fine), and one line on each. A reader with two minutes should leave knowing the four futures and what to do across them.
3. **Axes and forces.** The two critical uncertainties chosen as axes and why; the predetermined elements forming the shared backdrop; and the forces considered but set aside.
4. **Per-scenario sections (four).** For each: name, the path from today, what the world looks like, and the implications for the focal question. Grounded in specifics, not generic futures.
5. **Strategy.** Robust moves up front, then contingent moves each tied to its scenario and trigger.
6. **Signposts.** The monitoring dashboard: indicator, which scenario it points toward, and why it discriminates.
7. **Caveats.** Scenarios are plausible futures to prepare for, not predictions, and carry no probabilities; the set is only as good as the two axes; the value is in the strategy and signposts, not the stories; and the scenarios are a tool for thinking, to be revisited as forces shift.

## Principles

- **Prepare, do not predict.** The output is strategy that holds across futures, not a guess at which one arrives. No scenario gets a probability.
- **Axes must be uncertain and independent.** Only high-impact, high-uncertainty forces earn an axis, and the two must be uncorrelated. Predetermined trends are the backdrop, never the cross.
- **Four distinct worlds, not four intensities.** Each quadrant must demand a different response. If the scenarios are one future dialed up and down, the axes were wrong.
- **End in strategy.** Robust moves, contingent hedges, and the signposts that trigger them. Vivid narratives with no strategy are entertainment.
