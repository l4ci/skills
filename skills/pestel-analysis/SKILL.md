---
name: pestel-analysis
description: Use when the user wants to scan the macro-environment around a company, industry, market, or decision using PESTEL (Political, Economic, Social, Technological, Environmental, Legal). Fans out six parallel analyst subagents (one per factor) to identify and assess the external forces, then prioritizes them by impact and certainty and draws implications in a detailed markdown report. Triggers include "PESTEL", "PEST analysis", "PESTLE", "macro-environment", "external factors", "what trends affect this market".
---

# pestel-analysis

Scans the macro-environment around a subject using PESTEL: the Political, Economic, Social, Technological, Environmental, and Legal forces that shape a market but lie outside any one firm's control. The skill identifies the forces in each factor, prioritizes them by impact and certainty, and draws the implications.

The six factors, their probes, the prioritization logic, and the pitfalls live in [references/pestel.md](references/pestel.md). Load that file before analyzing.

## When to use

The user wants the external macro context for a company, industry, market entry, or strategic decision. PESTEL is the macro layer: for industry competitive structure prefer Five Forces, and for an internal view prefer a value chain or 7-S. PESTEL output feeds naturally into the Opportunities and Threats of a SWOT.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **SUBJECT** (required): the company, industry, market, or decision the scan is for. A force only matters relative to a subject.
- **GEOGRAPHY** (required): the region or regions in scope. Macro forces are location-specific; push for this if missing.
- **HORIZON** (optional): the time frame to scan over. Defaults to the next three to five years.
- **CONTEXT** (optional): the decision the scan informs, which sharpens the "so what" of each force.

## Orchestration map

```
Stage 1  Factor Scan   ── 6 analyst subagents IN PARALLEL ──┐  (one per PESTEL factor, forces + assessment)
Stage 2  Synthesis     ── 1 agent, needs all 6 ────────────┘  (prioritize by impact x certainty, linkages, implications)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval to ground forces in real, current developments.

## Stage 1: Factor Scan (PARALLEL)

Dispatch six analyst subagents at once, one per factor. Give each the shared framing plus its factor's probes from the reference file.

**Shared framing (send to every analyst):**

> Scan one PESTEL factor for **[SUBJECT]** in **[GEOGRAPHY]** over **[HORIZON]**. Identify the forces in your factor that actually bear on this subject, not a generic list. Stay at the macro level (do not drift into specific competitors or the company itself). For each force return:
> - The force in one line, with evidence
> - **Direction** (rising, falling, shifting) and **timeframe**
> - **Opportunity or threat** for the subject, and the "so what"
> - **Impact** (1 to 5) and **Certainty** (high, medium, low)
>
> Context: [CONTEXT]

Assign the six factors from the reference file: Political, Economic, Social, Technological, Environmental, Legal. Collect all six before continuing, and re-dispatch any that fail.

## Stage 2: Synthesis (SEQUENTIAL, needs all 6)

One agent turns the forces into a prioritized picture:

1. **Prioritize.** Rank the forces by impact crossed with certainty. Separate the high-impact and high-certainty forces (plan and act) from the high-impact and high-uncertainty ones (the watch list to monitor and build scenarios around).
2. **Map linkages.** Identify where forces across factors chain together into a larger movement, since the consequential story usually crosses factors.
3. **Split into opportunities and threats** for the subject, ready to feed a SWOT.
4. **Draw implications.** What the prioritized forces mean for the subject and the decision, and what to monitor.

## Report structure

Write a thorough markdown report and save it to `pestel-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The subject, the geography, the horizon, and the date.
2. **Priority forces.** The top forces up front in a ranked table: force, factor, impact, certainty, opportunity or threat. A reader with two minutes should leave knowing what matters most.
3. **Per-factor detail (six sections).** The forces found in each factor, with direction, timeframe, evidence, and the "so what".
4. **Linkages.** The cross-factor chains that add up to a larger movement.
5. **Opportunities and threats.** The two lists, ready to feed a SWOT.
6. **Implications and watch list.** What to act on now, and what to monitor with scenarios.
7. **Caveats.** PESTEL is a macro snapshot; forces shift; certainty is judgment, not data; and the scan is only useful when each force is tied to the subject with a clear implication.

## Principles

- **Anchor every force to the subject and geography.** A force in the abstract is noise.
- **Prioritize, do not enumerate.** Impact crossed with certainty is what turns a list into analysis.
- **Right altitude.** Stay macro. Competitors and the company belong in other frameworks.
- **Separate plan from monitor.** A near-certain force and a speculative one demand different responses.
- **Parallel where independent.** The six factors are scanned concurrently; the synthesis needs all six and runs after.
