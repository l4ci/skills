# FMEA: failure modes, the three scales, RPN, and action priority

Failure Mode and Effects Analysis works one unit at a time. A unit is a process step (in a process FMEA, PFMEA), or a component or function (in a design FMEA, DFMEA). Each unit has a function; a *failure mode* is a way that function fails. For every failure mode you record seven things:

1. **Failure mode**: how the function fails ("valve fails to close", "form submits with empty field", "weld cracks").
2. **Effect(s)**: what the failure causes, and on whom: the local unit, the next step downstream, the end user, safety, or regulatory compliance. A mode can have several effects; score the worst.
3. **Severity (S)**: how bad the worst effect is. Scale below.
4. **Cause(s)**: the mechanism that triggers the mode ("seal degrades", "missing validation", "insufficient preheat"). A mode can have several causes; each cause gets its own occurrence.
5. **Occurrence (O)**: how often the cause produces the mode. Scale below.
6. **Current controls**: what is in place today. Two kinds: *prevention* controls reduce the cause (lower O), *detection* controls catch the cause or mode before it reaches the customer (lower D).
7. **Detection (D)**: how likely the current controls are to catch the cause or mode before impact. Scale below.

## The three anchored 1-to-10 scales

Score each on a 1-to-10 scale. The anchors fix what a number means, so two analysts mean the same thing by a 7. Higher is always worse.

### Severity (S): how bad the effect is

| S | Effect |
|---|---|
| 1 | No discernible effect. |
| 2-3 | Minor: slight annoyance, minor rework, no functional loss. |
| 4-5 | Moderate: noticeable loss of function or quality; customer dissatisfied. |
| 6-7 | High: major function lost or degraded; significant customer impact or cost. |
| 8 | Very high: primary function lost; possible regulatory noncompliance with warning. |
| 9 | Hazardous **with warning**: potential safety or regulatory failure, but with advance warning to operator or user. |
| 10 | Hazardous **without warning**: safety or regulatory failure with no warning. |

### Occurrence (O): how often the cause occurs

| O | Likelihood |
|---|---|
| 1 | Failure eliminated by design / prevention control; essentially never. |
| 2-3 | Low: isolated failures, well-controlled cause. |
| 4-6 | Moderate: occasional failures. |
| 7-8 | High: repeated failures; cause poorly controlled. |
| 9 | Very high: failure frequent. |
| 10 | Almost certain: failure nearly always occurs / very high frequency. |

### Detection (D): how likely current controls catch it before impact

Note the inverted sense: a *low* D means detection is *strong*. Detection scores the controls, not the failure.

| D | Detectability |
|---|---|
| 1 | Control will almost certainly detect the cause or mode before impact (e.g. error-proofing / poka-yoke). |
| 2-3 | High chance of detection; automated or robust check. |
| 4-6 | Moderate chance; checks exist but may miss. |
| 7-8 | Low chance; weak, manual, or sampled checks. |
| 9 | Very remote chance of detection. |
| 10 | No control, or the failure cannot be detected before it reaches the customer. |

## RPN and criticality

For each failure mode (or each cause within a mode):

- **RPN = S x O x D**, ranging 1 to 1000. The headline risk index.
- **Criticality = S x O**. The inherent risk independent of detection. Report it alongside RPN, because RPN can be pulled down by a strong detection control even when the underlying failure is severe and frequent. Detection does not prevent failure; it only catches it.

## Action priority

Ranking by RPN alone is not enough. Apply both of these:

1. **Threshold.** Set a cutoff above which a mode requires action (e.g. RPN >= 100), agreed with the team rather than assumed. Everything above the threshold gets an action.
2. **Severity override.** Any mode with **S >= 9 gets action regardless of its RPN.** A catastrophic failure that is rare and currently detectable can post a low RPN and still be the most important thing in the analysis. This override is the guard against RPN tunnel vision.

### The modern fix: AIAG-VDA Action Priority (AP)

The 2019 AIAG-VDA standard replaces the RPN cutoff with **Action Priority: High, Medium, or Low**, read off a lookup table keyed on the S, O, and D combination rather than their product. AP exists because RPN has known weaknesses: different S/O/D triples multiply to the same RPN while representing very different risks, the scale is unevenly populated (many products are unreachable), and the product hides severity inside an aggregate. AP weights severity first, then occurrence, then detection, so a high-severity item is forced up the priority order. Where the team uses AIAG-VDA, drive action from the AP table instead of a raw RPN cutoff; where it does not, the threshold-plus-override above approximates the same intent.

## Actions reduce S, O, or D

Every recommended action attacks one of the three terms; name which:

- **Reduce S**: redesign so the effect no longer occurs or is contained (add a fail-safe, remove the hazardous outcome, add redundancy). The only way to cut severity is to change the design or process so the failure's consequence changes; you cannot inspect severity away.
- **Reduce O**: prevent the cause (error-proofing, more robust design, tighter process control, better material). This stops the failure from happening.
- **Reduce D**: improve detection (better tests, automated checks, inspection, monitoring). This catches the failure earlier but does not stop it.

Favor reducing S and O over D: prevention beats detection. After an action, estimate the revised S, O, D and recompute a **target RPN**, so the expected payoff of each action is explicit and comparable across the FMEA.

## Pitfalls to guard against

- **RPN tunnel vision.** Acting only on the highest RPNs and ignoring a high-severity, low-RPN mode (severe but rare and detectable). The S >= 9 override exists precisely for this; a 9 or 10 in severity is never "low priority."
- **Over-reliance on detection.** Driving RPN down by adding detection controls. Detection catches the failure; it does not prevent it. A low D on a high-S, high-O failure is fragile, the control can lapse, and criticality stays high. Prefer reducing S or O.
- **Scoring without rationale.** A number with no stated reason is unauditable and usually biased. Every S, O, and D carries a one-line justification grounded in failure history, specifications, or a named assumption.
- **Treating tied RPNs as equivalent.** RPN is ordinal, not a measured probability. Two modes at RPN 120 reached by (S6, O4, D5) and (S10, O3, D4) are not the same risk; the second is a safety item. Ranking ties are not priority ties; break them by severity, then criticality.
