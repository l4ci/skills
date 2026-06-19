# scarf

Reads a situation for social threat and reward using David Rock's SCARF model (*SCARF: A Brain-Based Model for Collaborating with and Influencing Others*, 2008). The model assumes the brain treats social experience much like physical survival, weighing every interaction across five domains. Status is your relative standing; Certainty is your ability to predict what comes next; Autonomy is your sense of control and choice; Relatedness is your sense of belonging and safety with others; Fairness is your read on whether exchanges are even-handed. A threat in any domain pushes people to pull away; a reward pulls them in.

This skill runs the read in parallel. Five analyst subagents each take one domain, assess what the situation does there for the people affected, mark the threat and the reward with evidence and a severity, and propose specific levers. A synthesis pass then ranks the threats, names the domains most at risk, and designs concrete moves that lower threat and add reward, prioritizing the few highest-leverage ones. The output is a saved markdown report with a per-domain read, a verdict on where it lands hardest, and an ordered list of what to do first.

SCARF gets misapplied in three ways, and the skill guards against each. People treat SCARF as hard science and report severities as if they were measured, when it is a heuristic for noticing social threat, not an instrument. People fix one domain while the real threat sits in another, polishing a plan when the wound was that no one was consulted. And people fall back on generic advice like "communicate more" instead of a domain-specific move. The skill caveats the science throughout, ranks by which domain carries the biggest threat, and forces every fix to name a domain and a concrete action. It also keeps the asymmetry in view: a threat fires harder than a reward, so removing one usually beats adding another.

## Starting

**You provide:** one concrete situation (a change, message, or decision) and, where you can, who is affected and from whose point of view to read the threat. A phrase like "Use SCARF on the reorg announcement I'm about to send."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the five domains, their threat and reward triggers, the levers, and the pitfalls are in [references/scarf.md](references/scarf.md).
