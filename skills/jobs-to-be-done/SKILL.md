---
name: jobs-to-be-done
description: Use when the user wants to understand why customers hire a product, shape or reposition an offering around real customer motivation, or decide what to build based on the progress customers are trying to make. Defines the customer and the struggling moment, then fans out parallel analyst subagents over the functional job, the emotional and social job, the desired outcomes, the competing solutions and nonconsumption, and the four forces of progress, and synthesizes a job story, an opportunity-scored ranking of outcomes, and implications for the offering into a detailed markdown report. Triggers include "jobs to be done", "JTBD", "what job is the customer hiring this for", "why do customers switch", "outcome-driven innovation".
---

# jobs-to-be-done

Clayton Christensen's Jobs-to-Be-Done lens: customers do not buy products, they hire a solution to make progress in a struggling moment. It catches the trap of profiling the customer instead of understanding the **job in a circumstance**, which is solution-agnostic and the same whether a drill, a hook, or a handyman does it. People don't want a quarter-inch drill; they want a quarter-inch hole, and really the progress the hole enables.

The three dimensions of a job (functional, emotional, social), the circumstance, desired outcomes as measurable outcome statements, competing solutions including nonconsumption, the four forces of progress, the job-story format, and the opportunity-scoring formula live in [references/jtbd.md](references/jtbd.md). Load that file before analyzing.

## When to use

The user wants to shape or reposition a product around what customers are actually trying to accomplish, decide what to build, or understand why customers switch from one solution to another. The unit of analysis is the job and its desired outcomes, not the company and not a feature list. This skill *finds* the job, the outcomes, and where current solutions fall short; value-proposition-canvas then *maps* a specific offering onto a job already understood, so run this first when the job itself is unclear and reach for value-proposition-canvas when the user already knows the job. Pairs with design-thinking (empathize and define), lean-startup, and kano-model.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **SUBJECT** (required): the product, service, or category whose job is in question, and the customer it serves. If the customer or the product is vague, narrow it with one or two questions before starting.
- **CIRCUMSTANCE** (optional): the struggling moment or trigger the user already has in mind, the segment, market, or geography, and the decision the analysis should inform (what to build, how to position, why churn is happening). This focuses the job; it does not replace Stage 1.

## Orchestration map

```
Stage 1  Frame the Job   ── 1 agent inline ───────────────────┐  (customer + struggling moment / circumstance)
Stage 2  Job Analysis     ── 5 analyst subagents IN PARALLEL ──┤  (functional; emotional+social; outcomes; competing solutions; four forces)
Stage 3  Synthesis        ── 1 agent, needs all 5 ─────────────┘  (job story, opportunity ranking, implications)
```

## Stage 1: Frame the Job (inline)

Before any fan-out, define two things precisely; every analyst depends on them:

1. **The customer.** Who is doing the hiring. Resist demographics; describe the person by the situation they are in, not by age or income.
2. **The struggling moment / circumstance.** The specific situation and trigger that makes the job active: when and where the struggle bites, what just happened that makes progress worth seeking now.

State the candidate job in one provisional line: *when [situation], a person trying to make [progress].* Keep it solution-free. If the user gave a CIRCUMSTANCE, sharpen it here; if not, name the most likely struggling moment and flag it as an assumption to be tested. Pass the framed customer and circumstance to every Stage 2 analyst.

## Stage 2: Job Analysis (PARALLEL)

Dispatch five analyst subagents at once, one per facet of the job. Give each the shared framing plus its facet's brief from the reference file.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground the job in real evidence: reviews, forums, support logs, interviews, named competitors, prices, public usage data.

**Shared framing (send to each analyst):**

> Analyze one facet of the job to be done for this customer and struggling moment. Customer: **[CUSTOMER]**. Circumstance / trigger: **[CIRCUMSTANCE]**. Provisional job: **[PROVISIONAL JOB LINE]**. Stay solution-agnostic: describe the progress the customer is trying to make, never assume our product is the answer. Ground every material claim in real evidence where you can find it. For each claim, mark it as a **fact** (evidence exists) or an **assumption** (a hypothesis still to be tested). Then return:
> - **Facet summary**: a tight account of your facet of the job for this customer and circumstance
> - **Contents**: the specific items your facet calls for (see your brief below), each with supporting evidence
> - **Facts vs assumptions**: which claims are grounded and which are hypotheses
> - **Confidence**: high, medium, or low, lowered if evidence was thin
> - **Gaps**: what is missing, unclear, or unknowable from available information

Assign the five facets, each with its brief from the reference file:

1. **The functional job:** the practical task the customer is trying to accomplish; the objective, measurable work, stated solution-free.
2. **The emotional and social job:** how the customer wants to feel (emotional) and to be perceived by others (social) while making progress.
3. **Desired outcomes:** the metrics by which the customer judges the job done well, each phrased as a measurable outcome statement (direction + metric + object of control + context), with an Importance and a Satisfaction rating where evidence allows.
4. **Competing solutions:** everything the customer hires today: direct rivals, indirect and cross-category options, homemade workarounds, and nonconsumption (doing nothing). Note where each falls short.
5. **The four forces of progress:** the Push of the situation, the Pull of a new solution, the Anxiety of the new, and the Habit of the present, and a read on whether Push + Pull beats Anxiety + Habit.

Collect all five structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five analyses into a decision, not a restatement of the facets:

1. **The job story.** Write the job in one line, solution-free: *When [situation], I want to [motivation], so I can [expected outcome].* If the line contains a product or category, rewrite it. Capture the functional, emotional, and social dimensions the story implies.
2. **Opportunity ranking.** Rank the desired outcomes by the opportunity score, `Opportunity = Importance + max(Importance − Satisfaction, 0)`. Name the **underserved** outcomes (high importance, low satisfaction) at the top, the served outcomes (table stakes), and any overserved outcomes worth disinvesting. Where ratings are assumptions rather than survey data, say so and lower confidence.
3. **Where current solutions fail.** Cross the competing solutions against the underserved outcomes: which outcomes no current solution serves well, and what the workarounds and nonconsumption reveal about unmet need.
4. **Force balance.** Whether the four forces currently favor a switch, and which lever (raise Pull, cut Anxiety, loosen Habit) would tip a customer who is stuck.
5. **Implications for the offering.** What to build, change, or say to win the underserved outcomes and tip the forces, tied to the decision in CIRCUMSTANCE. Concrete moves, not restatements of the job.

## Report structure

Write a thorough markdown report and save it to `jobs-to-be-done-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The subject and customer analyzed, the circumstance and decision if given, the date, and a one-line note that the job is solution-agnostic and the analysis describes motivation, not a roadmap.
2. **The job story.** The one-line job story up front, with its functional, emotional, and social dimensions named.
3. **The job in detail.** The five facets laid out: functional job; emotional and social job; desired outcomes as outcome statements; competing solutions including workarounds and nonconsumption; the four forces. For each, its contents, the evidence, and what is fact versus assumption.
4. **Opportunity ranking.** The desired outcomes ranked by opportunity score in a table (outcome statement, importance, satisfaction, opportunity, served/underserved/overserved), underserved outcomes called out first.
5. **Implications.** Where current solutions fail, the force balance and the lever that tips it, and the concrete moves for the offering, tied to the decision.
6. **Caveats.** JTBD describes the customer's motivation and the progress they seek, not a product roadmap, a market size, or a financial case; outcomes and force readings drawn without customer interviews or survey data are assumptions, not measurements, and importance/satisfaction scores from the team rather than the customer are guesses; a well-framed job clarifies *what* progress to enable, not *whether* a given solution will sell.

## Principles

- **The job, not the product.** If the job names your product, you have described a feature and missed the real competition.
- **Circumstances, not demographics.** The same person hires different solutions in different moments.
- **All three dimensions.** Functional explains what the product does; emotional and social explain why people switch. Carry all three through to synthesis.
- **Nonconsumption is competition.** Doing nothing and homemade workarounds are usually the largest rivals and the loudest signal of an underserved job. Never list only the direct competitors.
