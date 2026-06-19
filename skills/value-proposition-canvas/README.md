# value-proposition-canvas

Runs a Value Proposition Canvas for one offering and one customer segment, testing whether the two fit. The canvas comes from Alexander Osterwalder, Yves Pigneur, Greg Bernarda, and Alan Smith (*Value Proposition Design*, 2014) and zooms into two blocks of the Business Model Canvas, Value Propositions and Customer Segments. It has two halves: the Customer Profile, where you describe the customer's jobs, pains, and gains; and the Value Map, where you describe the offering's products and services, pain relievers, and gain creators. Fit is the match between them.

This skill runs the analysis in parallel. Six analyst subagents work the two sides at once: three describe and rank the Customer Profile, three describe the Value Map, and all mark every claim a fact or an assumption still to be tested. A fit-assessment pass then ranks the customer side and checks the match: which of the customer's most important jobs, severest pains, and most-wanted gains the value map actually addresses, which it misses, and which relievers and creators chase pains and gains nobody ranks highly. The output is a saved markdown report with both sides laid out, a fit verdict at the right level, and the riskiest assumptions called out.

The framework fails in one predictable way, and the skill guards against it: people fill the value map with relievers and creators for pains and gains the customer does not care much about, producing a polished answer to the wrong question. The guard is the ranking. The customer side is ranked by importance to the customer before the value side is touched, and the value side is then mapped onto that ranking, so effort aimed at minor items is exposed rather than hidden. The skill is also explicit about what a canvas can show: it establishes problem-solution fit on paper, not product-market fit (which needs market evidence) and not business-model fit (which needs the Business Model Canvas).

## Starting

**You provide:** the one offering to test and the one customer segment it's aimed at (both required), plus optional context like stage, evidence available, and the decision it should inform. Something like "build a Value Proposition Canvas for our app."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the two sides, the ranking rule, the fit-check table, and the pitfalls are in [references/value-proposition.md](references/value-proposition.md).
