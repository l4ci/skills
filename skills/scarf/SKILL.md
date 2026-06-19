---
name: scarf
description: Use when the user is rolling out a change, giving feedback, designing a communication, planning a reorganization, or making a contentious decision and wants to see where people will feel socially threatened and how to lower it. Runs David Rock's SCARF model by fanning out five parallel analyst subagents, one per domain (Status, Certainty, Autonomy, Relatedness, Fairness), each assessing the threat and reward the situation creates in its domain with evidence and a severity, then synthesizes the biggest threats, the domains most at risk, and specific moves that lower threat and raise reward into a detailed markdown report. Triggers include "SCARF", "SCARF model", "social threat", "why are people resisting this change", "David Rock SCARF".
---

# scarf

Runs David Rock's SCARF model to read a situation for social threat and reward across five domains: Status, Certainty, Autonomy, Relatedness, and Fairness. The brain treats social experience much like physical survival: threat in any domain triggers an avoid response (defensiveness, disengagement), reward triggers an approach response (engagement), and a single high threat outweighs rewards spread across the rest. The output is specific moves that lower threat and raise reward, not labels for feelings.

The five domains, their threat and reward triggers, the practical levers, and the pitfalls live in [references/scarf.md](references/scarf.md). Load that file before analyzing. SCARF is a popularization of neuroscience, a useful heuristic, not a measurement instrument; keep that in view throughout.

## When to use

The user is about to do something to or with people who may feel threatened: announce a change, give feedback, send a difficult message, reorganize a team, or make a decision others will react to. The unit of analysis is one situation and the people it affects, read for social threat. Use the change cluster (kotter-change, adkar, force-field-analysis) to plan the change itself and psychological-safety for the standing climate of a team; reach for SCARF when the question is specifically *where will this land as a threat, and how do I defuse it.*

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **SITUATION** (required): the change, message, decision, or interaction to analyze. Push for one concrete situation. If it is vague, narrow it with a question or two first.
- **PEOPLE** (optional but valuable): who is affected and from whose point of view to read the threat (a team, a peer, a report, a whole org). Different people feel threat in different domains; name them where you can.
- **CONTEXT** (optional): history, prior reactions, constraints, and what the user wants the interaction to achieve. This shapes which domains matter most and how the moves are framed.

## Orchestration map

```
Stage 1  Framing        ── inline ─────────────────────────────┐  (the situation and the people affected)
Stage 2  Domain Read    ── 5 analyst subagents IN PARALLEL ─────┤  (threat + reward per domain, with severity)
Stage 3  Synthesis      ── 1 agent, needs all 5 ───────────────┘  (rank threats, design moves, prioritize)
```

## Stage 1: Framing (inline)

State the SITUATION in one or two sentences: what is changing or being said, by whom, to whom. Name the PEOPLE affected and the point of view the read should take. Pull in any CONTEXT that colors how people will receive it. This framing goes to every analyst so all five read the same situation.

## Stage 2: Domain Read (PARALLEL)

Dispatch five analyst subagents at once, one per domain. Give each the shared framing plus its domain's section from the reference file.

**Shared framing (send to each analyst):**

> Read one SCARF domain for this situation: **[SITUATION]**, affecting **[PEOPLE]**. Work only your assigned domain using its section of the reference file. Assess what the situation does in your domain and return:
> - **Threat:** what registers as an avoid response in this domain, for whom, with the specific evidence; rate it high / medium / low.
> - **Reward:** what already creates an approach response in this domain, with evidence; rate it high / medium / low.
> - **Levers:** two to four specific, domain-appropriate moves that would lower the threat or add reward. No generic "communicate more"; name the concrete action.
> - **Who:** which people feel this domain most, if it varies across them.
> - **Confidence:** high, medium, or low, lowered when you are inferring rather than working from stated facts.
>
> SCARF is a heuristic, not a measurement; your severities are judgment calls, so flag what you assumed. Context: [CONTEXT]

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their read in real evidence where the situation references documents, history, or stated reactions.

Assign the five domains from the reference file: Status, Certainty, Autonomy, Relatedness, Fairness. Collect all five structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five reads into a plan of action by ranking and designing rather than restating:

1. **Rank the threats.** Order all five domains by threat severity. Name the one or two domains most at risk; these set the agenda. Remember the asymmetry: a high threat outweighs rewards elsewhere, and removing it usually beats adding a new reward.
2. **Watch the cross-domain trap.** Check that the top threat is not being masked by an easy fix in another domain (a polished plan addresses certainty while the real wound is autonomy). Fix the domain that carries the threat.
3. **Design the moves.** For each at-risk domain, turn its levers into specific actions for this situation: what to do, say, or change, in what order. Lower the threat first, then add reward. Every move names a domain and a concrete action.
4. **Prioritize.** Choose the highest-leverage interventions across all five domains, by how much threat they remove for the effort. A SCARF read yields more moves than anyone will make; say which two or three to do first.

## Report structure

Write a thorough markdown report and save it to `scarf-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The situation and people analyzed, the context if given, the date, and a one-line note that SCARF is a heuristic for social threat, not a measurement.
2. **Verdict.** In a few sentences, where this lands hardest and what to do first, with a summary table: each domain, its threat rating, its reward rating, and confidence. Flag the one or two domains most at risk up front.
3. **Domain reads.** The five domains in SCARF order. For each: the threat and its evidence, the reward, the severities, who feels it, and the candidate levers.
4. **Synthesis.** The ranked threats, the cross-domain check, and the designed moves per at-risk domain.
5. **Priority moves.** The two or three highest-leverage interventions, in order, with what each defuses.
6. **Caveats.** SCARF is a popularization of neuroscience, a heuristic for noticing social threat, not a measured or clinically validated instrument; the severities are analyst judgment, not readings; the same situation threatens different people differently, so a read for one group may not hold for another; and defusing threat improves the odds of an approach response, it does not guarantee agreement.

## Principles

- **Threat beats reward.** A single high threat outweighs rewards spread across the other domains. Rank by threat severity and remove the worst first.
- **It is a heuristic, not a meter.** Caveat the science and treat severities as judgment, not measurements.
- **People differ.** The same change threatens different people in different domains; read for who, not just what.
