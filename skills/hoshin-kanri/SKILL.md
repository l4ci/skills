---
name: hoshin-kanri
description: Use when the user wants to deploy a strategy into aligned, measurable action using Hoshin Kanri (policy deployment, strategy deployment), or asks to build an X-matrix, cascade breakthrough objectives, or align daily work with strategy. Establishes the vital few breakthrough objectives and their annual objectives, fans out one strategist subagent per annual objective to develop improvement priorities, targets, and owners, then synthesizes the X-matrix, the correlations, the alignment check, and the catchball and review cadence into a detailed markdown report. Triggers include "Hoshin Kanri", "policy deployment", "strategy deployment", "X-matrix", "hoshin planning", "catchball", "cascade strategy to execution".
---

# hoshin-kanri

Hoshin Kanri (TQM policy deployment) deploys a strategy into aligned, measurable action: choose the vital few breakthrough objectives, cascade them into annual objectives, improvement priorities, and targets, and tie every level back to the strategy via the X-matrix and two-way catchball. It catches the failure where strategy stays at the top and daily work drifts from it.

The X-matrix, the catchball process, and the review cadence live in [references/hoshin.md](references/hoshin.md). Load that file before facilitating.

## When to use

The user has a strategy or vision and needs to turn it into a focused, owned, measurable plan that reaches the working level. It pairs with [okr](../okr/) and [balanced-scorecard](../balanced-scorecard/) (both turn strategy into goals; Hoshin Kanri is the TQM lineage built around the X-matrix and two-way catchball), and it runs on the PDCA loop ([pdca-cycle](../pdca-cycle/)) for review. Use it when alignment across levels matters, not for a quick personal goal list.

## Language

Facilitate the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **ORGANIZATION** (required): the company, unit, or team deploying the strategy.
- **STRATEGY** (required): the strategy, vision, or the breakthrough objectives themselves. If only a vague direction is given, draw out the few breakthrough objectives first before fanning out.
- **CONTEXT** (optional): the planning horizon, the levels to cascade through, and any fixed constraints. This shapes the cascade depth and the review cadence.

## Orchestration map

```
Stage 1  Breakthrough + annual objectives  ── 1 agent with the user ──┐  (the vital few, then this year's)
Stage 2  Cascade each annual objective      ── N strategist subagents IN PARALLEL ──┤  (priorities, targets, owners)
Stage 3  Build the X-matrix                  ── 1 agent, needs all N ──┘  (correlations, alignment, catchball, review)
```

Tell each subagent its final message is the return value: structured data, not prose for a human.

## Stage 1: Breakthrough and annual objectives (SEQUENTIAL, with the user)

Set the breakthrough objectives, then derive this year's annual objectives from them.

1. **Breakthrough objectives.** The 3-to-5-year step-changes the strategy demands. Hold the line on the vital few: if the user lists ten, push them to the three or four that would matter most. Each should be a real change in position, not business as usual.
2. **Annual objectives.** What must happen this year to stay on track for each breakthrough objective. These are the unit of the parallel cascade in Stage 2. Keep them few and concrete.

State the breakthrough objectives and annual objectives back to the user and confirm before fanning out.

## Stage 2: Cascade each annual objective (PARALLEL)

Dispatch one strategist subagent per annual objective at once. Give each the shared framing plus its annual objective and the breakthrough objective it serves.

**Shared framing (send to every strategist):**

> Develop the deployment of one annual objective for **[ORGANIZATION]**: **[ANNUAL OBJECTIVE]**, which serves the breakthrough objective **[BREAKTHROUGH OBJECTIVE]**. Return:
> - **Improvement priorities**: the few initiatives or changes (the "how") that would move this objective this year, each phrased as a priority, not a vague theme.
> - **Targets**: for each priority, a measurable target (the metric and the level to reach, by when). A target is a number, not an activity.
> - **Owners**: who should be accountable for each priority, and which other teams must contribute.
> - **Catchball**: the pushback the working level would realistically raise (capacity, dependencies, whether the target is achievable), since the plan is negotiated, not dictated.
> - **Confidence**: high, medium, or low, lowered where the target or capacity is uncertain.
>
> Context: [CONTEXT]

Collect all structured results before continuing. Re-dispatch any strategist that fails rather than synthesizing with a gap.

## Stage 3: Build the X-matrix (SEQUENTIAL, needs all)

One agent assembles the cascades into the X-matrix and checks that the whole thing holds together:

1. **The X-matrix.** Lay out the four legs and the ownership grid as the reference file describes: breakthrough objectives, annual objectives, improvement priorities, targets, and owners.
2. **Correlations.** Mark how strongly each leg connects to the next (strong, weak, none): which annual objectives serve which breakthrough objective, which priorities drive which targets, and who owns what. The marks are where the plan's logic is visible or missing.
3. **Alignment check (the golden thread).** Trace every priority and target up to a breakthrough objective. Flag orphans: a priority with no target, a target with no owner, a breakthrough objective with no priority supporting it, and an owner loaded with too much.
4. **Catchball.** Summarize the pushback the strategists surfaced and where the plan needs a second pass between levels before it is committed.
5. **Review cadence.** Set how the targets will be tracked (a monthly review against target, the bowling chart) and the PDCA rhythm that adjusts the plan when reality diverges.

## Report structure

Write a thorough markdown report and save it to `hoshin-kanri-<org-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The organization, the planning horizon, the date, and a one-line note on the method.
2. **The vital few.** The breakthrough objectives and this year's annual objectives, stated plainly so the focus is unmistakable.
3. **The X-matrix.** The four legs and the ownership grid rendered as a structured table (and a nested list where the table cannot hold it), with the correlation marks. This is the headline deliverable.
4. **Deployment detail.** Per annual objective: its improvement priorities, the measurable targets, and the owners.
5. **Alignment check.** The golden-thread trace and any orphans found, with the fix for each.
6. **Catchball and review.** The pushback to resolve before commitment, and the tracking and PDCA cadence.
7. **Caveats.** Hoshin deploys a strategy; it does not judge whether the strategy is right. Focus depends on holding the vital few. The matrix is worth nothing if it is built once and never reviewed, and a target that is really an activity will not tell you whether you are winning.

## Principles

- **The vital few.** Three or four breakthrough objectives, not a wish list. Focus is the method's whole point; dilution defeats it.
- **Catchball, not dictation.** A plan handed down without the working level's pushback buys no commitment and usually no realism.
- **Targets are numbers.** An activity dressed as a target cannot be tracked.
- **Built to be reviewed.** The X-matrix lives through its review cadence. Without the PDCA loop it is wall decoration.
