---
name: psychological-safety
description: Use when the user wants to diagnose a team's psychological safety and prescribe how to improve it, or asks why people are not speaking up, why mistakes get hidden, or why learning has stalled. Fans out parallel assessor subagents across the dimensions of the climate (voice, response to mistakes, help-seeking, inclusion of difference, risk-taking and challenge), each scoring the climate against Amy Edmondson's behavioral markers with evidence and confidence, then places the team on the safety-by-accountability 2x2, names the weakest dimensions and the behaviors driving them, and prescribes leader and team interventions in a detailed markdown report. Triggers include "psychological safety", "people aren't speaking up", "mistakes get hidden", "Edmondson", "safe to take risks", "fearless team".
---

# psychological-safety

Runs Amy Edmondson's psychological safety construct to diagnose whether a team is safe for interpersonal risk-taking, speaking up, admitting mistakes, asking questions, challenging, without fear of punishment or humiliation, and to prescribe how to raise it. Psychological safety is a property of the team climate, not of any individual, and it predicts learning and performance.

The point is not whether the team is comfortable but whether it is candid under challenge: high safety with low standards is the comfort zone, and the target is high safety paired with high accountability, the learning zone. The behavioral markers, the safety-by-accountability 2x2, the three leader practices, and the pitfalls live in [references/psych-safety.md](references/psych-safety.md). Load that file before diagnosing and score the climate against the markers exactly.

## When to use

The user wants to diagnose and improve a team's psychological safety: learning or innovation is stalling, people are not speaking up, mistakes get hidden, or there has just been a failure or near-miss. The unit of analysis is a single team with a leader and recurring interaction, not a whole company and not an individual. Distinguish from neighbours: five-dysfunctions-of-a-team treats safety's cousin, trust, as the base of a team-effectiveness stack; the change cluster handles organizational transitions; scarf models the individual threat response. This skill diagnoses the team climate against Edmondson's specific construct and markers.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **TEAM** (required): the team to diagnose, with its leader and its work. Push for one defined team with recurring interaction. If the user names a whole department or several teams, narrow to one first, since safety is local and varies team to team.
- **SIGNALS** (optional): observable evidence the user can supply, how meetings go, who speaks and who stays silent, how mistakes and bad news are handled, whether people ask for help, recent failures or near-misses. This grounds the assessment; gather it in Stage 1 if not given.
- **CONTEXT** (optional): why the diagnosis is wanted now (a failure, an innovation push, turnover, a reorg) and the accountability picture (the standards the team is held to and how). This shapes the placement on the 2x2 and the prescription, not the markers.

## Orchestration map

```
Stage 1  Signals          ── 1 agent, inline ─────────────────┐  (identify the team, gather observable evidence)
Stage 2  Dimension Scan   ── 5 assessor subagents IN PARALLEL ─┤  (each scores one dimension of the climate)
Stage 3  Synthesis        ── 1 agent, needs all 5 ────────────┘  (place on 2x2, weakest dimensions, prescribe)
```

## Stage 1: Signals (INLINE)

Before fanning out, fix the unit of analysis and gather the raw evidence. Confirm the one team and its leader. Collect observable signals from the user or from available materials: how meetings run and who talks versus who is silent; what happens when someone makes a mistake or delivers bad news; whether and how people ask for help; how dissent and challenge are received; any recent failure or near-miss and how the team responded. Note the accountability picture: the standards the team is held to and how they are enforced. This is the evidence base every assessor will draw on; thin signals mean lower confidence downstream, not invented detail.

## Stage 2: Dimension Scan (PARALLEL)

Dispatch five assessor subagents at once, one per dimension of the climate. Give each the shared framing plus its dimension and the relevant markers from the reference file. The five dimensions: **voice and speaking up**; **response to mistakes and failure**; **help-seeking**; **inclusion of difference**; **risk-taking and challenge**.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their assessment in real evidence.

**Shared framing (send to each assessor):**

> Assess one dimension of psychological safety for this team: **[TEAM]**. Score the climate on your assigned dimension against the relevant behavioral markers from the framework, judging the team, not any individual. Ground every claim in observable behavior: specific episodes, patterns, and what happens when a member takes an interpersonal risk on your dimension. Diagnose candor under challenge, not pleasantness, a polite, agreeable team can be deeply unsafe. Then return:
> - **Dimension summary**: a tight read of the climate on this dimension
> - **Score**: low, moderate, or high safety on this dimension, against the markers
> - **Evidence**: the episodes, behaviors, and patterns supporting the score, each tied to its source
> - **Driving behaviors**: what specifically builds or breaks safety here (for example, how the leader responds to a raised concern)
> - **Gaps**: what is unobserved or unknowable from available signals
> - **Confidence**: high, medium, or low, lowered when evidence was thin or anecdotal
>
> Signals: [SIGNALS]   Context: [CONTEXT]

Assign the five dimensions from the reference file. Collect all five structured results before continuing. Re-dispatch any assessor that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five dimension scans into a diagnosis and a prescription. This is where the analysis earns its value, by placing the team and prescribing toward the learning zone rather than restating the scores:

1. **Place the team on the 2x2.** Locate it on the safety axis from the five dimension scores, and on the accountability axis from the observed standards and how they are enforced. Name the zone: apathy, comfort, anxiety, or learning. Justify both coordinates with evidence.
2. **Weakest dimensions and driving behaviors.** Which one or two dimensions are most unsafe, which behavioral markers they violate, and the concrete behaviors driving them, anchored to specific episodes, not low averages.
3. **Leader interventions.** Prescribe against Edmondson's three leader practices, framing the work as a learning problem, acknowledging fallibility, modeling curiosity through inquiry, made specific to this team's weakest dimensions and behaviors.
4. **Team interventions.** Norms and practices that reinforce the leader's moves: how bad news and mistakes get met, how help-seeking is normalized, how dissent is protected so the person who raises the hard thing is thanked, not penalized.
5. **The accountability check.** Confirm every prescription raises safety while holding the standard. If the team is in the anxiety zone, the move is up into learning, not sideways into comfort; if in comfort, raise the bar without breaking safety. State explicitly that no recommendation lowers standards in the name of safety.
6. **What to watch.** The leading indicators that safety is rising or falling, tied to the markers, so the team can tell whether the interventions are working.

## Report structure

Write a thorough markdown report and save it to `psychological-safety-<team-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The team and leader diagnosed, the context if given, the date, and a one-line note that psychological safety is a team climate, not an individual trait, and that the target is the learning zone, not comfort.
2. **Verdict.** Which zone the team sits in and the one or two weakest dimensions, in a few sentences, with a summary table: each dimension, its score, and confidence.
3. **The climate.** The five dimensions laid out, each with its score, the evidence, and the behaviors driving it, read against the seven markers.
4. **Placement.** The team plotted on the safety-by-accountability 2x2, both coordinates justified, the zone named.
5. **Prescription.** Leader interventions against the three practices, team interventions, and the accountability check that confirms each move targets the learning zone.
6. **What to watch.** Leading indicators tied to the markers.
7. **Caveats.** Psychological safety is a team climate read from observable behavior at a moment, not a fixed trait and not a verdict on any individual; it is not niceness, consensus, comfort, or low standards; the assessment is only as good as the signals behind it, and a confident-sounding score on thin evidence is a guess; raising safety enables high performance but does not by itself produce it, accountability must hold.

## Principles

- **Climate, not person.** Safety is a property of the team, built and broken by how members respond to interpersonal risk. Diagnose the climate; prescribe to the leader and the team, never label an individual.
- **Candor, not comfort.** The target is the learning zone, high safety with high accountability, not the comfort zone. A pleasant, agreeable team can be the least safe. Diagnose candor under challenge.
- **Never trade standards for safety.** The comfort-zone trap is to relax the bar and call it safety. Every prescription must raise safety while holding accountability.
- **Behaviors or honesty.** Ground each marker in observed behavior and episodes. Where signal is thin, say so and lower confidence rather than asserting a climate.
- **Parallel where independent.** The five dimensions can be assessed concurrently. Placement and prescription need all five, so synthesis runs after.
