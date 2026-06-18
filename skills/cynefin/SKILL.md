---
name: cynefin
description: Use when the user faces a hard, messy, or stuck problem and needs to pick the right approach before reaching for any other tool, or when plans keep failing because a complex problem is being handled as if it were merely complicated. Surfaces the constituent issues of a situation, then fans out parallel classifiers that place each issue into one of Cynefin's domains (Clear, Complicated, Complex, Chaotic, or Disorder) with evidence and the matching action model, then synthesizes the portfolio across the domains, flags any issue on the Clear-Chaotic cliff or stuck in Disorder, and recommends a domain-appropriate approach and which other framework fits each. Triggers include "Cynefin", "what kind of problem is this", "complex vs complicated", "why do our plans keep failing", "Snowden sense-making".
---

# cynefin

Runs Dave Snowden's Cynefin framework to sort a situation by its kind of cause-and-effect and so choose how to act. Cynefin is a meta-framework: it does not solve the problem, it tells you what kind of problem you have and therefore which approach, and which other tool, fits. The point is not to label the situation but to stop applying the wrong kind of response to it.

The five domains, their decision models, their diagnostic questions, the cliff between Clear and Chaotic, and the failure of misdiagnosis live in [references/cynefin.md](references/cynefin.md). Load that file before analyzing.

## When to use

At the start of a hard or messy problem, to pick the right way to act and the right framework before committing to either. Reach for it when plans keep failing: usually a complex problem is being treated as merely complicated, so the team analyzes harder when it should be running experiments. The unit of analysis is a situation, which almost always spans several domains, not a single decision. Cynefin complements tosca-problem-definition and mece-decomposition: those frame and split a problem; Cynefin tells you what kind of cause-and-effect governs each part and so how to attack it. Use it before the analytic frameworks, not instead of them.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **SITUATION** (required): the problem, decision, or mess to make sense of. If it is stated as one tidy question, push for the underlying situation, since a single phrasing usually hides several issues in different domains.
- **CONTEXT** (optional): what has already been tried and failed, the stakes and time pressure, who must act, and what decision the analysis should inform. This shapes which misdiagnoses are most costly and how to phrase the recommended action, not which domain an issue belongs in.

## Orchestration map

```
Stage 1  Issue Surfacing  ── 1 agent, inline ───────────────┐  (break the situation into its constituent issues)
Stage 2  Classification    ── N classifier subagents IN PARALLEL ──┐  (place each issue in a domain with evidence)
Stage 3  Synthesis         ── 1 agent, needs all N ──────────┘  (portfolio across domains, cliff, disorder, action, frameworks)
```

## Stage 1: Issue Surfacing (inline)

Break the SITUATION into its constituent issues or aspects. A real situation spans domains: a product launch can hold a Clear logistics issue, a Complicated pricing model, and a Complex market-reception question all at once. Do not force the whole thing into one domain, which is the first step toward misdiagnosis. List each issue as a short, self-contained statement that can be classified on its own. Aim for the natural seams of the problem, not an exhaustive decomposition.

## Stage 2: Classification (PARALLEL)

Dispatch one classifier subagent per issue at once. Give each the shared framing plus its single issue and the full diagnostic questions from the reference file.

**Shared framing (send to every classifier):**

> Place one issue from this situation into a single Cynefin domain: **[ISSUE]**. Work through the diagnostic questions for each domain in the reference file and decide which kind of cause-and-effect actually governs this issue: obvious to all (Clear), knowable through analysis or expertise (Complicated), coherent only in retrospect (Complex), or absent (Chaotic). If you cannot tell, say so and place it in Disorder rather than guessing. Then return:
> - **Domain**: Clear, Complicated, Complex, Chaotic, or Disorder
> - **Evidence**: the specific facts about this issue that fix it in that domain, answered against the diagnostic questions
> - **Action model**: the matching decision sequence (sense-categorize-respond for Clear, sense-analyze-respond for Complicated, probe-sense-respond for Complex, act-sense-respond for Chaotic) and what the first concrete move is
> - **Practice**: best, good, emergent, or novel, per the domain
> - **Misdiagnosis risk**: what goes wrong if this issue is treated as belonging to an adjacent domain (for example, applying a best-practice recipe to a Complex issue, or over-analyzing a Complex issue when the answer is emergent and cannot be known in advance)
> - **Confidence**: high, medium, or low, lowered if the evidence is thin or the issue sits near a boundary
>
> Context: [CONTEXT]

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their classification in real evidence. Collect all classifications before continuing. Re-dispatch any classifier that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all N)

One agent maps the classified issues into a single picture and turns it into action. This is where the meta-framework earns its value, by routing each issue to the right response rather than restating the domains:

1. **The portfolio.** Lay the issues out across the domains so the shape of the situation is visible at a glance. Most situations are mixed; name the mix.
2. **The cliff and Disorder.** Flag any issue sitting on the fold between Clear and Chaotic, where complacency about a stable, well-understood thing risks a sudden catastrophic fall. Flag any issue still in Disorder, where no one yet knows which domain it is in, and say how to break it down further, since Disorder is the danger zone where people default to their comfort domain.
3. **Domain-appropriate action.** For each issue, the matching move: apply best practice (Clear), bring in expert analysis (Complicated), run small safe-to-fail experiments and watch what emerges (Complex), or act first to stabilize and then move out of chaos (Chaotic). Do not over-analyze the Complex issues; the answer is emergent, not knowable in advance.
4. **Which framework fits where.** Suggest the other tools that suit each domain: checklists and standard operating procedure for Clear; the analytic frameworks (most of this collection: SWOT, BMC, decision trees, expert modeling) for Complicated; experiment design and short feedback loops for Complex; rapid triage and command for Chaotic. Cynefin is the dispatcher, not the destination.
5. **Movement between domains.** Name the signals that an issue is moving: a Complex experiment that has revealed a repeatable pattern is becoming Complicated; a Clear process drifting toward complacency is creeping toward the cliff; a Chaotic situation stabilizing can be re-sorted into Complex or Complicated. Tie this to the CONTEXT: what to watch and when to reclassify.

## Report structure

Write a thorough markdown report and save it to `cynefin-<situation-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The situation analyzed, the context if given, the date, and a one-line note that Cynefin is a sense-making meta-framework: it picks the approach, it does not solve the problem.
2. **Verdict.** The shape of the situation in a few sentences, with a summary table: each issue, its domain, its matching action model, and confidence. Note up front any issue on the cliff or stuck in Disorder.
3. **The portfolio.** The issues laid out by domain, so the mix is scannable. For each issue: the evidence that fixes it in its domain, the action model, and the misdiagnosis risk.
4. **Action and frameworks.** The domain-appropriate move for each issue, which other framework to reach for, and the order to attack them in.
5. **Movement.** The signals that any issue is shifting domains, and what to re-examine when they appear.
6. **Caveats.** Cynefin classifies cause-and-effect to choose an approach; it does not produce the answer, which still comes from acting in the chosen way. Boundaries between domains are judgments, not facts, and an issue can be near a fold; the classification is a working hypothesis, not a verdict. The framework guards against misdiagnosis but cannot prevent it where evidence is thin, so low-confidence placements are exactly the ones to revisit as the situation reveals itself.

## Principles

- **Diagnose before you act.** The whole value is choosing the right kind of response. A correct answer to the wrong kind of problem still fails.
- **Misdiagnosis is the failure mode.** Applying best-practice recipes to a Complex problem fails; over-analyzing a Complex problem also fails, slower, because the answer is emergent and cannot be known in advance. Guard every classification against the adjacent domain.
- **Mind the cliff.** Complacency in the Clear domain is how a stable thing falls into chaos. The most dangerous issue is often the one everyone thinks is settled.
- **Disorder is the default trap.** When you do not know the domain, people fall back to their comfort domain. Name the Disorder explicitly and break it down rather than letting habit decide.
- **Cynefin is the dispatcher.** It routes each issue to the matching response and the matching framework; it is not itself the analysis. Hand off to the right tool.
- **Parallel where independent.** Each issue can be classified concurrently. The portfolio, cliff, and routing need all of them, so synthesis runs after.
