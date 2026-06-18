---
name: cognitive-bias-audit
description: Use when the user wants to audit a decision, plan, forecast, or analysis for cognitive biases before committing to it, or to stress-test where reasoning might be systematically distorted. Fans out five parallel hunter subagents, one per bias family, each finding where THIS decision is exposed with evidence from the actual reasoning, then ranks the live biases by how much they threaten the call, names the one or two most dangerous, and prescribes specific debiasing moves plus a corrected read in a detailed markdown report. Triggers include "cognitive bias", "audit this decision for bias", "what biases are at play", "debias", "am I fooling myself", "stress-test my reasoning".
---

# cognitive-bias-audit

Audits a decision, plan, forecast, or analysis for cognitive biases. Biases are systematic, not random: the same pressures bend reasoning the same way every time, which is why you cannot introspect them away. The point is not to label biases generically but to find where *this specific decision* is exposed and change the process that produced it.

The bias families, each with its tell (how it shows up in actual reasoning) and a countermeasure, plus the debiasing toolkit, live in [references/biases.md](references/biases.md). Load that file before auditing and work the decision against each family exactly.

## When to use

The user is about to commit to a high-stakes decision or forecast, or wants to pressure-test an analysis they or someone else produced. The unit of analysis is one decision and the reasoning behind it. Distinguish from a pre-mortem, which imagines the decision has failed and works backward from the failure; this skill inspects the reasoning as it stands now. Distinguish from a weighted-decision-matrix, which scores options against criteria; this audits how the choice between them is being reasoned about. A bias audit often prescribes those two as countermeasures.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **DECISION** (required): the decision, plan, forecast, or claim under audit. If only a topic is given, pull out the actual call being made before starting.
- **REASONING** (required): the reasoning and evidence behind it, the key claims, and how the conclusion was reached. Without the reasoning there is nothing to audit; if it is missing, ask for it. A bias audit of a bare conclusion is bias-spotting theater.
- **STAKES** (optional): what rides on the decision and what being wrong would cost. Sharpens the severity ranking, since a bias matters in proportion to how much it could distort a consequential call.

## Orchestration map

```
Stage 1  Capture       ── inline, 1 pass ───────────────────────┐  (decision, reasoning, key claims, stakes)
Stage 2  Bias Hunt     ── 5 hunter subagents IN PARALLEL ───────┤  (one per family: where is THIS reasoning exposed)
Stage 3  Synthesis     ── 1 agent, needs all 5 ─────────────────┘  (rank, name the worst, prescribe, corrected read)
```

## Stage 1: Capture (inline)

Before dispatching, pin down what is being audited so every hunter works the same target:

1. **The call.** State the decision, plan, forecast, or claim in one line.
2. **The reasoning.** The argument and evidence that lead to it, as actually given, including the key claims each step rests on.
3. **The stakes.** What rides on it and what being wrong costs, if known.

If the reasoning is thin or absent, get it before continuing. The hunters need real reasoning to cite, not a conclusion to speculate about.

## Stage 2: Bias Hunt (PARALLEL)

Dispatch five hunter subagents at once, one per bias family from the reference file: Belief & evidence, Confidence & prediction, Attachment & loss, Social, Framing & salience. Give each the captured decision and reasoning, the shared framing, and its family's entries.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground severity claims (base rates, comparable cases, how similar decisions turned out) in real evidence.

**Shared framing (send to each hunter):**

> Audit this decision and its reasoning for exposure to your assigned bias family. Decision: **[DECISION]**. Reasoning: **[REASONING]**. Stakes: **[STAKES]**.
> For each bias in your family, decide whether it is *live* here. A bias is live only when you can point to the place in the reasoning where it operates; a generic warning does not count. Apply the families to the reasoning as given, including the reasoner's own bias, not just biases you would attribute to others. For each live bias, return:
> - **Bias**: the named bias
> - **Where exposed**: the exact step, claim, or evidence in the reasoning where it operates, quoted or closely paraphrased
> - **Severity** (1 to 5): how much it could distort *this* call given the stakes, not how bad the bias is in general
> - **Confidence** (high, medium, low): how sure you are it is actually operating here, lowered when the evidence in the reasoning is ambiguous
> - **Countermeasure**: the specific debiasing move that would address this exposure
> Skip biases in your family that are not live. Do not pad the list; an honest "not exposed here" is a finding.

Collect all five structured results before continuing. Re-dispatch any hunter that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five hunts into a ranked, actionable audit:

1. **Drop the theater.** Cut any flagged bias that cites no real place in the reasoning. A label without evidence is removed, not ranked.
2. **Rank by threat to this decision.** Order the live biases by severity times confidence, weighted by the stakes. The question is not "which bias is worst in general" but "which most threatens this call."
3. **Name the one or two most dangerous.** The biases that, left unaddressed, would most likely flip or wreck the decision. Say why for each, tied to the reasoning.
4. **Prescribe specific debiasing moves.** For each top bias, a concrete process change, not "be aware." Tie to the toolkit: a pre-mortem for optimism and planning fallacy, the outside view / reference-class forecasting for base-rate neglect, a weighted-decision-matrix to force explicit criteria where framing or salience is bending the choice, six-thinking-hats to separate the emotional, optimistic, and critical reads where one mode dominates. Name who does what.
5. **Corrected read.** Re-state the decision as it looks once the top biases are accounted for: what the reasoning understated or overstated, and how the call changes (or holds) after debiasing. Do not use the audit to dismiss a conclusion; show what survives it.

## Report structure

Write a thorough markdown report and save it to `cognitive-bias-audit-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The decision audited, the stakes if given, the date, and a one-line note that a bias audit inspects the reasoning, it does not prove the conclusion wrong.
2. **Verdict.** In a few sentences: how exposed this decision is, and the one or two biases that most threaten it. A summary table of live biases with family, where exposed, severity, and confidence.
3. **Exposure by family (five sections).** Each family's live biases with the exact reasoning where each operates, severity, and confidence. Note explicitly where a family is not exposed.
4. **The dangerous few.** The top one or two biases ranked, why each threatens this call, and the specific debiasing move prescribed for each, with who does what.
5. **Corrected read.** The decision re-stated after accounting for the top biases: what shifts, what holds.
6. **Caveats.** A bias audit inspects reasoning, it does not verify facts or guarantee a good outcome; severity and confidence are judgment, not measurement; an unbiased process can still reach a wrong answer and a biased one a right answer; identifying a bias shows where the process is exposed, it does not by itself refute the conclusion; and the audit can itself be motivated, so a disliked conclusion is not debunked merely by attaching a bias label.

## Principles

- **Evidence, not labels.** Every flagged bias cites the exact place in the reasoning where it operates. A name without that place is theater and gets cut.
- **Audit yourself too.** Apply the families to the reasoning at hand whoever produced it, including the reasoner's own. The easy biases to spot are always someone else's.
- **Severity-rank to this decision.** A bias matters in proportion to how much it could distort *this* call. Rank by threat, not by how notorious the bias is.
- **Prescribe process, not awareness.** "Be aware of anchoring" changes nothing. Prescribe a structural move: pre-mortem, outside view, blind review, pre-committed criteria, who does it.
- **A label is not a refutation.** The audit shows where reasoning is exposed; it does not decide the conclusion is wrong. Give a corrected read, do not dismiss.
- **Parallel where independent.** The five families share no state, so hunt them concurrently. The ranking needs all five, so synthesis runs after.
