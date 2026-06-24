# Contributing a skill

A skill is one folder under `skills/`, named after the skill in kebab-case. This guide covers what goes in that folder, how each file is structured, and what to update outside the folder. The [README](README.md) has the short version under "Contributing"; this is the long version with the parts that are easy to miss.

Read [swot-analysis](skills/swot-analysis/) end to end before you start. It is the reference skill, and copying its shape is faster than working from this document alone.

## What you build

```
skills/<skill-name>/
├── SKILL.md                              # the skill, loaded by the agent (required)
├── README.md                             # human overview, rendered on GitHub (required)
└── references/                           # material the skill loads at runtime
    ├── <skill-name>.md                   # the framework: theory, checklists, scoring
    ├── example.md                        # the invocation: what to type, what it needs
    └── <skill-name>-<subject>-<date>.md  # one full saved run, linked from example.md
```

Every existing skill has all of these. The README's "Layout" section calls `README.md` and `references/` optional in the general case, but for a skill that ships here they are expected. Treat the four files above as the baseline.

Adding a skill needs no change to `.claude-plugin/plugin.json` or `marketplace.json`. The plugin discovers skills by folder, so the manifest stays as is.

## SKILL.md

This is the skill itself, the procedure the agent runs. It is the file that matters most and the one with the least guidance elsewhere, so follow the pattern in [swot-analysis/SKILL.md](skills/swot-analysis/SKILL.md) closely.

Start with YAML frontmatter:

```markdown
---
name: <skill-name>
description: <when to reach for this skill, plus the trigger words that should activate it>
---
```

The `description` is what the runtime matches on to decide whether to load the skill, so it carries real weight. Write a sentence or two that names the situation, says what the skill produces, and lists the phrases a user would actually type. The SWOT description ends with `Triggers include "SWOT", "SWOT analysis", "strengths and weaknesses", "TOWS", "analyze our position"`. Match that density. A vague one-liner will leave the skill dormant when it should fire.

The frontmatter is YAML, and the `description` is an unquoted scalar, so keep it valid. The trap is a colon followed by a space (`over-trimming: the floor`): YAML reads it as a key/value separator and the whole block fails to parse, after which the installer silently skips the skill and it never appears in the catalog. Rephrase to avoid `: ` inside the description (a comma or a reworded clause does the job). Double quotes around trigger words are fine. Before you commit, confirm the frontmatter parses, for example `python3 -c "import yaml,sys; yaml.safe_load(open(sys.argv[1]).read().split('---')[1])" skills/<skill-name>/SKILL.md` (no output means it parsed).

The body of an analysis skill follows a consistent shape:

1. **Title and a short summary.** One paragraph: what the skill does and the failure it exists to prevent.
2. **A link to the framework reference**, with an instruction to load it before working.
3. **When to use**, including which sibling skill to prefer when the question is a better fit for one.
4. **Language**, telling the agent to run the session in the user's language while keeping the framework keyed to the English reference.
5. **Inputs**, marked required or optional, with the rule that anchors the analysis (for SWOT, refusing to start without an objective).
6. **An orchestration map**, a small ASCII diagram of the stages and which run in parallel.
7. **A section per stage.** Parallel stages give each subagent its shared framing as a quoted prompt block and a reminder that its return value is structured data, not prose. Synthesis stages say what to validate, build, and rank.
8. **Report structure**, listing the sections of the saved markdown output and the filename to save it under: `<skill-name>-<subject-slug>-<YYYY-MM-DD>.md`.
9. **Principles**, the few rules that keep the method honest.

Not every skill fans out into parallel subagents. The questionnaires ([ocean-personality-test](skills/ocean-personality-test/), [hexaco-personality-test](skills/hexaco-personality-test/)) and the guided facilitators ([pdca-cycle](skills/pdca-cycle/), [okr](skills/okr/)) are conversational and skip the orchestration map. Drop the sections that do not apply, but keep the frontmatter, the framework link, when-to-use, inputs, and a defined output.

## references/

Three kinds of file live here, all for the agent rather than the reader.

- **`<skill-name>.md`** holds the framework: the theory, the quadrant or stage checklists, the scoring rules, the source. Name it after the skill, not `framework.md`. SKILL.md and the README both link to it.
- **`example.md`** shows one invocation. Keep the format the other skills use: "You invoke it with", "It needs from you" (each input filled in), "You get back", and a link to the full worked report.
- **`<skill-name>-<subject>-<date>.md`** is one complete run of the skill, saved and committed so a reader can see real output without running anything. `example.md` links to it. This is the file most often forgotten; every skill in the repo has one.

## README.md

The human-facing overview. Four sections, in this order, H1 is the skill name:

1. **What this is** is the framework: what it is, its parts, where it came from. It ends with a link to the framework reference file.
2. **What it does** is the mechanics: the stages, the parallel subagents, the report it produces, and the guardrails.
3. **When to use it** says when to reach for the skill and which sibling to use instead when the fit is wrong. Link siblings with relative paths.
4. **How to get started** says what the user provides, then links `references/example.md` and `SKILL.md`.

[swot-analysis/README.md](skills/swot-analysis/README.md) is the model. No em dashes anywhere in the README.

## Register the skill in the root README

A new folder is invisible until it is listed. Edit [README.md](README.md) and add the skill to:

- the right table under "Available skills", with a one-line "What it does" that matches the style of its neighbors, and
- the matching input shape under "How to start a skill" (just invoke it, give a subject then get interviewed, give a subject and an objective, and so on).

## Style rules

These hold across every file:

- **Harness-agnostic.** Speak in actions ("read the file", "dispatch a subagent", "save the report"), never in one runtime's tool names. Each platform maps the actions to its own tools.
- **Model-agnostic.** No dependence on a specific model, context window, or vendor feature.
- **Self-contained.** Everything the skill needs lives in its folder.
- **Single responsibility.** One skill, one job. Compose skills, do not bloat one.
- **No em dashes.** Use a period, comma, colon, or parentheses instead.

## Before you open a pull request

- [ ] Folder is kebab-case under `skills/`.
- [ ] `SKILL.md` has frontmatter with a trigger-rich `description`, and a defined output.
- [ ] The frontmatter parses as YAML (no stray `: ` in the unquoted `description`), so the installer does not skip the skill.
- [ ] `references/` has `<skill-name>.md`, `example.md`, and one saved `<skill-name>-<subject>-<date>.md` run.
- [ ] `README.md` follows the four sections, with sibling links in "When to use it".
- [ ] The skill is listed in the root README catalog and the "How to start a skill" section.
- [ ] No em dashes, no harness-specific tool names.
