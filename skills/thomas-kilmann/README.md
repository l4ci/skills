# thomas-kilmann

Helps you decide how to handle a specific conflict, using the Thomas-Kilmann Conflict Mode Instrument from Kenneth Thomas and Ralph Kilmann. The TKI places conflict behavior on two axes: assertiveness, or how much you push for your own goals, and cooperativeness, or how much you work to satisfy the other party's. The two axes produce five modes: Competing (assertive, uncooperative), Collaborating (assertive, cooperative), Avoiding (unassertive, uncooperative), Accommodating (unassertive, cooperative), and Compromising in the middle. The instrument's founding claim is that none of them is best: each fits some situations and fails in others.

This skill runs the analysis in parallel. First it pins down the situation: the stakes for each side, the power balance, how much the relationship matters, the time pressure, and the trust between the parties. Then five analyst subagents each take one mode and judge how well it fits those exact facts, with pros, cons, a likely outcome, and a fit score. A synthesis pass ranks the modes, recommends a primary mode and a fallback for when it stalls, and turns the choice into concrete things to say and do. The output is a saved markdown report with a verdict, the situation, the five mode assessments, and the recommendation.

Three misuses are common, and the skill guards against them. People treat one mode as universally right, usually chronic collaborating, which wastes time on issues that do not deserve it, or chronic avoiding, which lets conflicts fester. People also ignore the realities of power and time, chasing a win/win when they have no leverage or no clock. And people misuse the instrument to label personalities instead of choosing an approach for the situation in front of them. The skill anchors every judgment to the situational factors, refuses a universal favorite, and ends by flagging when the user's habitual style is the wrong fit for this particular conflict.

## Starting

**You provide:** the conflict to navigate (the parties, what each wants, what's at stake), plus any context on power, the relationship, time, and your own habitual style. Something like "Help me handle this conflict with a co-founder using Thomas-Kilmann".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the two axes, the five modes with their fits and risks, and the pitfalls are in [references/thomas-kilmann.md](references/thomas-kilmann.md).
