---
name: tosca-problem-definition
description: Use when the user has a fuzzy or broad problem and needs to sharpen it into a crisp, solvable problem statement before analyzing or solving it. Walks through the TOSCA framework (Trouble, Owner, Success criteria, Constraints, Actors) as a guided interview, challenges weak answers, stress-tests the framing with parallel critic subagents, and writes a problem-definition brief. Triggers include "TOSCA", "define the problem", "frame this problem", "problem statement", "I'm not sure what the real problem is", "Bulletproof Problem Solving".
---

# tosca-problem-definition

Turns a vague problem into a crisp, solvable one using TOSCA (Trouble, Owner, Success criteria, Constraints, Actors), the problem-definition framework from *Bulletproof Problem Solving* (Conn and McLean). It catches the failure of solving the wrong problem precisely. This skill does the framing, not the solving.

The five elements, their sharp questions, their pitfalls, and the marks of a good problem statement live in [references/tosca.md](references/tosca.md). Load that file before starting.

## When to use

The user has a problem that is broad, fuzzy, or possibly mis-stated, and wants it sharpened before committing effort. It pairs naturally upstream of analysis or solving work: run this first, then hand the problem statement to a solving method (issue tree, hypotheses, the strategy skills in this collection). If the problem is already crisp and owned, skip straight to solving.

## Language

Conduct the interview and write the brief in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## How to run

This is primarily an interview, with one parallel stress-test before the brief is finalized.

1. **Set up.** Briefly explain that TOSCA sharpens the problem before solving it, and that you will ask focused questions on each of the five elements. Capture the user's problem in their own words first, as the raw starting point.

2. **Elicit the five elements (T, O, S, C, A), in order.** For each, ask the sharp questions from the reference file, one focused question at a time rather than a wall of them. Challenge weak answers rather than accepting them:
   - If the Trouble is a symptom, push for the underlying cause. If it hides a solution ("we need X"), strip the solution out and recover the real need.
   - If the Owner cannot actually act, find who can.
   - If Success criteria are vague, force a metric, a target, and a date, and name any trade-offs.
   - For each Constraint, ask whether it is a hard boundary or an untested assumption, and mark which.
   - For Actors, capture each stakeholder's interest, not just their name, and probe for anyone who could block.
   Reflect each answer back tightened, and confirm before moving on.

3. **Stress-test the framing (PARALLEL).** Once a draft TOSCA exists, dispatch three critic subagents at once, each given the full draft and one lens. Tell each its final message is the return value: a list of specific challenges, not prose.
   - **Critic A, root and solution:** Is the Trouble the root problem or a symptom? Is a solution smuggled into the problem statement?
   - **Critic B, owner and success:** Can the named Owner actually act? Are the Success criteria measurable, time-bound, and free of unnamed conflicts?
   - **Critic C, constraints and actors:** Which Constraints are assumptions over-narrowing the solution space? Which Actors are missing, especially blockers?
   Bring the strongest challenges back to the user and resolve them.

4. **Synthesize the brief.** Write the crisp problem statement (see the reference file's criteria) plus the structured TOSCA brief, and save it.

## Report structure

Write the brief as markdown and save it to `tosca-<problem-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** A short title and the date.
2. **Problem statement.** The single crisp statement, ideally phrased as the question the owner needs answered. This is the headline deliverable; it must be specific, measurable, time-bound, decision-oriented, answerable, and free of an embedded solution.
3. **TOSCA brief.** One section or table row per element:
   - **Trouble:** the root problem and why it matters now.
   - **Owner:** who decides and acts, and what they value.
   - **Success criteria:** the metrics, targets, deadline, and trade-offs.
   - **Constraints:** each one marked real or assumed.
   - **Actors:** each with their interest and whether they can block.
4. **Open questions.** What is still unknown and must be resolved to act, flagged honestly rather than papered over.
5. **Stress-test notes.** The framing challenges raised and how each was resolved or left open.
6. **Suggested next step.** How to move from this definition into solving (for example an issue tree off the problem statement, or which analysis to run next).
7. **Caveats.** TOSCA frames the problem; it does not solve it. A brief is only as good as the owner's honesty about constraints and success, and the framing should be revisited if those change.

## Principles

- **Frame, do not solve.** The deliverable is a sharp problem, not a solution. If the user pushes to solve, capture the impulse as a hypothesis to test later and return to framing.
- **A problem needs an owner.** If no one owns it or can act on it, say so; framing it further is wasted effort.
- **The value is in the pushback, not the form-filling.** Challenge weak answers; do not just collect them.
