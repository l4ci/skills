# Weighted decision matrix: method, the Pugh variant, and sensitivity

The weighted scoring model (also called a decision matrix or weighted decision matrix) chooses among several options against multiple criteria. Stuart Pugh formalized the comparative variant in his concept-selection work (*Total Design*, 1991; the method dates to his teaching in the early 1980s). The idea is plain: a "which is best" question that feels like a hunch becomes a score you can show, defend, and argue with. The matrix informs the decision. It does not make it.

The unit of analysis is a **choice between named options**. If there is only one option, there is nothing to score; if the options are not yet known, generate them before scoring.

## The method, step by step

1. **List the options.** The alternatives actually on the table. Drop any that fail a hard constraint (out of budget, illegal, technically impossible) before scoring, rather than letting the matrix re-discover that they are bad.
2. **Define the criteria.** What the decision depends on. Criteria should be **independent** (so nothing gets counted twice) and **together cover** what matters (so nothing decisive is left out). State what each criterion means in one line, so a high score and a low score are not a matter of taste.
3. **Weight the criteria, before any scoring.** Assign each criterion an importance: percentages summing to 100, or a 1-to-5 importance, or points to spend. Set the weights from the decision-maker's priorities, *before* anyone scores an option, so the weights cannot be quietly tuned to crown a favourite.
4. **Score each option on each criterion.** Use one fixed scale for every cell (1-to-5 or 1-to-10), with a short rationale or piece of evidence per cell. A score with no rationale is a guess wearing a number.
5. **Compute the weighted sum.** For each option, sum (weight x score) across the criteria, and rank the totals.
6. **Sensitivity check.** Vary the weights and re-rank. If the winner survives plausible changes, it is robust; if a small reweight flips it, the result is fragile and the two top options are effectively tied.

## Choosing criteria that are independent and covering

The criteria are the spine of the matrix; weak criteria produce a confident-looking wrong answer.

- **Independent (no overlap).** Two criteria that measure the same underlying thing double-count it. "Cost" and "price" are the same axis; "running cost" and "purchase cost" are not. If two criteria always move together across the options, fold them into one. (This is the no-overlap half of a MECE split: criteria should not overlap each other.)
- **Covering (nothing decisive missing).** The criteria together should span what the decision turns on. A criterion that would change the ranking if added, but was left out, is the most expensive mistake in the method. Ask: "If the winner scored worst on something not in this list, would we still pick it?" If no, that something is a missing criterion.
- **Decision-relevant, not generic.** Use criteria that discriminate between *these* options. A criterion every option scores identically on adds weight noise and no signal; drop it or note it as an entry requirement instead.
- **Right number.** Enough to cover the decision, few enough to weight honestly. Many criteria tend to dilute the few that actually matter; if one criterion clearly dominates, say so rather than burying it among ten near-zero-weight others.

## Why weights come before scores

Setting weights after seeing the scores is the single easiest way to rig a matrix without lying. Once you know option B wins on speed, nudging speed's weight up "because speed really does matter here" backfills a conclusion you already wanted. Fix the weights from priorities first, write them down, and treat changing them afterwards as a sensitivity test you disclose, not a silent edit. The weights encode whose priorities the decision serves; make that explicit.

## Scoring scales

Pick one scale and use it for every cell:

| Scale | When to use |
|---|---|
| 1-to-5 | Default. Coarse enough to score honestly, fine enough to separate options. |
| 1-to-10 | When options are close and 1-to-5 collapses them into ties. |
| Pugh +/S/- | Comparative concept selection against a baseline (see below). |

Anchor the ends so scorers agree on what a 5 and a 1 mean for each criterion (a 5 on cost = cheapest plausible option; a 1 = breaks the budget). Score with evidence where it exists and a stated assumption where it does not; lower confidence rather than inventing a figure.

## The weighted-sum computation

For each option, the total is the sum over criteria of (criterion weight x option's score on that criterion). Rank options by total. A worked mini-matrix, choosing a database for a small service, weights as percentages, scores 1-to-5:

| Criterion | Weight | Option A | Option B | Option C |
|---|---|---|---|---|
| Operational cost | 40% | 4 | 2 | 5 |
| Team familiarity | 30% | 5 | 3 | 2 |
| Scaling headroom | 20% | 2 | 5 | 4 |
| Ecosystem / tooling | 10% | 3 | 5 | 3 |
| **Weighted total** | | **3.8** | **3.2** | **3.7** |

A's total: 0.40(4) + 0.30(5) + 0.20(2) + 0.10(3) = 3.8. C comes in just behind at 0.40(5) + 0.30(2) + 0.20(4) + 0.10(3) = 3.7. That near-tie is not a defect: A and C are genuinely close, and the decision now rests on which of "team familiarity" (A) or "operational cost and scaling" (C) the decision-maker trusts more. The matrix has narrowed three options to a real two-way choice and named the criterion that breaks it.

## The Pugh variant (+ / S / -)

When the job is comparative concept selection rather than absolute scoring, use Pugh's method:

1. Pick a **baseline** (reference) option, often the incumbent or the simplest candidate.
2. Score every other option against the baseline on each criterion as **better (+)**, **same (S)**, or **worse (-)**. The baseline is all S by definition.
3. Tally the +'s and -'s per option (weighted by criterion if you want), giving a net comparative score.
4. Read the pattern, not just the net. A column of +'s with one hard - tells you where each concept is strong and where it pays its price. Often the best move is to hybridize: take the winning concept and fix its one - by borrowing from another.

Pugh is faster than absolute scoring, harder to fake (relative judgments are easier to defend than "this is a 7"), and built for iterating concepts rather than declaring a final number. Use it early in option selection; use weighted-sum when you need a defensible ranking with stated magnitudes.

## Sensitivity analysis

A single set of weights gives a single ranking; sensitivity asks whether that ranking is real or an artifact of the exact weights chosen.

- **Vary the weights.** Move the most important criterion's weight up and down by a plausible margin and re-rank. Try the decision-maker's weights and a sceptic's weights.
- **Watch for flips.** If the winner holds across plausible weights, report it as robust. If a small change flips the winner, the top options are effectively tied and the choice is really about which criterion you trust, not which option scored higher.
- **Find the break-even.** For a close pair, the weight at which they swap is informative: "B wins only if speed is worth more than 35% of the decision" turns a fuzzy result into a sharp question the decision-maker can actually answer.
- **Report close calls as close.** A 3.8 versus a 3.9 is a tie within the method's precision. Saying so is more useful than declaring a winner the numbers do not support.

## Pitfalls

- **Overlapping criteria that double-count.** Two criteria measuring the same thing give that thing hidden double weight. Check independence before scoring.
- **Weights tuned after seeing scores.** Backfilling weights to make a favourite win. Set and record weights first; treat later changes as disclosed sensitivity tests.
- **Scores with no rationale.** Numbers picked to feel right. Every cell needs a reason or a piece of evidence.
- **False precision.** Treating 3.8 versus 3.9 as decisive. The inputs are judgment; the outputs inherit that coarseness. Round to the method's real resolution and call near-ties ties.
- **Ignoring sensitivity.** Reporting a winner without checking whether a small reweight flips it, so a fragile result looks solid.
- **A missing criterion.** Leaving out something the decision actually turns on. The matrix can only weigh what is in it; an omitted criterion is invisible no matter how good the arithmetic.
- **Letting the matrix decide.** The total is an input to judgment, not a verdict. Hard constraints, strategic must-dos, and the decision-maker's gut about a missing criterion all legitimately override a higher score.
