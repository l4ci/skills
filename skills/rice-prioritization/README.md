# rice-prioritization

Ranks a backlog of product initiatives by RICE = (Reach × Impact × Confidence) / Effort, the scoring model Intercom built to sequence its roadmap without the loudest voice winning. Each item gets one comparable number: how many people or events it reaches in a fixed window, how much it moves a single goal, how confident the estimate is, and how much whole-team effort it costs. Higher score, do first. The score is a rate, so a cheap win can outrank a large feature that costs a year of work.

This skill runs the scoring in parallel. It first calibrates with the user: the goal, the Reach time window and its data source, the Impact multiplier scale, the Confidence levels, and the Effort unit. It writes those down before touching any item, the same way a weighted matrix locks its weights before scoring. Then one scorer subagent per initiative estimates the four factors against those fixed definitions, each with a rationale and its stated evidence or assumption, lowering Confidence rather than inventing data. A synthesis pass computes the scores, ranks them, and runs a sensitivity check.

Four mistakes recur, and the skill guards against each. People treat Reach as a measured fact when it is a guess about the future; they skip Confidence, the very factor that penalizes wishful thinking; they underestimate Effort, which sits in the denominator and silently inflates the score; and they compare items whose Reach uses different time windows. Calibration catches the window and goal mismatches, Confidence stays mandatory and caps below-50% items at "go validate," and the synthesis varies Confidence and Effort, the two factors that swing the ranking hardest, to flag any high-rank item that rests on an optimistic estimate as "validate before committing."

## Starting

**You provide:** the backlog of initiatives to rank, plus the one goal Impact is measured against. A phrase like "Run RICE on our Q3 backlog."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the formula, the four factors, their scales, the Confidence bias check, and the pitfalls are in [references/rice.md](references/rice.md).
