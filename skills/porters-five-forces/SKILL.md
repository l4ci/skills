---
name: porters-five-forces
description: Use when the user wants a Porter's Five Forces analysis of an industry or market, or asks to assess an industry's competitive structure, attractiveness, or profit potential. Fans out five parallel analyst subagents (one per force), each scoring its force against the standard determinants with real evidence, then synthesizes overall industry attractiveness and strategic implications into a detailed markdown report. Triggers include "Five Forces", "Porter analysis", "how attractive is this industry", "competitive structure of X".
---

# porters-five-forces

Michael Porter's Five Forces assesses an industry's structure and profit potential: the stronger the forces, the lower the profit an average competitor can sustain. It corrects the mistake of judging an industry by its growth or hype instead of the structural forces that actually set its returns.

The five forces, their determinants, and the 1-to-5 scoring rubric live in [references/forces.md](references/forces.md). Load that file before analyzing and score each force against its determinants exactly.

## When to use

The user wants to understand the competitive structure or attractiveness of an industry or market, evaluate entering or exiting one, or ground a strategy in industry structure. The unit of analysis is an industry, not a single company. If the user names a company, analyze the industry that company competes in, then translate the findings into implications for that company.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework and scoring keyed to it regardless of the output language.

## Inputs

- **INDUSTRY** (required): the market to analyze. Push for a defined product or service in a defined geography, since "the software industry" is too broad to score. If the user is vague, narrow it with one or two questions first.
- **CONTEXT** (optional): the firm's position in the industry (incumbent, entrant, supplier, buyer), the time horizon, and the decision the analysis should inform. This shapes the strategic implications, not the force scores.

## Orchestration map

```
Stage 1  Force Analysis   ── 5 analyst subagents IN PARALLEL ──┐  (each scores one force with evidence)
Stage 2  Synthesis        ── 1 agent, needs all 5 ────────────┘  (attractiveness, dominant forces, strategy)
```

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground scores in real figures.

## Stage 1: Force Analysis (PARALLEL)

Dispatch five analyst subagents at once, one per force. Give each the shared framing plus its force's determinant checklist from the reference file.

**Shared framing (send to every analyst):**

> Analyze one of Porter's Five Forces for this industry: **[INDUSTRY]**. Work through each determinant for your assigned force, judging whether it pushes the force up or down, with real evidence (concentration, switching costs, growth rates, named players or substitutes) where you can find it. Then return:
> - **Intensity score** (1 to 5) with a one-paragraph justification
> - **Determinant assessment**: each determinant, its direction (raises or lowers the force), and the evidence
> - **Key drivers**: the two or three determinants that most decide this force
> - **Trend**: is the force strengthening or weakening over the relevant horizon, and why
> - **Confidence**: high, medium, or low, lowered if evidence was thin or unavailable
>
> Context: [CONTEXT]

Assign the five forces from the reference file: new entrants, supplier power, buyer power, substitutes, and competitive rivalry. Collect all five structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 2: Synthesis (SEQUENTIAL, needs all 5)

One agent merges the five force analyses into the strategic picture:

1. **Overall structure and attractiveness.** Combine the five scores into a read on profit potential. This is not a simple average: name which forces dominate and why. An industry with one severe force can be unattractive even if the other four are mild.
2. **The dominant forces.** Which one or two forces most shape profitability here, and through which determinants. This is where strategy gets its leverage.
3. **Where the profit pool sits.** Given who holds power (powerful suppliers or buyers capture value), where in the value chain does profit accumulate, and who is squeezed.
4. **Strategic implications.** Tied to the CONTEXT: how should the firm position to defend against or neutralize the strongest forces, which forces could it reshape, and what would change the verdict on entering or exiting. For an incumbent, how to build barriers; for an entrant, where the structure is soft.
5. **Dynamics and the sixth force.** How the structure is trending, and whether complementors or government materially shape this industry beyond the five forces (see the reference file).

## Report structure

Write a thorough markdown report and save it to `porters-five-forces-<industry-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The industry and geography analyzed, the firm's position if given, the date, and a one-line note on the framework and its snapshot nature.
2. **Verdict.** Overall industry attractiveness in a few sentences, with a summary table: each force, its 1-to-5 score, intensity label, and confidence. Include a compact visual (for example a star or bar per force) so the profile is scannable.
3. **Per-force sections (five).** For each force: the score and key drivers, the determinant assessment, the evidence, and the trend. Ground each in the industry's specifics, not textbook definitions.
4. **Synthesis.** The dominant forces, where the profit pool sits, and what the structure means for returns.
5. **Strategic implications.** Concrete moves tied to the context: barriers to build, forces to neutralize, positions to take or avoid.
6. **Dynamics and beyond the five forces.** Where the structure is heading; complementors and government where relevant.
7. **Caveats.** The framework is a structural snapshot, not a forecast; it underweights dynamics, complementors, and ecosystems; scores are informed judgment, not precise measurement; and industry structure explains average profitability, not the position of any single well-run firm.

## Principles

- **Industry, not company.** Score the structure of the market. Keep firm-specific strengths in the strategic-implications section, not in the force scores.
- **Determinant-driven.** Every force score must trace to its determinants with evidence. A bare "rivalry is high" with no drivers is not an analysis.
- **Evidence or honesty.** Use real figures where retrieval allows. Where data is missing, say so and lower confidence rather than inventing numbers.
- **Not an average.** Synthesis weighs the forces, it does not mean them. The binding constraint on profit is usually one or two forces, not the arithmetic of all five.
