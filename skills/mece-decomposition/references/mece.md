# MECE: decomposition principles, archetypes, and tests

MECE (Mutually Exclusive, Collectively Exhaustive) is the test of a good breakdown. A set of categories is MECE when:

- **Mutually Exclusive (ME):** no item fits in more than one category. The branches do not overlap.
- **Collectively Exhaustive (CE):** every item fits in some category. The branches leave no gap.

The principle comes from structured problem solving (McKinsey; Barbara Minto's *Pyramid Principle*). It is how a vague problem becomes a logic tree (also called an issue tree) that can be divided, delegated, and solved without double-counting or blind spots.

The single most important decision is the **first cut**: the logic used to split the top level. A clean cut makes the whole tree fall out naturally; a muddled cut produces overlaps and gaps no amount of tidying will fix.

---

## Decomposition archetypes (ways to cut)

Most good breakdowns use one of these logics at each level. Pick the one that fits the problem, and use exactly one logic per level.

1. **Algebraic (formula-based).** Break a quantity into its mathematical drivers. Profit = Revenue minus Cost; Revenue = Units times Price. MECE by construction, and the strongest cut when the target is a number.
2. **Process or stages.** Split along the steps of a sequence or funnel: awareness, consideration, purchase, retention. MECE when the stages are distinct and the sequence is complete.
3. **Components or structure.** Split a whole into its parts: business units, product lines, cost categories, system modules.
4. **Segments.** Split a population by a defining attribute: customer segments, channels, geographies.
5. **Binary (A versus not-A).** Split on a yes/no attribute: internal versus external, new versus existing customers. MECE by logic, useful when other cuts risk gaps.
6. **Hypothesis-driven.** Structure the tree around candidate answers or drivers, used when the goal is to test which explanation holds.

A formula or binary cut is MECE automatically. The others require checking.

---

## The tests

Apply these to every node, level by level.

### Mutually Exclusive
Take a concrete example item and ask: does it land in exactly one branch? If any item fits two branches, the categories overlap. Overlaps usually mean two cutting logics were mixed at one level (for example splitting partly by geography and partly by product). Fix the cut, do not patch the symptom.

### Collectively Exhaustive
Ask: is there any item that fits in no branch? If yes, there is a gap. Close it by adding the missing branch, or, only when the remainder is genuinely small and varied, by a clearly labeled "Other" branch. An "Other" that hides a real, large category is a failure, not a fix.

### Same level, same logic
Every branch at a given level must use the same cutting dimension and sit at the same level of abstraction. Mixing "by region" and "by product" at one level breaks ME. Mixing a broad category with a narrow one breaks the tree's readability.

### Right breadth
A node usually splits into two to five branches. One branch is not a split. More than about seven is a sign the level is too granular or the cut is wrong; group first, then go deeper.

---

## Common violations

- **Overlap:** categories that share members (the classic ME failure), almost always from mixing cutting logics.
- **Gap:** a real category left out (the classic CE failure).
- **Lazy "Other":** a catch-all standing in for a category that should be named.
- **Mixed levels:** different cutting dimensions or abstraction levels at the same level.
- **Premature depth:** drilling one branch four levels deep while siblings stay shallow, before the top-level cut is sound.
- **Solution-shaped branches:** decomposing by preferred answers rather than by a clean logic, which biases what gets found.

---

## What good looks like

A finished MECE tree:

- Splits each node by one clear logic, stated at that node.
- Passes the ME and CE tests at every level.
- Goes only as deep as the problem needs, with branches roughly balanced.
- Names its "Other" branches honestly and keeps them small.
- Can be read top to bottom as a complete, non-overlapping map of the problem, ready to be divided into workstreams.
