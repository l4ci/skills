# pestel-analysis

Scans the macro-environment around a company, industry, market, or decision using PESTEL: the Political, Economic, Social, Technological, Environmental, and Legal forces that shape a market but lie outside any single firm's control. It is the macro layer of strategy analysis, sitting above industry forces and a firm's own position.

This skill runs the scan in parallel. Six analyst subagents each take one factor and identify the forces that actually bear on the subject, with each force's direction, timeframe, whether it is an opportunity or a threat, and how certain it is. A synthesis pass then prioritizes the forces by impact crossed with certainty (separating what to act on from what to merely monitor), maps the chains where forces across factors add up to a larger movement, and draws the implications. The output is a saved markdown report led by the priority forces, with per-factor detail and an opportunities-and-threats list ready to feed a SWOT.

The skill guards against the framework's most common failure, the unranked laundry list, by forcing prioritization and a "so what" on every force, and by keeping the analysis at the macro altitude rather than drifting into competitors or the company itself.

The procedure is in [SKILL.md](SKILL.md); the six factors, the prioritization logic, and the pitfalls are in [references/pestel.md](references/pestel.md).
