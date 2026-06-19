---
name: five-dysfunctions-of-a-team
description: Use when the user wants to diagnose why a team is underperforming, conflict-avoidant, political, or not delivering, using Patrick Lencioni's Five Dysfunctions model. Fans out five parallel analyst subagents, one per layer of the pyramid (Absence of Trust, Fear of Conflict, Lack of Commitment, Avoidance of Accountability, Inattention to Results), each assessing the team against that layer's tells with behavioral evidence, then synthesizes by locating the lowest broken layer, tracing how a cracked base surfaces as higher-layer symptoms, and prescribing interventions from the base upward into a detailed markdown report. Triggers include "five dysfunctions", "Lencioni", "why is my team dysfunctional", "team isn't delivering", "diagnose this team".
---

# five-dysfunctions-of-a-team

Runs Patrick Lencioni's Five Dysfunctions of a Team to diagnose why a team underperforms. The five dysfunctions are a hierarchy, not a list: Absence of Trust at the base, then Fear of Conflict, Lack of Commitment, Avoidance of Accountability, and Inattention to Results at the top. Each layer rests on the one below it, so find the lowest broken layer: everything above it inherits the break.

The pyramid, the hierarchy rule, each layer's tells and interventions, and the classic failure modes live in [references/five-dysfunctions.md](references/five-dysfunctions.md). Load that file before diagnosing and assess each layer against its tells exactly.

## When to use

The user has a real, named team that is conflict-avoidant, political, slow to decide, or not delivering, and wants to know why. The unit of analysis is one working team with a shared goal, not an individual, a whole organization, or a one-off project group. This skill pairs with **psychological-safety** (which examines the trust base in more depth) and **tuckman** (which places a team on its forming-storming-norming-performing arc); reach for those when the question is specifically about safety or developmental stage rather than the full dysfunction pyramid.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **TEAM** (required): the team to diagnose. Push for one defined working team. If the user describes an individual or a whole company, narrow it to one team with one or two questions first.
- **CONTEXT** (optional): observable behaviors and symptoms the user has noticed (guarded meetings, missed deadlines, silos, a leader carrying everything), the team's makeup and history, and the decision the diagnosis should inform. This focuses the evidence-gathering, not the layer definitions.

## Orchestration map

```
Stage 1  Intake          ── inline ───────────────────────────┐  (identify the team, gather observable behaviors)
Stage 2  Layer Analysis  ── 5 analyst subagents IN PARALLEL ──┐│  (each scores one layer against its tells, with evidence)
Stage 3  Synthesis       ── 1 agent, needs all 5 ────────────┘┘  (lowest broken layer, the cascade, ordered interventions)
```

## Stage 1: Intake (inline)

Confirm it is one working team, then assemble the raw material. Gather every observable behavior and symptom the user can give: what meetings look like, how decisions get made and unmade, who confronts whom, what slips, where silos sit, what the leader carries. Capture these as concrete behaviors, not labels. This is the evidence the analysts will score against; thin intake produces a thin diagnosis.

## Stage 2: Layer Analysis (PARALLEL)

Dispatch five analyst subagents at once, one per layer of the pyramid. Give each the shared framing plus its layer's tells and interventions from the reference file.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their assessment in real evidence.

**Shared framing (send to each analyst):**

> Assess one layer of Lencioni's Five Dysfunctions pyramid for this team: **[TEAM]**. Work only your assigned layer. Compare the team's behavior against your layer's specific tells (from the layer brief below), grounding each judgment in concrete behavioral evidence, what was actually observed or said, not impressions. Then return:
> - **Layer verdict**: is this dysfunction present? Score its severity (none / mild / moderate / severe).
> - **Tells observed**: which of your layer's tells show up, each with the specific behavior that evidences it.
> - **Tells absent**: which tells you checked for and did not find, so synthesis knows what was ruled out.
> - **Candidate interventions**: which of your layer's interventions fit what you found.
> - **Confidence**: high, medium, or low, lowered if behavioral evidence was thin or you were inferring.
>
> Do not judge the other layers or guess where the root cause sits; synthesis owns that. Stay inside your layer.
>
> Team behaviors and context: [CONTEXT]

Assign the five layers from the reference file: Absence of Trust, Fear of Conflict, Lack of Commitment, Avoidance of Accountability, and Inattention to Results. Collect all five structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five layer assessments into a single diagnosis. Respect the hierarchy; do not sum five scores.

1. **Locate the lowest broken layer.** Read the pyramid bottom to top. The first layer scored mild or worse is the binding constraint. This is where the diagnosis centers, regardless of which layer the user's complaint pointed at.
2. **Trace the cascade upward.** Explain how the cracked base surfaces as symptoms higher up: how absence of trust produces the conflict the conflict-analyst saw, how that starves commitment, and so on. Show which higher-layer "problems" are really the lower break showing through, so the team does not chase the wrong fix.
3. **Reconcile the surface complaint.** If the user named a symptom ("we need more accountability") that sits above the real break, say so plainly and explain why fixing it directly would fail without the layer beneath it.
4. **Prescribe from the base.** Draw the interventions for the lowest broken layer from the reference file. Be specific to what the analysts observed.
5. **Sequence the rebuild upward.** Lay out the order: stabilize the base layer, then the next, up the pyramid. Note what success at each layer looks like before moving up, because installing a higher layer's rituals on a missing foundation does not hold.

## Report structure

Write a thorough markdown report and save it to `five-dysfunctions-of-a-team-<team-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The team diagnosed, the context and surface complaint if given, the date, and a one-line note that the five dysfunctions are a hierarchy read bottom to top.
2. **Verdict.** The lowest broken layer and why it is the binding constraint, in a few sentences, with a summary table: each layer (in pyramid order, base first), its severity score, and confidence.
3. **The pyramid, layer by layer.** Each layer from the base up: its verdict, the tells observed with their behavioral evidence, the tells ruled out, and confidence.
4. **The cascade.** How the lowest break surfaces as higher-layer symptoms, and the reconciliation of the user's surface complaint with where the real break sits.
5. **Interventions and sequence.** What to do at the base layer first, then the ordered rebuild up the pyramid, with what success looks like at each step.
6. **Caveats.** The model is a lens, not a measurement; severity scores rest on the behaviors reported and a thin intake yields a thin diagnosis; it diagnoses team dynamics, not individual capability or fit; a clean diagnosis names the binding constraint, it does not by itself rebuild the team; and the hierarchy is a strong heuristic, not a law: occasionally a higher layer is independently broken and must be watched as the base is repaired.

## Principles

- **Hierarchy, not checklist.** The five stack. The diagnosis is the bottom-up read, not the five numbers.
- **Find the lowest break.** The lowest broken layer is the binding constraint. Everything above it inherits the crack. Start there, always.
- **Symptoms point down.** A high-layer complaint is usually a low-layer break showing through. Trace it down before treating it.
