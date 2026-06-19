---
name: key-assumptions-check
description: 'Use when an analysis, plan, estimate, or forecast rests on things being taken for granted, and the user wants to find the load-bearing assumptions before one of them breaks. Runs the Key Assumptions Check (KAC), a core structured analytic technique: surfaces the full set of assumptions in parallel from several stances, restates each as an explicit testable proposition, stress-tests each one for confidence and the conditions under which it fails, classifies them as solid, caveated, or unsupported, and names the few linchpin assumptions that would collapse the conclusion if wrong. Triggers include "key assumptions check", "what are we assuming", "what is this resting on", "check our assumptions", "what if we''re wrong about", "pressure-test this plan''s premises".'
---

# key-assumptions-check

The Key Assumptions Check (KAC) is a core structured analytic technique from Richards Heuer and Randolph Pherson (*Structured Analytic Techniques for Intelligence Analysis*). It catches the failure where a conclusion rests on assumptions the analyst never noticed making, so when one breaks the whole structure falls. An assumption is anything taken as true, without current proof, to let the analysis proceed; the stated ones are rarely the problem, the unstated ones are. KAC surfaces every assumption, tests it, and reports which ones the answer depends on.

## When to use

The user has an analysis, plan, recommendation, forecast, or estimate and wants to know what it silently rests on before committing. Triggers: "what are we assuming", "check the assumptions", "what is this resting on", "what if we're wrong about X", "pressure-test the premises".

Reach for it when the cost of an unexamined assumption breaking is high: a strategy that assumes a competitor won't react, a forecast that assumes the past pattern holds, a plan that assumes a dependency lands on time. Pairs with [analysis-of-competing-hypotheses](../analysis-of-competing-hypotheses/) (ACH tests which hypothesis the evidence supports; KAC tests the assumptions both rest on) and [pre-mortem](../pre-mortem/) (KAC finds the fragile premises; the pre-mortem imagines them failing).

Do not use it to gather evidence (KAC says which assumptions to verify, it does not verify them) or to choose between options on value grounds (use [weighted-decision-matrix](../weighted-decision-matrix/)).

## Inputs

- **SUBJECT** (required): the analysis, plan, claim, or forecast to check. Paste the reasoning, or the conclusion with its main supporting argument. If only a conclusion is given, ask for the reasoning behind it; assumptions live in the reasoning, not the headline.
- **CONTEXT** (optional): domain, stakes, the decision it feeds, constraints. Sharpens which assumptions are load-bearing.
- **ROLE** (optional): who relies on the analysis. Defaults to "a decision-maker about to act on this analysis."

## Orchestration map

```
Stage 1  Elicit assumptions     ── N proposer subagents IN PARALLEL ── then dedupe to a clean register
Stage 2  Articulate             ── 1 agent ── restate each as an explicit, testable proposition
Stage 3  Test each assumption   ── 1 subagent PER ASSUMPTION IN PARALLEL ── confidence, basis, failure conditions
Stage 4  Classify               ── 1 agent, needs all results ── solid / caveated / unsupported; build the matrix
Stage 5  Linchpins + gaps       ── 3 critic subagents IN PARALLEL ── what collapses the conclusion; what's missing
Stage 6  Report                 ── 1 agent ── register, classifications, linchpins, what to verify and monitor
```

Each subagent's final message is its return value: structured data, not prose for a human. Subagents testing an assumption against the world use whatever retrieval the runtime offers; with no retrieval, reason from first principles and lower confidence rather than invent facts.

---

## Stage 1: Elicit assumptions (PARALLEL)

Aim for near-exhaustiveness, including the assumptions too obvious to state; one never written down can never be tested. Dispatch three to five proposers in parallel, each surfacing assumptions in the SUBJECT from one stance:

- **Stated premises:** assumptions explicit in the reasoning. Start here, then go past it.
- **Unstated premises:** what must be true for the argument to hold but was never said. Check each inferential leap.
- **Cultural / default:** assumptions inherited from "how things are done here" or the field's conventional wisdom. Hardest to see from inside.
- **Continuity:** that the future resembles the past, a current trend holds, a relationship that was true still holds.
- **Actor:** what other people, competitors, markets, or systems will do, want, or know.

Each proposer returns candidate assumptions, each a single declarative claim ("the vendor will deliver the API by Q3", not "the vendor timeline").

Reconcile into one register: merge duplicates, split any item bundling two assumptions, add a residual prompt ("what else must be true that no one has questioned?"), and keep every candidate. KAC's value often lies in the "obviously safe" assumption that turns out to be the linchpin. Output: the numbered register A1…An.

## Stage 2: Articulate

Rewrite each assumption as a falsifiable proposition. "The market is stable" cannot be tested; "monthly churn stays below 3% through year-end" can. For each:

- State it with scope, quantity, and timeframe explicit.
- Note whether it was stated or unstated (unstated ones tend to be more dangerous).
- Note what part of the analysis depends on it.

Output: the articulated register with each dependency noted.

## Stage 3: Test each assumption (PARALLEL)

Dispatch one subagent per assumption (batch several per agent if the register is long), each told to break its assumption, not defend it, answering for assumption Ak:

- **Confidence:** high, medium, or low that it is correct?
- **Basis:** what the confidence rests on: hard evidence, track record, analogy, or habit. Name the source.
- **Failure conditions:** what would make it false. Be concrete: the event, threshold, or actor's choice.
- **Decay:** could it have been true once but no longer? Flag any running on a date-stamped fact.
- **Uncertainty test:** is this really a key uncertainty in disguise? If we don't know it and it matters, it belongs in the research-gap pile, not the foundation.
- **Impact if wrong:** does a footnote, a section, or the whole conclusion break?

Each agent returns confidence, basis, failure conditions, decay flag, uncertainty flag, and impact for its assumption.

## Stage 4: Classify

Classify each assumption by confidence against impact-if-wrong:

- **Solid:** high confidence, robust to plausible change. Safe to build on.
- **Caveated:** holds only under stated conditions, or medium confidence. Keep it with the condition attached.
- **Unsupported:** low confidence, thin basis, or a key uncertainty in disguise. A finding: verify it, hedge it, or re-examine the analysis without it.

The cell that matters most is low confidence and high impact. Render the matrix as an auditable table:

| Assumption | Confidence | Basis | If wrong, impact | Class |
|---|---|---|---|---|
| A1: vendor delivers API by Q3 | low | vendor's verbal commitment only | launch slips a quarter (high) | unsupported |
| A2: churn stays below 3% | medium | 4 quarters of history | revenue model off ~15% (high) | caveated |
| A3: users have broadband | high | usage analytics (med) | minor (low) | solid |
| … | | | | |

## Stage 5: Linchpins and gaps (PARALLEL)

Dispatch three critics in parallel against the Stage 4 result:

- **Linchpin critic:** find the few assumptions the conclusion hangs on (usually the low-confidence, high-impact cells). For each: if it flips, does the analysis survive in modified form, or collapse? Name the load-bearing few.
- **Completeness critic:** attack the register. What did every proposer miss, especially an assumption so foundational it reads as fact (the shared definition, the unquestioned goal, the constraint taken as a law of nature)? A missing assumption is the most dangerous kind, since it was never eligible for testing.
- **Reversal critic:** assume the two or three most consequential assumptions are false. If reversing one produces a materially different answer, it is not a premise, it is the whole game.

Reconcile: confirm the linchpin set, fold any newly surfaced assumptions back through Stage 3's test, and state how robust the conclusion is to its assumptions failing.

## Stage 6: Report

Write the briefing for the ROLE. Lead with what the analysis rests on, then show the work.

1. **Bottom line.** How sound the foundation is overall, and the one or two assumptions that most threaten the conclusion if wrong.
2. **Assumption register.** The Stage 4 table.
3. **Linchpins.** The assumptions the conclusion depends on, what happens to the analysis if each is wrong, and confidence in each.
4. **Unsupported assumptions, with action.** For each, the next step: the evidence that would confirm it, the hedge to add if it can't be confirmed, or the rework needed without it.
5. **Caveats to carry.** The conditions on the caveated assumptions, restated so the analysis travels with its own fine print.
6. **Indicators to monitor.** Signals that an assumption is starting to break, as tripwires for a re-check.

---

## Principles

- **The dangerous assumption is the invisible one.** Spend the most effort surfacing what reads as fact and was never stated.
- **Rank by confidence against impact.** A shaky assumption only matters when the conclusion depends on it.
- **A flagged assumption is a task, not a verdict:** verify it, hedge it, or rebuild without it.
