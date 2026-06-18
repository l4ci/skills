---
name: mckinsey-7s
description: Use when the user wants to assess organizational alignment or effectiveness, diagnose why an organization underperforms, plan a major change, or integrate after a merger, using the McKinsey 7-S framework (Strategy, Structure, Systems, Shared Values, Skills, Style, Staff). Fans out seven parallel analyst subagents (one per element), then runs an alignment analysis across them to find misalignments and recommend fixes, in a detailed markdown report. Triggers include "7-S", "7S framework", "McKinsey 7-S", "organizational alignment", "why is this org not working".
---

# mckinsey-7s

Assesses an organization through the McKinsey 7-S framework: Strategy, Structure, Systems (hard), and Shared Values, Skills, Style, Staff (soft). The seven elements are interdependent, and effectiveness comes from their alignment. The analysis assesses each element, then finds where they pull against each other.

The seven elements, the hard/soft split, the alignment checks, and the pitfalls live in [references/seven-s.md](references/seven-s.md). Load that file before analyzing.

## When to use

The user wants to understand organizational effectiveness or alignment: diagnosing underperformance, planning or sequencing a change, integrating post-merger, or realigning after a strategy shift. The unit of analysis is an organization or a unit within one, not a market or a product.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **ORGANIZATION** (required): the organization or unit to analyze.
- **CONTEXT** (required): why the analysis is being run (diagnose underperformance, plan a specific change, integrate a merger). For a change, also state the intended future state. The context decides whether this is a current-state diagnosis or a current-versus-desired gap analysis, so ask if it is unclear.

## Orchestration map

```
Stage 1  Element Scan      ── 7 analyst subagents IN PARALLEL ──┐  (one per S, current state and desired if change)
Stage 2  Alignment Synthesis ── 1 agent, needs all 7 ──────────┘  (fit between elements, misalignments, fixes)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval where the organization is public.

## Stage 1: Element Scan (PARALLEL)

Dispatch seven analyst subagents at once, one per element. Give each the shared framing plus its element's definition and probes from the reference file.

**Shared framing (send to every analyst):**

> Assess one element of the McKinsey 7-S for **[ORGANIZATION]**. Describe what is actually true, with evidence, not what the organization aspires to. Return:
> - **Current state** of your element, concrete and specific
> - **Desired state and gap**, only if the context names a change
> - **Evidence** behind the assessment
> - **Tensions you already see** with other elements, named
> - **Confidence** (high, medium, low), lowered when evidence is thin
>
> Context: [CONTEXT]

Assign the seven elements from the reference file: Strategy, Structure, Systems, Shared Values, Skills, Style, Staff. Collect all seven before continuing, and re-dispatch any that fail.

## Stage 2: Alignment Synthesis (SEQUENTIAL, needs all 7)

One agent runs the alignment analysis, which is the actual point of the framework:

1. **Map the fit between elements.** Assess the consequential relationships, especially each element against Shared Values, Strategy against Structure and Systems, and Style and Staff against the Skills the strategy needs. For each, judge whether the two reinforce each other or conflict.
2. **Surface the misalignments.** List every place two elements pull in opposite directions, with the consequence each misalignment produces.
3. **Rank them** by impact on the organization's effectiveness or on the change in question.
4. **Recommend alignment moves.** For the top misalignments, what to change, in what element, and how the change ripples to the others. Since the elements are interdependent, name the knock-on adjustments rather than treating a fix as isolated.
5. **Verdict.** Overall coherence of the organization, and for a change context, the realignment needed for it to succeed.

## Report structure

Write a thorough markdown report and save it to `7s-<organization-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The organization, the purpose and any target change, and the date.
2. **Element summary.** A table of all seven elements with their current state (and desired state plus gap, for a change) and confidence.
3. **Per-element detail (seven sections).** The assessment and evidence for each, grounded in specifics.
4. **Alignment analysis.** The fit between elements, presented so the reinforcing and conflicting pairs are clear (a matrix or a grouped list).
5. **Key misalignments.** Ranked, each with its consequence and a recommended fix and the knock-on adjustments it requires.
6. **Verdict and next steps.** Overall coherence and, for a change, the sequence of realignment.
7. **Caveats.** The framework is a structured snapshot, not a forecast; the soft elements are judgment, not measurement; and alignment is necessary but not sufficient for performance.

## Principles

- **Alignment is the point.** Seven separate write-ups are not a 7-S analysis. The value is in the fit between elements.
- **Describe what is, not what is claimed.** Especially for the soft elements, name what the organization actually rewards and tolerates.
- **Interdependence cuts both ways.** A fix in one element forces adjustments in others. State the ripple, do not pretend a change is local.
- **Hard and soft both matter.** The soft elements are harder to assess and usually decide whether change holds.
- **Parallel where independent.** The seven elements can be assessed concurrently; the alignment synthesis needs all seven and runs after.
