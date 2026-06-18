---
name: storm-research
description: Use when the user wants deep, PhD-level research on a topic. Runs a STORM-style multi-perspective investigation by fanning out parallel expert subagents (each doing its own retrieval), mapping where they contradict, synthesizing a CEO-grade briefing, then peer-reviewing it with a panel of independent critics that assign confidence scores and name the gaps.
---

# storm-research

A parallel replication of Stanford's STORM method (Synthesis of Topic Outlines through Retrieval and Multi-perspective Question Asking). One agent cannot hold five conflicting epistemic positions at once, so this skill splits them into separate minds first and reconciles them second.

The skill runs four stages. Stage 1 and Stage 4 fan out across many subagents in parallel. Stages 2 and 3 run sequentially, because each one depends on the output before it.

## When to use

The user wants a rigorous, multi-source, self-critiqued briefing on a topic rather than a quick answer. Triggers: "research X deeply", "PhD-level research", "STORM", "give me a briefing with confidence scores", "what does the evidence actually say about X".

## Inputs

- **TOPIC** (required): what to research. If it is vague, ask one or two narrowing questions first.
- **ROLE** (optional): who the actionable insight is for, such as "a product manager" or "a clinician". Defaults to "a decision-maker acting on this topic."

## Orchestration map

```
Stage 1  Multi-Perspective Scan   ── 5 subagents IN PARALLEL ──┐  (each researches + answers as one expert)
Stage 2  Contradiction Map        ── 1 agent, needs all 5 ─────┤  (sequential: depends on Stage 1)
Stage 3  Synthesis                ── 1 agent, needs 1 + 2 ─────┤  (sequential: depends on Stage 2)
Stage 4  Peer Review              ── 3 critic subagents IN PARALLEL ── then reconcile
```

Tell each subagent that its final message is the return value, meaning structured data rather than prose written for a human. Subagents should use whatever retrieval or search tools the runtime offers so each perspective rests on real sources. If the runtime has no retrieval tools, the subagent should say so and lower its own confidence rather than inventing citations.

---

## Stage 1: Multi-Perspective Scan (PARALLEL)

Dispatch five subagents at once, one per perspective. Give every subagent the shared scaffold below plus exactly one perspective block. Each one returns the same three fields.

**Shared scaffold (send to every perspective agent):**

> You are researching the topic: **[TOPIC]**.
> Adopt the single perspective assigned below, fully and only this one. Use the available search and retrieval tools to ground your answer in real sources, and cite them. Then return exactly these three fields:
> - **Core position** (2 sentences)
> - **Strongest supporting evidence** (with sources)
> - **The one thing only this perspective would tell me** (what every other lens misses)

**Perspective blocks (one per agent):**

1. **THE PRACTITIONER** works with this daily. What do they know that academics miss? What practical realities get ignored?
2. **THE ACADEMIC** has studied this for years. What does the peer-reviewed evidence actually say? Where does the evidence contradict popular belief?
3. **THE SKEPTIC** thinks the mainstream view is wrong. What is the strongest counterargument? What evidence do proponents conveniently ignore?
4. **THE ECONOMIST** follows the money. Who profits from the current narrative? What financial incentives shape the research?
5. **THE HISTORIAN** has seen similar patterns before. What historical parallels exist? What can we learn from how those played out?

Collect all five structured results before continuing. If a subagent fails, re-dispatch that one perspective rather than proceeding with a hole.

---

## Stage 2: Contradiction Map (SEQUENTIAL, needs all 5)

One agent receives all five perspective results and produces the map. You can also do this inline.

1. **Conflicts**: where two or more perspectives directly contradict each other. List each clash with the specific claims involved.
2. **Strongest vs. weakest**: which perspective has the strongest evidence, which has the weakest, and why.
3. **The crux question**: the one question that, if answered, would resolve the biggest contradiction.
4. **Unanimous agreement**: what every perspective agrees on. Treat these as load-bearing, since even opponents confirm them.
5. **The blind spot**: what none of the perspectives addressed. This is the gap in the field and often the most valuable finding.

---

## Stage 3: Synthesis (SEQUENTIAL, needs Stages 1 and 2)

One agent synthesizes everything into a briefing.

1. **One-paragraph summary**: brief a CEO who has 60 seconds and needs the nuance, not just the headline.
2. **5 key findings**: ranked by reliability. For each, note which perspectives support it and which challenge it.
3. **Hidden connection**: one non-obvious link between findings that only appears when all five perspectives are viewed together.
4. **Actionable insight**: what someone in **[ROLE]** should actually do differently. Be specific.
5. **Frontier question**: the one question that, if answered, would change how we understand the topic.

---

## Stage 4: Peer Review (PARALLEL, then reconcile)

Stanford's own researchers flagged that STORM does not self-critique, so source bias and misattributed facts slip through. An independent panel fixes that.

Dispatch three critic subagents in parallel. Give each one the full Stage 3 briefing plus the Stage 1 and 2 material, and assign each a different lens:

- **Critic A, Methodology and evidence:** verify the strongest claims against sources, and flag misattributed or unsupported facts.
- **Critic B, Bias and representation:** which perspective is overrepresented? Did one voice dominate the synthesis?
- **Critic C, Completeness:** what 6th perspective is missing that would change the conclusions?

Each critic returns the same review schema:

1. **Confidence scores**: rate each of the 5 key findings 1 to 10 for reliability, with a one-line justification per score.
2. **Weakest link**: the claim they are least confident in, and the specific information needed to verify it.
3. **Bias check**: which perspective may be overrepresented.
4. **Missing perspective**: the 6th angle that would change conclusions, if any.
5. **Overall grade**: the grade a Stanford professor would assign, and the top fixes.

**Reconcile the panel** into the final peer-review section. Take the median of each finding's confidence score, and take the union of the weakest links and missing perspectives. Report a consensus grade with the dissent noted. When critics disagree by more than two points on a score, report the range and mark the finding as contested rather than averaging the disagreement away.

---

## Final output

Deliver the **Synthesis briefing** (Stage 3) first, then the **reconciled Peer Review** (Stage 4). Lead with the one-paragraph summary. Surface the load-bearing claims (the unanimous agreement) and the named blind spot prominently, since those are the most reliable and most valuable results respectively.

## Principles

- **Real retrieval, not roleplay.** The value comes from each perspective grounding its claims in sources. A simulated debate with no evidence just produces five confident opinions and no new information.
- **Parallel where independent, sequential where dependent.** The five perspectives and three critics share no state, so run them concurrently. The map and the synthesis need everything upstream, so run them after.
- **Keep the epistemic positions separate.** Do not let one agent soften a perspective to sound balanced. The skeptic should be maximally skeptical. Reconciliation happens in Stage 2, not inside Stage 1.
