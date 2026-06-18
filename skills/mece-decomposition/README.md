# mece-decomposition

Breaks a problem, question, metric, or topic into a clean structure: branches that are Mutually Exclusive (no overlaps) and Collectively Exhaustive (no gaps). The result is a logic tree (issue tree) that can be split into workstreams and solved without double-counting or blind spots. MECE comes from structured problem solving (McKinsey; Barbara Minto's Pyramid Principle).

The hardest part of any breakdown is the first cut, so this skill does not commit to the first idea. Three decomposer subagents propose competing top-level cuts in parallel, each using a different logic (algebraic, process, segment, and so on). A selection pass picks or merges the sharpest, the tree is built to the depth the purpose needs, and then two checkers audit it in parallel: one hunts overlaps, the other hunts gaps and inconsistent levels. The tree is refined at the level where each violation originates, not patched at the leaves. The output is a saved markdown logic tree with its MECE check and the alternatives considered.

This skill structures the problem; it does not solve it. It pairs downstream of [tosca-problem-definition](../tosca-problem-definition/) and upstream of analysis or solving work.

The procedure is in [SKILL.md](SKILL.md); the principles, decomposition archetypes, and ME and CE tests are in [references/mece.md](references/mece.md).
