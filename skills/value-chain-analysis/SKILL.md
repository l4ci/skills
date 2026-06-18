---
name: value-chain-analysis
description: Use when the user wants to analyze how a company creates value and where its competitive advantage lies, using Porter's Value Chain (inbound logistics, operations, outbound logistics, marketing and sales, service, plus firm infrastructure, HR, technology development, procurement). Fans out parallel analyst subagents per activity to assess cost and value contribution versus competitors, then synthesizes the sources of advantage, weak links, and linkages in a detailed markdown report. Triggers include "value chain", "value chain analysis", "where do we create value", "cost and differentiation drivers", "Porter value chain".
---

# value-chain-analysis

Analyzes how a firm creates value using Porter's value chain, breaking it into nine activities (five primary, four support) to locate where competitive advantage actually lives. Advantage comes from specific activities and from how they link, not from the firm as a whole.

The nine activities, what to assess for each, the role of linkages, and the pitfalls live in [references/value-chain.md](references/value-chain.md). Load that file before analyzing.

## When to use

The user wants an internal view of how a company creates and could create more value, where it carries excess cost, or where its competitive advantage lives. It is the internal counterpart to the external frameworks (PESTEL, Five Forces). For organizational alignment rather than value creation, prefer 7-S.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **COMPANY** (required): the firm or business unit to analyze. If the firm spans very different products or segments, agree which chain to analyze, since diverse businesses have different chains.
- **STRATEGY** (required): the advantage the firm pursues, cost leadership or differentiation. The same chain reads differently through each lens, so ask if it is unclear.
- **CONTEXT** (optional): key competitors and any known cost or differentiation concerns.

## Orchestration map

```
Stage 1  Activity Analysis ── 1 analyst subagent per activity IN PARALLEL ──┐  (cost, value, vs competitors)
Stage 2  Synthesis         ── 1 agent, needs all activities ────────────────┘  (advantage, weak links, linkages)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval where the company is public.

## Stage 1: Activity Analysis (PARALLEL)

Dispatch one analyst subagent per activity, all at once (the five primary and four support activities from the reference file). Group support activities under their own label if helpful. Give each the shared framing and one activity.

**Shared framing (send to each analyst):**

> Analyze one value-chain activity for **[COMPANY]**, which pursues a **[STRATEGY]** advantage. Describe how the firm actually performs this activity, then assess:
> - **Cost:** the activity's rough share of total cost and its main cost drivers
> - **Value:** how the activity contributes to what buyers will pay, through lower cost or valued differentiation
> - **Versus competitors:** is this an advantage, parity, or disadvantage, with evidence
> - **Linkages:** how this activity connects to others in ways that create or could create value
> - **Confidence** (high, medium, low), lowered when evidence is thin
>
> Context: [CONTEXT]

Collect all activities before continuing, and re-dispatch any that fail.

## Stage 2: Synthesis (SEQUENTIAL, needs all activities)

One agent assembles the value-creation picture, read through the firm's chosen strategy:

1. **Locate the advantage.** Which activities and linkages actually create the firm's competitive advantage, and why they are hard for rivals to copy.
2. **Find the leaks.** Which activities carry excess cost or destroy value, and which are at parity where the firm needs an edge.
3. **Exploit linkages.** Where connecting activities differently would create value or cut cost, since linkages are a durable, hard-to-copy source of advantage.
4. **Recommend.** Strengthen the advantage-creating activities, fix or outsource the weak ones, and act on the linkages, all tied to whether the firm competes on cost or differentiation.

## Report structure

Write a thorough markdown report and save it to `value-chain-<company-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The company and unit, the strategy lens (cost or differentiation), key competitors, and the date.
2. **Value chain map.** A table of all nine activities with cost contribution, value contribution, and the competitive verdict (advantage, parity, disadvantage), scannable at a glance.
3. **Per-activity detail.** For each activity: how the firm performs it, its cost and value, and the comparison to competitors.
4. **Sources of advantage.** The activities and linkages where the firm's advantage lives.
5. **Weak links and leaks.** Where cost is excessive or value is lost, and where parity is a problem.
6. **Recommendations.** Strengthen, fix, outsource, and link, tied to the strategy.
7. **Caveats.** Cost and value shares are often estimates; advantage is relative to competitors and shifts as they move; and a diverse firm may need separate chains per business.

## Principles

- **Cost and value, not description.** Every activity is assessed for both. A description of what the firm does is not an analysis.
- **Advantage is relative.** Compare to competitors. Doing something well is not an advantage if rivals do it as well.
- **Linkages are the durable edge.** The connections between activities are harder to copy than any single activity; hunt them.
- **Read through the strategy.** Cost leadership and differentiation surface different priorities from the same chain.
- **Parallel where independent.** Activities are analyzed concurrently; the synthesis needs them all and runs after.
