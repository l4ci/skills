# three-horizons

Manages growth and innovation across time using McKinsey's Three Horizons model (Baghai, Coley, and White, The Alchemy of Growth, 1999). Initiatives are split into three horizons by maturity: Horizon 1, the mature core that produces today's cash and must be defended and optimized; Horizon 2, the emerging businesses gaining customers that should be built into the next core; and Horizon 3, the nascent options and experiments that seed the future. The point of the model is simultaneity: a healthy organization funds all three at once.

This skill runs the analysis in parallel. Three analyst subagents each take one horizon, place the relevant initiatives by maturity stage, and assess the horizon's health, its gaps, and how it should be measured. A synthesis pass then checks the portfolio balance (naming the common pathology where the certain, measurable core starves the future), traces whether the pipeline flows inward over time, prescribes how investment should shift, and sets out why each horizon needs its own funding and metrics. The output is a saved markdown report with a horizon map, per-horizon detail, and a balance-and-pipeline verdict.

Two distinctions keep it honest: horizons are stages of maturity, not calendar periods, so a long-dated project already winning customers is Horizon 2; and an empty Horizon 3 is treated as a finding (no future options), not a section to skip.

## Starting

**You provide:** the organization in scope and, ideally, its current and proposed initiatives (plus any context on growth ambition and industry pace). Something like "Map our product portfolio onto the three horizons".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the three horizons, the balance and pipeline logic, and the pitfalls are in [references/three-horizons.md](references/three-horizons.md).
