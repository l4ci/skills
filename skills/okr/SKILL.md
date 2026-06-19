---
name: okr
description: Use when the user wants to turn strategy into measurable goals using OKRs (Objectives and Key Results), the goal-setting method from Andy Grove at Intel and popularized by John Doerr in Measure What Matters. Guides a drafting cycle: clarify a qualitative objective, draft 3-5 measurable key results, stress-test the key results with parallel critics, set ambition and cadence, and check alignment. Maintains an OKR document. Triggers include "OKR", "OKRs", "objectives and key results", "set quarterly goals", "Measure What Matters", "draft our objectives".
---

# okr

OKRs (Andy Grove at Intel; popularized by John Doerr, *Measure What Matters*) pair a qualitative, time-bound objective with 3-5 quantitative key results, so a vague ambition becomes something you can score: hit every key result and the objective is met by definition.

The anatomy of objectives and key results, outcome-versus-output, scoring, cadence, alignment, and the pitfalls live in [references/okr.md](references/okr.md). Load that file before facilitating.

## When to use

The user wants to convert a strategy or ambition into goals that can be measured and reviewed, usually for a quarter. OKRs are the goal-setting layer; for the broader performance-measurement frame that links goals across financial, customer, process, and learning perspectives, the balanced-scorecard skill is the companion. Use OKRs when the question is "what are we committing to achieve this period, and how will we know."

## Language

Facilitate and write the document in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **SCOPE** (required): the level (company, team, or individual) and the period (for example, Q3 2026).
- **DIRECTION** (optional): the strategy or higher-level OKRs these should align to.
- **CONTEXT** (optional): the current situation, constraints, and what the unit owns.

## How to facilitate

Run one OKR drafting cycle with the user. Name the current stage at each step and record it in the OKR document. Do not skip the Stage 3 stress-test.

1. **Clarify the objective(s).** Help the user state what they want to achieve as a qualitative, memorable, time-bound sentence. Keep it to 1-3 objectives. Strip any metric out of the objective; if it has a number, that number belongs in a key result. An objective is direction and meaning ("Delight new customers with a fast onboarding experience"), not a measure.

2. **Draft the key results.** For each objective, draft 3-5 key results, each carrying a number and a target. Push every one toward an outcome (a result the customer or business feels) and away from an output (a task the team completes). Note the baseline where you can.

3. **Stress-test the key results (PARALLEL).** Dispatch a small set of critic subagents at once, each applying one test to the drafted key results. Tell each its final message is the return value: specific findings and concrete rewrites, not prose. Run these four:
   - **Outcome vs output.** Is each key result a result, or a disguised task list ("launch X", "ship Y", "hold 3 workshops")?
   - **Measurability.** Does each have a real number, a target, and ideally a baseline, or is it unmeasurable ("improve", "better")?
   - **Completeness.** If every key result is hit, is the objective truly achieved, or is there a gap the set does not cover?
   - **Ambition.** Is the set sandbagged (a sure thing dressed as a goal) or impossibly stretched (no credible path)?
   Reconcile the findings and revise the key results with the user.

4. **Set ambition, cadence, owners, and scoring.** For each OKR, mark it committed (expected to reach ~1.0; a miss is a real failure) or aspirational/stretch (success looks like ~0.7; full attainment would mean it was set too low). Set the cadence (typically quarterly, with a regular check-in rhythm), name an owner per objective, and state the scoring method (commonly 0.0-1.0 per key result, averaged for the objective).

5. **Check alignment.** Show how these OKRs ladder up to the DIRECTION or higher-level OKRs, and flag where a key result depends on another team. Good alignment mixes top-down and bottom-up, not a rigid waterfall; if nothing came from the team, say so.

## OKR document

Maintain a markdown document, saved to `okr-<scope-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location:

1. **Header.** The scope (level and period) and the date.
2. **Objectives.** Each objective as a qualitative, time-bound sentence, numbered.
3. **Key results.** Under each objective, its 3-5 key results, each with a baseline (where known), a target, and a number.
4. **Ambition and owners.** Per OKR: committed or aspirational, the owner, the cadence, and the scoring method.
5. **Alignment.** How these ladder up to higher-level goals, and cross-team dependencies.
6. **Check log.** What the Stage-3 critics found and how the key results were revised.
7. **Caveats.** OKRs measure what was chosen to be measured, so a perfect score on a weak set means little; scores judge the goals, not the people; and an OKR set without a review rhythm decays into a forgotten list.

## Principles

- **Completeness is the test.** If hitting every key result would still leave the objective unmet, the set is incomplete.
- **Review or it rots.** OKRs work on a cadence of check-ins and an end-of-period score, not set-and-forget. Keep them out of compensation, which corrupts the ambition.
