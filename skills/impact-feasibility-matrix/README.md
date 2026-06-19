# impact-feasibility-matrix

Prioritizes a list of initiatives, ideas, features, or projects by plotting them on two axes, impact and feasibility, and sorting them into four quadrants: quick wins (high impact, high feasibility, do first), major projects (high impact, low feasibility, plan and stage), fill-ins (low impact, high feasibility, spare capacity only), and thankless tasks (low impact, low feasibility, drop). Also known as the impact-effort matrix.

This skill starts by calibrating the axes, stating exactly what impact means for the stated objective and what drives feasibility (effort, cost, risk, dependencies), because unanchored scores just encode bias. It then scores every option in parallel, one subagent per option, deliberately pessimistic about feasibility. A synthesis pass recalibrates the scores for consistency (the parallel scorers did not see each other), places the quadrants, maps dependencies between options, and produces a sequenced plan rather than four unordered piles. The output is a saved markdown report with the matrix, scored options, and a recommended order of action.

The skill guards against two classic failures of the framework. Undefined axes are handled by the calibration step, and optimism on effort is handled by prompting scorers to probe what could make each option harder. Often the most useful output is a clear case for stopping the thankless work.

## Starting

**You provide:** the list of options to prioritize and the objective impact is measured against; optionally the resources, constraints, timeframe, and known dependencies. Something like "prioritize these by impact and feasibility".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the axes, quadrants, and scoring guidance are in [references/impact-feasibility.md](references/impact-feasibility.md).
