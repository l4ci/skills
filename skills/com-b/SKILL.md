---
name: com-b
description: Use when the user wants to understand why a target behaviour is or is not happening and what would actually change it — product adoption, process compliance, safety behaviour, habit formation, organizational change. Fans out six parallel analyst subagents, one per COM-B sub-component (Physical and Psychological Capability, Physical and Social Opportunity, Reflective and Automatic Motivation), each judging whether its component is sufficient or a barrier with evidence, severity, and confidence, then synthesizes the binding constraint, maps it to the right intervention functions of the Behaviour Change Wheel, and designs targeted interventions. Guards against the default error of assuming the problem is motivation when it is opportunity or capability. Triggers include "COM-B", "Behaviour Change Wheel", "why won't people do X", "behaviour change", "drive adoption", "improve compliance".
---

# com-b

Runs Michie, van Stralen, and West's COM-B model and the Behaviour Change Wheel to diagnose a specific behaviour: a behaviour happens only when Capability, Opportunity, and Motivation are all sufficient at once, so the missing component is the binding constraint and the intervention must target it. The point is not to assume the problem is motivation but to find which of the three is the actual barrier — because people who fail to act are usually willing but lack the capability or the opportunity, and motivating someone who lacks the opportunity changes nothing.

The behaviour definition, the six sub-components, the nine intervention functions, and the deficit-to-function mapping live in [references/com-b.md](references/com-b.md). Load that file before diagnosing and judge each component against it exactly.

## When to use

The user has an adoption, compliance, habit, or behaviour-change problem and wants to know why the behaviour is not happening and what would change it. The unit of analysis is one specific behaviour by one specific actor or population, not a strategy or a culture in the abstract. Use ADKAR or Kotter when the question is how to run an organizational change programme; use Jobs-to-be-Done when the question is what outcome a customer is hiring a product for; use COM-B when the question is the mechanics of a single behaviour: capability, opportunity, motivation. If the user names several behaviours, diagnose the one they care about most or run each separately; do not blur them.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **BEHAVIOUR** (required): the target behaviour to diagnose. Push for one specific action — who does what, when, where. If it is stated as a goal ("be healthier", "adopt the tool"), narrow it to a concrete behaviour with one or two questions first.
- **ACTOR** (required): the person or population expected to perform the behaviour. Different actors face different barriers; if the user names a broad group, segment it or pick the segment that matters.
- **CONTEXT** (optional): the setting, what has already been tried, and the decision the diagnosis should inform. This shapes the severity weighting and the intervention design, not the component assessments.

## Orchestration map

```
Stage 1  Define          ── inline ──────────────────────────────┐  (pin down the behaviour and the actor)
Stage 2  Component Scan   ── 6 analyst subagents IN PARALLEL ─────┤  (each judges one sub-component: barrier or sufficient)
Stage 3  Synthesis        ── 1 agent, needs all 6 ────────────────┘  (binding constraint → intervention functions → design)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their assessment in real evidence.

## Stage 1: Define the behaviour (inline)

Before any analysis, state the target behaviour as a concrete action — who does what, when, where — and the specific actor expected to perform it. A vague behaviour cannot be diagnosed, because each component is judged against a concrete action by a concrete actor. If BEHAVIOUR or ACTOR is loose, sharpen it now; carry the sharpened definition into every subagent prompt.

## Stage 2: Component Scan (PARALLEL)

Dispatch six analyst subagents at once, one per sub-component: Physical Capability, Psychological Capability, Physical Opportunity, Social Opportunity, Reflective Motivation, Automatic Motivation. Give each the shared framing plus its sub-component's definition from the reference file.

**Shared framing (send to each analyst):**

> Assess one sub-component of COM-B for this behaviour: **[BEHAVIOUR]**, performed by **[ACTOR]**. Judge only your assigned sub-component, using its definition from the framework. Ground each claim in real evidence (observed conditions, data, documented practice, what the actor actually faces) where you can find it. Then return:
> - **Verdict**: is this sub-component sufficient for the behaviour, or is it a barrier?
> - **Evidence**: the specific conditions, facts, or observations behind the verdict, each grounded where possible and marked as fact or assumption
> - **Severity**: if a barrier, how binding a constraint it is — does it alone block the behaviour, or only weaken it — on a low/medium/high scale
> - **Interactions**: how your sub-component depends on or trades off against others (for example, a cue is useless without the skill to act on it)
> - **Confidence**: high, medium, or low, lowered if evidence was thin or the verdict rests on assumption
>
> Context: [CONTEXT]

Assign the six sub-components from the reference file. Collect all six structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 6)

One agent merges the six assessments into a diagnosis and an intervention plan. This is where the model earns its value, by finding the real barrier rather than restating the components:

1. **The binding constraint.** Rank the barriers by severity. Identify the one or two components that actually block the behaviour — the missing components without which the behaviour cannot happen — distinguished from sub-components that merely weaken it. Roll the six sub-components up into the three components (C, O, M) so the picture is clear.
2. **Check the motivation reflex.** State explicitly whether the binding constraint is motivation, capability, or opportunity. If anyone (the user, prior attempts, the obvious framing) has assumed motivation is the problem, test that assumption against the evidence and say plainly if the real gap is opportunity or capability. This is the single most common and most expensive error; name it.
3. **Map to intervention functions.** Using the deficit-to-function mapping in the reference file, route each binding constraint to the intervention functions that can plausibly close it. Do not map by intuition: a capability gap is not closed by persuasion, a motivation gap is not closed by training.
4. **Design targeted interventions.** For each function selected, specify the concrete intervention for this behaviour and this actor — what to actually do. Tie it to the CONTEXT and to what has already been tried. Note any secondary constraint that will surface once the binding one is removed, so the intervention does not stall after the first barrier falls.

## Report structure

Write a thorough markdown report and save it to `com-b-<behaviour-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The behaviour and actor diagnosed, the context if given, the date, and a one-line note on the framework and that COM-B diagnoses one behaviour, not a strategy.
2. **The behaviour.** The behaviour as defined — who does what, when, where — and the actor, so the diagnosis is anchored to a concrete action.
3. **Verdict.** The binding constraint in a few sentences, with a summary table: each of the six sub-components, its verdict (sufficient or barrier), severity if a barrier, and confidence. State up front whether the gap is capability, opportunity, or motivation.
4. **Component scan.** The six sub-components, grouped under Capability, Opportunity, and Motivation, each with its verdict, evidence, severity, and what is fact versus assumption.
5. **Diagnosis and interventions.** The binding constraint, the explicit check against the motivation reflex, the intervention functions it maps to, and the targeted interventions designed for this actor — plus any secondary constraint waiting behind it.
6. **Caveats.** COM-B diagnoses one specific behaviour at a point in time, not a strategy or a culture; the mapping to intervention functions narrows the field but does not guarantee a chosen intervention will work in practice; assessments marked as assumptions are untested; and removing the binding constraint may reveal a barrier it was masking.

## Principles

- **Find the barrier, do not assume it.** The whole method is locating which of Capability, Opportunity, and Motivation is the binding constraint. Assuming it is motivation is the classic, costly error.
- **It is usually opportunity or capability.** People who fail to act are mostly willing. Check the world and the skills before blaming the will.
- **Match the function to the deficit.** Education and persuasion fix motivation and knowledge; environmental restructuring and enablement fix opportunity. Use the mapping, not intuition.
- **Define the behaviour or diagnose nothing.** A goal is not a behaviour. Pin down who does what, when, where, before assessing any component.
- **Parallel where independent.** The six sub-components can be assessed concurrently. The binding-constraint and intervention logic needs all six, so synthesis runs after.
