---
name: adkar
description: Use when the user wants an ADKAR analysis of a change, asks why a change is not sticking or not being adopted, or wants to diagnose the people side of a change initiative. Identifies the affected groups, then fans out five parallel subagents (one per element: Awareness, Desire, Knowledge, Ability, Reinforcement), each rating the current state per group with evidence, then synthesizes the barrier point for each group and designs sequenced interventions into a detailed markdown report. Triggers include "ADKAR", "Prosci", "individual change model", "change adoption", "why is this change not sticking", "people side of change".
---

# adkar

Runs the Prosci ADKAR model to diagnose the people side of a change across five sequential blocks: Awareness of the need, Desire to support it, Knowledge of how to change, Ability to perform the new way, and Reinforcement to sustain it. Because the blocks are sequential, a change stalls at the first one a person has not achieved; the job is to find that barrier point, per affected group, and fix it before working the blocks beyond it.

The five elements, their diagnostic questions, the strength-rating scale, and the barrier-point logic live in [references/adkar.md](references/adkar.md). Load that file before assessing and rate each element against it exactly.

## When to use

The user has a change in flight (or planned) and wants to understand why it is not being adopted, or to plan the people side before launching. ADKAR is the individual, people-side companion to `kotter-change`, which covers the organizational steps of leading change; run both when a change needs work at both levels. It pairs with `stakeholder-analysis` for mapping who the affected groups are. The unit of analysis is the individual moving through the change, assessed per affected group, not the project plan or the technology.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the elements, the rating scale, and the barrier-point logic keyed to it regardless of the output language.

## Inputs

- **CHANGE** (required): the change being made and the organization or unit making it. Push for a specific change ("moving field sales onto the new CRM") rather than a vague one ("digital transformation"), since the elements can only be rated against a concrete change.
- **GROUPS** (optional): the affected audiences (for example frontline staff, their managers, the support team). If absent, surface a first cut of the distinct groups from the change itself and confirm with the user, because different groups sit at different barrier points and a single org-wide read hides the gaps.
- **CONTEXT** (optional): history with past changes, known resistance, the timeline, who is sponsoring it. Sharpens the Desire and Reinforcement reads and the intervention design.

## Orchestration map

```
Stage 0  Scope groups     ── identify the affected audiences (confirm if absent)
Stage 1  Element Assessment ── 5 subagents IN PARALLEL ──┐  (each rates one element per group, with evidence)
Stage 2  Synthesis          ── 1 agent, needs all 5 ─────┘  (barrier point per group, interventions, sequencing)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should ground ratings in real evidence (what was communicated, what training exists, observed behavior, incentives in place) rather than assumption.

## Stage 0: Scope the groups

Settle the affected groups before dispatching. If the user gave GROUPS, use them. If not, propose a small set of distinct audiences implied by the change (those who must change their own work, those who must lead others through it, those affected downstream) and confirm. Keep the set small and genuinely distinct; merge groups that sit at the same barrier with the same drivers.

## Stage 1: Element Assessment (PARALLEL)

Dispatch five subagents at once, one per element. Give each the shared framing, its element's section from the reference file, and the list of groups. Each rates its element across all groups. (If the change has many sharply different audiences and one element dominates, the cleaner cut may be one subagent per group instead; the default is one per element, assessed across groups, and the report should state which cut was used.)

**Shared framing (send to every subagent):**

> Assess one ADKAR element for this change: **[CHANGE]**. For each affected group **[GROUPS]**, work through the diagnostic questions for your assigned element, judging how well it is currently achieved with real evidence (what was actually communicated, what training exists, observed behavior, incentives and recognition in place). Then return, per group:
> - **Strength score** (1 to 5 on the reference scale) with a one-sentence justification
> - **Evidence**: what you are basing the score on, and what is missing
> - **The gap**: specifically what is absent or weak for this element and this group
> - **Confidence**: high, medium, or low, lowered where evidence was thin
>
> Do not assume an element is fine because a later one looks handled; rate only your own element. Context: [CONTEXT]

Assign the five elements from the reference file: Awareness, Desire, Knowledge, Ability, Reinforcement. Collect all five structured results before continuing. Re-dispatch any subagent that fails rather than synthesizing with a gap.

## Stage 2: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five assessments into a per-group diagnosis and an intervention plan:

1. **Barrier point per group.** For each group, read the five scores in order (Awareness to Reinforcement) and name the first element scoring 3 or below. That is the barrier: where this group is stuck and where effort goes first. Treat scores after the barrier as provisional.
2. **Why the barrier holds.** The specific gap behind each barrier, drawn from the assessment evidence, not a restatement of the element name.
3. **Targeted interventions.** For each group, design interventions for the barrier element first, then for the blocks after it, drawn from the reference file's intervention table and tailored to the evidence. Name who owns each (sponsor, manager, project team), since Desire and Reinforcement rarely belong to the project team.
4. **Sequencing.** Order the effort so earlier blocks are secured before later ones. Call out where the project is currently working a block past the barrier (for example running training while Desire is unaddressed) and what to stop or re-time.
5. **The dominant gap across groups.** If one element is the binding constraint across most groups, say so; that is where the change program gets its leverage. Note any group whose barrier is unique and needs its own track.

## Report structure

Write a thorough markdown report and save it to `adkar-<change-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The change and the unit making it, the affected groups, the date, and a one-line note that ADKAR assesses individual change per group and is a snapshot to be re-checked as the change progresses.
2. **Verdict.** The barrier point for each group in a few sentences, with a summary table: rows are groups, columns are the five elements, each cell a 1-to-5 score, and the barrier cell marked. A reader should see at a glance where each group is stuck.
3. **Per-group sections.** For each group: its barrier point and why it holds, the five element scores with evidence and gaps, and the interventions sequenced from the barrier onward with owners.
4. **Cross-group synthesis.** The dominant gap across groups, where the program's leverage sits, and any group needing its own track.
5. **Sequenced plan.** The interventions ordered across groups, with what to start, what to re-time, and what to stop because it is running ahead of a barrier.
6. **Caveats.** ADKAR is a snapshot of individual readiness, not a forecast; scores are informed judgment, not measurement; barrier points move as the change progresses, so re-assess; and the model addresses the people side, not the organizational steps (see `kotter-change`) or the project plan.

## Principles

- **Sequential, so fix the first gap first.** The barrier point is the first weak element in order; working a later block before it is resolved wastes effort.
- **Per group, not per organization.** A single org-wide score is an average that hides where adoption actually breaks. Assess each distinct group.
- **Desire cannot be forced.** Treat resistance as information about where Desire is missing, and address the group's actual fears rather than pushing past them.
- **Evidence or honesty.** Rate against what was actually communicated, trained, observed, and rewarded. Where evidence is missing, say so and lower confidence.
