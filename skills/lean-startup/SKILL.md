---
name: lean-startup
description: Use when the user wants to test a startup, product, or business idea under uncertainty using the Lean Startup method (Build-Measure-Learn, MVP, validated learning, pivot or persevere). Surfaces the leap-of-faith assumptions, ranks them by risk with parallel analysis, designs the smallest experiment with a pre-committed metric, and runs the loop toward a pivot-or-persevere decision. Triggers include "lean startup", "MVP", "build measure learn", "validate my idea", "value and growth hypothesis", "pivot or persevere".
---

# lean-startup

Tests a venture under uncertainty using the Lean Startup method: treat the idea as a set of untested hypotheses, run the smallest experiment on the riskiest one, measure real behavior, and decide whether to pivot or persevere. Progress is validated learning, not features shipped.

The core concepts (leap-of-faith assumptions, Build-Measure-Learn, MVP, actionable versus vanity metrics, pivot or persevere) live in [references/lean-startup.md](references/lean-startup.md). Load that file before facilitating.

## When to use

The user has a product or business idea facing real uncertainty about whether customers want it or whether it will grow, and wants to test it cheaply before committing. For designing the solution itself around user needs, Design Thinking fits upstream; this skill is about validating that the thing should exist and will work.

## Language

Facilitate and write the document in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **IDEA** (required): the product or business idea, and who it is for.
- **CONTEXT** (optional): stage, resources, what has been built or tried, and any evidence so far.

## How to facilitate

This skill runs one Build-Measure-Learn loop end to end, and sets up the next. Work through the steps with the user, recording everything in the experiment document.

1. **Surface the leap-of-faith assumptions.** Help the user write down what must be true for the venture to work, concrete and falsifiable, including the value hypothesis (customers get real value) and the growth hypothesis (the venture acquires customers and grows). Push vague beliefs into testable statements.

2. **Rank by risk (parallel).** Dispatch a few analyst subagents at once, each examining the assumption set through a different lens (for example: which assumption is most uncertain, which is most fatal if false, which has hidden sub-assumptions, what a skeptical investor would attack first). Tell each its final message is the return value: a ranked list with reasoning, not prose. Reconcile into the single riskiest assumption: the one most uncertain and most fatal if wrong. That is what the first experiment tests, not the easiest one.

3. **Design the smallest experiment.** With the user, define the MVP or test that produces evidence on the riskiest assumption (landing page, concierge or Wizard-of-Oz done manually, single feature, pre-sale), the specific customer behavior to observe, and the actionable metric with a pass-and-fail threshold committed before running. Reject vanity metrics. Build the least that answers the question.

4. **Build, Measure, Learn.** Help the user run the experiment, measure real behavior against the threshold, and state plainly what was learned about the assumption.

5. **Decide: pivot or persevere.** On the evidence, recommend persevere (the path holds, and what the next loop tests) or pivot (which assumption changes, what kind of pivot, and the new hypothesis the next loop tests). The decision rests on the pre-committed threshold, not on hope.

## Experiment document

Maintain a markdown document, saved to `lean-startup-<idea-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location:

1. **Header.** The idea, the customer, and the date.
2. **Leap-of-faith assumptions.** The list, with the value and growth hypotheses marked, each falsifiable.
3. **Riskiest assumption.** The one chosen to test first, and why it beat the others.
4. **Experiment design.** The MVP or test, the behavior observed, and the actionable metric with its pre-committed pass-and-fail threshold.
5. **Results and learning.** What customers actually did against the threshold, and what was learned.
6. **Decision.** Pivot or persevere, with the next hypothesis to test.
7. **Loop log.** Each cycle: hypothesis tested, result, decision.
8. **Caveats.** One experiment tests one assumption, not the whole venture; a passed test reduces risk, it does not prove success; and learning is only valid if the metric was actionable and the threshold was set in advance.

## Principles

- **Validated learning is the unit of progress.** Not features, not motion. What have you proven about customers.
- **Test the riskiest assumption first.** The one most uncertain and most fatal, not the most convenient.
- **MVP is a learning tool, not a small product.** Build the least that runs a full loop.
- **Actionable metrics and a pre-committed threshold.** Decide the pass-and-fail line before running, or the result will be rationalized.
- **Decide on evidence at a cadence.** Pivot or persevere is a disciplined call on data, not a mood.
