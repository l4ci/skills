# value-chain-analysis

Analyzes how a company creates value and where its competitive advantage actually lives, using Porter's value chain (Competitive Advantage, 1985). The firm is broken into nine activities: five primary (inbound logistics, operations, outbound logistics, marketing and sales, service) and four support (firm infrastructure, HR, technology development, procurement). Advantage comes from specific activities and from how they link, not from the firm as a whole, and the gap between the value the output commands and the cost of the activities is the firm's margin.

This skill runs the analysis in parallel. One analyst subagent takes each activity, describing how the firm actually performs it and assessing its cost contribution, its value contribution, and whether it is an advantage, parity, or disadvantage versus competitors. A synthesis pass, read through the firm's chosen strategy (cost leadership or differentiation), locates where the advantage lives, finds the value leaks and weak links, and surfaces the linkages between activities that are hardest for rivals to copy. The output is a saved markdown report with a value-chain map, per-activity detail, and recommendations.

Two guardrails: every activity is assessed for cost and value rather than merely described, and advantage is always judged relative to competitors, since doing something well is no edge if every rival does it as well.

## Starting

**You provide:** the company or business unit and the strategy it pursues (cost leadership or differentiation), both required, plus optional competitors and known concerns. Something like "run a value chain analysis on our coffee roastery."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the activities, what to assess, and the role of linkages are in [references/value-chain.md](references/value-chain.md).
