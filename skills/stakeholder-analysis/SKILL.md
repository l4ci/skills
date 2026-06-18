---
name: stakeholder-analysis
description: Use when the user wants a stakeholder analysis or stakeholder map of a project, change, or decision, or asks who they need on board and how to engage them. Identifies the stakeholders, then fans out one analyst subagent per stakeholder in parallel to assess power, interest, current stance, interests and fears, and how to engage them, then synthesizes a power-interest grid, a per-quadrant engagement plan, the supporter coalition, the set of blockers, and the highest-leverage relationships to shift, in a detailed markdown report. Triggers include "stakeholder analysis", "stakeholder mapping", "power-interest grid", "power/interest matrix", "Mendelow", "stakeholder management", "who do we need on board".
---

# stakeholder-analysis

Runs a stakeholder analysis on the power-interest grid (Mendelow, 1991) to map the people and groups who affect or are affected by an initiative, and to decide where engagement effort should go. Each stakeholder is placed by two axes (their power over the outcome and their interest in it) and read for stance, interests, fears, and influence over others. The output is an engagement plan, not just a map.

The two axes, the four quadrants and their engagement strategies, the stance and influence-network dimensions, and the pitfalls live in [references/stakeholders.md](references/stakeholders.md). Load that file before analyzing and follow the power-versus-interest and check-don't-assume rules exactly.

## When to use

The user is launching or steering a project, change, decision, or rollout and needs to know who matters, where they stand, and how to bring them along: who to involve, who to keep satisfied, who could block it, and who to win over. It feeds change-management work and the adoption-risk lens of a [pre-mortem](../pre-mortem/) (a key player turned blocker is a classic way initiatives fail); run it before or alongside those when the risk is people rather than technical execution.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework, axes, and quadrants keyed to it regardless of the output language.

## Inputs

- **INITIATIVE** (required): the project, change, or decision whose stakeholders are being mapped. Push for a defined thing with a defined outcome, since "the reorg" is easier to map than "our strategy".
- **CONTEXT** (optional): the phase the initiative is in, what success actually requires, and any known tensions or factions. This sharpens both the stakeholder list and the engagement plan.

## Orchestration map

```
Stage 1  Identify         ── with the user, surface the stakeholder list ──┐
         Per-stakeholder   ── N analyst subagents IN PARALLEL ─────────────┤  (one per stakeholder: power, interest, stance, interests, engagement)
Stage 2  Synthesis         ── 1 agent, needs all N ──────────────────────────┘  (grid, engagement plan, coalition, blockers, leverage)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval and context tools to ground their reading in real evidence.

## Stage 1: Identify, then per-stakeholder analysis (PARALLEL)

First build the stakeholder list with the user. Surface candidates across the categories that tend to be forgotten: who holds formal authority or budget, who supplies resources or does the work, whose work the initiative changes, who it affects downstream, and the external parties (customers, regulators, partners). Decide the grain deliberately: some stakeholders are individuals, some are groups that move as one, and "the leadership team" sometimes hides a supporter and a blocker who must be split apart. Confirm the list with the user before fanning out.

Then dispatch one analyst subagent per stakeholder (or stakeholder group) at once. Give each the shared framing for its assigned stakeholder.

**Shared framing (send to every analyst):**

> Analyze one stakeholder for this initiative: **[INITIATIVE]**. Your stakeholder is **[STAKEHOLDER]**. Assess them on their own evidence (what they have said, done, and stand to gain or lose), not on assumption or job title. Return:
> - **Power** (1 to 5): their ability to influence the outcome, anchored to a concrete lever (decision authority, budget, control of resources or people, a veto). A senior name with no lever over *this* initiative is not high-power.
> - **Interest** (1 to 5): how much they care about or are affected by the outcome. This measures intensity of attention, positive or negative, not which side they are on.
> - **Stance**: supporter, neutral, blocker, or unknown, with the evidence. Mark unknown rather than guessing.
> - **Interests and fears**: what they actually want (their underlying interest, not just their stated position) and what they fear or stand to lose.
> - **Influence**: who they sway and who sways them, including informal influence the org chart does not show.
> - **How to engage**: the lever that would move or hold this stakeholder, given their stance and concerns.
> - **Confidence** (high, medium, low), lowered when the reading rests on assumption rather than evidence.
>
> Context: [CONTEXT]

Collect all the structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: Synthesis (SEQUENTIAL, needs all N)

One agent merges the per-stakeholder readings into the map and the plan:

1. **Place everyone on the power-interest grid.** Plot each stakeholder by power and interest into one of the four quadrants (manage closely, keep satisfied, keep informed, monitor). Note any stakeholder sitting near a boundary, since small shifts move them across.
2. **Build the engagement plan per quadrant.** For each quadrant, the strategy from the reference file, made concrete for these stakeholders: who to involve and co-create with (manage closely), who to keep comfortable without overloading and what could spike their interest (keep satisfied), who to communicate with and recruit as advocates (keep informed), and who to leave to general channels (monitor).
3. **Map the coalition and the blockers.** Name the set of supporters and the set of blockers, overlaid on the grid (a high-power blocker is the priority; a low-power blocker is noise). For each blocker, what they want and the influence path to reach them. For the coalition, which supporters carry weight with stakeholders you cannot reach directly.
4. **Flag the highest-leverage relationships to shift.** Working the gradients from the reference file (blockers toward neutral, neutrals toward support, supporters held and used), name the few moves that change the most: a high-power blocker, an influencer who controls a bloc of neutrals, a key player whose stance is still unknown. Effort follows leverage, not headcount.
5. **Verdict.** A short read on whether the stakeholder field favors the initiative as it stands, where the field is fragile, and what the analysis means for the engagement effort ahead.

## Report structure

Write a thorough markdown report and save it to `stakeholder-analysis-<initiative-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The initiative analyzed, its phase and what success requires if given, the date, and a one-line note on the framework and its snapshot nature.
2. **Verdict.** Whether the stakeholder field favors the initiative in a few sentences, with a summary table: each stakeholder, their power and interest scores, quadrant, and stance.
3. **The power-interest grid.** The 2-by-2 grid as a table (or a scannable plot), each stakeholder placed in their quadrant so the picture reads at a glance.
4. **Per-stakeholder detail.** For each: power and interest with the levers behind them, stance and the evidence, what they want and fear, who they influence, and the engagement lever. Lead with the key players.
5. **Engagement plan.** Organized by quadrant, the concrete strategy for each stakeholder, including what could move a satisfied stakeholder's interest up and which informed stakeholders to recruit as advocates.
6. **Coalition and blockers.** The supporter coalition and the set of blockers overlaid on the grid, with the influence path to each blocker and the supporters who carry weight where you cannot reach directly.
7. **Highest-leverage moves.** The few relationships to shift that change the most, sequenced by leverage, each with the gradient it works (blocker to neutral, neutral to support, hold and deepen).
8. **Caveats.** The grid is a snapshot, not a fixture: power, interest, and stance all move as the initiative progresses, so re-run it at milestones; scores are informed judgment, not measurement; and stances read from thin evidence should be marked low-confidence and checked, not trusted.

## Principles

- **Power is not interest.** They are independent axes, and keeping them apart is the whole point. A loud stakeholder with no lever is not powerful; a quiet sponsor who controls the budget is. Conflating them puts effort in the wrong quadrant.
- **Check stance, don't assume it.** Read where each stakeholder stands from what they have said and done. "They're senior, so they're on board" and "they complained once, so they're a blocker" are both guesses; mark unknowns as unknown.
- **The map is a snapshot.** Positions move with every decision and announcement. The analysis is dated the moment it is written, so it is a basis for engagement and re-checking, not a fixed record.
- **Follow the informal influence.** The org chart is not the influence network. The highest-leverage move is often engaging the person who sways a stakeholder, not the stakeholder.
- **Effort follows leverage.** Most engagement goes to the key players; the monitor quadrant gets minimal effort. Spreading attention evenly across everyone is the failure the grid exists to prevent.
- **Parallel where independent.** Each stakeholder is read on its own, so analyze them concurrently. The grid, the plan, and the influence map need all of them, so synthesis runs after.
