---
name: six-sigma-dmaic
description: Use when the user wants to improve an existing process by reducing defects or variation using Six Sigma DMAIC (Define, Measure, Analyze, Improve, Control). Guides the five phases with gate checks, uses parallel root-cause hypotheses in Analyze, insists on verifying causes against data, and maintains a DMAIC project document. Triggers include "Six Sigma", "DMAIC", "reduce defects", "process improvement", "root cause analysis", "reduce variation".
---

# six-sigma-dmaic

Guides a Six Sigma DMAIC cycle to improve an existing process: Define the problem, Measure current performance, Analyze and verify root causes, Improve by fixing those causes, and Control to sustain the gain. The discipline is data over opinion and causes over symptoms.

The five phases, their gate questions, and the pitfalls live in [references/dmaic.md](references/dmaic.md). Load that file before facilitating.

## When to use

The user wants to fix an existing process where data can be gathered: reducing defects, errors, cycle time, or variation. For designing a new process from scratch, DMAIC does not apply (DMADV does). For a lighter, faster improvement loop without heavy measurement, prefer PDCA.

## Language

Facilitate and write the document in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **PROCESS** (required): the process and the problem with it.
- **CONTEXT** (optional): available data, the customer and their requirements, scope limits, and the process owner.

## How to facilitate

Work phase by phase. Each phase has a gate question that must be answered before the next begins; hold the gate. Record everything in the project document, and name the current phase at each step.

1. **Define.** Help the user write a measurable problem statement (what, where, how big, since when, no presumed cause or solution), the goal and target, the scope (process start and end), the customer and CTQs, and a SIPOC map. Gate: is the problem clear, measurable, and worth solving? If a presumed solution is hiding in the problem statement, strip it out.

2. **Measure.** Help define the defect and metric, plan data collection, sanity-check whether the measurement can be trusted, and establish a baseline with its variation. Gate: do we trust the baseline? If data is unavailable, say what must be collected rather than proceeding on guesses.

3. **Analyze (parallel root causes).** Dispatch several analyst subagents at once, each generating candidate root causes through a different lens (for example: people, process, materials, equipment, environment, measurement, the fishbone categories, or a 5 Whys chain). Tell each its final message is the return value: a list of candidate causes with the reasoning, not prose. Pool and dedupe them, then verify each against the data with the user, keeping only causes the evidence supports. Gate: are the root causes proven, not merely plausible? This gate is where DMAIC most often fails; do not pass it on assertion.

4. **Improve.** Help generate solutions that target the proven root causes, select against impact and feasibility, and design a small-scale pilot with a measure of success. Gate: does the pilot move the metric? Confirm with data before recommending full rollout.

5. **Control.** Help build a control plan: standardized procedure, ongoing monitoring (control charts or equivalent) with response rules when the metric drifts, and handover to the process owner. Gate: will the gain hold without the project team?

## Project document

Maintain a markdown document, saved to `dmaic-<process-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location:

1. **Header.** The process, the date, and the project owner.
2. **Define.** Problem statement, goal and target, scope, customer and CTQs, SIPOC.
3. **Measure.** Defect and metric definition, data-collection plan, measurement trust, baseline and variation.
4. **Analyze.** Candidate causes, the data tests applied, and the proven root causes (the vital few).
5. **Improve.** Solutions, the selection, the pilot design, and the pilot result against the metric.
6. **Control.** Control plan, monitoring and response rules, and owner handover.
7. **Phase gates.** A short record that each gate question was answered before advancing.
8. **Caveats.** Conclusions are only as good as the data and the measurement system behind them; verified root causes reduce, not eliminate, the chance of a wrong fix; and a gain holds only if Control is real.

## Principles

- **Hold the gates.** Do not advance a phase that has not answered its question. Define clear, baseline trusted, causes proven, pilot working, control real.
- **Data over opinion.** Causes and effects are tested against data. The method exists to defeat the plausible-but-wrong fix.
- **Causes, not symptoms.** Improve targets the root causes proven in Analyze. A symptom fix returns.
- **Pilot before rollout.** Prove the change on a small scale with data first.
- **Parallel where independent.** Root-cause hypotheses are generated concurrently, then verified together against data.
