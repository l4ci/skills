# RICE: the four factors, scales, formula, and pitfalls

RICE ranks a backlog of initiatives by expected value per unit of effort. It comes from Intercom, where it was built to stop product decisions from being won by whoever argued loudest. The score is one number per item, computed the same way for every item, so the items can be ordered.

## The formula

```
            Reach × Impact × Confidence
RICE score = ───────────────────────────
                      Effort
```

Higher score, do first. The numerator is expected benefit; the denominator is cost. The score is a rate, not a total: a small benefit cheaply earned can outrank a large benefit that costs a year of work.

The score is only comparable across items if all four factors were estimated on the same definitions. Calibrate the factors once, then apply them to every item. An item scored on its own private scale is noise in the ranking, not a competitor in it.

## The four factors

### Reach

How many people or events this initiative affects in a fixed time period. Count something real and countable: users per quarter, transactions per month, sign-ups per release. Use a number from data where the data exists ("2,000 users/quarter"), and a stated estimate where it does not.

Pick ONE time window and use it for every item. Reach measured per quarter for one feature and per month for another cannot be compared, and the ranking that results is meaningless. The window is set once in calibration and never varies between items.

Reach is an estimate, not a measurement. Treating "2,000 users/quarter" as a precise fact is the first failure mode: it is a best guess about the future, and its softness is what Confidence later discounts.

### Impact

How much the initiative moves the goal for each person or event it reaches. Estimated on a fixed multiplier scale, not in free units:

| Impact | Multiplier |
|---|---|
| Massive | 3 |
| High | 2 |
| Medium | 1 |
| Low | 0.5 |
| Minimal | 0.25 |

The multiplier is per-person, against the one goal fixed in calibration. "Impact on what" must be the same goal for every item, or a high Impact on one goal is being weighed against a high Impact on another and the comparison is fake.

### Confidence

A percentage that discounts shaky estimates. It is the built-in bias check: it exists precisely to penalize wishful thinking, so an item with thin evidence cannot outrank a well-grounded one on enthusiasm alone.

| Confidence | Meaning |
|---|---|
| 100% | High: solid data behind Reach, Impact, and Effort |
| 80% | Medium: some data, some judgment |
| 50% | Low: a moonshot, mostly assumption |

Below 50% means the estimate is too speculative to score. Do not score it lower; go validate it first, then score it once there is something to score. Skipping or ignoring Confidence is a failure mode in its own right: dropping the factor turns RICE back into the loudest-voice ranking it was built to replace.

### Effort

Total work to ship the initiative, as a whole-team number, estimated in person-months (or person-weeks for smaller items). Count everyone: product, design, engineering, whatever the item needs. This is the denominator, so it sets the cost the benefit is divided by.

Underestimating Effort is the most common bias and the one that does the most damage: because Effort is the denominator, a too-low estimate inflates the score and floats a costly item to the top of the roadmap. Estimate Effort as if committing to it, not as if pitching it.

## Pitfalls to guard against

- **False precision in Reach.** Reach is an estimate dressed as a number. Carry it as a range or a stated assumption, not a measured fact, and let Confidence absorb the uncertainty.
- **Skipping or ignoring Confidence.** Confidence is the bias check; an item scored without it is an item with no penalty for being a guess. Always apply it, and never score an item below 50% confidence: validate instead.
- **Underestimating Effort.** The denominator's the easiest place to flatter a favored project. A low Effort estimate is the single biggest source of a rigged ranking.
- **Mismatched time windows in Reach.** Reach on different windows is not comparable. Fix one window in calibration and hold every item to it.
- **Mismatched goals in Impact.** Impact is impact on one named goal. Different goals across items make the Impact column meaningless.

## Sensitivity

Two factors swing the ranking hardest: Confidence (a multiplier that can halve a score) and Effort (a denominator that can double one). After ranking, vary these two within their plausible range for the close items and check whether the order holds. A top-ranked item whose lead depends on an optimistic Effort or a generous Confidence is fragile, and the ranking should say so.
