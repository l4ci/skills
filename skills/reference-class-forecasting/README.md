# reference-class-forecasting

Forecasts a duration, cost, success rate, or outcome by anchoring on how similar past cases actually turned out, using reference-class forecasting — the discipline grounded in Daniel Kahneman and Amos Tversky's *inside view vs outside view*, and operationalized for real planning by Bent Flyvbjerg, who used it to expose the chronic cost and schedule overruns of large projects. It treats your case not as a unique story to reason about from its details, but as one instance of a class of comparable efforts whose realized outcomes are the most reliable anchor available.

The method exists to defeat the **planning fallacy**: forecasting from the inside view — the specific plan, the specific team, the reasons this time will go smoothly — systematically underestimates time and cost and overstates success, because the inside view sees the plan but not the unknown unknowns that derailed every comparable effort. The outside view corrects this by starting from the base rate: how cases *like this* actually turned out, before adjusting for anything special about yours.

This skill runs reference-class forecasting inside an agent and parallelizes it. It fans out subagents to build a reference class several ways (balancing similarity against sample size), constructs the empirical distribution of how that class actually performed, then places the case in that distribution under adversarial review — a regression-to-the-mean critic and an optimism critic that keep the adjustments small and evidence-backed. It reports the base rate, the forecast as a distribution, and the planning-fallacy gap between the inside-view estimate and the outside view.

It is the outside-view complement to [fermi-estimation](../fermi-estimation/): Fermi builds an estimate up from the case's own specifics, while reference-class anchors on how the class performed — running both and reconciling the gap is a strong cross-check.

The skill itself lives in [SKILL.md](SKILL.md).
