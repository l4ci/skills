---
name: fmea
description: Use when the user wants to systematically anticipate how a process, product, or design can fail before launching or changing it (Failure Mode and Effects Analysis). Scopes the system and breaks it into functions or steps, then dispatches one analyst per function in parallel to list failure modes with effects, causes, controls, and Severity/Occurrence/Detection scores, before a synthesis pass computes the Risk Priority Number, ranks the modes, applies an action threshold plus a high-severity override, and recommends actions that reduce S, O, or D. Triggers include "FMEA", "failure mode and effects analysis", "what could go wrong with this process", "risk priority number", "RPN", "DFMEA", "PFMEA", "design failure analysis".
---

# fmea

Failure Mode and Effects Analysis (FMEA, military/aerospace lineage, later AIAG-VDA) anticipates how a process, product, or design can fail by listing each way it can break, scoring severity, occurrence, and detection, then acting on the worst before they happen. It catches the failure where a known risk is named and scored but never acted on: every high-priority mode must leave with a specific change that reduces S, O, or D.

The seven columns (failure mode, effects, severity, causes, occurrence, controls, detection), the three anchored 1-to-10 scales, the RPN and criticality computations, the action-priority rules, and the pitfalls live in [references/fmea.md](references/fmea.md). Load that file before scoring.

## When to use

Use before launching or changing a process, product, or design where failures carry real cost, safety risk, or regulatory exposure, and where the system is decomposable into functions, steps, or components worth scoring one at a time. Pairs with [pre-mortem](../pre-mortem/SKILL.md), its qualitative cousin: a pre-mortem imagines one big failure of a plan and works backward through its story, FMEA enumerates and scores many failure modes of a system. Also pairs with [six-sigma-dmaic](../six-sigma-dmaic/SKILL.md), where an FMEA often supplies the Analyze and Improve phases. Reach for pre-mortem when the subject is a one-off plan with a single dominant way to fail; reach for FMEA when the subject is a system with many independent failure points.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **SUBJECT** (required): the process, product, or design under analysis, and its **BOUNDARY** (where it starts and stops, what is in scope and what is assumed reliable outside it). If only a vague subject is given, fix the boundary with the user in Stage 1.
- **TYPE** (optional): whether this is a process FMEA (PFMEA, scoring process steps), a design FMEA (DFMEA, scoring components and functions), or mixed. If absent, infer from the subject.
- **CONTEXT** (optional): known failure history, safety or regulatory requirements, existing controls, and the action threshold the team will commit to. Absent a stated threshold, propose one in Stage 3.

## Orchestration map

```
Stage 1  Scope & decompose ── fix subject, boundary, type; split into functions/steps/components (inline)
Stage 2  Analyze each unit  ── 1 analyst subagent per function/step IN PARALLEL ──┐  (failure modes, effects, causes, controls, S/O/D)
Stage 3  Synthesis          ── 1 agent, needs all units ───────────────────────────┘  (RPN, criticality, ranking, actions, target RPN)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground failure modes, causes, and scores in real evidence (failure history, standards, specifications) rather than inventing data.

## Stage 1: Scope and decompose (inline, with the user)

Before any scoring, fix and write down:

1. **Subject and boundary.** Name exactly what is under analysis and draw the line: which steps, components, or functions are inside, and what is assumed reliable outside. An undrawn boundary makes the analysis either bottomless or accidentally silent on a real risk.
2. **Type.** Process, design, or mixed. It sets what each unit is (a step versus a component) and what a failure mode means.
3. **Decomposition.** Break the subject into the functions, process steps, or components to analyze. Each unit should have a clear function, so a failure mode is "fails to perform function X." Keep the units at one consistent level of granularity; too coarse hides distinct modes, too fine drowns the analysis.

Confirm the unit list with the user before dispatching; every later stage builds on it.

## Stage 2: Analyze each unit (PARALLEL)

Dispatch one analyst subagent per unit, all at once, each given the subject, boundary, type, the three scales, and its one unit. The analysts do not see each other; each scores on the absolute anchored scales, not relative to other units.

**Shared framing (send to each analyst):**

> Analyze one unit of this FMEA. Subject: **[SUBJECT]**, boundary: **[BOUNDARY]**, type: **[TYPE]**. Your unit and its function: **[UNIT]**. Use these three anchored 1-to-10 scales exactly: **[Severity, Occurrence, and Detection anchor tables from the reference]**. For your unit, identify every plausible failure mode (a way the function fails). For each failure mode return:
> - **Failure mode**: how the function fails
> - **Effect(s)**: the consequence and on whom (the local unit, the next step, the end user, safety, regulatory), with the **Severity (S, 1-10)** of the worst effect and a one-line rationale
> - **Cause(s)**: the mechanism(s) that trigger the mode, with **Occurrence (O, 1-10)** and a one-line rationale
> - **Current controls**: prevention controls (that reduce the cause) and detection controls (that catch the mode or cause), with **Detection (D, 1-10)** and a one-line rationale
> - **Confidence** (high, medium, or low), lowered where failure history or evidence was thin rather than inventing data
>
> Do not compute RPN; report S, O, and D only. Context: [CONTEXT]

Collect all units before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all units)

One agent assembles the ranked, actioned FMEA:

1. **Reconcile the scales.** The parallel analysts did not see each other, so check that S, O, and D mean the same thing across units. Re-anchor any score applied on a drifting scale and note the adjustment.
2. **Compute RPN and criticality.** For each failure mode, RPN = S x O x D (1-1000) and Criticality = S x O. Report both; criticality isolates inherent risk independent of how well you happen to detect it.
3. **Rank and apply action priority.** Rank by RPN, then apply the stated action threshold AND the override: any failure mode with S >= 9 gets action regardless of its RPN. Where the team uses the modern AIAG-VDA Action Priority (High/Medium/Low) tables, apply those instead of a raw RPN cutoff. Flag any high-severity, low-RPN mode explicitly so it is not lost to RPN tunnel vision.
4. **Recommend actions targeting S, O, or D.** For each prioritized mode, recommend a specific action and name which term it attacks: reduce **S** by redesigning to remove or contain the effect, reduce **O** by preventing the cause, or reduce **D** by improving detection. Favor prevention (lower S or O) over detection, which catches the failure but does not stop it.
5. **Recompute the target RPN.** For each action, estimate the revised S, O, D after it lands and give a target RPN, so each action's expected payoff is visible and comparable.

## Report structure

Write a thorough markdown report and save it to `fmea-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The subject, the boundary, the type, the date, and a one-line note on the framework. State the three scales and the action threshold (plus the S >= 9 override) up front, since the ranking is only as good as these.
2. **Verdict.** The top failure modes by risk and which carry the highest severity, in a few sentences, with the headline actions and their expected effect.
3. **The FMEA table.** One row per failure mode with columns: unit/function, failure mode, effect(s), S, cause(s), O, current controls, D, RPN, criticality, recommended action, and target RPN. Sorted by current RPN, with high-severity rows marked.
4. **Per-unit detail.** For each unit: its failure modes, the rationale behind notable S/O/D scores, and the analyst's confidence.
5. **Action plan.** The prioritized actions, each naming whether it reduces S, O, or D, why prevention was preferred over detection where it was, the owner placeholder, and the before/after RPN.
6. **Caveats.** RPN is an ordinal index, not a measured probability: equal RPNs reached by different S/O/D triples are not equivalent risks, and a tie in RPN is not a tie in priority. Detection scores reflect today's controls and decay as the system changes. The analysis only covers failure modes that were enumerated; an unimagined mode is invisible. Scores are calibrated judgment, not measurement, and a high-severity safety or regulatory mode warrants action even at a low RPN.

## Principles

- **Action is the deliverable.** The ranking exists to drive change. Every prioritized mode leaves with an action that lowers S, O, or D and a target RPN, or the FMEA did nothing.
- **Severity can override the number.** RPN tunnel vision, ignoring a catastrophic but rare and detectable failure, is the framework's classic and most dangerous failure mode.
- **Every score earns a rationale.** A number with no reason is a guess wearing a number. Ground S, O, and D in failure history or evidence where retrieval allows, and lower confidence rather than inventing data.
- **RPN is ordinal, not arithmetic.** Equal RPNs from different triples are not equal risks and ties are not equivalences; report criticality alongside.
