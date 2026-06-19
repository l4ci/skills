---
name: pre-mortem
description: Use when the user wants to stress-test a plan, proposal, PRD, strategy, or decision before committing to it. Runs a prospective-hindsight pre-mortem by fanning out independent failure-finder subagents across distinct risk lenses, deduplicating and scoring the risks by likelihood and impact, then designing mitigations for the worst ones. Triggers include "pre-mortem", "red-team this plan", "what could go wrong", "stress-test this", "poke holes in this proposal".
---

# pre-mortem

A pre-mortem uses prospective hindsight (Gary Klein): imagine it is some months from now and the plan has already failed, then work backward to explain why. Naming a failure that has "already happened" surfaces risks that "what could go wrong?" misses, because it removes the optimism of an open future.

## When to use

The user has a plan, PRD, strategy, launch, migration, or decision and wants it stress-tested before committing. Not for work already shipped (that is a post-mortem) and not for debugging a specific failure (use a debugging workflow).

## Inputs

- **PLAN** (required): the thing under review. A pasted document, a file path, or a described decision.
- **CONTEXT** (optional): goals, constraints, budget, timeline, and what "failure" concretely means here (missed deadline, low adoption, blown budget, harm to users). If missing, ask one or two questions before starting, since the lenses are only as good as the definition of failure.
- **HORIZON** (optional): the point to imagine standing at. Defaults to the plan's own deadline, or "six months after launch" if none is given.

## Orchestration map

```
Stage 1  Failure Scan      ── 6 finder subagents IN PARALLEL ──┐  (each attacks from one lens)
Stage 2  Blind-spot Pass   ── 1 critic, needs all 6 ──────────┤  (what did every lens miss?)
Stage 3  Reconcile & Score ── 1 agent, needs 1 + 2 ───────────┤  (dedupe, cluster, rank by likelihood x impact)
Stage 4  Mitigations       ── 1 subagent per top risk IN PARALLEL ── then assemble report
```

Tell each subagent its final message is the return value: structured data, not prose for a human.

## Stage 1: Failure Scan (PARALLEL)

Dispatch six finder subagents at once, one per lens. Give every finder the shared framing plus one lens.

**Shared framing (send to every finder):**

> It is **[HORIZON]**. The plan below has failed. It did not just underperform; it clearly failed by the definition of failure given in the context. Working only from your assigned lens, explain what went wrong. Be specific and concrete, not generic. Return a list of failure modes; for each one give:
> - **Failure mode** (one line: what happened)
> - **Mechanism** (how it actually unfolded, step by step)
> - **Early warning signs** (what we would have noticed first, while there was still time)
> - **Likelihood** (1 to 5) and **Impact** (1 to 5), each with a one-line reason
>
> Plan under review: [PLAN]
> Context and definition of failure: [CONTEXT]

**Lenses (one per finder):**

1. **Execution and technical:** the build itself breaks. Hidden complexity, integration, scaling, unknowns, things that look simple and are not.
2. **People and adoption:** the people who must use it or do the work do not. Incentives, change resistance, training, the gap between "available" and "used".
3. **Timeline and resources:** it runs out of time, money, or people. Estimation error, dependency chains, key-person bottlenecks, scope creep.
4. **Assumptions and dependencies:** a load-bearing assumption was false, or an external dependency moved. The single belief that, if wrong, sinks the rest.
5. **Second-order effects:** it "succeeds" and breaks something else. Perverse incentives, cannibalization, technical debt, harm to a group not considered.
6. **External and competitive:** the world moved. Competitor action, market shift, regulation, a stakeholder or supplier change outside the team's control.

Collect all six structured results before continuing. Re-dispatch any finder that fails rather than proceeding with a gap.

## Stage 2: Blind-spot Pass (SEQUENTIAL, needs all 6)

One critic receives all six finders' output and answers: what plausible failure mode did every lens miss? Where are the finders crowded onto the same few risks while a whole category sits unexamined? Return any additional failure modes in the same format as Stage 1. This catches the risk that the lens set itself created a blind spot.

## Stage 3: Reconcile and Score (SEQUENTIAL, needs Stages 1 and 2)

One agent merges everything:

1. **Deduplicate and cluster.** The same risk often appears under several lenses worded differently. Merge them, and note which lenses raised each, since cross-lens agreement is itself a signal of severity.
2. **Score.** For each merged risk, settle on a likelihood (1 to 5) and impact (1 to 5), and compute **severity = likelihood x impact** (1 to 25). When finders disagreed on a score, use the range and lean toward the higher end for impact, since pre-mortems exist to catch the costly cases.
3. **Rank** by severity. Band them: 20 to 25 critical, 12 to 19 high, 6 to 11 medium, 1 to 5 low.

## Stage 4: Mitigations (PARALLEL, then assemble)

For each risk banded critical or high (cap at the top eight if there are more), dispatch one subagent to design the response. Each returns:

- **Mitigation:** the specific action that lowers likelihood or impact, and which of the two it targets.
- **Leading indicator:** the one metric or signal to watch that would fire early, before the failure is locked in.
- **Contingency:** what to do if it happens anyway.
- **Suggested owner:** the role best placed to hold this, if the context names roles.

Run these in parallel, then assemble the report.

## Report structure

Write a thorough markdown report and save it to `pre-mortem-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** What was reviewed, the imagined horizon, the definition of failure used, the date, and a one-line note that this is a prospective-hindsight pre-mortem.
2. **Executive summary.** The overall risk posture in a few sentences, then the top three to five risks as a tight list. A reader with two minutes should leave knowing what most threatens the plan.
3. **Risk register.** A ranked table: risk, likelihood, impact, severity, band, and which lenses raised it.
4. **Detailed entries** for every critical and high risk: mechanism, early warning signs, mitigation, leading indicator, contingency, and suggested owner.
5. **The blind spot.** The failure mode from Stage 2 that the standard lenses nearly missed. Flag it prominently; it is often the most valuable finding.
6. **What this pre-mortem is not worried about.** A short, honest list of risks considered and judged low, so the report does not read as uniformly alarmist and the reader can see what was weighed and dismissed.
7. **Caveats.** A pre-mortem surfaces plausible failures, not certainties; likelihoods are judgment, not data. It is only as good as the definition of failure it was given. It will not catch a true unknown unknown. Use it to decide what to watch and what to harden, not as a verdict on whether to proceed.

## Principles

- **Failure as a fact, not a possibility.** The framing must be "it failed, explain why", not "what might go wrong". The certainty is what unlocks the honest answers.
- **Keep the lenses sharp and separate.** Do not let one finder hedge into balance; reconciliation happens in Stage 3.
- **Severity beats volume.** A long list of risks is not the goal. Ranked, scored, mitigated risks are. Cross-lens agreement and high impact push a risk to the top.
- **Honest about limits.** A pre-mortem informs judgment; it does not replace it.
