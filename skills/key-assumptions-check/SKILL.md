---
name: key-assumptions-check
description: Use when an analysis, plan, estimate, or forecast rests on things being taken for granted, and the user wants to find the load-bearing assumptions before one of them breaks. Runs the Key Assumptions Check (KAC), a core structured analytic technique: surfaces the full set of assumptions in parallel from several stances, restates each as an explicit testable proposition, stress-tests each one for confidence and the conditions under which it fails, classifies them as solid, caveated, or unsupported, and names the few linchpin assumptions that would collapse the conclusion if wrong. Triggers include "key assumptions check", "what are we assuming", "what is this resting on", "check our assumptions", "what if we're wrong about", "pressure-test this plan's premises".
---

# key-assumptions-check

A parallel implementation of the Key Assumptions Check (KAC), one of the foundational structured analytic techniques codified by Richards Heuer and Randolph Pherson in *Structured Analytic Techniques for Intelligence Analysis*. KAC exists to defeat a quiet failure mode: a confident conclusion is built on a foundation of assumptions the analyst never noticed making, and when one of them turns out to be wrong, the whole structure falls — and nobody saw it coming, because the assumption was never on the table to be questioned.

An assumption is anything taken to be true without current proof so the analysis can proceed. Some are stated; the dangerous ones are not. KAC drags every one into the open, tests it, and tells you which assumptions the answer actually depends on.

The skill runs six stages. Stage 1 (elicitation) and the testing in Stage 3, plus the adversarial check in Stage 5, fan out across parallel subagents. The stages in between are sequential because each builds on the assumption register the previous stage produced.

## When to use

The user has an analysis, plan, recommendation, forecast, or estimate and wants to know what it is silently resting on before committing to it. Triggers: "what are we assuming here", "check the assumptions", "what is this plan resting on", "what if we're wrong about X", "pressure-test the premises", "key assumptions check".

Reach for it whenever the cost of an unexamined assumption breaking is high: a strategy that assumes a competitor won't react, a forecast that assumes the past pattern holds, a project plan that assumes a dependency lands on time, a diagnosis that assumes the reported symptoms are complete. It is the natural partner to [analysis-of-competing-hypotheses](../analysis-of-competing-hypotheses/): ACH tests which *hypothesis* the evidence supports; KAC tests the *assumptions* both the analysis and the evidence rest on. It also pairs with [pre-mortem](../pre-mortem/) — KAC finds the fragile premises, the pre-mortem imagines them failing.

Do **not** use it as a substitute for gathering evidence (a KAC tells you which assumptions to go verify; it does not verify them for you), nor for choosing between options on value grounds (use a [weighted-decision-matrix](../weighted-decision-matrix/)).

## Inputs

- **SUBJECT** (required): the analysis, plan, claim, or forecast whose assumptions are to be checked. Paste the reasoning, the plan, or the conclusion with its main supporting argument. If only a conclusion is given, ask for the reasoning behind it — assumptions live in the reasoning, not the headline.
- **CONTEXT** (optional): the domain, the stakes, the decision the analysis feeds, and any constraints. Sharpens which assumptions are load-bearing.
- **ROLE** (optional): who relies on the analysis, so the report can pitch the "so what". Defaults to "a decision-maker about to act on this analysis."

## Orchestration map

```
Stage 1  Elicit assumptions     ── N proposer subagents IN PARALLEL ── then dedupe to a clean register
Stage 2  Articulate             ── 1 agent ── restate each as an explicit, testable proposition
Stage 3  Test each assumption   ── 1 subagent PER ASSUMPTION IN PARALLEL ── confidence, basis, failure conditions
Stage 4  Classify               ── 1 agent, needs all results ── solid / caveated / unsupported; build the matrix
Stage 5  Linchpins + gaps       ── 3 critic subagents IN PARALLEL ── what collapses the conclusion; what's missing
Stage 6  Report                 ── 1 agent ── register, classifications, linchpins, what to verify and monitor
```

Tell each subagent that its final message is the return value, meaning structured data rather than prose for a human. Subagents that test an assumption against the world should use whatever retrieval or search tools the runtime offers. If the runtime has no retrieval tools, the agent should reason from first principles and lower its confidence rather than invent facts.

---

## Stage 1: Elicit assumptions (PARALLEL)

The quality of a KAC is capped by how many assumptions it surfaces. An assumption that is never written down can never be tested, and the most dangerous ones are precisely the ones so taken for granted that nobody thinks to state them. The goal here is near-exhaustiveness, including the assumptions that feel too obvious to mention.

Dispatch three to five proposer subagents in parallel, each told to surface the assumptions in the SUBJECT from a different stance, so the set is not all of one kind:

- **The stated-premises read** — the assumptions written or spoken explicitly in the reasoning. Start here, then go past it.
- **The unstated-premises read** — what must be true for the argument to hold but was never said. Read each inferential leap and ask "what bridges this gap?".
- **The cultural / default read** — assumptions inherited from "how things are done here", from the organization's worldview, or from the field's conventional wisdom. These are the hardest to see from inside.
- **The continuity read** — assumptions that the future resembles the past, that a current trend holds, that a relationship that was true remains true. Time breaks these.
- **The actor read** — assumptions about what other people, competitors, markets, or systems will do, want, or know.

Each proposer returns a short list of candidate assumptions, each phrased as a single declarative claim ("the vendor will deliver the API by Q3", not "the vendor timeline").

Then **reconcile** the lists into a single clean register:

- Merge duplicates; split any item that bundles two assumptions into one line.
- Add an explicit residual prompt: "what else must be true that no one has questioned?" and capture anything it surfaces.
- Keep every candidate for now. Do **not** drop an assumption because it seems obviously safe — KAC's value often lies in the "obviously safe" assumption that turns out to be the linchpin.

Output: the numbered assumption register A1…An, each one declarative sentence.

## Stage 2: Articulate each assumption

Rewrite each assumption as an explicit, testable proposition. A vague assumption ("the market is stable") cannot be tested; a sharp one ("monthly churn stays below 3% through year-end") can. For each item:

- State it as a falsifiable claim with the relevant scope, quantity, and timeframe made explicit.
- Note whether it is currently stated or was unstated (unstated ones tend to be more dangerous precisely because they escaped scrutiny).
- Note what part of the analysis depends on it — which conclusion or step would change if it were false.

Output: the articulated register, each assumption now a sharp proposition with its dependency noted.

## Stage 3: Test each assumption (PARALLEL)

This is the core of the method. Dispatch **one subagent per assumption**, in parallel (batch several per agent if the register is long). Each agent is told to try to *break* its assumption, not defend it, and to answer Heuer and Pherson's diagnostic questions for its assumption Ak:

- **Confidence.** How much confidence is warranted that this is correct — high, medium, or low?
- **Basis.** What is that confidence actually based on — hard evidence, a track record, an analogy, or just habit and convenience? Name the source.
- **Failure conditions.** What circumstances or new information would make this assumption false? Be concrete: name the event, the threshold, the actor's choice.
- **Decay.** Could it have been true once but no longer? Assumptions rot; flag any that are running on a date-stamped fact.
- **Uncertainty test.** Is this really a key *uncertainty* dressed up as an assumption? If we don't actually know it and it matters, it belongs in the research-gap pile, not the foundation.
- **Impact if wrong.** If this assumption is false, how much of the analysis breaks — a footnote, a section, or the whole conclusion?

Each agent returns, for its assumption: a confidence rating, the basis, the concrete failure conditions, a decay flag, an uncertainty flag, and an impact rating. Scoring each assumption with an independent mind committed to breaking it is what stops the analyst's own attachment from quietly waving its premises through.

## Stage 4: Classify

Assemble the tested assumptions into one matrix and classify each by combining its confidence with its impact-if-wrong:

- **Solid** — well-supported, high confidence, and robust to plausible change. Safe to build on; note it and move on.
- **Caveated** — holds only under stated conditions, or has medium confidence. Keep it, but attach the condition explicitly so the analysis carries its own caveat.
- **Unsupported** — low confidence, thin basis, or really a key uncertainty in disguise. This is a finding: it must be verified, hedged, or the analysis re-examined without it.

The cell that matters most is **low confidence × high impact**: an assumption you are not sure of, that the whole conclusion depends on. Render the matrix as a table so it is auditable:

| Assumption | Confidence | Basis | If wrong → impact | Class |
|---|---|---|---|---|
| A1 — vendor delivers API by Q3 | low | vendor's verbal commitment only | launch slips a quarter (high) | unsupported |
| A2 — churn stays below 3% | medium | 4 quarters of history | revenue model off ~15% (high) | caveated |
| A3 — users have broadband | high | usage analytics (med) | minor (low) | solid |
| … | | | | |

## Stage 5: Linchpins and gaps (PARALLEL)

Not every weak assumption matters, and not every register is complete. Dispatch three critic subagents in parallel, each with a distinct attack on the Stage 4 result:

- **The linchpin critic** — identify the few assumptions the entire conclusion hangs on (typically the low-confidence × high-impact cells). For each, ask: if this one flips, does the analysis survive in modified form, or collapse outright? Name the load-bearing few loudly; a confident conclusion resting on one untested premise should be reported as exactly that.
- **The completeness critic** — attack the register itself. What assumption did every proposer miss? Look especially for the assumption so foundational it reads as fact — the definition everyone shares, the goal no one questioned, the constraint taken as a law of nature. A missing assumption is the most dangerous kind, because it was never even eligible for testing.
- **The reversal critic** — take the two or three most consequential assumptions and assume each is false. What would the analysis then conclude? If reversing a single assumption produces a materially different answer, that assumption is not a premise, it is the whole game.

Each critic returns its finding. Reconcile: confirm the linchpin set, fold any newly-surfaced assumptions back through Stage 3's test, and state how robust the conclusion is to its assumptions failing.

## Stage 6: Report

Write the briefing for the ROLE. Lead with what the analysis is resting on, then show the work.

1. **Bottom line.** How sound the foundation is overall, and the one or two assumptions that most threaten the conclusion if wrong.
2. **The assumption register.** The Stage 4 table, so every premise and its classification is auditable at a glance.
3. **Linchpins.** The few assumptions the conclusion depends on, what happens to the analysis if each is wrong, and how confident we are in each.
4. **Unsupported assumptions → action.** For each unsupported assumption, the concrete next step: the evidence that would confirm it, the hedge to add if it can't be confirmed, or the part of the analysis to rework without it.
5. **Caveats to carry.** The conditions attached to the caveated assumptions, restated so the analysis travels with its own fine print.
6. **Indicators to monitor.** Observable signals that an assumption is starting to break — the tripwires that should trigger a re-check. This converts a one-time audit into a live early-warning system.

---

## Principles

- **The dangerous assumption is the invisible one.** The premise stated and debated is rarely what sinks an analysis. The one taken so for granted that it reads as fact, never written down, never questioned — that is the one this method exists to catch. Spend the most effort surfacing what no one thought to say.
- **Test to break, not to bless.** Each assumption is examined by a mind trying to find the conditions under which it fails, not one looking for reasons it is fine. Confirmation is cheap and proves little.
- **Separate assumption from uncertainty.** If you genuinely don't know whether something is true and it matters, it is not an assumption you may rest on — it is a key uncertainty you must resolve or hedge. Misfiling uncertainties as assumptions is how analyses acquire hidden fault lines.
- **Confidence times impact is what ranks.** A shaky assumption that doesn't matter is noise; a shaky assumption the conclusion depends on is the finding. Always cross confidence with consequence.
- **Assumptions decay.** A premise true when it was first adopted may be false now. Flag every assumption running on a date-stamped fact and ask whether its expiry has passed.
- **A flagged assumption is a task, not a verdict.** The output of KAC is not "this is wrong" but "this is unverified and load-bearing — go check it, hedge it, or rebuild without it." Each unsupported assumption should leave with an action attached.
- **Name the linchpins out loud.** Always state how few assumptions the conclusion truly rests on. A confident answer hanging on one untested premise should be reported as a confident answer hanging on one untested premise.
