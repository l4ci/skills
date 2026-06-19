# Latticework

> *"You've got to have models in your head and array your experience — both vicarious and direct — on this latticework of models."* — Charlie Munger

The name comes from Munger's idea: no single framework explains much on its own, but held together they compound into judgment. This repo is that latticework — one model per skill, most useful when you reach for several at once.

A collection of structured thinking and analysis frameworks, packaged as agent skills. Each skill lives in its own folder and is written to be **model- and harness-agnostic**, usable from Claude Code, Codex, Copilot CLI, Gemini CLI, or any agent runtime that can load a skill.

Most are business strategy, analysis, and management frameworks: SWOT, Porter's Five Forces, the Business Model Canvas, Hoshin Kanri, and so on. Others cover the human side of work: team development, behavior change, conflict, and negotiation. And a few are general-purpose thinking and research tools, including Cynefin, the Six Thinking Hats, a cognitive bias audit, the pre-mortem, MECE decomposition, the SCQA pyramid, STORM research, a key assumptions check, Fermi estimation, reference-class forecasting, and the OCEAN personality test.

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
| [vrio-analysis](skills/vrio-analysis/) | Tests whether a firm's resources are a source of sustained advantage (Valuable, Rare, Costly to Imitate, Organized). One parallel analyst per resource runs the four gates with evidence, then synthesis names the few that yield durable advantage. Complements value-chain analysis. |

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
| [fmea](skills/fmea/) | Failure Mode and Effects Analysis. Scopes a process, product, or design, breaks it into functions, then one parallel analyst per function lists failure modes and scores Severity, Occurrence, and Detection. Synthesis computes the Risk Priority Number, ranks the modes, applies an action threshold and a high-severity override, and recommends actions that cut S, O, or D. A systematic, scored counterpart to the pre-mortem. |
| [rice-prioritization](skills/rice-prioritization/) | Ranks a backlog by Intercom's RICE score (Reach x Impact x Confidence / Effort). Calibrates the goal, reach window, impact scale, confidence levels, and effort unit, scores each initiative in parallel, then computes and ranks the scores, runs a sensitivity check on confidence and effort, and recommends a roadmap order. A product-roadmap version of the weighted decision matrix. |

### Process and innovation methods

#### Innovation and product

| Skill | What it does |
|-------|--------------|
| [design-thinking](skills/design-thinking/) | Facilitates the five Design Thinking modes (Empathize, Define, Ideate, Prototype, Test) as an iterative loop, with parallel idea generation during Ideate and a living design document. |
| [lean-startup](skills/lean-startup/) | Runs a Build-Measure-Learn loop: surfaces leap-of-faith assumptions, ranks them by risk in parallel, designs a minimum viable test with a pre-committed metric, and decides pivot or persevere. |
| [business-model-canvas](skills/business-model-canvas/) | Maps how a business creates, delivers, and captures value across the nine blocks of Osterwalder's Business Model Canvas. One parallel analyst per block, then a synthesis pass checks whether the blocks cohere and flags the riskiest assumptions. |
| [value-proposition-canvas](skills/value-proposition-canvas/) | Osterwalder's Value Proposition Canvas, which zooms into the customer-and-value fit. Six parallel analysts describe and rank the customer profile (jobs, pains, gains) and the value map (products, pain relievers, gain creators), then a fit pass checks which top pains and gains the offer actually addresses and which relievers chase things nobody ranks high. |
| [jobs-to-be-done](skills/jobs-to-be-done/) | Finds the job a customer hires a product to do. Defines the customer and the struggling moment, fans out parallel analysts across the functional, emotional, and social job, the desired outcomes, the competing solutions, and the four forces of progress, then writes the job story and ranks outcomes by opportunity to show where current solutions underserve. |
| [kano-model](skills/kano-model/) | Classifies product features by how they drive satisfaction (must-be, performance, attractive, indifferent, reverse). One parallel analyst per feature works the functional and dysfunctional responses for a segment, then synthesis covers the must-bes first, picks the performance features to compete on, chooses a few delighters, and sequences with a decay timeline. |

#### Process improvement

| Skill | What it does |
|-------|--------------|
| [six-sigma-dmaic](skills/six-sigma-dmaic/) | Guides a Six Sigma DMAIC cycle (Define, Measure, Analyze, Improve, Control) with phase gates, parallel root-cause hypotheses verified against data, and a project document. |
| [pdca-cycle](skills/pdca-cycle/) | Guides a lightweight PDCA loop (Plan, Do, Check, Act): plan a change with a prediction, try it small, check against the prediction, and adopt, adjust, or abandon, then loop. |
| [root-cause-analysis](skills/root-cause-analysis/) | Finds and verifies the root cause of a problem with the Ishikawa fishbone and the 5 Whys. Parallel finders hunt candidate causes across the cause categories (the 6 Ms), then the strongest are drilled with why-chains to verified roots, separated from contributing causes, and turned into countermeasures that remove the roots rather than the symptom. |

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

### People and teams

Frameworks for the human side of work: how teams develop, how people respond to change, and how to handle conflict and negotiation.

#### Team dynamics

| Skill | What it does |
|-------|--------------|
| [five-dysfunctions-of-a-team](skills/five-dysfunctions-of-a-team/) | Diagnoses a team against Lencioni's pyramid (trust, conflict, commitment, accountability, results). One parallel analyst per layer scores it against the tells, then synthesis finds the lowest broken layer, traces how a cracked base surfaces as symptoms higher up, and sequences the rebuild from the base. |
| [psychological-safety](skills/psychological-safety/) | Diagnoses whether a team is safe for interpersonal risk-taking (Edmondson). Parallel assessors score the climate across voice, response to mistakes, help-seeking, inclusion, and challenge, then synthesis places the team on the safety-by-accountability grid and prescribes leader practices to reach the learning zone, not mere comfort. |
| [tuckman](skills/tuckman/) | Locates a team's stage of development (Forming, Storming, Norming, Performing, Adjourning). One parallel assessor per stage scores the team against its markers and notes regression, then synthesis names the current stage and the matching leadership focus and moves to advance, especially past the Storming stall. |

#### Motivation and behavior

| Skill | What it does |
|-------|--------------|
| [com-b](skills/com-b/) | Diagnoses why a behavior is or is not happening (Capability, Opportunity, Motivation) and routes to the right intervention via the Behaviour Change Wheel. Six parallel analysts test the sub-components, then synthesis names the binding constraint and the intervention functions that fit it, guarding the reflex to reach for motivation when the gap is opportunity or capability. |
| [scarf](skills/scarf/) | Analyzes a change, interaction, or message for social threat and reward across five domains (Status, Certainty, Autonomy, Relatedness, Fairness). One parallel analyst per domain scores the threat and reward it creates, then synthesis ranks the biggest threats and designs domain-specific moves to lower threat and raise reward. |

#### Conflict and negotiation

| Skill | What it does |
|-------|--------------|
| [thomas-kilmann](skills/thomas-kilmann/) | Chooses the conflict-handling mode that fits a situation (Competing, Collaborating, Compromising, Avoiding, Accommodating) on the assertiveness-by-cooperativeness grid. One parallel analyst per mode scores its fit, then synthesis recommends a primary mode and a fallback and flags when a habitual default is mismatched to this situation. |
| [negotiation-prep](skills/negotiation-prep/) | Prepares for a negotiation with principled, interest-based bargaining plus BATNA and ZOPA. Parallel analysts work both sides' interests and BATNAs and the options for mutual gain, then synthesis maps the zone of possible agreement, sets target and walk-away, and sequences the moves. Interests over positions; your BATNA is your power. |

### Thinking and decision

General-purpose reasoning tools, not tied to business strategy. Reach for these to pick the right approach to a problem or to examine a decision from every angle.

| Skill | What it does |
|-------|--------------|
| [cynefin](skills/cynefin/) | Classifies the issues in a messy situation into Cynefin's domains (Clear, Complicated, Complex, Chaotic, Disorder) so each gets the right approach. Surfaces the constituent issues, classifies each in parallel with its matching action model, then maps the portfolio across the domains, flags the Clear-Chaotic cliff, and routes each issue to its fitting response and framework. A meta-tool for picking the right tool. |
| [six-thinking-hats](skills/six-thinking-hats/) | De Bono's Six Thinking Hats examines an idea or decision from every angle by parallel thinking. The Blue hat sets the focus question, five hats (White, Red, Black, Yellow, Green) examine it in parallel each in its strict mode, then a Blue-hat synthesis reaches a conclusion with actions, the emotional read, and the risks that must be mitigated. |
| [cognitive-bias-audit](skills/cognitive-bias-audit/) | Audits a decision, plan, or forecast for the cognitive biases distorting it. One parallel hunter per bias family (belief, confidence, attachment, social, framing) cites where this specific reasoning is exposed, then synthesis ranks the most dangerous biases and prescribes structural debiasing. Evidence from the actual reasoning, not generic warnings. |

### Research

| Skill | What it does |
|-------|--------------|
| [storm-research](skills/storm-research/) | PhD-level research on a topic. Fans out five expert perspectives as parallel subagents, maps their contradictions, synthesizes a briefing, and peer-reviews it with confidence scores. Parallel replication of Stanford's STORM method. |
| [analysis-of-competing-hypotheses](skills/analysis-of-competing-hypotheses/) | Decides which of several rival explanations the evidence actually supports (Heuer's ACH). Proposes a near-exhaustive hypothesis set, scores every datum against each hypothesis in parallel by working to disprove, drops non-diagnostic evidence, ranks by fewest weighted inconsistencies, then stress-tests the linchpin facts for fragility and deception. Ranks by disconfirmation rather than confirmation. |
| [key-assumptions-check](skills/key-assumptions-check/) | Surfaces and stress-tests the assumptions an analysis or plan is silently resting on (Heuer & Pherson's KAC). Fans out parallel proposers to elicit the full set of assumptions including the unstated and the cultural, restates each as a testable proposition, tests each in parallel for confidence and failure conditions, classifies them solid / caveated / unsupported, and names the few linchpins that would collapse the conclusion if wrong. Where ACH tests the hypotheses, KAC tests what they rest on. |
| [fermi-estimation](skills/fermi-estimation/) | Produces a defensible order-of-magnitude estimate with no data at hand (Enrico Fermi's method). Decomposes the unknown quantity in parallel into a chain of estimable factors several different ways, estimates each as a low/best/high range, multiplies the chain and propagates the uncertainty into an honest band, then cross-checks against an independent decomposition and known bounds and names the factor that dominates the error. The inside-view counterpart to reference-class forecasting. |
| [reference-class-forecasting](skills/reference-class-forecasting/) | Forecasts a duration, cost, or success rate by anchoring on how similar past cases actually turned out (Kahneman's outside view, Flyvbjerg's method). Builds a reference class in parallel, constructs the base-rate distribution from realized outcomes, then places the case in it under adversarial checks for optimism and regression to the mean. Counters the planning fallacy by starting from the base rate rather than the case specifics. |

### Personal insight

| Skill | What it does |
|-------|--------------|
| [ocean-personality-test](skills/ocean-personality-test/) | Conducts the Big Five (OCEAN) personality test conversationally using the public-domain 50-item IPIP questionnaire, scores each dimension, and writes a detailed markdown report. |
| [hexaco-personality-test](skills/hexaco-personality-test/) | Conducts the HEXACO six-factor personality test conversationally using the public-domain 240-item IPIP-HEXACO questionnaire, scoring each factor and its facets. Adds Honesty-Humility, the integrity dimension Big Five omits. A longer, facet-level alternative to the OCEAN test. |

## How to start a skill

You don't have to prepare documents or fill in a form. Invoke the skill and give it what it needs in plain language — it asks for anything missing. Inputs come in a few shapes:

- **Just invoke it** — questionnaires interview you, no prep: [ocean-personality-test](skills/ocean-personality-test/), [hexaco-personality-test](skills/hexaco-personality-test/).
- **Give a subject, then get interviewed** — guided framing and facilitation that draws the rest out of you: [tosca-problem-definition](skills/tosca-problem-definition/), [okr](skills/okr/), [design-thinking](skills/design-thinking/), [pdca-cycle](skills/pdca-cycle/).
- **Give a topic, or paste your reasoning** — research and thinking tools that work on what you hand them: [storm-research](skills/storm-research/), [cognitive-bias-audit](skills/cognitive-bias-audit/), [pre-mortem](skills/pre-mortem/), [six-thinking-hats](skills/six-thinking-hats/).
- **Give a subject + an objective** — most analyses; the objective is what anchors them: [swot-analysis](skills/swot-analysis/), [pestel-analysis](skills/pestel-analysis/), [porters-five-forces](skills/porters-five-forces/), [business-model-canvas](skills/business-model-canvas/).
- **Give a list of options to score** — prioritization and decision tools: [rice-prioritization](skills/rice-prioritization/), [weighted-decision-matrix](skills/weighted-decision-matrix/), [impact-feasibility-matrix](skills/impact-feasibility-matrix/).

Each skill's README has a short **Starting** note, and its `references/example.md` shows a full worked example — what to type, the input filled in, and what you get back.

## What's a skill?

A skill is a self-contained unit of reusable instructions an agent loads on demand. It tells the agent *how* to do something (a procedure, a discipline, a domain workflow) without hard-coding any one platform's tools or any specific model.

## Layout

```
latticework/
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
- **`references/`** (optional) is also for the agent. It holds material the skill pulls in at runtime, such as prompt templates, scripts, or worked examples — including an `example.md` that shows how the skill is invoked and what input it expects. It is not the place for human documentation.

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

Install the skills with [`skills`](https://github.com/vercel-labs/skills), a small CLI that pulls `SKILL.md` folders from GitHub and drops them into whichever agents you have (Claude Code, Codex, Cursor, Copilot, and more):

```shell
# see what's in this repo
npx skills add l4ci/latticework --list

# add one skill
npx skills add l4ci/latticework --skill swot-analysis

# or add all of them
npx skills add l4ci/latticework --all
```

**Standalone (any runtime):** or copy a folder from `skills/` into your agent's skills directory by hand, or point your runtime at `skills/`. Conventions vary by platform:

- **Claude Code:** drop a `skills/<name>/` folder under `~/.claude/skills/` and invoke via the skill mechanism.
- **Codex / Copilot CLI / Gemini CLI:** place under the platform's skills path; most auto-discover by folder.

Check your runtime's docs for the exact path.

## Contributing

New skill → new folder under `skills/` with a `SKILL.md`. Keep it harness-agnostic, keep it focused, keep supporting material inside the folder.

## License

[MIT](LICENSE)
