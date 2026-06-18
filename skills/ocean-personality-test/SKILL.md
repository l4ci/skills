---
name: ocean-personality-test
description: Use when the user wants to take a Big Five (OCEAN) personality test or asks to assess their personality across Openness, Conscientiousness, Extraversion, Agreeableness, and Neuroticism. Administers the public-domain 50-item IPIP questionnaire conversationally, scores it, and writes a detailed markdown report. Triggers include "OCEAN test", "Big Five", "personality assessment", "what's my personality type".
---

# ocean-personality-test

Administers the Big Five personality assessment (OCEAN: Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism) using the public-domain 50-item IPIP Big-Five Factor Markers, then scores it and writes a detailed markdown report.

The item bank, OCEAN-oriented keying, scoring rules, and bands live in [references/items.md](references/items.md). Load that file before administering the test and follow its keying exactly.

## When to use

The user wants to take a Big Five / OCEAN personality test, or wants their personality assessed across the five dimensions. Not a clinical or diagnostic tool. If the user shows signs of distress or asks for a mental-health diagnosis, say plainly that this is a non-clinical self-report questionnaire and point them to a professional.

## Language

Conduct the whole session in the language the user is writing in. Translate the items and the Likert anchors faithfully, and write the final report in that language. The items in the reference file are English originals; keep the scoring keyed to those originals regardless of the language shown to the user.

## How to run

1. **Set up.** Briefly explain what the test measures, how long it takes (about 50 short statements, roughly 10 minutes), and that honest first-instinct answers work better than over-thinking. State up front that this is a non-clinical self-report tool, not a diagnosis. Ask for consent to begin.
2. **Administer.** Present the 50 items in the original order from the reference file, in batches of 10 so the user is not flooded. Show the 1-to-5 Likert scale with each batch. Accept answers as a list (for example "1, 4, 3, ..."), and let the user answer all at once if they prefer. Re-show the scale if they seem unsure. Do not reveal which factor an item belongs to or how it is keyed while testing, since that biases answers.
3. **Score.** Apply the scoring rules from the reference file: reverse `-` keyed items as `6 - answer`, sum each factor's 10 items into a total (10 to 50), and compute the per-item average (1.0 to 5.0). Assign each factor a band from the bands table.
4. **Interpret and write the report.** Build the markdown report described below from the scores. Ground the interpretation in the user's actual answers, not generic trait descriptions: when a factor's items split (for example high on sociability items but low on attention-seeking items), say so.
5. **Save.** Write the report to a markdown file named `ocean-report-<YYYY-MM-DD>.md` using today's date, in the working directory unless the user names another location. Tell the user where it was saved.

## Report structure

Write a thorough markdown report with these sections:

1. **Header.** Title, date, instrument name ("IPIP Big-Five Factor Markers, 50 items"), and a one-sentence non-clinical disclaimer.
2. **Summary table.** One row per dimension with the total (out of 50), the per-item average, and the band. Include a compact text bar (for example `████░` style or a 0-to-50 marker) so the profile is scannable at a glance.
3. **Per-dimension deep dive (five sections).** For each of O, C, E, A, N: the score and band, what the dimension means in plain language, what a high versus low score tends to look like, and where this specific taker falls and what their answer pattern suggests. Name concrete strengths and likely blind spots or growth areas. Briefly note how the trait tends to show up at work, in relationships, and under stress.
4. **Profile interactions.** Two to four notable combinations across dimensions (for example high Openness with high Conscientiousness, or high Extraversion with high Neuroticism) and what the interplay tends to mean. This is where the report earns "detailed": single-trait readouts miss how traits combine.
5. **Reflection prompts.** A few open questions the user can sit with, tied to their specific results.
6. **Caveats and how to read this.** Self-report captures self-image on one day, not fixed truth. Bands describe the taker's own answer pattern, not a percentile against the population (the IPIP-50 has no official norms). Traits are continua, not types. Mood and context shift answers. This is not a clinical or diagnostic instrument. For a normed, facet-level result, point to a longer instrument such as the IPIP-NEO-120.

## Principles

- **Faithful instrument.** Use the exact items and keying from the reference file. Do not improvise items, drop items, or reorder factors mid-test. The validity depends on it.
- **No leakage during testing.** Keep factor labels and keying hidden until scoring, so the user answers the statement rather than the trait.
- **Specific over generic.** A good report reads like it is about this person's answers. Cite the answer patterns that drove each band rather than reciting textbook trait blurbs.
- **Honest about limits.** Always carry the non-clinical, self-report, no-norms caveats into the report. Do not overclaim precision.
