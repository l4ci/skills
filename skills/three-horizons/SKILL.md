---
name: three-horizons
description: Use when the user wants to assess or plan growth and innovation across time using McKinsey's Three Horizons model (Horizon 1 core, Horizon 2 emerging, Horizon 3 options). Fans out three parallel analyst subagents (one per horizon) to place and assess initiatives, then synthesizes portfolio balance, pipeline gaps, and how each horizon should be funded and measured, in a detailed markdown report. Triggers include "three horizons", "3 horizons", "horizon 1 2 3", "growth horizons", "innovation portfolio", "balance core and future".
---

# three-horizons

Manages growth and innovation across the Three Horizons (McKinsey): Horizon 1 (the mature core), Horizon 2 (emerging businesses being built into the next core), and Horizon 3 (nascent options on the future). The skill places initiatives into horizons, checks whether the portfolio funds all three at once, and prescribes how each should be managed.

The three horizons, the balance and pipeline logic, and the pitfalls live in [references/three-horizons.md](references/three-horizons.md). Load that file before analyzing. The horizons are stages of maturity, not calendar periods; keep that distinction.

## When to use

The user wants to see whether an organization is investing in its future as well as its present, to plan an innovation or growth portfolio, or to diagnose why the future pipeline is thin. The unit is an organization or business and its set of initiatives.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **ORGANIZATION** (required): the organization or business in scope.
- **INITIATIVES** (optional but valuable): the current and proposed businesses, products, and bets. If not given, work with the user to list them, since the model places real initiatives, not abstractions.
- **CONTEXT** (optional): the growth ambition, the pace of the industry (which compresses or stretches the horizons), and the investment available.

## Orchestration map

```
Stage 1  Horizon Analysis ── 3 analyst subagents IN PARALLEL ──┐  (place and assess initiatives per horizon)
Stage 2  Synthesis        ── 1 agent, needs all 3 ────────────┘  (balance, pipeline gaps, allocation, metrics)
```

Tell each subagent its final message is the return value: structured data, not prose for a human.

## Stage 1: Horizon Analysis (PARALLEL)

Dispatch three analyst subagents at once, one per horizon. Give each the shared framing plus its horizon's definition from the reference file. Place each initiative by its maturity, not its age.

**Shared framing (send to each analyst):**

> Analyze one horizon for **[ORGANIZATION]**: **[horizon]**. From the initiative list, identify which belong in this horizon by maturity stage, and assess the horizon overall. Return:
> - The initiatives in this horizon, each with its role, revenue or value, investment, and risk or certainty
> - The **health** of this horizon: is it adequately populated and funded for its job
> - **Gaps:** what is missing (for example, too few options, or a thin pipeline to the next horizon)
> - How initiatives here should be **measured and managed**, given the horizon
>
> Initiatives: [INITIATIVES]. Context: [CONTEXT]

Collect all three before continuing, and re-dispatch any that fail.

## Stage 2: Synthesis (SEQUENTIAL, needs all 3)

One agent assembles the portfolio view:

1. **Assess the balance.** Whether the organization runs all three horizons at once: H1 generating cash, H2 building the next core, H3 seeding options. Name the pathology if present, usually the tyranny of the core (H1 starving H2 and H3), occasionally the reverse.
2. **Trace the pipeline.** Whether initiatives flow inward over time (H3 to H2 to H1), and where the pipeline breaks: an empty H3 (no future), a thin H2 (a cliff when H1 declines).
3. **Allocate.** How investment, talent, and attention should shift across horizons to fix the imbalance.
4. **Differentiate management.** How each horizon should be funded, measured, and governed, since one set of metrics across all three destroys the future or wastes the core.
5. **Verdict.** Whether the organization is investing in its future, and the few moves that matter most.

## Report structure

Write a thorough markdown report and save it to `three-horizons-<organization-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The organization, the growth ambition, the date, and a note that horizons are maturity stages, not calendar time.
2. **Horizon map.** A table placing every initiative in its horizon with role, value, investment, and risk, scannable at a glance.
3. **Per-horizon detail (three sections).** The initiatives, the health of the horizon, and how it should be managed.
4. **Balance and pipeline.** Whether all three run at once, the pathology if any, and where the pipeline breaks.
5. **Allocation and management.** How to shift investment across horizons and how to measure each differently.
6. **Verdict.** Whether the future is funded and the priority moves.
7. **Caveats.** Horizon placement is judgment about maturity; the model shows balance, not which specific bets will pay off; and industry pace changes how far apart the horizons really sit.

## Principles

- **Maturity, not calendar.** A project's horizon is its stage, not its age. A long-dated project already winning customers is H2.
- **Fund all three at once.** The point is simultaneity: cash from H1, building in H2, options in H3. A portfolio missing a horizon has a hidden cliff.
- **Different horizons, different rules.** Each needs its own funding, metrics, and governance. H1 metrics applied to H3 kill the future.
- **An empty H3 is a finding.** Treat a thin future pipeline as a result to report, not a section to skip.
- **Parallel where independent.** The three horizons are analyzed concurrently; the balance synthesis needs all three and runs after.
