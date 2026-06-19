---
name: value-proposition-canvas
description: 'Use when the user wants a Value Proposition Canvas for an offering and a customer segment, or asks to test whether a product fits what a customer actually needs. Fans out six parallel analyst subagents, three describing and ranking the Customer Profile (jobs, pains, gains) and three describing the Value Map (products and services, pain relievers, gain creators), each marking claims as fact or assumption, then ranks the customer side and assesses fit: which top jobs, pains, and gains the value map addresses, which it misses, and which relievers and creators chase things the customer does not care about. Produces a detailed markdown report. Triggers include "Value Proposition Canvas", "VPC", "value proposition design", "problem-solution fit", "does this fit the customer".'
---

# value-proposition-canvas

Runs Osterwalder, Pigneur, Bernarda, and Smith's Value Proposition Canvas to test whether an offering fits a customer segment: the **Customer Profile** (jobs, pains, gains) describes the customer, the **Value Map** (products and services, pain relievers, gain creators) describes the offering. It catches the failure of relievers and creators that land on minor jobs, pains, and gains rather than the customer's most important ones.

The two sides, the ranking discipline, the fit-check table, and the three levels of fit live in [references/value-proposition.md](references/value-proposition.md). Load that file before analyzing. The order is fixed: ground and rank the customer side first, then map the value side onto it.

## When to use

The user wants to test problem-solution fit for one value proposition aimed at one customer segment. This is the zoom-in companion to the Business Model Canvas: where the BMC maps a whole business model across nine blocks, the VPC takes just two of those blocks, Value Propositions and Customer Segments, and examines them in detail. Use the BMC for the whole model and its viability; use this when the question is narrower, whether the offer matches the customer. It pairs with jobs-to-be-done, which goes deeper on the Customer Jobs half. One offer aimed at several segments is several canvases; model the one the user names, or model each separately, and do not blur them into one.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **VALUE PROPOSITION** (required): the offering to test, named specifically (a product, service, or feature set), not a whole company.
- **CUSTOMER SEGMENT** (required): the one segment whose fit is being tested. If the user names several, narrow to one or split into separate canvases with a question first.
- **CONTEXT** (optional): the stage (idea, early, in-market), the evidence available (interviews, usage data, none yet), and the decision the canvas should inform (build, pivot, prioritize). This shapes which assumptions matter most and how the fit verdict is framed, not the content of the two sides.

## Orchestration map

```
Stage 1  Profile + Value Map  ── 6 analyst subagents IN PARALLEL ──┐
           3 on Customer Profile (Jobs, Pains, Gains; each ranks)  │
           3 on Value Map (Products & Services, Relievers, Creators)│
Stage 2  Fit Assessment       ── 1 agent, needs all 6 ─────────────┘  (rank customer side, assess fit, flag irrelevance, name riskiest assumptions)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their side in real evidence.

## Stage 1: Profile and Value Map (PARALLEL)

Dispatch six analyst subagents at once: three on the Customer Profile (one each on Customer Jobs, Pains, Gains) and three on the Value Map (one each on Products & Services, Pain Relievers, Gain Creators). Give each the shared framing plus its component's content from the reference file.

The Customer Profile analysts must **rank** their items by importance to the customer, with rationale, and must describe the customer rather than invent one. The Value Map analysts describe the offering. Both sides mark every claim fact or assumption.

**Shared framing (send to every analyst):**

> Analyze one component of a Value Proposition Canvas for this value proposition, **[VALUE PROPOSITION]**, aimed at this customer segment, **[CUSTOMER SEGMENT]**. Work through your assigned component using its definition from the framework, grounding each material claim in real evidence (observed behavior, interview data, usage, sales records) where you can find it. For every material claim, mark it a **fact** (evidence exists) or an **assumption** (a hypothesis still to test), and rate confidence **high, medium, or low**, lowered if evidence was thin.
>
> If your component is on the **Customer Profile** (Jobs, Pains, or Gains): describe the customer as they actually are, do not invent a customer to fit the offer, and **rank your items by importance to the customer** (jobs by importance, pains by severity, gains by relevance) with a one-line rationale for each rank.
>
> If your component is on the **Value Map** (Products & Services, Pain Relievers, or Gain Creators): describe the offering, and for each item name the specific customer job, pain, or gain it is meant to enable, relieve, or create.
>
> Then return:
> - **Component summary**: a tight description of this component for this case
> - **Items**: the specific jobs / pains / gains, or products / relievers / creators, each with its evidence, and (Profile side) its rank and rationale, or (Value side) the profile item it targets
> - **Facts vs assumptions**: which items are grounded and which are hypotheses, each with confidence
> - **Gaps**: what is missing, unclear, or unknowable from available information
>
> Context: [CONTEXT]

Collect all six structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: Fit Assessment (SEQUENTIAL, needs all 6)

One agent merges the six components and assesses fit, testing the match rather than restating the two sides:

1. **Rank the customer side.** Consolidate the three profile components into one ranked picture: the most important jobs, the most severe pains, the most-wanted gains, each with its fact/assumption status. This ranking governs everything below.
2. **Assess fit, item by item.** Using the fit-check table, take each top job, pain, and gain and ask whether the value map addresses it: which products enable the top jobs, which pain relievers address the top pains, which gain creators produce the top gains. Mark each hit, partial, or miss. Name every top item the value map misses.
3. **Flag irrelevant relievers and creators.** Find every pain reliever and gain creator that addresses a low-ranked or absent pain or gain. These are effort spent where the customer does not care. List them and say so.
4. **State the fit level.** Declare which of the three levels the analysis reaches. The canvas can establish problem-solution fit at most; do not claim product-market fit (needs market evidence) or business-model fit (needs the BMC).
5. **Riskiest assumptions to test.** The one or two assumptions, usually on the customer side, that would break the fit if wrong. Tie these to the CONTEXT: what to test first before building or committing.

## Report structure

Write a thorough markdown report and save it to `value-proposition-canvas-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The value proposition and segment analyzed, the stage and context if given, the date, and a one-line note that the canvas tests problem-solution fit, not market or business-model fit.
2. **Verdict.** Whether the value map fits the profile, in a few sentences, with the fit level stated. A summary line on the strongest match and the biggest miss.
3. **Customer Profile.** Jobs, pains, and gains, each ranked by importance to the customer, with evidence and fact-versus-assumption noted. The ranking is the spine of the report.
4. **Value Map.** Products and services, pain relievers, and gain creators, each tied to the profile item it targets, with evidence and fact-versus-assumption noted.
5. **Fit assessment.** The fit-check table (top jobs, pains, gains against the value map; hit, partial, miss), the top items the map misses, and the relievers and creators that address things nobody ranks highly.
6. **Riskiest assumptions to test.** Ranked, tied to the context, with what to test first.
7. **Caveats.** The canvas tests problem-solution fit on paper, not whether the market will respond (product-market fit, needs market evidence) or whether a profitable model can carry it (business-model fit, needs the Business Model Canvas); the customer side is described from available evidence and assumptions marked as such are untested; good fit on the canvas describes a promising hypothesis, not a validated one.

## Principles

- **Rank, do not list.** Lists with no order cannot be tested for fit, because every item looks equal.
- **Fit is the few, not the all.** Good fit addresses the highest-ranked jobs, pains, and gains, not every item.
- **Mark facts or assumptions honestly.** Where evidence is missing, lower confidence rather than inventing the customer or the offer's effect.
- **Name the fit level.** The canvas reaches problem-solution fit at most; claiming more overstates what it can show.
