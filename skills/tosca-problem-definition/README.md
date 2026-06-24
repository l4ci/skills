# tosca-problem-definition

## What this is

TOSCA is a checklist for defining a problem before anyone tries to solve it. The letters stand for Trouble, Owner, Success criteria, Constraints, and Actors: the felt pain and why it matters now, the decision-maker who will act on the answer, what a good outcome looks like in measurable terms, the real boundaries the solution must fit inside, and the stakeholders who affect or are affected by it. The framework comes from the McKinsey-rooted approach in *Bulletproof Problem Solving* (Charles Conn and Robert McLean, 2018). Its premise is that a well-defined problem is half-solved, and that most failed analysis traces back to solving the wrong problem precisely.

The five elements, their sharp questions, their pitfalls, and the marks of a good problem statement are in [references/tosca.md](references/tosca.md).

## What it does

The skill runs as a guided interview rather than a parallel analysis. It walks through the five elements in order with focused questions and challenges weak answers: a symptom gets pushed to its root, a solution hiding inside the problem gets stripped out, vague success criteria are forced into a metric and a date, and each constraint is marked real or merely assumed. Once a draft exists, three critic subagents stress-test the framing in parallel, each on one lens (root and solution, owner and success, constraints and actors). The output is a saved markdown brief with one crisp problem statement and the structured TOSCA behind it.

One rule holds throughout: this skill frames the problem, it does not solve it. If you push to solve, the impulse gets captured as a hypothesis to test later and the work returns to framing.

## When to use it

Reach for TOSCA when a problem is broad, fuzzy, or possibly mis-stated and you want it sharpened before committing effort. It runs upstream of the analysis and solving skills here, so the brief it produces hands off cleanly to the next step:

- To break the defined problem into a clean issue tree, use [mece-decomposition](../mece-decomposition/).
- To surface the load-bearing assumptions hiding in the framing, use [key-assumptions-check](../key-assumptions-check/).
- To structure the eventual answer for a reader, answer first, use [scqa-pyramid](../scqa-pyramid/).

## How to get started

**You provide:** nothing structured, just the fuzzy problem in your own words, and the skill interviews you through the five TOSCA elements. Something like "help me frame this problem with TOSCA."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md).
