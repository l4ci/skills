# key-assumptions-check

Surfaces and stress-tests the assumptions an analysis, plan, or forecast is silently resting on, using the Key Assumptions Check (KAC) — one of the foundational structured analytic techniques codified by Richards Heuer and Randolph Pherson in *Structured Analytic Techniques for Intelligence Analysis*.

KAC is built to defeat a quiet failure: a confident conclusion stands on a foundation of assumptions the analyst never noticed making, and when one of them breaks, the whole thing collapses — because the assumption was never on the table to be questioned. KAC drags every premise into the open, tests it, and tells you which ones the answer actually depends on.

This skill runs KAC inside an agent and parallelizes it. It fans out subagents to surface the full set of assumptions from several stances (including the cultural defaults and the unstated leaps), restates each as an explicit testable proposition, then tests each one with an independent mind committed to breaking it — how much confidence is warranted, on what basis, and under what conditions it fails. It classifies the assumptions as solid, caveated, or unsupported, names the few linchpins the conclusion hangs on, and reports what to verify and what to monitor.

It is the natural partner to [analysis-of-competing-hypotheses](../analysis-of-competing-hypotheses/): ACH tests which hypothesis the evidence supports; KAC tests the assumptions both the analysis and the evidence rest on. It also pairs with the [pre-mortem](../pre-mortem/), which imagines those fragile premises actually failing.

The skill itself lives in [SKILL.md](SKILL.md).
