---
name: analysis-of-competing-hypotheses
description: Use when the user must decide which of several explanations is true and wants to avoid latching onto the first plausible story. Runs Heuer's Analysis of Competing Hypotheses (ACH): lays out all plausible hypotheses at once, scores every piece of evidence against each one in parallel by working to disprove rather than confirm, then ranks hypotheses by fewest inconsistencies, stress-tests the linchpin evidence for fragility and deception, and reports relative likelihoods with the indicators that would change the answer. Triggers include "ACH", "competing hypotheses", "which explanation is most likely", "what's really going on here", "rule out the alternatives".
---

# analysis-of-competing-hypotheses

A parallel implementation of Analysis of Competing Hypotheses (ACH), the structured analytic technique developed by Richards Heuer at the CIA and laid out in *Psychology of Intelligence Analysis* (1999). ACH defeats one failure: the mind picks a favored explanation early, then reads every new fact as confirmation. It forces all hypotheses to compete on the same evidence at once and ranks them by **disconfirmation**, the most likely being the one with the *least evidence against it*, not the most evidence for it.

## When to use

The user faces a question with several rival explanations and wants a disciplined adjudication rather than a hunch. Triggers: "which of these is actually true", "what's the most likely explanation", "help me rule out alternatives", "ACH", "competing hypotheses", "is this X or Y or Z". It pairs well with [storm-research](../storm-research/): STORM gathers the evidence and the perspectives; ACH decides which story that evidence actually supports.

Reach for it when the cost of anchoring on the wrong explanation is high: incident root-cause, diagnosis, intelligence-style "what is the other side doing", attributing a trend to a cause, or any "we think it's X" claim that deserves to be tested against the alternatives.

Do **not** use it for problems with a single obvious answer, for value choices (ACH adjudicates what is *true*, not what is *preferable* — use a [weighted-decision-matrix](../weighted-decision-matrix/) for that), or for forecasting a number (use [scenario-planning](../scenario-planning/)).

## Inputs

- **QUESTION** (required): the issue under analysis, framed as something rival explanations can answer. If it is vague ("what should we do about churn"), narrow it to a truth question first ("what is the primary cause of the Q2 churn spike"). Ask one or two clarifying questions if needed.
- **EVIDENCE** (optional): any facts, observations, reports, or data the user already has. If none is supplied, the skill gathers it in Stage 2 using whatever retrieval the runtime offers.
- **ROLE** (optional): who acts on the answer, so the report can pitch the "so what". Defaults to "a decision-maker who must act on the most likely explanation."

## Orchestration map

```
Stage 1  Hypothesis set        ── N proposer subagents IN PARALLEL ── then dedupe to a clean, near-exhaustive set
Stage 2  Evidence inventory     ── 1 agent (uses retrieval) ── list every datum, incl. absence-of-evidence
Stage 3  Matrix scoring         ── 1 subagent PER HYPOTHESIS IN PARALLEL ── score each datum C / I / N/A
Stage 4  Diagnosticity + tally  ── 1 agent, needs all columns ── drop non-diagnostic rows, weight, rank by inconsistency
Stage 5  Sensitivity + deception ── 3 critic subagents IN PARALLEL ── how fragile is the ranking; what if the linchpin is wrong/planted
Stage 6  Report                 ── 1 agent ── relative likelihoods, linchpins, indicators to watch
```

Tell each subagent that its final message is the return value, meaning structured data rather than prose for a human. Subagents that gather or test evidence should use whatever retrieval or search tools the runtime offers; with no retrieval, say so and lower confidence rather than invent facts.

---

## Stage 1: Hypothesis set (PARALLEL)

A missing hypothesis can never win, so aim for near-exhaustiveness, including the explanations nobody wants to be true. Dispatch three to five proposer subagents in parallel, each generating candidate hypotheses for the QUESTION from a different stance, so the set is not all variations on one idea:

- **The conventional read** — the explanation most people would reach for first.
- **The unwelcome read** — explanations that implicate us, are politically costly, or are boring-but-true (incompetence over conspiracy, and the reverse).
- **The deception read** — the possibility that some evidence was shaped to mislead, or that the real driver is hidden.
- **The base-rate read** — what usually causes this class of outcome, regardless of the specifics here.
- **The structural / second-order read** — a system or incentive cause rather than an actor or event.

Each proposer returns a short list of candidate hypotheses, each phrased as a complete, mutually exclusive explanation ("The outage was caused by the schema migration", not "the migration").

Then **reconcile** the lists into a single clean set:

- Merge duplicates and split any hypothesis that secretly bundles two claims.
- Make the set as mutually exclusive and collectively exhaustive as the problem allows; add a residual "none of the above / unknown cause" hypothesis if the set might not be exhaustive.
- Keep it to a workable number, typically three to seven. Do **not** prune a hypothesis yet just because it seems unlikely; premature rejection is the bias the method is built to catch.

Output: the numbered hypothesis set H1…Hn, each one sentence.

## Stage 2: Evidence inventory

List every relevant piece of evidence, argument, and assumption as a discrete row. Cast wide: include hard data, observations, reports, expert judgments, *and assumptions* (label them as such), and — critically — **absence of evidence**. The dog that did not bark is a row: "no error spike in the auth service logs" can be highly diagnostic.

For each item capture:

- A short label and the full statement.
- **Type**: fact / observation / report / assumption / absence.
- **Credibility / weight**: high / medium / low, with a one-line reason (source reliability, directness, recency). Note anything that could be deliberately planted.

If EVIDENCE was supplied, start from it and fill gaps with retrieval. If not, gather it now. Aim for the evidence that could *discriminate* between hypotheses, not just describe the situation. Output: the numbered evidence list E1…Em with type and weight.

## Stage 3: Matrix scoring (PARALLEL)

Dispatch **one subagent per hypothesis**, in parallel. Each agent sees the full evidence list but owns exactly one column, and is told to **try to disconfirm its hypothesis**, not defend it.

For its hypothesis Hk, the agent scores every evidence item Ei:

- **C** — Consistent: the evidence is what you would expect to see if Hk were true.
- **I** — Inconsistent: the evidence is what you would *not* expect if Hk were true. (This is the score that does the work.)
- **N/A** — Not applicable / no bearing: the evidence neither supports nor undercuts Hk.

Allow doubling for strength where warranted: **CC** strongly consistent, **II** strongly inconsistent. Each cell gets a one-line rationale. Crucial rule, stated to every agent: ask "is this evidence *consistent* with my hypothesis", not "does this evidence *prove* my hypothesis". Many items are consistent with several hypotheses at once; that is expected and is exactly what Stage 4 uses.

Scoring each column with an independent mind committed to disconfirming that one hypothesis is what stops the favored answer from quietly winning. Output per agent: the column of scores for Hk with rationales.

## Stage 4: Diagnosticity and inconsistency tally

Assemble the columns into the full matrix: evidence as rows, hypotheses as columns. Then apply ACH's two signature moves.

**1. Find the diagnostic evidence; discount the rest.** Read across each row. An item that is Consistent (or N/A) with *every* hypothesis has **no diagnostic value**, however true or important it feels. Flag those rows as non-diagnostic and set them aside from the ranking (note them; do not delete the knowledge). The rows that matter are Inconsistent with some hypotheses but not others; those discriminate.

**2. Rank by fewest weighted inconsistencies.** For each hypothesis column, compute an **inconsistency score**: the weighted sum of its I and II cells (II counts double; weight by the evidence item's credibility, so a low-credibility "Inconsistent" counts less). The most likely hypothesis has the **lowest** inconsistency score, the one the evidence fails to disprove, *not* the one with the most C marks. State the ranking with each hypothesis's inconsistency tally and the specific items driving it.

Render the matrix as a table so it is auditable:

| Evidence (weight) | H1 | H2 | H3 | Diagnostic? |
|---|---|---|---|---|
| E1 — schema migration ran at 14:02 (high) | CC | I | N/A | yes |
| E2 — traffic was nominal (high) | C | C | C | no — consistent with all |
| … | | | | |
| **Inconsistency score (weighted)** | **0** | **3** | **5** | |

## Stage 5: Sensitivity and deception check (PARALLEL)

A ranking that turns on one or two pieces of evidence is fragile. Dispatch three critic subagents in parallel, each with a distinct attack on the Stage 4 conclusion:

- **The linchpin critic** — identify the few evidence items the ranking actually depends on. Ask of each: how few items would have to flip to change the winner? If the conclusion rests on one or two items, say so loudly.
- **The deception critic** — assume the most decisive evidence was deliberately planted or is wrong. Re-rank under that assumption. If a single deception flips the answer, that is a finding, not a footnote.
- **The hypothesis-gap critic** — attack the set itself. Is there a hypothesis nobody proposed? Does the winning hypothesis only win because a real rival is missing? Recommend any hypothesis that should be added and the analysis re-run.

Each critic returns its finding and a revised view if the conclusion does not hold up. Reconcile: if the conclusion is robust, say why; if it hinges on a fragile linchpin or a missing hypothesis, lower confidence accordingly and name what would firm it up.

## Stage 6: Report

Write the briefing for the ROLE. Lead with the answer, then show the work.

1. **Bottom line.** The ranked hypotheses with their relative likelihood (not just the top one — ACH reports the whole field), and the headline confidence.
2. **The matrix.** The Stage 4 table, so the reasoning is auditable at a glance.
3. **Why this ranking.** For the leading hypothesis, the evidence that fails to disprove it; for each rejected hypothesis, the specific inconsistent evidence that sinks it. Frame it as disconfirmation: "H2 is rejected because E1 and E7 are strongly inconsistent with it", not "H1 has the most support".
4. **Linchpins and fragility.** The few items the conclusion depends on (from Stage 5), and how the ranking shifts if any of them is wrong or planted.
5. **Indicators to watch.** Concrete future observations that would *change* the answer — milestones that, if seen, should raise a currently-trailing hypothesis. This converts the analysis into a live tripwire instead of a one-time verdict.
6. **Gaps and confidence.** What evidence is missing, which hypotheses remain too close to call, and the overall confidence with its basis.

---

## Principles

- **Rank by disconfirmation, not confirmation.** The winner is the hypothesis with the least evidence *against* it. Evidence "for" a hypothesis is usually consistent with several others and proves little; do not quietly revert to counting checkmarks.
- **Diagnostic evidence only.** A fact consistent with every hypothesis has zero power to discriminate, no matter how solid it feels. Identify it and set it aside from the ranking.
- **Hold all hypotheses at once.** Never prune to a favorite early. A hypothesis never on the matrix can never be tested, and the one you would have dropped is the one this method is designed to rescue.
