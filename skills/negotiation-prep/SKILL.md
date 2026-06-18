---
name: negotiation-prep
description: Use when the user is preparing for a negotiation (salary, deal, partnership, vendor, dispute settlement) and wants to go in ready rather than improvising. Fans out five parallel analyst subagents over the structure of principled, interest-based negotiation (Fisher and Ury, plus BATNA and ZOPA): your interests, their likely interests, your BATNA and walk-away, their likely BATNA and walk-away, and options for mutual gain with the objective criteria to invoke. Each marks every claim as fact or assumption with a confidence. A synthesis pass maps the zone of possible agreement, sets your target and walk-away, sequences the moves, and names the assumptions worth testing, into a detailed markdown report. Triggers include "prepare for a negotiation", "negotiation prep", "BATNA", "getting to yes", "salary negotiation", "how should I negotiate".
---

# negotiation-prep

Prepares for a negotiation using Fisher and Ury's principled (interest-based) method, anchored on BATNA and ZOPA. The point is not to script clever lines or steel yourself to hold a number; it is to walk in already knowing both sides' interests, both sides' best alternatives, where the zone of possible agreement lies, and which objective standards decide each issue. You negotiate over interests, not positions, and your real strength is your BATNA, not your stubbornness.

The four principles, positions versus interests, BATNA, reservation point and ZOPA, and the tactics live in [references/negotiation.md](references/negotiation.md). Load that file before preparing and key every stage to it.

## When to use

The user is preparing for a specific negotiation and wants the groundwork done: a salary or offer, a sales or purchase deal, a partnership, a vendor contract, a dispute settlement. The unit of work is one negotiation with identifiable parties, not a relationship in general. Use thomas-kilmann to choose a conflict mode (compete, collaborate, compromise, accommodate, avoid); use stakeholder-analysis to map who holds power across a wider field; use weighted-decision-matrix to score the offers once they are on the table. This skill prepares the room before you enter it.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **NEGOTIATION** (required): what is being negotiated and with whom. Push for one defined negotiation with identifiable parties. If it is vague, narrow it with one or two questions first.
- **GOAL** (optional): what a good outcome looks like for the user, the stakes, and the deadline. This shapes the target and the synthesis, not the analysis of interests.
- **CONTEXT** (optional): the relationship and its future, prior dealings, known constraints on either side, and any numbers already on the table. This grounds the BATNA and ZOPA estimates.

## Orchestration map

```
Stage 1  Define          ── inline ───────────────────────────┐  (parties, the deal, what is known)
Stage 2  Analysis        ── 5 analyst subagents IN PARALLEL ───┤  (interests, both BATNAs, options + criteria)
Stage 3  Synthesis       ── 1 agent, needs all 5 ──────────────┘  (ZOPA, target/walk-away, move sequence)
```

## Stage 1: Define the negotiation (inline)

Before dispatching anyone, fix the frame. Name the parties and who actually decides on each side. State what is being negotiated and the one or few issues at its core. Record what is already known: numbers on the table, deadlines, the relationship and whether it continues, prior dealings, and stated constraints. Note the GOAL and what a walk would mean for the user. This frame goes to every analyst so they work the same negotiation.

## Stage 2: Analysis (PARALLEL)

Dispatch five analyst subagents at once, one per assignment below. Give each the shared framing plus its assignment and the relevant section of the reference file.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their analysis in real evidence (market rates, comparable deals, public terms, precedent).

**Shared framing (send to each analyst):**

> You are preparing one party for this negotiation: **[NEGOTIATION]**. Parties and what is known: [Stage 1 frame]. Goal: [GOAL]. Context: [CONTEXT]. Work your assignment using principled, interest-based negotiation. For every material claim, mark it as a **fact** (evidence exists) or an **assumption** (a hypothesis still to be tested), and never present a hope as a fact. Then return:
> - **Findings**: the substance of your assignment, itemized, each with its supporting evidence
> - **Facts vs assumptions**: which claims are grounded and which are hypotheses
> - **What would change this**: the information that, if found, would most move your conclusions
> - **Confidence**: high, medium, or low, lowered if evidence was thin or you relied on assumptions

Assign the five:

1. **Your interests and priorities.** The needs and fears behind the user's position; rank them, and separate must-haves from nice-to-haves and from what is tradeable.
2. **Their likely interests and constraints.** The needs, fears, and pressures behind the other side's position; who on their side decides and what they answer to. Probe why and why-not, not just what they will demand.
3. **Your BATNA and reservation point.** The user's real best alternative if no deal happens, how to strengthen it before the table, and the walk-away point it implies.
4. **Their likely BATNA and reservation point.** The other side's best alternative if no deal happens, how strong it is, and the walk-away point it implies. The weaker their alternative, the more they need this deal.
5. **Options for mutual gain plus objective criteria.** Ways to expand the deal by trading on differing priorities, and the independent standards (market value, precedent, expert opinion, cost, law, fair procedure) to invoke for each contested issue.

Collect all five structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five analyses into a plan for the room:

1. **Map the ZOPA.** From both reservation points, determine whether a zone of possible agreement exists and where. If the user's walk-away and theirs do not overlap, say so plainly: no deal is the right outcome, or an alternative must change first. Do not paper over an empty ZOPA with optimism.
2. **Set target and walk-away.** An ambitious-but-justifiable target backed by objective criteria, and a firm walk-away derived from the BATNA, not a comfort number. Keep the two distinct from the ZOPA.
3. **Sequence the moves.** The opening anchor and the standard that justifies it; the planned concessions, shrinking and slowing, each traded for something worth more; and the objective criteria to invoke on each issue.
4. **Prepare for their tactics.** The hardball moves the other side is likely to use given their interests and BATNA, and the principled response to each (name the game, return to criteria, fall back on the BATNA).
5. **Name the assumptions worth testing.** The one or two assumptions whose being wrong would most change the plan, and how to test them before or at the table.

## Report structure

Write a thorough markdown report and save it to `negotiation-prep-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The negotiation, the parties, the goal and deadline if given, the date, and a one-line note on the framework and that preparation reduces but does not remove uncertainty about the other side.
2. **Verdict.** Whether a deal looks reachable and on what terms, in a few sentences, with the ZOPA, the target, and the walk-away stated up front.
3. **Interests.** The user's ranked interests and the other side's likely interests, positions distinguished from the interests beneath them, fact versus assumption marked.
4. **Alternatives and the ZOPA.** Both BATNAs and reservation points, how to strengthen the user's, and the resulting zone of possible agreement (or its absence) with the numbers shown.
5. **The plan.** Target and walk-away, the move sequence (anchor, concessions, criteria to invoke), and prepared responses to their likely tactics.
6. **Assumptions to test.** Ranked, with how to test each before or at the table.
7. **Caveats.** The other side's interests and BATNA are estimated, not known, and the plan is only as good as those estimates; a mapped ZOPA describes room for a deal, not a guarantee of one; people do not always negotiate rationally; and preparation informs the room but does not survive contact unchanged.

## Principles

- **Interests, not positions.** Trade on why each side wants what it wants. Haggling over numbers with no grasp of interests leaves joint gains on the table and strains the relationship.
- **Your BATNA is your power.** Strength comes from a strong, well-understood alternative, not from holding a number. Define it, improve it before the table, and estimate theirs.
- **Find the real ZOPA.** Derive both reservation points and check whether they actually overlap. Never mistake the outcome you want for the outcome their numbers allow; an empty ZOPA means no deal is the right answer.
- **Decide by objective criteria.** Where interests collide, settle by an independent standard, not by will or pressure. Yield to principle, never to a tactic.
- **Facts or honesty.** Mark every material claim as fact or assumption. Where data is missing, say so and lower confidence rather than inventing the other side's numbers.
- **Parallel where independent.** The five analyses can run concurrently. Mapping the ZOPA and sequencing the moves need all five, so synthesis runs after.
