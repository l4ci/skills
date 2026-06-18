---
name: root-cause-analysis
description: Use when a defect, failure, incident, or recurring problem has an unclear cause and the user wants to find and fix what actually causes it rather than patch the symptom. Combines the Ishikawa fishbone (cause-and-effect diagram) with the 5 Whys. Fans out parallel finder subagents, one per cause category (the 6 Ms by default), each brainstorming candidate causes for the category with reasoning and evidence; then drills the strongest candidates with iterative why-chains to reach verified root causes, separates root from contributing causes, and recommends countermeasures that remove the roots. Triggers include "root cause analysis", "RCA", "fishbone", "Ishikawa", "cause and effect", "5 whys", "why does this keep happening".
---

# root-cause-analysis

Finds the root cause of a problem by combining the Ishikawa fishbone with the 5 Whys: the fishbone scans every category of cause so nothing is missed, and the 5 Whys drills each strong candidate down to a cause you can actually act on. The point is not to explain the symptom but to find the cause that, if removed, prevents recurrence.

The fishbone head, the cause category sets (the 6 Ms and the service variants), the 5 Whys discipline, the verification tests, and the failure modes live in [references/root-cause.md](references/root-cause.md). Load that file before analyzing.

## When to use

A defect, failure, incident, or recurring problem has already happened and its cause is unclear. The unit of analysis is one precisely stated effect, not a vague dissatisfaction. This is the diagnostic engine of the Analyze phase of six-sigma-dmaic and the Check/Act of pdca-cycle; reach for it directly when you have an effect and need its cause. Distinguish it from pre-mortem, which anticipates the future failure of a plan that has not yet run: root-cause-analysis diagnoses a failure that already occurred.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **EFFECT** (required): the problem to diagnose. Push for one precisely stated effect, quantified where possible. If it is vague ("quality is bad", "the system is slow"), narrow it with one or two questions before starting.
- **CONTEXT** (optional): the domain (manufacturing, software, service, safety), when and where the effect occurs, its magnitude and frequency, what changed recently, and any data, logs, or incident records available. This selects the category set and grounds the verification.

## Orchestration map

```
Stage 1  Frame the head    ── inline ───────────────────────────┐  (state the effect precisely; pick the category set)
Stage 2  Cause finding     ── ~6 finder subagents IN PARALLEL ──┤  (one per category: ranked candidate causes + evidence)
Stage 3  Drill & verify    ── needs all categories ─────────────┘  (5 Whys per top candidate; verify; root vs contributing; countermeasures)
```

## Stage 1: Frame the head (inline)

Write the fish head: the effect stated as what, where, when, and magnitude, quantified where the data allows ("solder voids on connector J3, second shift, ~8% of boards since week 12", not "soldering problems"). A loose head produces a loose analysis. Then choose the category set from the reference file: default to the 6 Ms (People, Machine, Method, Material, Measurement, Environment); use the service 4 Ps/8 Ps when the effect is in a service or process with no physical product. State the chosen set and the head before fanning out.

## Stage 2: Cause finding (PARALLEL)

Dispatch one finder subagent per category in the chosen set (about six). Give each the shared framing plus its one assigned category and that category's probes from the reference file.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground candidate causes in real evidence (logs, incident records, specs, timelines, measurements).

**Shared framing (send to every finder):**

> Brainstorm the candidate causes of this effect that fall in your assigned category only: **[EFFECT]**. Stay within your category; another finder owns each of the others. For each candidate cause, give the reasoning for why it could produce this effect and any evidence for or against it (data, timing, a known change). Do not stop at the first plausible cause; list every candidate your category could contribute. Then return:
> - **Candidate causes**: each as a specific, testable statement (not "bad process" but "the reflow profile was changed in week 12 without re-qualification")
> - **Reasoning**: the mechanism by which each would cause the effect
> - **Evidence**: what supports or contradicts each, with sources where retrieval allows; mark each candidate as evidenced or speculative
> - **Rank**: your candidates ordered by how likely each is to be a real contributor, strongest first
> - **Confidence**: high, medium, or low per candidate, lowered when evidence is thin
>
> Context: [CONTEXT]

Assign the categories from the reference file. Collect all category results before continuing. Re-dispatch any finder that fails rather than synthesizing with a gap; a missing category is exactly where the real cause hides.

## Stage 3: Drill and verify (needs all categories)

Pool the ranked candidates across all categories and pick the strongest few (typically two to four) regardless of which category they came from. Then:

1. **Drill each with the 5 Whys.** For each strong candidate, ask "why" iteratively (roughly five times, not dogmatically) until reaching a root cause: a cause that, if removed, prevents recurrence and that you can actually act on. Stop at a root cause, not a proximate symptom. Let a chain branch where more than one cause operates at a level. This can run in parallel, one why-chain per top candidate; collect all chains before concluding.
2. **Verify each claimed root cause against evidence.** Distinguish correlation from causation. Test each: does the timeline fit (did the cause precede the effect), does removing it remove the effect, is there data, is there a plausible mechanism. Discard candidates that fail the tests.
3. **Classify root versus contributing.** Separate the root causes (remove it and recurrence stops) from contributing causes (they worsen or enable but are not the origin). Say which is which.
4. **Rank the root causes** by likelihood times contribution to the effect.
5. **Recommend countermeasures that target the root causes, not the symptom.** Each countermeasure names the specific root cause it removes. A fix that addresses a symptom or a contributing cause is labeled as such, not sold as a cure.

## Report structure

Write a thorough markdown report and save it to `root-cause-analysis-<effect-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The effect analyzed (the fish head, quantified), the context if given, the date, the category set used, and a one-line note on the framework.
2. **Verdict.** The root cause or causes, in a few sentences, with the lead countermeasure for each. State up front whether the cause is confirmed by evidence or remains the strongest hypothesis pending a test.
3. **The fishbone.** Every category with its candidate causes and evidence, so the full scan is visible and nothing was skipped. Mark each candidate evidenced or speculative.
4. **Why-chains.** For each drilled candidate, the why-by-why chain to its root cause, branching where it branched.
5. **Verification.** For each claimed root cause, the tests applied (timeline, removal, data, mechanism) and whether it passed; correlation explicitly separated from causation; root causes separated from contributing causes.
6. **Countermeasures.** Ranked, each tied to the root cause it removes, with what to verify after acting (does recurrence stop).
7. **Caveats.** A fishbone enumerates possible causes, it does not prove any; the 5 Whys is a structured guess until verified against evidence; an unconfirmed root cause is a hypothesis with a test attached, not a finding; the analysis is only as good as the data available; and removing a verified root cause stops this recurrence, not every future variant of the problem.

## Principles

- **Cause, not symptom.** The deliverable is the cause that stops recurrence when removed. A fix that quiets the symptom and leaves the cause is not the answer; name it as a stopgap if you offer it.
- **Scan every category before drilling.** Single-cause bias and first-guess fixation are the classic failure: the fishbone exists to force a look in every category, including the one you did not suspect, before committing to a chain.
- **Branch the whys.** A why-chain that stays linear assumes one cause per level. Real problems branch; let the chain branch and follow each fork.
- **Verify before concluding.** A 5 Whys chain is a hypothesis. Test it against the timeline, the data, and the removal question before calling it the root cause; correlation is not causation.
- **System, not blame.** "Operator error" is a stopping point that hides the real cause. Ask why the system allowed the error; the root cause is almost always in method, machine, measurement, or environment.
- **Parallel where independent.** The categories can be brainstormed concurrently. The drill, verification, and ranking need every category, so Stage 3 runs after the fan-out completes.
