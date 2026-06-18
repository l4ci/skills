---
name: vrio-analysis
description: Use when the user wants a VRIO analysis of a firm's resources and capabilities, or asks whether a resource is a source of sustained competitive advantage. Optionally surfaces candidate resources first, then fans out one analyst subagent per resource to run the four VRIO gates (Valuable, Rare, Costly to Imitate, Organized) with evidence and assign a competitive implication, then synthesizes the strategic core and fixable gaps into a detailed markdown report. Triggers include "VRIO", "VRIN", "resource-based view", "is this a sustainable advantage", "test our core competencies", "RBV".
---

# vrio-analysis

Runs Jay Barney's VRIO analysis to test whether a firm's resources and capabilities are a source of sustained competitive advantage. Each resource is run through four questions in order: is it Valuable, is it Rare, is it Costly to Imitate, and is the firm Organized to capture its value? The first "no" sets the verdict, which lands at one of competitive disadvantage, parity, temporary advantage, or sustained advantage.

The four questions, the sources of inimitability, the decision table, and the pitfalls live in [references/vrio.md](references/vrio.md). Load that file before analyzing and run each resource through the gates exactly.

## When to use

The user wants to know whether a firm's strengths actually hold up as durable advantages, or whether they are table stakes that rivals match. The unit of analysis is a resource or capability, not the industry and not the firm as a whole. It pairs downstream of value-chain-analysis: the value chain finds where advantage lives across the firm's activities, and VRIO then tests whether each candidate resource that emerges from it actually lasts. For the external view of industry structure, use porters-five-forces instead.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework and the four questions keyed to it regardless of the output language.

## Inputs

- **FIRM** (required): the company or business unit whose resources are tested.
- **RESOURCES** (optional): the resources or capabilities to put through VRIO. If the user has not listed them, surface candidates in Stage 0 before fanning out.
- **CONTEXT** (optional): the industry, key competitors, and the strategic question the analysis should inform. This shapes the value test (value is always relative to a specific opportunity or threat) and the synthesis.

## Orchestration map

```
Stage 0  Surface resources  ── 1 agent, only if RESOURCES not given ──┐  (sequential, optional)
Stage 1  Resource Analysis  ── 1 analyst subagent per resource IN PARALLEL ──┐  (four VRIO gates with evidence)
Stage 2  Synthesis          ── 1 agent, needs all resources ─────────────────┘  (strategic core, fixable gaps)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground judgments in real evidence.

## Stage 0: Surface resources (SEQUENTIAL, only if RESOURCES not given)

If the user has not listed resources, surface a candidate set before fanning out. Draw from the firm's value chain and key activities, its brand and reputation, intellectual property and patents, proprietary data, distribution and supplier relationships, tacit know-how, and culture. Aim for a focused set of firm-specific candidates rather than a long list, and screen out obvious industry table stakes (resources every competitor must have) so the parallel stage tests things that could plausibly clear the gates. Confirm the candidate list with the user if the set is large or ambiguous, then proceed.

## Stage 1: Resource Analysis (PARALLEL)

Dispatch one analyst subagent per candidate resource, all at once. Give each the shared framing plus its one resource.

**Shared framing (send to every analyst):**

> Run one resource of **[FIRM]** through the four VRIO questions, in order, stopping the verdict at the first "no": **[RESOURCE]**. For each question, judge the answer with real evidence and explain the reasoning:
> - **Valuable?** Does it let the firm exploit an opportunity or neutralize a threat, by raising what buyers pay or lowering cost? Tie value to a specific opportunity or threat, not value in the abstract.
> - **Rare?** Is it controlled by only a few competitors, or is it table stakes the whole industry holds?
> - **Costly to Imitate?** Could a rival duplicate or substitute it without a cost disadvantage? Name the mechanism that protects it (unique history or path dependence, causal ambiguity, social complexity, patents) and say why a specific competitor could not copy it cheaply.
> - **Organized to capture value?** Are the firm's structure, processes, and systems set up to actually exploit it?
>
> Then return:
> - **Verdict**: competitive disadvantage / parity / temporary advantage / unrealized advantage / sustained advantage, from the decision table
> - **Per-question answers**: yes/no for each of V, R, I, O with the evidence and reasoning behind each
> - **Inimitability source**: which mechanism (if any) protects it, and how durable it is
> - **Trend**: is the protection eroding (patent expiry, history reconstructable, ambiguity clearing) or holding
> - **Confidence**: high, medium, or low, lowered when evidence was thin or a rare/inimitable claim could not be backed
>
> Context: [CONTEXT]

Collect every resource's structured result before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: Synthesis (SEQUENTIAL, needs all resources)

One agent merges the per-resource verdicts into the strategic picture:

1. **Rank by competitive implication.** Order the resources from sustained advantage down to disadvantage, so the few that matter stand apart from the many at parity.
2. **Name the strategic core.** The resources that reach sustained competitive advantage (valuable, rare, costly to imitate, and organized) are where the firm's durable edge lives. Identify them and say which mechanism keeps each one protected.
3. **Flag the fixable gaps.** Resources that are valuable, rare, and costly to imitate but not organized are unrealized advantages: real potential the firm leaves on the table. These are the highest-leverage findings, because only the organization needs to change, not the resource.
4. **Read the eroding edges.** Resources at temporary advantage, and any sustained ones whose inimitability is decaying, are where the advantage needs defending or rebuilding before rivals close the gap.
5. **Connect to strategy.** Tied to the CONTEXT: which resources to defend and invest behind, which gaps to organize around, and where the firm relies on parity resources that give it no edge. Where this follows a value-chain analysis, map the verdicts back onto the activities the advantage was thought to live in.

## Report structure

Write a thorough markdown report and save it to `vrio-<firm-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The firm and unit, the industry and competitors if given, the date, and a one-line note on the framework and its snapshot nature.
2. **Verdict.** The strategic picture in a few sentences, with a summary table: each resource, its V/R/I/O answers (yes/no per gate), its competitive implication, the expected economic performance, and confidence. Sort the table by implication so the strategic core sits at the top.
3. **Per-resource sections.** For each resource: the four answers with their evidence and reasoning, the inimitability mechanism and its durability, and the trend. Ground each in the firm's specifics, not textbook definitions.
4. **The strategic core.** The resources that yield sustained advantage and why they hold.
5. **Fixable gaps.** Valuable, rare, costly-to-imitate resources that are not organized, with what would need to change to capture them.
6. **Eroding edges and dynamics.** Temporary advantages and decaying inimitability, and what defends or rebuilds them.
7. **Strategic implications.** Concrete moves tied to the context: invest, organize, defend, or stop relying on parity resources for an edge.
8. **Caveats.** VRIO scores resources, not the firm; rare and costly-to-imitate are judgments that need evidence, not assertions; the analysis is a snapshot and imitability erodes over time; and value is always relative to a specific opportunity or threat in the firm's environment.

## Principles

- **Resource, not firm.** Score each resource on its own. A strong firm is a portfolio of resources at different verdicts; the analysis is only useful if it separates the few that sustain advantage from the many at parity.
- **Gate in order.** Walk V, R, I, O in sequence and let the first "no" set the verdict. The questions are a gate, not four independent scores.
- **Evidence for rare and inimitable.** Name the mechanism and show why a specific rival could not copy the resource cheaply. An unbacked claim of rarity or inimitability is the framework's most common failure.
- **Organization is the fixable gap.** When a resource passes V, R, and I but not O, the advantage already exists and only the organization is in the way. Surface it; it is the most actionable finding VRIO produces.
- **Imitability erodes.** Treat costly-to-imitate as a statement about today and note its trajectory, or a sustained verdict quietly decays into temporary.
- **Parallel where independent.** Resources share no state, so analyze them concurrently. Synthesis needs them all, so it runs after.
