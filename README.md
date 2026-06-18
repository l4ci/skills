# Framewise

A collection of structured thinking and analysis frameworks, packaged as agent skills. Each skill lives in its own folder and is written to be **model- and harness-agnostic**, usable from Claude Code, Codex, Copilot CLI, Gemini CLI, or any agent runtime that can load a skill.

Most are business strategy, analysis, and management frameworks: SWOT, Porter's Five Forces, the Business Model Canvas, Hoshin Kanri, and so on. A few are general-purpose thinking and research tools, including [pre-mortem](skills/pre-mortem/), [mece-decomposition](skills/mece-decomposition/), [scqa-pyramid](skills/scqa-pyramid/), [storm-research](skills/storm-research/), and [ocean-personality-test](skills/ocean-personality-test/).

## Available skills

### Strategy and business analysis

#### Problem framing and structuring

| Skill | What it does |
|-------|--------------|
| [tosca-problem-definition](skills/tosca-problem-definition/) | Sharpens a fuzzy problem into a crisp, solvable problem statement using the TOSCA framework (Trouble, Owner, Success criteria, Constraints, Actors). A guided interview that challenges weak answers and stress-tests the framing with parallel critics. |
| [mece-decomposition](skills/mece-decomposition/) | Breaks a problem or metric into a MECE issue tree (no overlaps, no gaps). Generates competing top-level cuts in parallel, picks the sharpest, builds the tree, then audits it for mutual exclusivity and exhaustiveness with parallel checkers. |
| [scqa-pyramid](skills/scqa-pyramid/) | Structures a recommendation so the answer comes first, using SCQA and Minto's Pyramid Principle. Generates competing SCQA framings in parallel, picks the sharpest, builds the supporting pyramid, then audits its logic and key line with parallel checkers. The step that turns analysis into something a reader can follow. |

#### Positioning and environment

| Skill | What it does |
|-------|--------------|
| [swot-analysis](skills/swot-analysis/) | SWOT analysis anchored to an objective. Fans out four parallel analyst subagents (one per quadrant), prioritizes the factors, then crosses them into a TOWS strategy matrix with ranked recommendations. |
| [pestel-analysis](skills/pestel-analysis/) | PESTEL macro-environment scan. Fans out six parallel analyst subagents (Political, Economic, Social, Technological, Environmental, Legal), then prioritizes the forces by impact and certainty and draws implications. |
| [porters-five-forces](skills/porters-five-forces/) | Porter's Five Forces industry analysis (Branchenstrukturanalyse). Fans out five parallel analyst subagents, scores each force against its determinants with evidence, and synthesizes industry attractiveness and strategy. |
| [scenario-planning](skills/scenario-planning/) | Builds several plausible futures instead of one forecast. Gathers driving forces, picks the two critical uncertainties as axes, develops the four resulting scenarios with one parallel subagent each, then derives strategy that holds across them and the signposts to watch. |
| [blue-ocean-strategy](skills/blue-ocean-strategy/) | Blue Ocean Strategy and value innovation. Maps the industry's strategy canvas, then fans out four parallel subagents (Eliminate, Reduce, Raise, Create) to build a new value curve that lifts buyer value and cuts cost at once, and tests it for focus and divergence. |

#### Internal and organizational

| Skill | What it does |
|-------|--------------|
| [value-chain-analysis](skills/value-chain-analysis/) | Porter's Value Chain analysis. One parallel analyst per activity assesses cost and value versus competitors, then synthesizes the sources of advantage, the value leaks, and the linkages. |
| [mckinsey-7s](skills/mckinsey-7s/) | McKinsey 7-S organizational analysis. Fans out seven parallel analyst subagents (Strategy, Structure, Systems, Shared Values, Skills, Style, Staff), then runs an alignment analysis to find where the elements conflict and recommend fixes. |
| [digital-maturity-assessment](skills/digital-maturity-assessment/) | Scores digital maturity across seven dimensions on a five-level scale with parallel assessors, then maps the binding gaps and a sequenced roadmap toward a target. |
| [vrio-analysis](skills/vrio-analysis/) | Tests whether a firm's resources are a source of sustained advantage (Valuable, Rare, Costly to Imitate, Organized). One parallel analyst per resource runs the four gates with evidence, then synthesis names the few that yield durable advantage. The partner test to value-chain analysis. |

#### Growth and portfolio

| Skill | What it does |
|-------|--------------|
| [bcg-matrix](skills/bcg-matrix/) | BCG Growth-Share Matrix portfolio analysis. Places each business unit (Stars, Cash Cows, Question Marks, Dogs) with one parallel analyst per unit, then assesses portfolio cash-flow balance and reallocation. |
| [ansoff-matrix](skills/ansoff-matrix/) | Ansoff Matrix growth strategy. Fans out four parallel strategist subagents (Penetration, Market Development, Product Development, Diversification) to generate concrete options with risk, then sequences a prioritized growth path. |
| [three-horizons](skills/three-horizons/) | McKinsey Three Horizons model. Three parallel analysts place initiatives by maturity (core, emerging, options), then assess portfolio balance, pipeline gaps, and how each horizon should be funded and measured. |

#### Prioritization and risk

| Skill | What it does |
|-------|--------------|
| [impact-feasibility-matrix](skills/impact-feasibility-matrix/) | Prioritizes a list of options by impact and feasibility (the impact-effort matrix). Calibrates the axes, scores options in parallel, then sequences a plan of quick wins, major projects, fill-ins, and tasks to drop. |
| [weighted-decision-matrix](skills/weighted-decision-matrix/) | Chooses among options against multiple weighted criteria. Calibrates the criteria, weights, and scale first, scores each option in parallel, then computes weighted totals, ranks, and runs a sensitivity check. Generalizes the impact-feasibility matrix to many criteria. |
| [pre-mortem](skills/pre-mortem/) | Stress-tests a plan or decision before you commit. Fans out parallel failure-finder subagents across distinct risk lenses, scores the risks by likelihood and impact, and designs mitigations for the worst ones. |

### Process and innovation methods

#### Innovation and product

| Skill | What it does |
|-------|--------------|
| [design-thinking](skills/design-thinking/) | Facilitates the five Design Thinking modes (Empathize, Define, Ideate, Prototype, Test) as an iterative loop, with parallel idea generation during Ideate and a living design document. |
| [lean-startup](skills/lean-startup/) | Runs a Build-Measure-Learn loop: surfaces leap-of-faith assumptions, ranks them by risk in parallel, designs a minimum viable test with a pre-committed metric, and decides pivot or persevere. |
| [business-model-canvas](skills/business-model-canvas/) | Maps how a business creates, delivers, and captures value across the nine blocks of Osterwalder's Business Model Canvas. One parallel analyst per block, then a synthesis pass checks whether the blocks cohere and flags the riskiest assumptions. |

#### Process improvement

| Skill | What it does |
|-------|--------------|
| [six-sigma-dmaic](skills/six-sigma-dmaic/) | Guides a Six Sigma DMAIC cycle (Define, Measure, Analyze, Improve, Control) with phase gates, parallel root-cause hypotheses verified against data, and a project document. |
| [pdca-cycle](skills/pdca-cycle/) | Guides a lightweight PDCA loop (Plan, Do, Check, Act): plan a change with a prediction, try it small, check against the prediction, and adopt, adjust, or abandon, then loop. |

### Execution and change

#### Goals and measurement

| Skill | What it does |
|-------|--------------|
| [balanced-scorecard](skills/balanced-scorecard/) | Translates a strategy into objectives and measures across the four Balanced Scorecard perspectives (Financial, Customer, Internal Process, Learning and Growth). One parallel analyst per perspective, then a synthesis pass links them into a cause-and-effect strategy map. |
| [okr](skills/okr/) | Turns strategy into measurable goals with OKRs. Guides a drafting cycle (a qualitative objective, then three to five measurable key results), stress-tests the key results with parallel critics for outcome-versus-task, measurability, coverage, and ambition, and sets cadence and scoring. |
| [hoshin-kanri](skills/hoshin-kanri/) | Deploys a strategy into aligned action with Hoshin Kanri (policy deployment). Holds the vital few breakthrough objectives, fans out one strategist per annual objective to set priorities, targets, and owners, then builds the X-matrix, traces the golden thread, and sets the catchball and review cadence. |

#### Change management

| Skill | What it does |
|-------|--------------|
| [stakeholder-analysis](skills/stakeholder-analysis/) | Maps the people and groups behind a project or change on Mendelow's power-interest grid. One parallel analyst per stakeholder assesses power, interest, and stance, then a synthesis pass builds the engagement plan and the coalition-and-blocker map. |
| [kotter-change](skills/kotter-change/) | Leads an organizational change through Kotter's eight steps (urgency, coalition, vision, communication, removing barriers, short-term wins, sustaining, anchoring). A phased facilitator with a gate check per step and a living change plan. |
| [adkar](skills/adkar/) | Diagnoses the people side of a change with ADKAR (Awareness, Desire, Knowledge, Ability, Reinforcement). Five parallel subagents assess each element per affected group, then a synthesis pass finds the barrier point where change stalls and designs targeted interventions. |
| [force-field-analysis](skills/force-field-analysis/) | Lewin's force field analysis for a proposed change. Parallel finders hunt the driving and restraining forces across several lenses and score each, then synthesis builds the net field and finds the highest-leverage moves, favoring the weakening of restrainers. |

### Research

| Skill | What it does |
|-------|--------------|
| [storm-research](skills/storm-research/) | PhD-level research on a topic. Fans out five expert perspectives as parallel subagents, maps their contradictions, synthesizes a briefing, and peer-reviews it with confidence scores. Parallel replication of Stanford's STORM method. |

### Personal insight

| Skill | What it does |
|-------|--------------|
| [ocean-personality-test](skills/ocean-personality-test/) | Conducts the Big Five (OCEAN) personality test conversationally using the public-domain 50-item IPIP questionnaire, scores each dimension, and writes a detailed markdown report. |

## What's a skill?

A skill is a self-contained unit of reusable instructions an agent loads on demand. It tells the agent *how* to do something (a procedure, a discipline, a domain workflow) without hard-coding any one platform's tools or any specific model.

## Layout

```
framewise/
├── README.md
├── LICENSE
├── .claude-plugin/
│   └── plugin.json       # Claude Code plugin manifest
└── skills/
    └── <skill-name>/
        ├── SKILL.md          # the skill itself, loaded by the agent (required)
        ├── README.md         # human-facing overview, rendered on GitHub (optional)
        └── references/       # files the skill loads at runtime (optional)
```

One folder per skill under `skills/`, named after the skill (kebab-case). Three kinds of file can live in it, split by who reads them:

- **`SKILL.md`** (required) is for the agent. It is the procedure the runtime loads on demand.
- **`README.md`** (optional) is for humans. GitHub renders it when someone opens the folder, so put the what and why here.
- **`references/`** (optional) is also for the agent. It holds material the skill pulls in at runtime, such as prompt templates, scripts, or worked examples. It is not the place for human documentation.

Each `SKILL.md` carries YAML frontmatter:

```markdown
---
name: <skill-name>
description: <one line, when an agent should reach for this skill>
---

<the skill body: the procedure, in plain action language>
```

## Design principles

- **Harness-agnostic:** speak in actions ("read the file", "dispatch a subagent", "run the tests"), never in one runtime's tool names. Let each platform map actions to its own tools.
- **Model-agnostic:** no dependence on a specific model, context window, or vendor feature.
- **Self-contained:** everything the skill needs lives in its folder.
- **Single responsibility:** one skill, one job. Compose, don't bloat.

## Using a skill

This repo is a Claude Code plugin named **framewise**, and the same skills work standalone in any runtime that loads `SKILL.md` folders.

**Claude Code (as a plugin):**

```shell
/plugin marketplace add l4ci/framewise
/plugin install framewise@framewise
```

The skills are then namespaced, for example `/framewise:swot-analysis` or `/framewise:hoshin-kanri`.

**Standalone (any runtime):** copy a folder from `skills/` into your agent's skills directory, or point your runtime at `skills/`. Conventions vary by platform:

- **Claude Code:** drop a `skills/<name>/` folder under `~/.claude/skills/` and invoke via the skill mechanism.
- **Codex / Copilot CLI / Gemini CLI:** place under the platform's skills path; most auto-discover by folder.

Check your runtime's docs for the exact path.

## Contributing

New skill → new folder under `skills/` with a `SKILL.md`. Keep it harness-agnostic, keep it focused, keep supporting material inside the folder.

## License

[MIT](LICENSE)
