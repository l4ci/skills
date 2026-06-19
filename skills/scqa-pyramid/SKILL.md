---
name: scqa-pyramid
description: Use when the user has a recommendation, findings, or decision to communicate and wants it structured top-down so the answer comes first. Generates competing SCQA framings in parallel, selects the sharpest, builds the supporting pyramid, then audits the logic and the key line with parallel checkers. Triggers include "Pyramid Principle", "SCQA", "Minto", "structure my argument", "executive summary", "answer first", "storyline", "structure this recommendation".
---

# scqa-pyramid

Structures a recommendation, set of findings, or decision (Barbara Minto's Pyramid Principle) so the reader gets the answer first and the rest of the document defends it. The output is an SCQA introduction that frames the reader's real question, and a pyramid of supporting arguments beneath the answer, each level summarizing the level below it.

SCQA in full, the pyramid rules, deductive versus inductive grouping, and the pitfalls live in [references/pyramid.md](references/pyramid.md). Load that file before structuring.

## When to use

The user has something to say and needs to say it in an order the reader can follow: an executive summary, a one-pager, a recommendation email, a deck storyline. It pairs downstream of the analysis skills, this is the step where the result of the thinking becomes a message. Define the problem, decompose and analyze it, then structure the answer for the reader. It shares its Minto lineage with [mece-decomposition](../mece-decomposition/): the key line of a pyramid must itself be MECE. If the user only needs a quick note, this is heavier than necessary; reach for it when the order of ideas decides whether the point lands.

## Language

Run the session and write the output in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **MESSAGE** (required): the recommendation, findings, or decision to communicate, plus the supporting material (the analysis, data, or reasons behind it).
- **AUDIENCE** (optional): who reads it and what they already know and care about. This shapes the SCQA, since the framing turns on the reader's existing question, so ask if it is unclear.
- **FORMAT** (optional): the vehicle, an exec summary, one-pager, email, or deck storyline. Affects length and how the pyramid is flattened into prose, not the structure itself.

## Orchestration map

```
Stage 1  Candidate framings ── 3 SCQA subagents IN PARALLEL ──────┐  (different complications and questions)
Stage 2  Select the framing ── 1 agent, needs all 3 ─────────────┤  (pick or merge the sharpest)
Stage 3  Build the pyramid  ── 1 agent ──────────────────────────┤  (answer on top, key line, evidence)
Stage 4  Logic audit        ── 2 checkers IN PARALLEL ── then refine ┘  (summary and grouping; MECE and Q&A)
```

Tell each subagent its final message is the return value: structured data, not prose for a human.

## Stage 1: Candidate framings (PARALLEL)

The Question fixed in the introduction is the question the whole pyramid must answer, so generate several framings rather than committing to the first. Dispatch three SCQA subagents at once, each told to frame the same material for a different reader or around a different complication, so each surfaces a different Question and therefore a different Answer.

**Shared framing (send to each subagent):**

> Frame **[MESSAGE]** for **[AUDIENCE]** as an SCQA introduction, emphasizing **[your assigned complication or reader]**. Return:
> - **Situation:** the uncontroversial background this reader already accepts
> - **Complication:** what changed or went wrong that creates the tension
> - **Question:** the question the Complication raises in this reader's mind
> - **Answer:** the one-sentence governing thought that answers that Question
> - A self-check: is this the question this reader actually has, and can the available evidence support this Answer
> - The strengths and weaknesses of this framing for the audience

## Stage 2: Select the framing (SEQUENTIAL, needs all 3)

One agent compares the candidate framings and picks the sharpest: the one whose Question is the real question the audience is asking, and whose Answer the supporting material can actually defend. Merge across framings if the best Situation and the best Complication come from different ones. State why this framing was chosen; the Question it fixes is the highest-leverage decision in the exercise, and everything below the Answer exists to defend it.

## Stage 3: Build the pyramid (SEQUENTIAL)

Set the chosen Answer as the governing thought at the top. Derive the **key line**: the two to five supporting arguments that, taken together, prove the governing thought. The key line must be MECE (no overlap, no gap) and each point must be a complete thought that summarizes what sits below it, not a topic label. Decide whether the grouping is **deductive** (premise, premise, therefore) or **inductive** (a set of the same kind of reason, step, or item, named by their commonality) and state which. Order the points by a real principle (time, structure, or degree). Then attach the evidence, data, or sub-arguments under each key-line point. Check vertically: each level should answer the "why?" or "how?" the level above raises.

## Stage 4: Logic audit (PARALLEL, then refine)

Audit the built pyramid. Dispatch two checkers at once, each given the full pyramid.

- **Checker A, summary and grouping:** at every level, does the parent genuinely *summarize* the children (state their combined message), or does it merely *label* them (name the topic)? And does each grouping hold together as one kind, a clean deductive chain or a clean inductive set, without mixing the two in a single grouping?
- **Checker B, MECE and answers-the-question:** is the key line MECE, no two points overlapping and nothing left out? And does each key-line point actually answer the "why?" or "how?" the governing thought raises, rather than drifting to a different question?

Then refine to resolve what the checkers found. Fix the problem at the level where it originates: a labeling parent gets rewritten into a summarizing statement, a non-MECE key line gets recut, a drifting point gets pulled back to the governing thought. Re-audit if the fix reshaped the pyramid.

## Report structure

Write the result as markdown and save it to `scqa-pyramid-<topic-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location. The deliverable is the structured argument, in three forms.

1. **Header.** The message in one line, the audience, the format, and the date.
2. **The SCQA introduction.** Situation, Complication, Question, Answer, each as a short paragraph. This is the opening of the document.
3. **The pyramid.** The full structure as a nested outline: governing thought at the top, the key-line points beneath it (with the grouping type, deductive or inductive, named), and the evidence under each point. This is the headline deliverable.
4. **The prose version.** The pyramid written out as a clean draft in the chosen format, answer first, ready to use or adapt.
5. **Framing note.** Which SCQA framing was chosen and why it beat the alternatives, so the structure is defensible.
6. **Logic check.** A short statement that each level summarizes the level below, each grouping is one kind, and the key line is MECE and on-question.
7. **Caveats.** The pyramid structures and communicates the message; it does not generate the analysis or make a weak case strong. A framing is only right relative to a stated audience; a different reader may have a different Question. If the evidence cannot support the Answer, the fix is more analysis, not a better outline.

## Principles

- **Answer first.** State the governing thought before its support. The reader should not have to assemble the conclusion from clues; a document is not a detective story.
- **The framing is everything.** The Question fixed by the SCQA decides what the whole pyramid must prove. Generate competing framings before committing.
- **Summarize, do not label.** A parent idea states the combined message of its children. "Three risks" is a label; "the launch is too risky to proceed this quarter" is a summary.
