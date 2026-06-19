# hoshin-kanri

Deploys a strategy into aligned, measurable action using Hoshin Kanri, the strategy-deployment method from Japanese Total Quality Management formalized by Yoji Akao in the 1960s and 1970s (also called policy deployment). It rests on two ideas: the vital few, where a year's strategy is concentrated into three or four breakthrough objectives rather than spread across everything, and catchball, where objectives and targets are negotiated up and down the organization so the people who must deliver them help shape them. Its central artifact is the X-matrix, a single page linking breakthrough objectives, annual objectives, improvement priorities, measurable targets, and owners, with correlation marks showing how each leg connects to the next.

This skill runs the cascade in parallel. It first sets the breakthrough objectives and this year's annual objectives with the user, holding the line on the vital few, then dispatches one strategist subagent per annual objective to develop its improvement priorities, measurable targets, owners, and the pushback the working level would raise. A synthesis pass then builds the X-matrix, marks the correlations, traces the golden thread so every priority and target ties back to a breakthrough objective, flags the orphans on either side, and sets the catchball rounds and the PDCA review cadence.

The method fails in predictable ways, and the skill is built against them. Teams cascade too many objectives and lose the focus that is the whole point, so Stage 1 pushes back toward three or four. Plans get handed down without catchball, so the strategists surface the realistic pushback before anything is committed. Activities get logged as targets, so every priority must earn a number with a level and a date. And the matrix gets built once and filed, so the report ends in a tracking and review rhythm rather than a static grid. Works alongside the lighter [okr](../okr/) method and the [balanced-scorecard](../balanced-scorecard/) as the TQM option, and it reviews on the [pdca-cycle](../pdca-cycle/).

## Starting

**You provide:** the organization deploying the strategy and the strategy or breakthrough objectives themselves; optionally the planning horizon, the levels to cascade through, and any fixed constraints. Something like "run a Hoshin Kanri on our new strategy".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the X-matrix, catchball, the review cadence, and the pitfalls are in [references/hoshin.md](references/hoshin.md).
