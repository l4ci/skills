---
name: mece-decomposition
description: Use when the user wants to break a problem, question, metric, or topic into a clean structure with no overlaps and no gaps, or build an issue tree / logic tree. Generates competing MECE decompositions in parallel, selects the sharpest cut, builds the tree, then audits it for mutual exclusivity and collective exhaustiveness with parallel checkers. Triggers include "MECE", "mutually exclusive collectively exhaustive", "issue tree", "logic tree", "break this down", "structure this problem", "decompose".
---

# mece-decomposition

Breaks a problem, question, metric, or topic into a MECE structure: branches that are Mutually Exclusive (no overlaps) and Collectively Exhaustive (no gaps). The output is a logic tree that can be divided into workstreams and solved without double-counting or blind spots.

The principle, the decomposition archetypes, and the ME and CE tests live in [references/mece.md](references/mece.md). Load that file before decomposing.

## When to use

The user wants structure: a problem to break down, a metric to decompose into drivers, a topic to map completely, or an issue tree to build. It pairs downstream of problem definition (define the problem, then decompose it) and upstream of solving (decompose, then work each branch). If the user only needs a quick informal list, this is heavier than necessary; reach for it when the breakdown must be rigorous.

## Language

Run the session and write the output in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **SUBJECT** (required): what to decompose. A problem statement, a question, a metric, or a topic.
- **PURPOSE** (optional): what the breakdown is for (diagnose a drop, divide work, map options, structure an analysis). The purpose often decides which cut is best, so ask if it is unclear.

## Orchestration map

```
Stage 1  Candidate Cuts   ── 3 decomposer subagents IN PARALLEL ──┐  (different top-level logics)
Stage 2  Select the cut   ── 1 agent, needs all 3 ───────────────┤  (pick or merge the sharpest)
Stage 3  Build the tree   ── 1 agent ────────────────────────────┤  (expand the chosen cut to depth)
Stage 4  MECE Audit       ── 2 checkers IN PARALLEL ── then refine ┘  (overlaps; gaps and consistency)
```

Tell each subagent its final message is the return value: structured data, not prose for a human.

## Stage 1: Candidate Cuts (PARALLEL)

The first cut decides everything, so generate several rather than committing to the first idea. Dispatch three decomposer subagents at once, each told to use a different archetype from the reference file (for example one algebraic or formula cut, one process or stages cut, one segment or component cut), whichever fit the subject.

**Shared framing (send to each decomposer):**

> Propose a top-level MECE breakdown of **[SUBJECT]** (purpose: [PURPOSE]) using the **[assigned archetype]** logic. Return:
> - The cutting logic in one line
> - The 2 to 5 top-level branches
> - A self-check: does any example item fit two branches (ME), and is anything left out (CE)
> - The strengths and weaknesses of this cut for the stated purpose

## Stage 2: Select the cut (SEQUENTIAL, needs all 3)

One agent compares the candidate cuts and picks the one that is cleanest (passes ME and CE most naturally) and most useful for the purpose, or merges the best top level from more than one. State why this cut was chosen over the others, since the choice of cut is the highest-leverage decision in the whole exercise.

## Stage 3: Build the tree (SEQUENTIAL)

Expand the chosen top-level cut into a logic tree, going only as deep as the purpose needs. At every node, split by a single logic and state it. Keep branches to two to five per node and roughly balanced. Do not drill one branch deep while siblings stay shallow.

## Stage 4: MECE Audit (PARALLEL, then refine)

Audit the built tree. Dispatch two checkers at once, each given the full tree.

- **Checker A, mutual exclusivity:** walk each level and find any overlap, testing concrete example items against the branches. Name the offending branches and the mixed logic causing the overlap.
- **Checker B, exhaustiveness and consistency:** find any gap (an item that fits no branch), any lazy "Other" hiding a real category, and any level that mixes cutting dimensions or abstraction levels.

Then refine the tree to resolve what the checkers found. Fix the cut at the level where the violation originates rather than patching leaves. Re-audit if the fix reshaped the tree.

## Report structure

Write the result as markdown and save it to `mece-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The subject, the purpose, and the date.
2. **The cut.** The top-level cutting logic chosen, and a one-line note on why it beat the alternatives considered.
3. **The tree.** The full MECE breakdown as a nested markdown list, with each node's cutting logic noted. This is the headline deliverable.
4. **MECE check.** A short statement, per level, that it passes ME and CE, with any "Other" branches justified.
5. **Alternatives considered.** The other candidate cuts and why they were not chosen, so the structure is defensible.
6. **How to use it.** How the branches map to workstreams, hypotheses, or analyses (the handoff to solving).
7. **Caveats.** MECE structures the problem; it does not solve it. A tree is only MECE relative to a stated scope, and a different purpose may call for a different cut. Real-world categories sometimes overlap slightly; note where ME is approximate rather than pretending otherwise.

## Principles

- **The first cut is everything.** Generate competing top-level logics before committing. A clean cut makes the tree fall out; a muddled one cannot be tidied into correctness.
- **One logic per level.** Mixing cutting dimensions at a level is the root of nearly every overlap. State the logic at each node.
- **Fix the cut, not the leaf.** When the audit finds an overlap or gap, repair the level where it originates.
- **Honest "Other".** A catch-all is allowed only when the remainder is genuinely small and varied, and it must be labeled, not used to hide a real category.
- **Only as deep as needed.** Stop when the branches are workable units. Premature depth on one branch is a common failure.
- **Parallel where independent.** Candidate cuts and the two audit checks share no state, so run them concurrently. Selection, building, and refinement depend on prior output, so they run in sequence.
