---
name: force-field-analysis
description: Use when the user wants a force field analysis of a proposed change, decision, or goal, or asks what is driving and what is holding a change back, or whether a change is feasible as things stand. Fans out finder subagents in parallel that hunt the driving forces and the restraining forces across people, organizational, technical, and external lenses and score each by strength, then synthesizes the scored force field, the net read, and the highest-leverage moves (favouring the weakening of restrainers) into a detailed markdown report. Triggers include "force field analysis", "Lewin", "driving and restraining forces", "what's holding this change back", "forces for and against", "change readiness".
---

# force-field-analysis

Runs Kurt Lewin's force field analysis to assess a proposed change. Any current situation is an equilibrium held in place by two opposing sets of forces: driving forces that push toward the change, and restraining forces that resist it and hold the status quo. The status quo is the balance point. To move toward the desired state you strengthen the drivers, weaken the restrainers, or both, and Lewin's point is that weakening restrainers usually beats adding drivers.

The equilibrium model, the driving and restraining forces with the lenses to hunt across, the 1-to-5 strength scale, the net-field read, and the principle that weakening restrainers beats adding drivers live in [references/force-field.md](references/force-field.md). Load that file before analyzing and score each force against the scale exactly.

## When to use

The user has a defined change, decision, or goal and wants to know what is pushing for it, what is holding it back, whether it is feasible as things stand, and where the leverage is. This is the lightweight analytical change tool: it diagnoses the field around a single change quickly and points to the moves. For leading a full organizational change through to completion use [kotter-change](../kotter-change/); for the individual people-and-adoption side of a change use [adkar](../adkar/). The unit of analysis is the change, not the organization as a whole.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework, the lenses, and the scoring keyed to it regardless of the output language.

## Inputs

- **CHANGE** (required): the change, decision, or goal being assessed. Push for a precise desired state, since forces can only be judged for or against a target sharp enough to be for or against. "Be more agile" cannot be scored; "move the support team to a four-day week by Q3" can. If the user is vague, sharpen it with one or two questions first.
- **CONTEXT** (optional): the current situation, who is involved, the constraints, the time horizon, and the decision the analysis should inform. This shapes which forces are in play and the leverage moves, not the scoring scale.

## Orchestration map

```
Stage 1  Force Hunt   ── finder subagents IN PARALLEL ──┐  (some hunt drivers, some hunt restrainers, by lens; each scores)
Stage 2  Synthesis    ── 1 agent, needs all finders ────┘  (scored field, net read, leverage moves)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground scores in real evidence where the change involves figures, stated positions, or deadlines.

## Stage 1: Force Hunt (PARALLEL)

Dispatch the finder subagents at once. Split the hunt by side and lens: assign some finders to driving forces and some to restraining forces, each covering one lens (people, organizational, technical, external) from the reference file. For a small change a finder may cover both sides of one lens; for a larger one give each side of each lens its own finder. Either way, the driving hunt and the restraining hunt must get equal effort so the field is not lopsided.

**Shared framing (send to every finder):**

> Hunt the **[driving | restraining]** forces around this change through the **[lens]** lens: **[CHANGE]**. Driving forces push toward the change; restraining forces resist it and hold the status quo. Surface every force you can find through your lens, then for each one return:
> - **Force**: a one-line statement of what it is and which way it pushes
> - **Strength score** (1 to 5) with a one-line rationale, grounded in evidence (a figure, a stated stakeholder position, a deadline, a known constraint) where you can find it
> - **Confidence**: high, medium, or low, lowered where evidence was thin
>
> Do not soften or pad your side to balance the other; surface what is really there at its real strength. Context: [CONTEXT]

Collect all finders' structured results before continuing. Re-dispatch any finder that fails rather than synthesizing with a gap, and check that neither side came back thin: a long driver list against two restrainers usually means the restrainer hunt was lazy, not that the change is easy.

## Stage 2: Synthesis (SEQUENTIAL, needs all finders)

One agent merges the finders into the force field and the moves:

1. **Build the scored field.** Deduplicate forces that several finders surfaced (keep the best-evidenced score), then lay out the two columns: driving forces with strengths, restraining forces with strengths.
2. **Read the net field.** Weigh the two columns and read the gap, but do not treat it as arithmetic. Name the binding restrainers and the load-bearing drivers. Answer the question: as the field stands today, will the situation move, hold, or need active intervention before it can move?
3. **Find the leverage.** Identify the highest-leverage moves. Favour weakening the strongest restrainers ("what would make this barrier smaller or go away?") over adding driving force, since adding drivers tends to provoke equal counter-pressure and produces fragile change (see the reference file). Strengthening weak or absent drivers that cost little to add is the second tool, not the first.
4. **Judge the shift.** Can the equilibrium realistically be moved with the available moves, and how, weighing feasibility? If not, say so plainly rather than padding the driver column to manufacture a feasible-looking field.

## Report structure

Write a thorough markdown report and save it to `force-field-<change-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The change analyzed, the context if given, the date, and a one-line note on the framework and the fact that the field shifts as the change proceeds.
2. **Verdict.** Whether the change is feasible as the field stands, in a few sentences, with the net read and the binding forces named.
3. **The scored force field.** A two-column layout, driving forces on one side and restraining forces on the other, each force with its 1-to-5 strength, so the balance is scannable. Show the column totals and the gap, with the caveat that the read is not the arithmetic.

   ```
   DRIVING (toward the change)        →  ←  RESTRAINING (holding the status quo)
   Force A ............... 4           |     Force X ............... 5
   Force B ............... 3           |     Force Y ............... 3
   Force C ............... 2           |     Force Z ............... 2
   ----                               |     ----
   total 9                            |     total 10
   ```
4. **The forces.** Each force with its strength, which way it pushes, the lens it came from, and the rationale or evidence. Grouped by side.
5. **Net field.** The binding restrainers, the load-bearing drivers, and what the balance means for whether the change will move.
6. **Leverage and moves.** The highest-leverage interventions, leading with restrainers to weaken and the drivers to strengthen second, each tied to the context and weighed for feasibility, and the judgment on whether the equilibrium can be shifted.
7. **Caveats.** The field is a starting read, not a fixed verdict; it shifts as the change proceeds and acting on it changes it; scores are informed judgment, not measurement; and a change blocked by one binding restrainer is blocked regardless of how the totals look.

## Principles

- **Define the change first.** Forces can only be judged against a target state sharp enough to be for or against. Sharpen a vague change before listing forces.
- **Both sides, equal effort.** Hunt drivers and restrainers across every lens with the same rigour. A lopsided list is a lazy hunt, not an easy change.
- **Score, do not just list.** Every force carries a 1-to-5 strength with a rationale. A bare list cannot be read as a field.
- **Weaken restrainers before adding drivers.** Removing barriers lowers tension and produces durable change; adding pressure provokes counter-pressure and produces fragile change. The leverage is usually on the restraining side.
- **Not an average.** The net read weighs the field, it does not mean it. One binding restrainer can block a change the totals call feasible.
- **Parallel where independent.** The driver hunt and the restrainer hunt share no state, so run them concurrently across lenses. Synthesis needs them all, so it runs after.
