---
name: balanced-scorecard
description: 'Use when the user wants to translate a strategy into a balanced set of objectives and measures using the Balanced Scorecard, or asks to build KPIs and a strategy map from a stated strategy or vision. Fans out four parallel analyst subagents (one per perspective: Financial, Customer, Internal Process, Learning & Growth), each deriving objectives, measures, targets, and initiatives from the strategy, then synthesizes a strategy map linking them by cause and effect and prunes to the vital few measures, all into a detailed markdown report. Triggers include "balanced scorecard", "BSC", "Kaplan Norton", "strategy map", "KPIs from strategy", "performance measurement framework".'
---

# balanced-scorecard

Runs Kaplan and Norton's Balanced Scorecard to translate a strategy into objectives and measures across four perspectives so a business is steered by more than its financial numbers: Financial, Customer, Internal Process, and Learning & Growth. The four are linked by cause and effect: capabilities built in Learning & Growth drive better Internal Processes, which deliver the Customer value proposition, which produces Financial results.

The four perspectives, their guiding questions, the objective/measure/target/initiative structure, the strategy map and its cause-effect logic, and the leading-versus-lagging distinction live in [references/scorecard.md](references/scorecard.md). Load that file before analyzing and follow its structure exactly.

## When to use

The user has a strategy or vision and wants it made measurable: a set of objectives, KPIs, targets, and initiatives that tracks whether the strategy is being executed, not just whether last quarter's revenue held up. This is where the analysis skills hand off. A Porter's or 7-S diagnosis produces a strategic direction; the Balanced Scorecard turns that direction into objectives and measures someone can be held to. It is a companion to OKRs: the scorecard sets the durable perspectives and cause-effect logic, OKRs cycle the near-term targets within them. The unit is an organization or business unit with a stated strategy, not an industry.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework, the four perspectives, and the objective/measure/target/initiative structure keyed to it regardless of the output language.

## Inputs

- **ORGANIZATION** (required): the company or business unit the scorecard is for.
- **STRATEGY** (required): the strategy or vision being translated. The scorecard is only as good as the strategy it serves, so if this is vague ("grow the business", "be the best"), draw it out first with one or two questions: what is the value proposition, to which customers, and how does the organization mean to win. A scorecard built on a slogan measures nothing.
- **CONTEXT** (optional): the unit level (corporate, division, function), the time horizon for targets, and any existing measures the organization already tracks.

## Orchestration map

```
Stage 1  Perspective Analysis  ── 4 analyst subagents IN PARALLEL ──┐  (each derives objectives, measures, targets, initiatives)
Stage 2  Synthesis             ── 1 agent, needs all 4 ─────────────┘  (strategy map, trace to strategy, balance, prune)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground measures and targets in real figures and benchmarks where they can.

## Stage 1: Perspective Analysis (PARALLEL)

Dispatch four analyst subagents at once, one per perspective. Give each the shared framing plus its perspective's guiding question and example measures from the reference file.

**Shared framing (send to every analyst):**

> Translate this strategy into one perspective of a Balanced Scorecard for **[ORGANIZATION]**. The strategy is: **[STRATEGY]**. Your perspective answers a specific question (from the reference file). Work from the strategy down: what does it require of your perspective, and how would you know it is being delivered. Then return:
> - **Objectives**: the few (two to four) things this perspective must achieve for the strategy to work, each phrased as an outcome, not an activity
> - **Measures (KPIs)**: for each objective, one or two measures that track it, marked as leading (a driver you can act on now) or lagging (a result that confirms it later)
> - **Targets**: the level each measure must hit, and by when, grounded in real benchmarks where you can find them
> - **Initiatives**: the concrete actions or programs that would move each measure
> - **Rationale**: for each objective, the line from the strategy to it, and a note on what enables it from below or what it pays off above (your guess at the cause-effect links into other perspectives)
> - **Confidence**: high, medium, or low, lowered where the strategy was too vague to derive a clean objective or where targets are ungrounded
>
> Context: [CONTEXT]

Assign the four perspectives from the reference file: Financial, Customer, Internal Process, and Learning & Growth. Collect all four structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: Synthesis (SEQUENTIAL, needs all 4)

One agent merges the four perspective analyses into a single scorecard and the strategy map that ties it together:

1. **Build the strategy map.** Lay the objectives out across the four perspectives and draw the cause-effect chain bottom-up: which Learning & Growth objectives enable which Internal Process objectives, which deliver which Customer objectives, which produce which Financial objectives. The map is the heart of the scorecard; a list of objectives without the links is just a KPI dashboard.
2. **Trace every objective to the strategy.** Each objective must answer to the stated strategy. Drop or flag any that is generic best practice rather than something this strategy specifically requires.
3. **Check the balance.** Confirm the scorecard mixes leading and lagging indicators, not only financial lagging results, and that it spans short-term and long-term. An all-lagging scorecard tells you the score after the game is over.
4. **Prune to the vital few.** Cut to the measures that matter, not the measures that are easy to collect. Aim for a handful per perspective. Note what you cut and why.
5. **Flag broken links.** Surface objectives with no enabler below them (a Customer goal with no process or capability driving it) or no payoff above them (a process improvement that connects to no customer or financial outcome). These are either missing objectives or objectives that do not belong.

## Report structure

Write a thorough markdown report and save it to `balanced-scorecard-<org-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The organization and unit level, the strategy being translated, the date, and a one-line note on the framework.
2. **The strategy in one paragraph.** The strategy as the scorecard reads it, so the reader can judge whether the objectives actually serve it.
3. **Scorecard table.** A four-row table, one row per perspective, columns for Objectives, Measures (marked leading or lagging), Targets, and Initiatives. This is the scorecard itself.
4. **Strategy map.** The cause-effect chain, drawn bottom-up from Learning & Growth to Financial, showing which objectives drive which. Use an ascii diagram or a structured list of links (X enables Y enables Z) so the logic is legible.
5. **Per-perspective sections (four).** For each perspective: its guiding question, its objectives with rationale tying each to the strategy, the measures and targets, and the initiatives. Ground each in the organization's specifics, not textbook examples.
6. **Balance and the vital few.** How leading and lagging are balanced, what was pruned and why, and the total measure count per perspective.
7. **Broken links and gaps.** Objectives with no enabler below or no payoff above, and what they imply (a missing objective, or one to drop).
8. **Caveats.** The scorecard is only as sound as the strategy it translates; targets grounded in thin data are flagged as such; the map shows hypothesized cause and effect, not proven causation, and should be revisited as evidence comes in.

## Principles

- **Strategy first, measures second.** Every objective traces to the stated strategy. A measure that serves no objective, and an objective that serves no strategy, do not belong.
- **The map is the point.** The cause-effect links between perspectives are what make it a scorecard rather than a dashboard. Build the map; do not just list KPIs.
- **Balance leading and lagging.** Financial results are lagging; they confirm the past. Pair them with leading drivers in the other perspectives that you can still act on.
- **The vital few.** Choose the measures that matter, not the ones that are easy to collect. Fewer, sharper measures beat a long list nobody reads.
