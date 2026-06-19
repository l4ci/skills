---
name: kano-model
description: Use when the user wants to decide which product features to build, prioritize, cut, or how to position them, or asks how features drive customer satisfaction. Fans out parallel analyst subagents (one per candidate feature) that reason through the functional and dysfunctional customer responses for a target segment, assign a Kano category (must-be, one-dimensional, attractive, indifferent, or reverse) with rationale, confidence, decay risk, and segment sensitivity, then synthesizes a feature set: confirm the must-bes are covered, pick the performance features to compete on, choose a few delighters, drop the indifferent, avoid the reverse, and sequence with a decay timeline into a detailed markdown report. Triggers include "Kano model", "Kano analysis", "must-be vs delighter", "classify these features", "delighters", "which features matter".
---

# kano-model

Noriaki Kano's model classifies candidate features by how their presence or absence drives customer satisfaction, so investment goes where it pays. It catches the mistake of treating all features alike: some only punish you when missing, some reward you in proportion to how well you do them, and a few delight precisely because no one expected them.

The five categories, the paired functional/dysfunctional question, the full 5×5 evaluation table, the satisfaction curves, the decay over time, and the pitfalls live in [references/kano.md](references/kano.md). Load that file before classifying.

## When to use

The user is deciding which features to build, prioritize, cut, or how to position them, and wants to know which features actually matter to satisfaction and why. The unit of analysis is a set of candidate features evaluated for one named customer segment. Pairs with rice-prioritization (Kano says which features matter and why; RICE then sequences the backlog by score), jobs-to-be-done (which jobs the features serve), and value-proposition-canvas (how the features map to customer pains and gains). Use Kano when the question is "what kind of feature is this and how much should we invest," not "in what order do we ship the backlog."

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **SEGMENT** (required): the target customer segment to classify for. Categories vary by segment, so one classification serves one segment. If the user names several segments, classify the primary one and flag where features likely differ, or run the analysis once per segment.
- **FEATURES** (required): the candidate feature list to classify. Push for concrete, distinct features, not vague themes. If the list is a wishlist of dozens, narrow to the set the decision actually turns on.
- **CONTEXT** (optional): the product, its market and competitors, the decision the analysis should inform (roadmap, MVP scope, cut list, positioning), and any real customer data available. This shapes the synthesis and confidence, not the categories themselves.

## Orchestration map

```
Stage 1  Setup            ── inline ───────────────────────────┐  (confirm segment + candidate feature list)
Stage 2  Classification   ── N analyst subagents IN PARALLEL ──┤  (one per feature: functional/dysfunctional → category)
Stage 3  Synthesis        ── 1 agent, needs all N ─────────────┘  (bucket, cover must-bes, pick, sequence, decay)
```

## Stage 1: Setup (inline)

Confirm the target SEGMENT and the candidate FEATURES before dispatching. If the segment is unstated, ask for it: the same feature lands in different categories for different segments. If the feature list is vague or huge, narrow it with the user to the concrete set the decision depends on. Do not classify yet.

## Stage 2: Classification (PARALLEL)

Dispatch one analyst subagent per feature, all at once. Give each the shared framing plus its single assigned feature and the SEGMENT.

**Shared framing (send to each analyst):**

> Classify one product feature using the Kano model for this segment: **[SEGMENT]**. Your feature is: **[FEATURE]**. Context: [CONTEXT].
>
> Reason through the paired Kano questions for this segment:
> - **Functional:** how would this segment feel if the feature is present / done well? (like it / expect it / neutral / tolerate it / dislike it)
> - **Dysfunctional:** how would they feel if it is absent / done poorly? (same scale)
>
> Map the answer pair through the Kano evaluation table to a category: **MUST-BE (M)**, **ONE-DIMENSIONAL (O)**, **ATTRACTIVE (A)**, **INDIFFERENT (I)**, or **REVERSE (R)**. If the pair is contradictory, that is **QUESTIONABLE (Q)**: re-reason the responses rather than forcing a category. Then return:
> - **Feature**: the feature, restated tightly
> - **Functional / dysfunctional answers**: the chosen answer on each, with one line of reasoning each
> - **Category**: M / O / A / I / R, derived from the table, with a short rationale
> - **Decay risk**: whether and how fast this is likely to migrate (attractive → one-dimensional → must-be), and roughly when
> - **Segment sensitivity**: segments for which this feature would likely land in a different category, especially any where it turns reverse
> - **Confidence**: high, medium, or low. Lower it when you have no real customer data: say explicitly that this is a reasoned proxy for an actual Kano survey, not survey data
>
> Ground the responses in real evidence (competitor offerings, reviews, stated customer behavior, comparable products) using available retrieval tools wherever you can, rather than guessing from intuition.

Tell each subagent its final message is the return value: structured data, not prose for a human. Collect all classifications before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all N)

One agent merges the per-feature classifications into a feature set and a sequence, turning categories into investment decisions:

1. **Bucket by category.** Sort every feature into must-be, one-dimensional, attractive, indifferent, or reverse, carrying its confidence. Flag any that came back questionable for re-evaluation.
2. **Cover the must-bes first.** Confirm every must-be is present and adequate. A missing or weak must-be sinks the product regardless of how many delighters sit on top, so these are non-negotiable table stakes.
3. **Pick the performance features to compete on.** From the one-dimensional set, choose the few where doing more clearly converts to satisfaction and where you can beat competitors. You cannot maximize all of them; pick the axes that matter to this segment.
4. **Select a few delighters.** From the attractive set, choose a small number of differentiators to invest in deliberately. Delight is expensive and short-lived, so concentrate rather than scatter.
5. **Drop the indifferent, avoid the reverse.** Cut indifferent features from the roadmap; they return nothing. Do not ship reverse features to this segment even if they delight a fringe.
6. **Sequence and time the decay.** Order the work must-be → performance → delighter. Lay out the decay timeline: which of today's delighters will become performance features and then must-bes, and roughly when, so the team plans a pipeline of new delighters rather than defending old ones.

## Report structure

Write a thorough markdown report and save it to `kano-model-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The segment and the feature set classified, the product and context if given, the date, and a one-line note on the framework and that this is a reasoned classification, not a fielded Kano survey, unless real survey data was used.
2. **Verdict.** The headline decision in a few sentences: are the must-bes covered, what to compete on, which delighters to back, what to cut. Lead with the riskiest gap (any missing must-be).
3. **Classification table.** Every feature, its category, its functional/dysfunctional answers, confidence, and decay risk, grouped by category so the buckets are scannable at a glance.
4. **Per-feature detail.** For each feature: the reasoning behind its category, segment sensitivity, and the evidence behind the call versus what was assumed.
5. **The feature set and sequence.** Must-bes to guarantee, performance features to compete on, delighters to back, what to drop, what to avoid, and the build order, with the decay timeline.
6. **Caveats.** Kano is a model of satisfaction, not of cost, effort, or revenue: it says which features matter and why, not in what order to build them by ROI (pair it with RICE for that). Categories are keyed to one segment and one moment in time and decay; classifications made without real customer data are reasoned proxies and should be validated with an actual functional/dysfunctional survey before large bets; and a clean classification describes how features drive satisfaction, not whether the product will succeed.

## Principles

- **Not every feature is performance.** "More features = better" is the default roadmap fallacy. Must-bes plateau, indifferent features return nothing, reverse features cost you; only genuine one-dimensional features reward "more."
- **The pair, not the wish.** A category comes from the functional and dysfunctional answers run through the table, never from how much customers say they want a feature. The dysfunctional answer is what discriminates.
- **One segment, one moment.** Categories vary by segment and decay over time. Treat the classification as a snapshot and plan to refill the delighter pipeline.
- **Honesty over precision.** Without real survey data this is a reasoned proxy. Say so, lower confidence, and recommend validating the high-stakes calls rather than presenting intuition as data.
