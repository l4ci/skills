# fermi-estimation

Produces a defensible, order-of-magnitude estimate of a quantity with no data at hand, using Fermi estimation, the method named for the physicist Enrico Fermi, famous for answering seemingly unanswerable questions ("how many piano tuners are there in Chicago?") by decomposing them into factors he could each guess roughly. It works because of how the errors behave: when you break a quantity into a chain of independent estimated factors, the over- and under-estimates tend to cancel, so a product of rough guesses is far more accurate than one rough guess at the whole.

The method handles two opposite failures. One is the blind guess: a number from nowhere, impossible to interrogate. The other is the refusal ("we have no data, so we can't say"). You can always get an auditable answer good to roughly an order of magnitude by decomposing the unknown into knowable pieces and being honest about the range on each.

This skill runs Fermi estimation inside an agent and parallelizes it. It fans out subagents to decompose the quantity several independent ways, estimates each leaf factor as a low/best/high range with its basis, multiplies the chain and propagates the uncertainty into an honest band, then cross-checks the result against a second decomposition and known bounds, and names the one factor whose uncertainty dominates the answer.

Pairs with [reference-class-forecasting](../reference-class-forecasting/) as the inside-view approach: Fermi builds the estimate up from components, while reference-class anchors it on how similar cases actually turned out. Running both and reconciling them is a strong cross-check.

The skill itself lives in [SKILL.md](SKILL.md).
