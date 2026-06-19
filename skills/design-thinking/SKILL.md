---
name: design-thinking
description: Use when the user wants to run a human-centered innovation process to design a product, service, feature, or experience, using Design Thinking (Empathize, Define, Ideate, Prototype, Test). Facilitates the five modes as an iterative loop, using parallel idea generation during Ideate, and keeps a living design document. Triggers include "design thinking", "human-centered design", "d.school process", "empathize define ideate", "How Might We", "design a solution for users".
---

# design-thinking

Facilitates a human-centered innovation process through the five d.school Design Thinking modes. It is a loop, not a checklist: guide the work mode by mode, keep a living design document, and send insights back to the right mode rather than marching straight through.

The five modes, how to use them, and the pitfalls live in [references/design-thinking.md](references/design-thinking.md). Load that file before facilitating.

## When to use

The user wants to design or redesign a product, service, feature, or experience around real user needs, especially when the right problem is not yet clear. For sharpening an already-clear problem statement, problem-framing methods are tighter; for testing a business hypothesis cheaply, Lean Startup fits better. These compose: Design Thinking can feed a Lean Startup experiment.

## Language

Facilitate and write the document in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **CHALLENGE** (required): the design challenge or area, and who it is for (the intended users).
- **CONTEXT** (optional): what is known already, constraints, and any prior research or attempts.

## How to facilitate

This is a facilitated loop. Work one mode at a time, confirm with the user before moving on, and record everything in the design document. Name the current mode at each step.

1. **Empathize.** Establish what is actually known about the users versus assumed. If real user research exists, synthesize it; if not, help the user plan interviews or observation, and capture what users say, do, think, and feel. Resist jumping to solutions. Flag assumptions as assumptions.

2. **Define.** Synthesize the empathy work into a human-centered point-of-view ("[user] needs [need] because [insight]") and a small set of "How Might We" questions that open the solution space without prescribing an answer. Confirm the framing with the user before ideating.

3. **Ideate (parallel divergence).** Diverge hard before converging. Dispatch several idea-generator subagents at once, each given the How Might We questions and a different ideation lens or technique (for example: analogous domains, extreme users, opposite-of-obvious, constraint removal, existing-tech recombination). Each returns a batch of distinct ideas. Tell each its final message is the return value: a list of ideas, not prose. Then converge with the user: cluster the pooled ideas, remove duplicates, and select a few to prototype against the user need.

4. **Prototype.** For each selected idea, help design the cheapest prototype that answers the open question (sketch, storyboard, paper, clickable mockup, fake door). Specify what each prototype is meant to learn, and keep it deliberately rough.

5. **Test.** Help design how to put the prototype in front of real users to seek disconfirming feedback, not applause: what to observe, what to ask, what would count as the idea failing. Capture results.

6. **Loop.** Decide with the user which mode the test results send the work back to: refine the prototype, reframe the Define, or return to Empathize. Record the decision and continue. Progress is learning, not stage completion.

## Design document

Maintain a markdown document, saved to `design-thinking-<challenge-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location, updated as the loop runs:

1. **Header.** The challenge, the intended users, and the date.
2. **Empathy.** User needs and insights, with what is evidence versus assumption.
3. **Point-of-view and How Might We.** The framed problem and the opening questions.
4. **Ideas.** The diverged set and the selected few, with why they were chosen.
5. **Prototypes.** Each prototype, what it is meant to learn, and how rough it is.
6. **Tests and learnings.** What was put in front of users, what came back, and what it disconfirmed.
7. **Loop log.** Each iteration: what was learned and which mode the work returned to.
8. **Caveats.** Design Thinking surfaces desirable solutions; viability and feasibility still need separate testing. Insights are only as good as the realness of the user contact behind them.

## Principles

- **User first, always.** Every mode anchors to a real person's need. Drift toward the solution is the main failure.
- **Cheap and tangible early.** Prototype and test sooner than comfortable. Learning beats planning.
- **Seek disconfirmation.** Testing is for finding what is wrong while it is cheap, not for validation.
