---
name: digital-maturity-assessment
description: Use when the user wants to assess an organization's digital maturity across strategy, customer experience, technology, data, operations, people and culture, and innovation, scoring each on a five-level scale and producing a gap analysis and roadmap. Fans out parallel assessor subagents per dimension, then synthesizes the maturity profile, the binding gaps, and a sequenced roadmap in a detailed markdown report. Triggers include "digital maturity", "digital maturity assessment", "how digitally mature are we", "digital transformation readiness", "maturity model".
---

# digital-maturity-assessment

Assesses how effectively an organization uses digital technology, data, and ways of working to create value, scoring seven dimensions on a five-level maturity scale, locating the gaps against the organization's ambition, and producing a roadmap.

The five maturity levels, the seven dimensions, the target-setting step, and the pitfalls live in [references/maturity.md](references/maturity.md). Load that file before assessing and score against its level descriptors exactly.

## When to use

The user wants to understand where an organization stands on digital and what to do next: a transformation baseline, a readiness check, or a roadmap input. The unit is an organization or business unit. It assesses maturity, not the technology estate alone; the soft dimensions matter as much as the hard ones.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **ORGANIZATION** (required): the organization or unit to assess.
- **TARGET** (optional but valuable): the ambition or target maturity level. Maturity is not maximized for its own sake, so gaps are only meaningful against a target. Ask if it is unclear.
- **EVIDENCE** (optional): documents, metrics, systems in place, and examples. Where evidence is thin, gather it by interviewing the user during the session rather than assuming.

## Orchestration map

```
Stage 1  Dimension Assessment ── 7 assessor subagents IN PARALLEL ──┐  (score 1-5 with evidence, gap to target)
Stage 2  Synthesis            ── 1 agent, needs all 7 ──────────────┘  (profile, binding gaps, sequenced roadmap)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Where evidence is missing for a dimension, the assessor should flag what it would need rather than scoring on aspiration.

## Stage 1: Dimension Assessment (PARALLEL)

Dispatch seven assessor subagents at once, one per dimension. Give each the shared framing plus its dimension and the five-level scale from the reference file.

**Shared framing (send to every assessor):**

> Assess one dimension of digital maturity for **[ORGANIZATION]** against the five-level scale. Score what is actually in production and in behavior, not what is planned or piloted. Target level: **[TARGET]**. Return:
> - **Current level** (1 to 5) with the evidence behind it
> - **What holds it at this level** and what the next level would require
> - **Gap to target** and its size
> - **Confidence** (high, medium, low); if evidence is thin, say what is needed rather than guessing high
>
> Evidence and context: [EVIDENCE]

Assign the seven dimensions from the reference file. Collect all seven before continuing, and re-dispatch any that fail.

## Stage 2: Synthesis (SEQUENTIAL, needs all 7)

One agent assembles the maturity picture:

1. **Draw the profile.** All seven dimension scores together, showing the uneven shape rather than a single average. The profile is the finding; an average hides it.
2. **Find the binding gaps.** The dimensions furthest below target, and the imbalances where a lagging dimension caps the value of an advanced one (the classic case: strong technology stranded behind weak people and culture).
3. **Sequence the roadmap.** The moves that raise the binding dimensions toward the target, split into quick wins and longer plays, recognizing the lagging dimension as the constraint on overall value.
4. **Verdict.** Overall maturity, the few moves that matter most, and the realistic path to the target.

## Report structure

Write a thorough markdown report and save it to `digital-maturity-<organization-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The organization, the target ambition, the date, and a note that scores reflect what is in production and in behavior.
2. **Maturity profile.** A table or radar-style layout of all seven dimensions with current level, target, gap, and confidence, scannable at a glance. Show the profile, not just an average.
3. **Per-dimension detail (seven sections).** For each: the level, the evidence, what holds it there, and what the next level requires.
4. **Binding gaps and imbalances.** The dimensions that most constrain value, including advanced dimensions stranded behind lagging ones.
5. **Roadmap.** Sequenced moves toward the target, quick wins and longer plays, focused on the binding dimensions.
6. **Verdict.** Overall maturity and the realistic path to the target.
7. **Caveats.** Scores reflect evidence available and are judgment, not certification; maturity is not an end in itself but relative to ambition; and the lagging dimension, not the average, governs the value the organization actually realizes.

## Principles

- **Score reality, not aspiration.** Production and behavior, not decks and pilots.
- **The soft dimensions bind.** People, culture, strategy, and data drag maturity down more often than technology lifts it.
- **Profile over average.** The uneven shape is the finding; the constraint is the lagging dimension.
- **Anchor to a target.** Gaps and roadmaps are meaningful only against the ambition, not against level 5 for its own sake.
- **Parallel where independent.** The seven dimensions are assessed concurrently; the synthesis needs all seven and runs after.
