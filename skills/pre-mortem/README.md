# pre-mortem

Stress-tests a plan, PRD, strategy, or decision before you commit to it. A pre-mortem uses prospective hindsight: imagine it is months from now and the plan has already failed, then work backward to explain why. Assuming the failure as a fact surfaces risks that asking "what could go wrong?" tends to miss.

This skill runs the exercise in parallel. Six independent failure-finder subagents each attack the plan from a different lens (execution, adoption, timeline, assumptions, second-order effects, external forces). A blind-spot pass catches what every lens missed. The risks are then deduplicated, scored by likelihood and impact, ranked, and the worst ones get concrete mitigations, leading indicators, and contingencies. The output is a saved markdown report with a ranked risk register.

It is the inverse of the [storm-research](../storm-research/) skill: the same fan-out engine, pointed at your own plan instead of the literature.

The procedure is in [SKILL.md](SKILL.md).
