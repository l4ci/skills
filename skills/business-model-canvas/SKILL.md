---
name: business-model-canvas
description: Use when the user wants a Business Model Canvas of a company, product, or venture, or asks to map out how a business creates, delivers, and captures value. Fans out nine parallel analyst subagents (one per building block), each describing its block for the specific business with evidence and flagging assumptions versus facts, then synthesizes whether the blocks cohere, where the model is strongest and weakest, and which assumptions are riskiest into a detailed markdown report. Triggers include "Business Model Canvas", "BMC", "map the business model", "Osterwalder canvas", "nine building blocks".
---

# business-model-canvas

Runs Osterwalder and Pigneur's Business Model Canvas to map how a business creates, delivers, and captures value across nine building blocks: Customer Segments, Value Propositions, Channels, Customer Relationships, Revenue Streams, Key Resources, Key Activities, Key Partnerships, and Cost Structure. The point is not to fill nine boxes but to test whether they fit each other.

The nine blocks, their key questions, the right-side/left-side/viability logic, and the pitfalls live in [references/canvas.md](references/canvas.md). Load that file before analyzing and work each block against its questions exactly.

## When to use

The user wants to map a business model on one page, understand how an existing business works, or pressure-test a new venture's model. The unit of analysis is a business model for a defined business, product, or venture, not a whole company's strategy and not a business plan. If a company runs more than one model, model the one the user names or model each separately; do not blur several models into one canvas.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework, block names, and fit logic keyed to it regardless of the output language.

## Inputs

- **BUSINESS** (required): the company, product, or venture to model. Push for one defined business model. If the business is vague or runs several models, narrow it with one or two questions first.
- **CONTEXT** (optional): the stage (idea, early, scaling, established), the market and geography, and the decision the canvas should inform (pitch, pivot, entry, investment). This shapes which assumptions matter most and the framing of the synthesis, not the content of the blocks.

## Orchestration map

```
Stage 1  Block Analysis   ── 9 analyst subagents IN PARALLEL ──┐  (each describes one block with evidence)
Stage 2  Synthesis        ── 1 agent, needs all 9 ────────────┘  (coherence, fit, the story, weakest links)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their block in real evidence.

## Stage 1: Block Analysis (PARALLEL)

Dispatch nine analyst subagents at once, one per building block. Give each the shared framing plus its block's key questions from the reference file.

**Shared framing (send to every analyst):**

> Describe one block of the Business Model Canvas for this business: **[BUSINESS]**. Work through the key questions for your assigned block, grounding each material claim in real evidence (named segments, prices, channels, partners, cost figures) where you can find it. For every material claim, mark it as a **fact** (evidence exists) or an **assumption** (a hypothesis still to be tested). Then return:
> - **Block summary**: a tight description of this block for this business
> - **Contents**: the specific items in the block (the segments, the revenue streams, the key resources, and so on), each with its supporting evidence
> - **Facts vs assumptions**: which claims are grounded and which are hypotheses
> - **Dependencies**: which other blocks this one most relies on or feeds (for example, which value proposition this channel delivers)
> - **Gaps**: what is missing, unclear, or unknowable from available information
> - **Confidence**: high, medium, or low, lowered if evidence was thin or the block rests mostly on assumptions
>
> Context: [CONTEXT]

Assign the nine blocks from the reference file: Customer Segments, Value Propositions, Channels, Customer Relationships, Revenue Streams, Key Resources, Key Activities, Key Partnerships, and Cost Structure. Collect all nine structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: Synthesis (SEQUENTIAL, needs all 9)

One agent merges the nine block analyses into a single coherent picture by checking fit rather than restating the blocks:

1. **Right-side coherence.** Does each value proposition map to a named segment, and each segment to a value proposition? Do the channels and customer relationships fit each segment's expectations and economics? Do the revenue streams capture value from the segments the value propositions serve? Name every mismatch.
2. **Left-side sufficiency.** Do the key resources, activities, and partnerships actually produce and deliver the value propositions? Is anything required to deliver the value missing? Is anything listed that no block depends on?
3. **Viability.** Do the revenue streams plausibly exceed the cost structure over a realistic horizon, given the volumes the segments and channels can support? Is the cost structure (cost-driven or value-driven) consistent with the pricing and the value proposition?
4. **The business-model story.** Tell the model as one connected narrative: who it serves, with what value, reached how, earning through which streams, produced with which resources, activities, and partners, at what cost. If the story does not hold together, say where it breaks.
5. **Weakest links and riskiest assumptions.** The one or two mismatches that most threaten the model, and the assumptions (usually on the right side) that would sink it if wrong. Tie these to the CONTEXT: what to test first, what to fix before the next stage or decision.

## Report structure

Write a thorough markdown report and save it to `business-model-canvas-<business-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The business and model analyzed, the stage and context if given, the date, and a one-line note on the framework and that a canvas is a model, not a plan.
2. **Verdict.** Whether the model coheres and looks viable, in a few sentences, with a summary table: each block, a one-line description, and confidence. Note up front the one or two weakest links.
3. **The canvas.** The nine blocks laid out in canvas order (right side, then left side, then a viability line), so the model is scannable on a glance. For each block: its contents, the evidence, and what is fact versus assumption.
4. **Synthesis.** Right-side coherence, left-side sufficiency, viability, and the business-model story told as one narrative.
5. **Weakest links and riskiest assumptions.** Ranked, tied to the context, with what to test or fix first.
6. **Caveats.** The canvas is a one-page model of how value is created, delivered, and captured, not a business plan, forecast, or execution roadmap; it captures the model at a moment; assumptions marked as such are untested; and a coherent canvas describes a sound model, not a guarantee the business will succeed.

## Principles

- **Fit, not boxes.** The value is in whether the nine blocks reinforce each other. Nine well-filled lists that contradict each other describe a broken model.
- **Value Propositions is the hinge.** Every right-side block exists to deliver a value proposition to a segment; every left-side block exists to produce one. Check each block against that.
- **Facts or honesty.** Mark every material claim as fact or assumption. Where data is missing, say so and lower confidence rather than inventing figures or presenting hopes as facts.
- **Viability is the cross-side test.** Desirable and feasible is not enough; revenue streams must plausibly exceed the cost structure. Synthesis must reach a view on this, not dodge it.
