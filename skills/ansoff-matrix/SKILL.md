---
name: ansoff-matrix
description: Use when the user wants to explore growth strategies for a company or product using the Ansoff Matrix (Market Penetration, Market Development, Product Development, Diversification). Fans out four parallel strategist subagents, one per quadrant, to generate concrete growth options with risk and capability fit, then synthesizes a prioritized growth path in a detailed markdown report. Triggers include "Ansoff matrix", "growth strategy", "how should we grow", "market penetration vs diversification", "product/market growth".
---

# ansoff-matrix

Explores growth options for a company or product with the Ansoff Matrix, which maps growth along two axes: products (existing or new) and markets (existing or new). The four cells are Market Penetration, Market Development, Product Development, and Diversification, in rising order of risk. The skill generates concrete options in each cell and sequences them into a prioritized growth path.

The four strategies, their risk profiles, how to use the matrix, and the pitfalls live in [references/ansoff.md](references/ansoff.md). Load that file before analyzing.

## When to use

The user wants growth options and a path: how a company or product should grow, and which moves to make first. It assumes a growth objective. If the question is which products to fund across an existing portfolio, prefer a BCG matrix; if it is how to frame the growth problem itself, prefer problem definition first.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **SUBJECT** (required): the company or product seeking growth.
- **OBJECTIVE** (optional but valuable): the growth goal (for example "double revenue in three years"). Shapes which options matter and how they are prioritized.
- **CONTEXT** (optional): current markets, products, capabilities, and constraints. Sharpens both the options and the risk and capability assessment.

## Orchestration map

```
Stage 1  Option Generation  ── 4 strategist subagents IN PARALLEL ──┐  (one per quadrant: concrete options + risk)
Stage 2  Path Synthesis     ── 1 agent, needs all 4 ───────────────┘  (prioritize, sequence a growth path)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval to ground options in real markets and competitors.

## Stage 1: Option Generation (PARALLEL)

Dispatch four strategist subagents at once, one per quadrant. Give each the shared framing and one quadrant from the reference file.

**Shared framing (send to each strategist):**

> Generate growth options for **[SUBJECT]** (objective: [OBJECTIVE]) in one Ansoff quadrant: **[quadrant]**. Produce concrete, specific options, not generic descriptions of the quadrant (name the market, segment, channel, or product). For each option return:
> - The option in one specific line
> - **Risk level** and the main sources of risk
> - **Capabilities required**, and whether the subject has them or has a gap
> - **Rough investment and reward**
> - A one-line case for why it could work
>
> Context: [CONTEXT]

The four quadrants are Market Penetration, Market Development, Product Development, and Diversification. For Diversification, note whether each option is related or unrelated. Collect all four before continuing, and re-dispatch any that fail.

## Stage 2: Path Synthesis (SEQUENTIAL, needs all 4)

One agent turns the options into a prioritized path:

1. **Compare all options** across the four quadrants on risk, capability fit, investment, and reward against the objective.
2. **Prioritize.** Rank the options, respecting that lower-risk growth is usually exhausted before higher-risk moves are justified. Flag any case where the firm is reaching for Diversification while Penetration is still open.
3. **Sequence a growth path.** A realistic order of moves over the horizon (for example, penetrate now, develop adjacent markets next, diversify only on a clear trigger), with the capability building each later step needs.
4. **Verdict.** The recommended growth strategy and the first concrete moves, tied to the objective.

## Report structure

Write a thorough markdown report and save it to `ansoff-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The subject, the growth objective, and the date.
2. **The matrix.** The 2-by-2 grid as a table, with the top options in each quadrant and their risk level, scannable at a glance.
3. **Per-quadrant options (four sections).** The concrete options in each cell with risk, capability fit, investment, and reward.
4. **Prioritized options.** All options ranked by fit to the objective and risk-adjusted reward.
5. **Recommended growth path.** The sequence of moves over the horizon, with triggers and the capabilities each step requires.
6. **Verdict.** The recommended strategy and first moves.
7. **Caveats.** Risk rises with unfamiliarity, but capability gaps drive risk as much as market novelty; new markets fail for reasons invisible from the home market; and the matrix prioritizes options, it does not validate demand. Test the top moves before committing.

## Principles

- **Concrete options, not cell descriptions.** "Enter new markets" is not a strategy. Name the market, channel, or product.
- **Exhaust the cheap growth first.** Penetration before development, development before diversification, unless a clear trigger justifies the jump.
- **Capability fit is risk.** Assess whether the firm can actually execute each move, not just whether the market is attractive.
- **Sequence, do not just list.** The deliverable is a prioritized path over time, not four lists of ideas.
- **Parallel where independent.** The four quadrants are explored concurrently; the path synthesis needs all four and runs after.
