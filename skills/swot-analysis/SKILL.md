---
name: swot-analysis
description: Use when the user wants a SWOT analysis of a company, product, project, team, or decision, or asks to assess strengths, weaknesses, opportunities, and threats. Fans out four parallel analyst subagents (one per quadrant), grounds each factor in evidence and prioritizes it, then crosses the quadrants into a TOWS strategy matrix and a ranked set of strategic options in a detailed markdown report. Triggers include "SWOT", "SWOT analysis", "strengths and weaknesses", "TOWS", "analyze our position".
---

# swot-analysis

Runs a SWOT analysis (Strengths, Weaknesses, Opportunities, Threats) anchored to a specific objective, then crosses the quadrants into a TOWS matrix to turn the four lists into ranked strategic options. A SWOT that stops at four lists is unfinished; the strategy comes from the crossing.

The framework, quadrant checklists, scoring, and the TOWS matrix live in [references/framework.md](references/framework.md). Load that file before analyzing and follow the internal-versus-external and anchor-to-objective rules exactly.

## When to use

The user wants to assess the position of a company, product, project, team, individual, or decision, usually to inform a strategy or choice. SWOT is broad and qualitative; if the question is specifically about industry profit structure, prefer a Five Forces analysis instead.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **SUBJECT** (required): what is being analyzed.
- **OBJECTIVE** (required): the goal the SWOT serves (for example "decide whether to launch in the EU", "grow revenue 30% in two years"). A SWOT without an objective is unanchored and nearly useless, so if the user does not give one, ask for it before starting.
- **CONTEXT** (optional): competitors, market, time horizon, and any constraints. Sharpens both the external scan and the strategic options.

## Orchestration map

```
Stage 1  Quadrant Scan   ── 4 analyst subagents IN PARALLEL ──┐  (Strengths, Weaknesses, Opportunities, Threats)
Stage 2  TOWS Synthesis  ── 1 agent, needs all 4 ────────────┘  (cross quadrants into ranked strategies)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground factors in real evidence.

## Stage 1: Quadrant Scan (PARALLEL)

Dispatch four analyst subagents at once, one per quadrant. Give each the shared framing plus its quadrant checklist from the reference file. Pair the two internal quadrants (Strengths, Weaknesses) and the two external quadrants (Opportunities, Threats) by reminding each analyst which axis it is on, so internal and external factors do not bleed across.

**Shared framing (send to every analyst):**

> Analyze one quadrant of a SWOT for **[SUBJECT]**, in service of this objective: **[OBJECTIVE]**. Judge every factor relative to that objective. Stay strictly within your quadrant's axis: Strengths and Weaknesses are internal attributes of the subject; Opportunities and Threats are external conditions in the environment. Ground factors in evidence where you can. Return:
> - A prioritized list of factors, strongest first
> - For each: a one-line statement, the evidence or reasoning, a **magnitude** (1 to 5), and for Opportunities and Threats a **likelihood** (1 to 5)
> - **Confidence** (high, medium, low) per factor, lowered when evidence is thin
> - The two or three factors that matter most to the objective
>
> Context: [CONTEXT]

Collect all four structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: TOWS Synthesis (SEQUENTIAL, needs all 4)

One agent crosses the quadrants into strategy:

1. **Validate the quadrants.** Before crossing, check that factors sit on the correct axis (no external factor filed as a strength, no objective-irrelevant noise). Move or drop misfiled items and note any corrections.
2. **Build the TOWS matrix.** For each cell, pair the highest-magnitude factors and write concrete strategic options:
   - **SO (offensive):** apply specific strengths to specific opportunities.
   - **ST (defensive):** use strengths to blunt specific threats.
   - **WO (improvement):** fix or bypass weaknesses to capture opportunities.
   - **WT (survival):** reduce weaknesses and steer clear of threats.
   Each option states what to actually do, not a restatement of the factors.
3. **Rank the options.** Score the options across all four cells by impact on the objective and feasibility, and recommend the few worth pursuing. A SWOT yields more options than anyone can act on; the ranking is the point.
4. **Verdict.** A short read on the subject's overall position relative to the objective, and what the analysis implies for the decision at hand.

## Report structure

Write a thorough markdown report and save it to `swot-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The subject, the objective the SWOT serves, the date, and any context (competitors, horizon).
2. **SWOT matrix.** The classic 2-by-2 grid as a table, with the top factors in each quadrant so the picture is scannable at a glance.
3. **Quadrant detail (four sections).** Each quadrant's prioritized factors with magnitude, likelihood where relevant, evidence, and confidence. Lead each with the two or three that matter most.
4. **TOWS strategy matrix.** The four cells (SO, ST, WO, WT) with the concrete options derived in each.
5. **Ranked recommendations.** The handful of strategic options worth pursuing, ranked by impact and feasibility, each tied to the factors and objective it serves.
6. **Verdict.** The overall position and what it means for the decision.
7. **Caveats.** SWOT is qualitative and only as good as its inputs and its objective; it is a snapshot, not a forecast; magnitudes are judgment, not measurement; and the four lists are worthless without the TOWS crossing that turns them into action.

## Principles

- **Anchor to the objective.** Every factor is judged relative to a stated goal. An unanchored SWOT is the framework's classic failure mode.
- **Right factor, right quadrant.** Internal attributes are Strengths or Weaknesses; external conditions are Opportunities or Threats. Validate this before crossing.
- **Finish with TOWS.** Four lists are not a SWOT analysis. The crossing into ranked strategic options is the deliverable.
- **Prioritize, do not enumerate.** A long flat list is a non-answer. Magnitude, likelihood, and ranking are what make it usable.
- **Parallel where independent.** The four quadrants share no state, so analyze them concurrently. The crossing needs all four, so it runs after.
