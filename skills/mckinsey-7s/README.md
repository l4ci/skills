# mckinsey-7s

## What this is

The McKinsey 7-S framework holds that organizational effectiveness comes from the alignment of seven interdependent elements: Strategy, Structure, and Systems (the "hard" elements) and Shared Values, Skills, Style, and Staff (the "soft" elements). It grew out of work at McKinsey around 1980 by Tom Peters, Robert Waterman, Richard Pascale, and Anthony Athos; the canonical write-up is Waterman, Peters, and Phillips, "Structure is not organization" (Business Horizons, 1980). There is no hierarchy among the elements, with Shared Values at the center connecting the rest. They are interdependent: change one and the others must realign, or the change fails.

The seven elements, the hard/soft split, and the alignment checks live in [references/seven-s.md](references/seven-s.md).

## What it does

The skill runs the analysis in parallel. Seven analyst subagents each assess one element from the evidence (current state, plus the desired state and gap when a change is in play), then a synthesis pass maps the fit between elements, surfaces where they conflict, ranks the misalignments by impact, and recommends fixes along with the knock-on adjustments each fix forces. The output is a saved markdown report with a per-element summary, an alignment analysis, and ranked misalignments.

Two rules keep it honest. The analysis describes what is actually true rather than what the organization aspires to, which matters most for the soft elements. And every fix names its ripple to the other elements, since the elements are interdependent and changing one affects the rest.

## When to use it

Reach for this to diagnose underperformance, plan or sequence a major change, integrate after a merger, or realign after a strategy shift. The unit of analysis is an organization or a unit within one, not a market or a product.

- For value creation and cost across the firm's activities rather than internal alignment, use [value-chain-analysis](../value-chain-analysis/).
- For an individual change-readiness diagnosis rather than whole-org alignment, use [adkar](../adkar/).
- For a step-by-step way to drive a change once the misalignments are clear, use [kotter-change](../kotter-change/).
- For digital capability specifically rather than general alignment, use [digital-maturity-assessment](../digital-maturity-assessment/).

## How to get started

**You provide:** the organization or unit to assess, and why you're running it (diagnose underperformance, plan a change, integrate a merger; name the future state for a change). Something like "Run a 7-S on our company after the acquisition."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md).
