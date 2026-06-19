---
name: bcg-matrix
description: Use when the user wants to analyze a portfolio of business units or product lines with the BCG Growth-Share Matrix, classifying each into Stars, Cash Cows, Question Marks, or Dogs and recommending where to invest, hold, harvest, or divest. Fans out one analyst subagent per unit in parallel to place it on market growth and relative market share, then synthesizes portfolio balance, cash flow, and strategy into a detailed markdown report. Triggers include "BCG matrix", "growth-share matrix", "Stars and Cash Cows", "portfolio analysis", "which products to invest in or kill".
---

# bcg-matrix

Analyzes a portfolio of business units or product lines with the BCG Growth-Share Matrix. Each unit is placed by market growth rate and relative market share into one of four quadrants (Stars, Cash Cows, Question Marks, Dogs), and the portfolio is assessed for cash-flow balance and reallocation.

The two axes, the four quadrants and their strategies, the underlying cash-flow logic, and the critiques live in [references/bcg.md](references/bcg.md). Load that file before analyzing and use its thresholds and definitions.

## When to use

The user has a set of business units or products and wants to decide where to invest, hold, harvest, or divest across them, or wants to see whether the portfolio is balanced. It needs a portfolio of two or more units; for a single market's competitive structure, prefer a Five Forces analysis.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **PORTFOLIO** (required): the business units or product lines to analyze.
- **DATA** (optional but valuable): for each unit, its market growth rate, its market share and the largest competitor's share (for relative share), and its revenue. Where data is missing, the analyst estimates it and lowers confidence rather than inventing precision.
- **CONTEXT** (optional): the company, the time horizon, and what decision the analysis informs.

## Orchestration map

```
Stage 1  Unit Placement   ── 1 analyst subagent per unit IN PARALLEL ──┐  (growth, relative share, size, quadrant)
Stage 2  Portfolio Synthesis ── 1 agent, needs all units ─────────────┘  (balance, cash flow, reallocation)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval to find market and share figures.

## Stage 1: Unit Placement (PARALLEL)

Dispatch one analyst subagent per unit, all at once. Give each the shared framing and one unit.

**Shared framing (send to each analyst):**

> Place this unit on the BCG matrix: **[UNIT]** (company context: [CONTEXT]). Determine, with evidence or a clearly labeled estimate:
> - **Market definition** used (state it; the placement depends on it)
> - **Market growth rate**, and whether it is high or low against the threshold
> - **Relative market share** (unit share divided by the largest competitor's share), and whether it is high or low against 1.0
> - **Revenue or size** of the unit
> - **Quadrant** (Star, Cash Cow, Question Mark, or Dog) with a one-line justification
> - **Confidence** (high, medium, low), lowered when figures were estimated

Collect all units before continuing, and re-dispatch any that fail. Decide and state the growth and share thresholds consistently across units so placements are comparable.

## Stage 2: Portfolio Synthesis (SEQUENTIAL, needs all units)

One agent assembles the portfolio view:

1. **Plot the portfolio.** Lay out every unit by quadrant with its growth, relative share, and size.
2. **Assess balance.** Is the portfolio self-funding? Are there Cash Cows generating surplus, Stars worth funding, and not too many Dogs or unfunded Question Marks? Name the imbalance if there is one (for example, no engine, or no future).
3. **Trace the cash flow.** Which units should fund which: Cash Cows funding Stars and the Question Marks worth backing.
4. **Recommend per unit.** Invest, hold, harvest, or divest, with the reasoning, and for Question Marks the harder build-or-divest call.
5. **Recommend portfolio moves.** Reallocation across units and the resulting shape over the horizon, flagging where a critique (market definition, profitability, synergy) changes the naive verdict.

## Report structure

Write a thorough markdown report and save it to `bcg-matrix-<company-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The company and portfolio, the thresholds used for both axes, the date, and a note that placements depend on market definition.
2. **The matrix.** A table or quadrant layout of all units with growth, relative share, size, and quadrant, scannable at a glance.
3. **Per-unit detail.** For each unit: the market definition, the data or estimates behind its placement, its quadrant, and its recommended strategy.
4. **Portfolio balance.** Whether the portfolio is self-funding, where the imbalance lies, and the cash-flow map.
5. **Recommendations.** Per-unit calls and portfolio-level reallocation, with the strategic exceptions noted.
6. **Caveats.** Market definition drives the result; relative share is a crude proxy for advantage; the matrix sees only two dimensions and misses profitability, synergy, and external forces; a Dog can be profitable and a Star can lose money. Use it to structure the decision, not to automate it.

## Principles

- **State the market definition.** It silently determines every placement. Make it explicit per unit.
- **Consistent thresholds.** Use the same growth and share cutoffs across all units, or the matrix is not comparable.
- **Balance over placement.** The deliverable is a funded, future-proof portfolio, not just four labeled lists. Trace the cash flows.
- **Estimate honestly.** Where data is missing, estimate and lower confidence; do not invent precise figures.
