# root-cause-analysis

Finds and verifies the root cause of a problem instead of patching its symptom. It combines two classic tools: Kaoru Ishikawa's fishbone (cause-and-effect) diagram, which sorts possible causes into categories so the search covers everything; and the 5 Whys, popularized at Toyota, which drills a candidate cause down through repeated "why" questions until it reaches a cause you can actually act on. The default category set is the 6 Ms used in manufacturing and operations: People, Machine, Method, Material, Measurement, and Environment, with service variants (the 4 Ps and 8 Ps) for process and service problems.

This skill runs the cause search in parallel. It first states the problem precisely as the "head" of the fish, quantified where the data allows, and picks the category set. Then a finder subagent takes each category and brainstorms the candidate causes that live there, with the mechanism for each and any supporting evidence, ranked strongest first. A final pass pools the candidates across every category, drills the strongest with why-chains to reach root causes, verifies each against the timeline and the data, separates root causes from merely contributing ones, and recommends countermeasures that remove the roots. The output is a saved markdown report with the full fishbone, the why-chains, the verification, and ranked countermeasures.

A root-cause hunt fails in a few recurring ways, and the skill guards against each. People stop at the symptom, or fixate on the first cause that comes to mind and never look in the other categories, or quietly settle on "human error" and assign blame instead of finding the system cause that let the error through. The 5 Whys, run alone, often collapses into a single unverified linear guess that feels rigorous because it has five steps. The skill scans every category before drilling, branches the why-chains, and verifies each claimed cause against evidence before concluding. It also holds the line that a fishbone only lists possible causes and a why-chain is only a hypothesis until the evidence backs it.

## Starting

**You provide:** one precisely stated effect to diagnose (quantified where possible), plus any data, logs, or context on when it occurs and what changed. A phrase like "Run an RCA, our checkout API has been timing out since Tuesday."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the fish head, the category sets, the 5 Whys discipline, the verification tests, and the pitfalls are in [references/root-cause.md](references/root-cause.md).
