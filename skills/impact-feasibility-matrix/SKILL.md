---
name: impact-feasibility-matrix
description: Use when the user has a list of initiatives, ideas, features, or projects and wants to prioritize them by impact and feasibility (the impact-effort matrix), sorting into quick wins, major projects, fill-ins, and thankless tasks. Defines the axes, scores each option in parallel, places them in quadrants, and recommends a sequenced plan in a markdown report. Triggers include "impact vs feasibility", "impact-effort matrix", "prioritize these", "what should we do first", "quick wins", "prioritization matrix".
---

# impact-feasibility-matrix

The impact-effort matrix prioritizes a set of options by plotting them on impact and feasibility, sorting them into quick wins, major projects, fill-ins, and thankless tasks, and recommending a sequenced plan. It catches the trap of treating a sorted pile as a plan: the deliverable is a sequence that respects dependencies.

The axes, the four quadrants, and how to score live in [references/impact-feasibility.md](references/impact-feasibility.md). Load that file before scoring.

## When to use

The user has more options than they can do and needs to decide what to do first, what to plan, and what to drop. If the options do not yet exist, generate them first (for example with a growth or decomposition skill); this skill prioritizes an existing set.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **OPTIONS** (required): the list of initiatives, ideas, or projects to prioritize.
- **OBJECTIVE** (required): the goal impact is measured against. Impact is meaningless without it, so ask if it is missing.
- **CONTEXT** (optional): the resources, constraints, and timeframe that define feasibility, and any known dependencies between options.

## Orchestration map

```
Stage 0  Calibrate     ── define impact and feasibility for this objective (inline)
Stage 1  Score options ── 1 scorer subagent per option IN PARALLEL ──┐  (impact, feasibility, rationale)
Stage 2  Synthesis     ── 1 agent, needs all options ───────────────┘  (quadrants, dependencies, sequence)
```

Tell each subagent its final message is the return value: structured data, not prose for a human.

## Stage 0: Calibrate (inline)

Before scoring, state exactly what impact means for this objective and what drives feasibility (effort, cost, risk, dependencies), with a 1-to-5 anchor for each axis. Every option is then judged on this same scale. Skipping this is the framework's main failure mode: unanchored scores just encode bias.

## Stage 1: Score options (PARALLEL)

Dispatch one scorer subagent per option, all at once, each given the calibrated definitions and one option.

**Shared framing (send to each scorer):**

> Score one option against this objective: **[OBJECTIVE]**, using these definitions of impact and feasibility: **[calibrated anchors]**. Option: **[OPTION]**. Return:
> - **Impact** (1 to 5) with a one-line rationale and the evidence or assumption behind it
> - **Feasibility** (1 to 5) with rationale, accounting for effort, cost, risk, and unknowns (do not be optimistic; probe what could make it harder)
> - **Dependencies:** any other option or precondition this one needs first
> - **Confidence** (high, medium, low)
>
> Context: [CONTEXT]

Collect all options before continuing, and re-dispatch any that fail.

## Stage 2: Synthesis (SEQUENTIAL, needs all options)

One agent assembles the prioritized plan:

1. **Recalibrate for consistency.** Check that scores are comparable across options (the parallel scorers did not see each other). Adjust outliers that were scored on a different implicit scale, and note the adjustment.
2. **Place the quadrants.** Assign each option to quick win, major project, fill-in, or thankless task.
3. **Map dependencies.** Identify where one option enables another, since this overrides a naive quadrant order.
4. **Sequence.** Quick wins first for momentum, major projects planned and staged, fill-ins as capacity allows, thankless tasks dropped, all respecting dependencies. Flag the fill-in-creep risk if there are many easy low-impact options.
5. **Verdict.** The recommended order of action and what to stop doing.

## Report structure

Write the result as markdown and save it to `impact-feasibility-matrix-<objective-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The objective, the date, and the calibrated definitions of impact and feasibility.
2. **The matrix.** A 2-by-2 layout (or a scored table) placing every option in its quadrant, scannable at a glance.
3. **Scored options.** A table of all options with impact, feasibility, quadrant, dependencies, and confidence.
4. **Quadrant detail.** The options in each quadrant, with the rationale for the notable ones.
5. **Recommended sequence.** The order of action respecting dependencies, with quick wins first and thankless tasks dropped.
6. **Caveats.** Scores are judgment anchored to a stated definition, not measurement; feasibility is routinely overestimated; dependencies can override quadrant order; and strategic must-dos or hard constraints can override the matrix.

## Principles

- **Be pessimistic on feasibility.** Effort, risk, and dependencies are routinely underestimated. Probe them.
- **Dependencies override quadrant order.** An option's enabling chain beats its naive quadrant placement.
- **The clearest win is permission to stop.** Naming the thankless tasks to drop is often the most valuable output.
