# swot-analysis

Runs a SWOT analysis of a company, product, project, team, or decision, then turns it into strategy. SWOT sorts the factors bearing on a goal into four quadrants: Strengths and Weaknesses (internal) and Opportunities and Threats (external). On its own, that is just four lists. The value comes from the TOWS matrix, which crosses the quadrants into concrete strategic options.

This skill runs the analysis in parallel. Four analyst subagents each take one quadrant, ground their factors in evidence, and prioritize them by magnitude (and likelihood for the external quadrants). A synthesis pass then validates that each factor sits on the right axis, builds the TOWS matrix (SO, ST, WO, WT), and ranks the resulting options by impact and feasibility. The output is a saved markdown report with the SWOT grid, prioritized quadrants, the TOWS strategy matrix, and ranked recommendations.

Two rules keep it honest: every factor is judged against a stated objective, and internal attributes never get filed as external conditions. Both are common SWOT failures the skill guards against.

## Starting

**You provide:** what's being analyzed and the objective the SWOT serves (plus any context on competitors and horizon). Something like "Run a SWOT on our meal-kit startup, to decide whether to expand into California".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the framework, checklists, scoring, and TOWS logic are in [references/framework.md](references/framework.md).
