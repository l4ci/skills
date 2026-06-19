---
name: tuckman
description: 'Use when the user wants to diagnose a team''s stage of development and what it needs to advance, or asks why a team is stuck, conflicted, or not yet performing. Fans out five parallel assessor subagents (one per stage: Forming, Storming, Norming, Performing, Adjourning), each scoring how well the team''s observable behaviors match that stage with evidence and noting regression signals, then synthesizes the current stage, the matching leadership focus, the concrete moves to advance, and what is blocking the transition into a detailed markdown report. Triggers include "Tuckman", "stages of team development", "forming storming norming performing", "what stage is my team at", "why is my team stuck".'
---

# tuckman

Runs Bruce Tuckman's stages of group development (Forming, Storming, Norming, Performing, Adjourning) to locate where a team sits today and match support to the actual stage. It catches the failure of expecting Performing prematurely or skipping Storming, which stalls teams.

The five stages, their behaviors, team mood, the leadership focus each needs, how to advance, regression, and the pitfalls live in [references/tuckman.md](references/tuckman.md). Load that file before diagnosing and key every assessment to its markers exactly.

## When to use

The user has a real team and wants to know what stage it is at and what would help it advance: a new team, a team that just changed shape, a team stuck in conflict, an onboarding situation, or a team trying to mature. The unit is one team's developmental stage, not its interpersonal dysfunctions and not its sense of safety. For the five behaviors that break a team's results, reach for five-dysfunctions-of-a-team; for whether members feel safe to speak up, reach for psychological-safety. Tuckman pairs with both but answers a different question: where is this team in its development, and what does it need next.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **TEAM** (required): the specific team to diagnose. Push for one defined team. If several teams or a whole department are named, narrow to one first.
- **CONTEXT** (optional): tenure, recent changes (new members, new leader, new goal, reorg), how meetings run, how conflict surfaces or hides, how decisions get made, and the outcome the user wants. This shapes the regression check and the framing of the moves to advance, not the stage markers themselves.

## Orchestration map

```
Stage 1  Observe          ── 1 agent inline ───────────────────┐  (identify the team, gather behaviors and history)
Stage 2  Stage Assessment ── 5 assessor subagents IN PARALLEL ──┤  (each scores the team against one stage's markers)
Stage 3  Synthesis        ── 1 agent, needs all 5 ─────────────┘  (current stage, regression, leadership, moves, blocker)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their assessment in real evidence.

## Stage 1: Observe (inline)

Before fanning out, establish the team and the observable record. Identify the one team in scope. Gather what can be observed: tenure and how the team came together, recent changes to membership, leadership, or goals, how meetings and decisions go, and how conflict surfaces or is avoided. If the picture is thin, ask one or two targeted questions rather than guessing. Pass this record to every assessor as shared evidence.

## Stage 2: Stage Assessment (PARALLEL)

Dispatch five assessor subagents at once, one per stage. Give each the shared framing plus its stage's markers from the reference file.

**Shared framing (send to each assessor):**

> Assess how well this team matches one stage of Tuckman's model: **[STAGE]** for **[TEAM]**. Work against the stage's markers in the reference file (behaviors, team mood, what would justify this label), grounding each judgment in observable behavior (how meetings run, how conflict surfaces or hides, how decisions get made, tenure, recent changes) rather than how the team describes itself. Then return:
> - **Match score** (1 to 5): how well the team's behaviors fit this stage
> - **Evidence**: the specific observed behaviors that support or undercut the match, each tied to a marker
> - **Counter-evidence**: what does not fit this stage
> - **Regression signal**: any sign the team has dropped back into this stage after a change in membership, leadership, or goals
> - **Confidence**: high, medium, or low, lowered if observation was thin or secondhand
>
> Observed record: [Stage 1 output]. Context: [CONTEXT]

Assign the five stages from the reference file: Forming, Storming, Norming, Performing, Adjourning. Collect all five structured results before continuing. Re-dispatch any assessor that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five assessments into a diagnosis, locating the stage and prescribing the matching support rather than restating the scores:

1. **Current stage.** Which stage the team is actually at, weighing match scores against evidence, not just the highest number. A conflict-avoidant team that scores high on Norming because it is quiet is likely stalled before Storming, not past it; say so.
2. **Regression.** Whether a recent change in membership, leadership, or goals has dropped the team back a stage. If so, name the trigger and the stage it fell to, and diagnose from there.
3. **Leadership focus.** The leadership style the current stage needs, drawn from the reference file: direct for Forming, coach for Storming, facilitate for Norming, delegate for Performing, close well for Adjourning. Name any mismatch between the current leadership and what the stage needs.
4. **Moves to advance.** Concrete actions to meet the bar for the next stage, tied to the team's actual evidence, not generic advice.
5. **The blocker.** What is preventing the transition. Watch especially for a Storming stall: a team stuck in conflict or, worse, one avoiding it. Name the one thing most in the way.

## Report structure

Write a thorough markdown report and save it to `tuckman-<team-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The team diagnosed, the context and recent changes if given, the date, and a one-line note on the framework and that a stage is a diagnosis at a moment, not a fixed trait.
2. **Verdict.** The current stage and the single most important move, in a few sentences, with a summary table: each stage, its match score, and confidence. Note any regression up front.
3. **Stage assessment.** The five stages in order, each with its match score, the evidence and counter-evidence, and any regression signal, so the diagnosis is scannable.
4. **Diagnosis.** Current stage, regression, the leadership focus the stage needs and any mismatch, the concrete moves to advance, and the blocker told as one read on where the team is and why.
5. **Caveats.** Tuckman is a lens, not a measurement; stages are not strictly linear and a team can sit between two or regress; the diagnosis rests on observed behavior at a moment and will shift as the team and its goals change; locating a stage tells you what support fits, not how long advancing will take.

## Principles

- **Locate before you treat.** The wrong leadership style at the wrong stage stalls a team faster than no diagnosis at all.
- **Storming is the work, not a detour.** A team that never storms has not yet become a team; a quiet team is not automatically a mature one.
- **Evidence over self-image.** Surface calm is not cohesion.
