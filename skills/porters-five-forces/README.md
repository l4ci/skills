# porters-five-forces

Runs a Porter's Five Forces analysis (Branchenstrukturanalyse) to assess how attractive an industry is and where its profits can be sustained or competed away. The framework, from Michael Porter (Harvard Business Review, 1979), reads industry profit potential through five forces: threat of new entrants, bargaining power of suppliers, bargaining power of buyers, threat of substitutes, and competitive rivalry. The stronger the forces, the thinner the profit an average competitor can hold.

This skill runs the analysis in parallel. Five analyst subagents each take one force, work through its standard determinants with real evidence, and score its intensity from 1 to 5. A synthesis pass then weighs the forces (not averages them), names the one or two that dominate, locates where the profit pool sits, and draws strategic implications. The output is a saved markdown report with a per-force breakdown, a verdict on attractiveness, and clear caveats.

## Starting

**You provide:** the industry to analyze (a defined product or service in a defined geography), and optionally the firm's position and the decision it informs. Something like "Run a Five Forces on the UK meal-kit industry".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the forces, their determinants, and the scoring rubric are in [references/forces.md](references/forces.md).
