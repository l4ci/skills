---
name: weighted-decision-matrix
description: Use when the user wants to choose among several options against multiple weighted criteria with a transparent, defensible score (the weighted scoring model or Pugh matrix). Calibrates the criteria, their weights, and the scoring scale first, then scores each option in parallel, one subagent per option, before computing weighted totals, ranking, and running a sensitivity check in a markdown report. Triggers include "decision matrix", "weighted scoring", "Pugh matrix", "compare options against criteria", "which option should we choose", "weighted decision model", "selection matrix".
---

# weighted-decision-matrix

Chooses among several options against multiple weighted criteria, turning a fuzzy "which is best" into a transparent score: define the criteria, weight them before scoring, score each option on each criterion, sum weight times score, rank, and check whether the winner survives a reweight. Stuart Pugh's comparative variant scores each option as better, same, or worse than a baseline. The matrix informs the decision; it does not make it.

The method, how to pick independent and covering criteria, why weights come before scores, the scoring scales, the weighted-sum computation, the Pugh +/S/- variant, sensitivity analysis, and the pitfalls live in [references/decision-matrix.md](references/decision-matrix.md). Load that file before calibrating and scoring.

## When to use

The user is choosing between named alternatives and wants the choice scored against several things that matter, not decided by gut alone. This generalizes [impact-feasibility-matrix](../impact-feasibility-matrix/SKILL.md) from two fixed axes (impact and effort) to N weighted criteria: use impact-feasibility when the two axes are exactly impact and effort, and use this skill when the criteria are many or specific to the decision. If there is only one option there is nothing to compare; if the options do not yet exist, generate them first, since this skill scores an existing set.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework and scoring keyed to it regardless of the output language.

## Inputs

- **DECISION** (required): what is being chosen, and the **OPTIONS** being chosen between. If only the decision is given without alternatives, ask for the options first.
- **CRITERIA** (optional): the criteria and any known weights. If absent, derive them with the user in Stage 1.
- **CONTEXT** (optional): constraints (budget, deadlines, hard requirements), and the decision-maker's priorities, which set the weights.

## Orchestration map

```
Stage 1  Calibrate     ── fix criteria, weights, and scale WITH the user (inline)
Stage 2  Score options ── 1 scorer subagent per option IN PARALLEL ──┐  (score per criterion, with rationale)
Stage 3  Synthesis     ── 1 agent, needs all options ────────────────┘  (totals, ranking, sensitivity, verdict)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Scorers should use available retrieval tools to ground scores in real figures.

## Stage 1: Calibrate (inline, with the user)

Before any scoring, fix three things and write them down:

1. **Criteria.** What the decision depends on. Keep them independent (no two measuring the same thing) and together covering (nothing decisive left out). State in one line what each criterion means, so a high and a low score are not a matter of taste. If the user supplied criteria, check them for overlap and gaps; if not, derive them from the decision and context.
2. **Weights, set now.** Assign each criterion an importance (percentages summing to 100, or a 1-to-5 importance) from the decision-maker's priorities, **before any option is scored**. Setting weights after seeing scores is the easiest way to rig the result, so lock them here.
3. **Scoring scale.** One fixed scale for every cell (default 1-to-5; use 1-to-10 only if options are close, or the Pugh +/S/- variant for comparative concept selection against a baseline). Anchor the ends so every scorer means the same thing by a 5 and a 1.

Drop any option that fails a hard constraint now, rather than scoring it. Skipping this stage is the framework's main failure mode: unanchored criteria and after-the-fact weights just encode bias.

## Stage 2: Score options (PARALLEL)

Dispatch one scorer subagent per option, all at once, each given the calibrated criteria, weights, and scale, plus its one option. The scorers do not see each other, so each scores its option on the absolute scale, not relative to the others.

**Shared framing (send to each scorer):**

> Score one option for this decision: **[DECISION]**. Score it on each of these criteria, using these definitions and this scale: **[calibrated criteria, weights, and scale]**. Option: **[OPTION]**. For each criterion, give the score and a one-line rationale with the evidence or assumption behind it; do not pad weak evidence, lower confidence instead. Then return:
> - **Per-criterion scores**: each criterion, the score, and its rationale or evidence
> - **Strongest and weakest criterion** for this option, and why
> - **Confidence** (high, medium, or low), lowered where evidence was thin or unavailable
>
> Context: [CONTEXT]

Collect all options before continuing. Re-dispatch any scorer that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all options)

One agent assembles the ranked decision:

1. **Reconcile for consistency.** The parallel scorers did not see each other, so check that scores are comparable across options. Adjust any cell scored on a different implicit scale and note the adjustment. Do not touch the weights; they were fixed in Stage 1.
2. **Compute weighted totals.** For each option, sum (weight x score) across the criteria. Rank the totals.
3. **Run the sensitivity check.** Vary the most important weights up and down by a plausible margin and re-rank. Report whether the winner holds (robust) or flips (fragile). For a close top pair, find the break-even weight where they swap.
4. **Surface the decisive criteria and the close calls.** Name which criteria most separate the top options, and report near-ties as ties: a 3.8 versus a 3.9 is within the method's precision, not a verdict.
5. **Recommend, with caveats.** Give a recommendation tied to the context, name what would change it (a reweight, a missing criterion, a hard constraint), and state that the matrix informs the call rather than making it.

## Report structure

Write a thorough markdown report and save it to `decision-matrix-<decision-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The decision, the options, the date, and a one-line note on the framework. State the calibrated criteria, their weights, and the scoring scale up front, since the result is only as good as these.
2. **Verdict.** The recommended option in a few sentences, with the ranking and whether it is robust or a close call.
3. **The scored matrix.** A table with criteria as rows (weight in a column) and options as columns, every cell scored, and a weighted-total row at the bottom. Scannable at a glance.
4. **Per-option detail.** For each option: its total and rank, its strongest and weakest criteria, the rationale behind the notable cells, and its confidence.
5. **Sensitivity note.** How the ranking moves as the weights vary, whether the winner holds, the break-even weight for any close pair, and which criteria are decisive.
6. **Recommendation.** The choice tied to the context, the caveats that qualify it, and what would flip it.
7. **Caveats.** Scores are judgment anchored to a stated scale, not measurement; near-ties are real ties, not a defect; weights encode whose priorities the decision serves; an omitted criterion is invisible no matter how clean the arithmetic; and hard constraints or a strategic must-do can legitimately override a higher score.

## Principles

- **Criteria first, independent and covering.** No two criteria measuring the same thing (no double-counting), and nothing decisive left out. Weak criteria produce a confident wrong answer.
- **Weights before scores.** Lock the weights from priorities before any option is scored. Changing them afterwards is a disclosed sensitivity test, never a silent edit.
- **Every score earns a rationale.** A number with no reason is a guess wearing a number. Use evidence where retrieval allows, a stated assumption otherwise, and lower confidence rather than inventing figures.
- **Near-ties are information.** A close result means the options are genuinely close and the choice rests on a criterion you trust, not on a defect in the matrix. Do not manufacture a winner the numbers do not support.
- **Sensitivity, always.** Report whether the winner survives a reweight. A fragile winner that looks solid is the costliest output.
- **The matrix informs, it does not decide.** The total is an input to judgment. Hard constraints, strategic must-dos, and a missing criterion can override the top score.
- **Parallel where independent.** Options are scored concurrently, then reconciled together for consistency before ranking.
