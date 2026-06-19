# bcg-matrix

Analyzes a portfolio of business units or product lines with the BCG Growth-Share Matrix (Boston Consulting Group, 1970). Each unit is placed on two axes, market growth rate and relative market share, landing it in one of four quadrants: Stars (high growth, high share), Cash Cows (low growth, high share), Question Marks (high growth, low share), and Dogs (low growth, low share). Each quadrant implies a move: invest, milk, build-or-divest, or release.

This skill runs the analysis in parallel. One analyst subagent places each unit, stating the market definition it used, finding the growth rate and the relative share against the largest competitor, and sizing the unit by revenue. A synthesis pass then assesses whether the portfolio is self-funding, traces which units should fund which (Cash Cows funding Stars and the Question Marks worth backing), and recommends per-unit and portfolio-level moves. The output is a saved markdown report with the matrix, per-unit placements, and a cash-flow balance assessment.

The skill carries the framework's well-known critiques into the analysis: market definition drives every placement, relative share is a crude proxy for advantage, and a Dog can be profitable while a Star loses money. The matrix structures the portfolio decision; it does not automate it.

## Starting

**You provide:** the portfolio of two or more business units or product lines (growth, share, and revenue data are optional but valuable; estimated where missing). Invoke with something like "Run a BCG matrix across our product portfolio".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the axes, quadrants, cash-flow logic, and critiques are in [references/bcg.md](references/bcg.md).
