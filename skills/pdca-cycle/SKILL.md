---
name: pdca-cycle
description: 'Use when the user wants to run a lightweight continuous-improvement loop using PDCA (Plan, Do, Check, Act), the Deming cycle. Guides a small, fast cycle: plan a change with an explicit prediction, try it at small scale, check results against the prediction, and act by adopting, adjusting, or abandoning, then loop. Maintains a cycle log. Triggers include "PDCA", "Deming cycle", "plan do check act", "continuous improvement", "Shewhart cycle", "kaizen loop".'
---

# pdca-cycle

PDCA (the Deming/Shewhart cycle) is a fast, small, repeating improvement loop that catches the failure of changing things without testing whether they worked: Plan a change with an explicit prediction, Do it small, Check results against the prediction, Act by adopting, adjusting, or abandoning.

The four stages, how to use them, and the pitfalls live in [references/pdca.md](references/pdca.md). Load that file before facilitating.

## When to use

The user wants quick, frequent, lower-stakes improvement: trying a change, testing a fix, iterating a routine. For a large, costly problem that needs statistical rigor and verified root causes, prefer Six Sigma DMAIC. PDCA favors speed and repetition over depth.

## Language

Facilitate and write the log in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **FOCUS** (required): the problem, opportunity, or change to work on.
- **CONTEXT** (optional): the current situation, constraints, and how results can be observed.

## How to facilitate

Run one PDCA cycle with the user, then set up the next. Keep it light and quick. Name the current stage at each step and record it in the cycle log.

1. **Plan.** Help the user state the objective, understand the current situation just enough to act, and define a specific, small change. Capture an explicit prediction (what they expect to happen and by how much) and how the result will be measured. Do not let the change be so big it cannot be tested quickly, and do not skip the prediction.

2. **Do.** Help the user run the change on a small scale (a pilot, one team, a limited run) and record what actually happened, including anything unexpected or any deviation from the plan.

3. **Check.** Compare the results to the Plan's prediction, honestly. Did the change produce the expected effect? What did the data and experience show, including surprises? Capture the learning, measured against the prediction rather than against hope.

4. **Act.** Help the user decide: adopt (it worked, standardize and roll out, make it the new baseline), adjust (modify and run another cycle), or abandon (discard it, keep the learning, plan a different change). Record the decision, update the baseline, and tee up the next cycle.

5. **Loop.** Start the next PDCA from the new baseline. Each turn should raise the standard a little.

## Cycle log

Maintain a markdown log, saved to `pdca-cycle-<focus-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location, with one entry per cycle:

1. **Header.** The focus and the date.
2. **Per cycle, a block with:**
   - **Plan:** objective, the change, the prediction, and the measure.
   - **Do:** what was actually done and what happened, including surprises.
   - **Check:** results versus prediction, and the learning.
   - **Act:** adopt, adjust, or abandon, and the new baseline.
3. **Running standard.** The current standardized practice after the latest adopted change, so the accumulated gain is visible.
4. **Caveats.** PDCA trades depth for speed; a small trial confirms a change in its context, not universally; and gains stick only if Act standardizes what works and the loop continues.

## Principles

- **Predict before you act.** A Plan without a prediction makes Check meaningless.
- **Standardize what works, or the gain never sticks.** Surprises are often the real learning.
- **It is a loop, not a project.** The point is repetition that compounds, not a single pass.
