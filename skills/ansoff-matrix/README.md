# ansoff-matrix

Explores how a company or product should grow, using the Ansoff Matrix (Igor Ansoff, 1957). It maps growth along two axes, products (existing or new) and markets (existing or new), into four strategies of rising risk: Market Penetration (sell more of what you have to who you have), Market Development (existing products to new markets), Product Development (new products to existing customers), and Diversification (new products to new markets, the riskiest).

This skill runs the analysis in parallel. Four strategist subagents each work one quadrant, generating concrete, specific growth options (a named market, channel, segment, or product) with their risk, the capabilities they require, and rough investment and reward. A synthesis pass then ranks every option against the growth objective and sequences a realistic growth path, on the principle that cheaper, lower-risk growth is usually exhausted before higher-risk moves are justified. The output is a saved markdown report with the matrix, per-quadrant options, prioritized options, and a recommended growth path.

Two guardrails keep it honest: options must be concrete rather than restatements of a quadrant, and capability fit is treated as a source of risk equal to market novelty, since a move is only as good as the firm's ability to execute it.

## Starting

**You provide:** the company or product seeking growth (a growth objective and current markets/capabilities are optional but valuable). Invoke with something like "Work up an Ansoff matrix for our meal-kit subscription".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the four strategies, their risk profiles, and the pitfalls are in [references/ansoff.md](references/ansoff.md).
