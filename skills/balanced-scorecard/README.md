# balanced-scorecard

The Balanced Scorecard, from Robert Kaplan and David Norton (Harvard Business Review, 1992), translates a strategy into objectives and measures across four perspectives: Financial, Customer, Internal Process, and Learning & Growth. The idea is to steer a business by more than its financial numbers, which only report results after the fact, and to tie every measure back to the strategy through a chain of cause and effect rather than collecting metrics for their own sake.

This skill runs the analysis in parallel. Four analyst subagents each take one perspective and derive, from the stated strategy, a few objectives, the measures that track them, the targets to hit, and the initiatives to get there. A synthesis pass then builds the strategy map, reading bottom-up so that the capabilities in Learning & Growth drive the Internal Processes that deliver the Customer value proposition that produces Financial results. It checks that every objective traces to the strategy, that leading and lagging indicators are balanced, and prunes the list to the measures that matter.

The framework fails in predictable ways, so the synthesis guards against them. A wall of KPIs with no strategy map behind it is a dashboard, not a scorecard, so the cause-effect links are built explicitly and objectives with no enabler below or payoff above are flagged. A scorecard of only financial lagging measures steers by the rear-view mirror, so the balance of leading and lagging is checked. And because every function wants its metric on the board, the measures are cut to a vital few per perspective. The output is a saved markdown report with the four-perspective scorecard table, the strategy map, and the caveats.

## Starting

**You provide:** the organization and the strategy being translated (a vague strategy gets drawn out first; unit level and horizon are optional). Invoke with something like "Turn our retention-led strategy into a balanced scorecard".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the four perspectives, the strategy-map logic, and the pitfalls are in [references/scorecard.md](references/scorecard.md).
