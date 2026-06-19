---
name: blue-ocean-strategy
description: Use when the user wants a Blue Ocean Strategy analysis of a business or product, or asks how to stop competing on the same factors as everyone else and create uncontested market space. Maps the industry's strategy canvas, then fans out four parallel subagents (eliminate, reduce, raise, create) to build a new value curve through value innovation, then synthesizes the blue-ocean move and its risks into a detailed markdown report. Triggers include "Blue Ocean", "value innovation", "ERRC", "four actions framework", "strategy canvas", "uncontested market", "stop competing on the same factors".
---

# blue-ocean-strategy

Runs W. Chan Kim and Renée Mauborgne's Blue Ocean Strategy to move a business out of crowded competition ("red ocean") into uncontested market space ("blue ocean"). The mechanism is value innovation: pursuing differentiation and low cost at the same time rather than trading one for the other. The skill maps how everyone currently competes, then rebuilds the offering with the four actions framework so the new value curve both lifts buyer value and cuts cost.

Value innovation, the strategy canvas, the ERRC four-actions grid, the six paths, and the focus/divergence/tagline test live in [references/blue-ocean.md](references/blue-ocean.md). Load that file before analyzing and work each tool exactly as defined there.

## When to use

The user wants to change the basis of competition rather than win on the existing one: when an industry has converged on the same factors and competes on price, when a new offering needs a position rivals are not already fighting over, or when the question is "how do we stop competing head-to-head". The unit of analysis is a strategic move (an offering and the market it could create), not an industry or a company as a whole.

It complements the structural frameworks rather than repeating them. Porter's Five Forces and SWOT analyze the game as it is played today; Blue Ocean is the move that changes which factors the game is played on. Run it after a five-forces or SWOT read when the structure looks unattractive and the answer is to reshape the market, not to fight harder inside it.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework, the ERRC grid, and the three tests keyed to it regardless of the output language.

## Inputs

- **BUSINESS** (required): the company or product and the industry it competes in. Push for a defined offering and market, since "we sell software" is too broad to draw a value curve for. If the user is vague, narrow it with one or two questions first.
- **CONTEXT** (optional): current positioning, the main competitors and any substitutes, and the decision the analysis should inform (a launch, a repositioning, a new line). This shapes the canvas and the move, not the framework.

## Orchestration map

```
Stage 1  Strategy Canvas   ── 1 agent (or quick fan-out by competitor) ──┐  (factors + how players score)
Stage 2  Four Actions      ── 4 subagents IN PARALLEL ───────────────────┤  (eliminate / reduce / raise / create)
Stage 3  Synthesis         ── 1 agent, needs all 4 ──────────────────────┘  (new value curve, tests, the move, risks)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their work in real offerings, prices, and competitor moves.

## Stage 1: Strategy Canvas

Map the current state of play before changing it. One agent assembles the canvas; if the field is crowded, fan out a quick pass by competitor and merge.

Identify the **competing factors**: the buyer-valued attributes the industry invests in and competes on (for example "ease of selection", "ambience", "speed of service"), not the firm's internal features. Then score how the main players and any substitutes offer on each factor, low to high, producing a **value curve** per player.

Read the canvas: where do the leading curves converge? Convergent curves are the signature of a red ocean and mark exactly the factors a blue-ocean move should question. Carry the factor list and the curves forward; the four actions operate on them.

## Stage 2: Four Actions (PARALLEL)

Dispatch four subagents at once, one per action of the ERRC grid. Each works on the factor list and curves from Stage 1 and proposes concrete moves with rationale and effect.

**Shared framing (send to every action agent):**

> We are building a new value curve for this offering: **[BUSINESS]**, to escape competing on the same factors as rivals. The industry's current competing factors and the players' value curves are: **[STAGE 1 CANVAS]**. You own one of the four actions. Propose concrete moves for your action, each tied to a specific competing factor (or, for Create, a factor the industry has never offered). For each move return its rationale and its effect on cost and on buyer value. Then return:
> - **Moves**: each as a factor, the action on it, the rationale, the cost effect, and the buyer-value effect
> - **Top moves**: the one or two that most change the offering, and why
> - **New-demand note**: for Create especially, which non-customers or neglected buyers this could open (see the six paths in the reference)
> - **Confidence**: high, medium, or low, lowered where evidence on rivals or buyers was thin
>
> Context: [CONTEXT]

Assign the four actions from the reference file:
- **Eliminate**: which factors the industry takes for granted should be removed entirely (cuts cost).
- **Reduce**: which factors should be reduced well below the industry standard, where the industry over-serves (cuts cost).
- **Raise**: which factors should be raised well above the industry standard, removing compromises buyers accept (adds cost, lifts value).
- **Create**: which factors should be created that the industry has never offered (adds cost, opens new demand).

Optionally also dispatch six-paths explorers (alternative industries, strategic groups, chain of buyers, complementary offerings, functional/emotional appeal, trends over time) to feed the Create and Eliminate agents. Collect all four action results before continuing. Re-dispatch any agent that fails rather than synthesizing with a gap; a missing Eliminate or Reduce result would hide the cost side and let a one-sided move through.

## Stage 3: Synthesis (SEQUENTIAL, needs all 4)

One agent assembles the four actions into the blue-ocean move and tests it:

1. **Assemble the new value curve.** Apply the eliminate, reduce, raise, and create moves to the Stage 1 factor list, adding the new created factors. Plot the resulting curve against the rivals' curves on the same canvas.
2. **Test for value innovation.** Does the move both cut cost and lift buyer value? Confirm that Eliminate and Reduce actually fund Raise and Create. A curve that only rises is differentiation, not value innovation; one that only falls is discounting. Either fails.
3. **Test focus, divergence, and tagline.** Is the curve focused on a few factors rather than high on all? Does it visibly diverge from the rivals' curves? Can you write one true, sharp tagline for it? If the tagline will not come, the curve is probably not focused, send it back.
4. **The blue-ocean move.** State the move plainly: what the offering becomes, which buyers and non-customers it opens, and why rivals are not already there.
5. **Risks.** Where the move could fail: new demand that will not pay for the added value, eliminated factors that buyers turn out to need, rivals who can imitate the curve quickly, or a cost structure that the volume does not support. Tie each risk to the move that creates it.

## Report structure

Write a thorough markdown report and save it to `blue-ocean-strategy-<business-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The business and industry analyzed, the current positioning if given, the date, and a one-line note on the framework.
2. **Verdict.** The blue-ocean move in a few sentences and the proposed tagline.
3. **Strategy canvas.** The competing factors, the players' value curves, and where they converge. Include a compact visual (for example a level per factor per player) so the convergence is scannable.
4. **The ERRC grid.** A four-cell grid (Eliminate, Reduce, Raise, Create) with the moves under each, each noting its cost and buyer-value effect.
5. **The new value curve.** The resulting curve plotted against rivals, with a visual on the same factor axis as the canvas, so the divergence is visible.
6. **Value-innovation test.** Confirmation that the move cuts cost and lifts value, and that it passes focus, divergence, and tagline.
7. **The move and new demand.** What the offering becomes and which buyers and non-customers it opens.
8. **Risks.** Concrete failure modes tied to the moves that create them.
9. **Caveats.** The framework finds the move, not the execution; value curves are informed judgment, not measurement; a blue ocean attracts imitators and eventually reddens; and the move still has to survive the cost and demand realities the canvas cannot prove.

## Principles

- **Both sides, always.** Value innovation is differentiation and low cost together. A move that only lifts value or only cuts cost is not a blue ocean; synthesis must confirm Eliminate and Reduce fund Raise and Create.
- **Buyer-valued factors, not internal features.** The canvas axis is what buyers value, not the firm's specs. A canvas built from features maps the company, not the market, and every later step inherits the error.
- **Divergence or it is red.** If the new curve tracks the rivals' curves, there is no blue ocean. The Eliminate and Create moves are where divergence comes from; weight them.
- **The tagline is a test.** A focused, divergent strategy yields one sharp line. If the line will not come, the curve is muddled, fix the curve, not the wording.
