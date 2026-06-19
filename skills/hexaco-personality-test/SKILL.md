---
name: hexaco-personality-test
description: Use when the user wants a HEXACO personality assessment, or a Big Five test that also measures Honesty-Humility. Administers the public-domain 240-item IPIP-HEXACO questionnaire conversationally across six factors (Honesty-Humility, Emotionality, eXtraversion, Agreeableness, Conscientiousness, Openness) and their 24 facets, scores it, and writes a detailed markdown report. Triggers include "HEXACO test", "HEXACO personality", "Honesty-Humility", "Big Five plus honesty", "six-factor personality assessment".
---

# hexaco-personality-test

HEXACO (Ashton and Lee) is the Big Five plus a sixth factor, **Honesty-Humility**, that OCEAN does not measure; its Emotionality and Agreeableness are rotated relative to Big Five Neuroticism and Agreeableness. Administered here via the public-domain 240-item IPIP-HEXACO scales. If the user wants the classic five-factor test instead, use [ocean-personality-test](../ocean-personality-test/).

The item bank, factor and facet structure, keying, scoring rules, and bands live in [references/items.md](references/items.md). Load that file before administering the test and follow its keying exactly. The items are public-domain IPIP items; the reference cites the source.

## When to use

The user wants a HEXACO / six-factor personality test, or specifically wants the Honesty-Humility dimension that Big Five omits. Not a clinical or diagnostic tool. If the user shows signs of distress or asks for a mental-health diagnosis, say plainly that this is a non-clinical self-report questionnaire and point them to a professional.

This is the long form: 240 items, roughly 30–40 minutes. If the user wants a quick read, say so up front and offer the 50-item [ocean-personality-test](../ocean-personality-test/) as the faster five-factor alternative (it cannot measure Honesty-Humility). There is no shorter public-domain HEXACO item set, so do not improvise a trimmed version.

## Language

Conduct the whole session in the language the user is writing in. Translate the items and the accuracy anchors faithfully, and write the final report in that language. The items in the reference file are English originals; keep the scoring keyed to those originals regardless of the language shown to the user.

## How to run

1. **Set up.** Briefly explain what the test measures (the six factors, and that the distinctive one is Honesty-Humility), how long it takes (240 short statements, roughly 30–40 minutes), and that honest first-instinct answers work better than over-thinking. State up front that this is a non-clinical self-report tool, not a diagnosis. Because it is long, offer to run it across several sittings, and confirm the user wants the full version. Ask for consent to begin.
2. **Administer.** Present the 240 items in batches (10 to 20 at a time), tracking each by its number from the reference file. Show the 1-to-5 accuracy scale (Very Inaccurate to Very Accurate) with each batch, and present each item as the stem "I …" plus the statement. Accept answers as a list (for example "1, 4, 3, ..."), and let the user answer a whole batch at once. Re-show the scale if they seem unsure. Do not reveal which factor or facet an item belongs to or how it is keyed while testing, since that biases answers. You may shuffle presentation order to reduce response-set bias, but keep scoring tied to item numbers.
3. **Score.** Apply the scoring rules from the reference file: reverse `−` keyed items as `6 - answer`, then take the mean of each facet's 10 items and each factor's 40 items (each on a 1.0-to-5.0 scale). Assign every factor and facet a band from the bands table.
4. **Interpret and write the report.** Build the markdown report described below from the scores. Ground the interpretation in the user's actual answers, not generic trait descriptions: when a factor's facets split (for example high Sociability but low Social Boldness within eXtraversion), say so: the facet structure is the main reason to run the 240-item form.
5. **Save.** Write the report to a markdown file named `hexaco-report-<YYYY-MM-DD>.md` using today's date, in the working directory unless the user names another location. Tell the user where it was saved.

## Report structure

Write a thorough markdown report with these sections:

1. **Header.** Title, date, instrument name ("IPIP-HEXACO, 240 items, public domain"), and a one-sentence non-clinical disclaimer.
2. **Summary table.** One row per factor with the per-item mean (1.0 to 5.0) and the band. Include a compact text bar (for example `████░` style) so the profile is scannable at a glance.
3. **Per-factor deep dive (six sections).** For each of H, E, X, A, C, O: the score and band, what the factor means in plain language, what a high versus low score tends to look like, the **facet breakdown** (the four facet means and any split among them), and where this specific taker falls and what their answer pattern suggests. Name concrete strengths and likely blind spots or growth areas. Briefly note how the trait tends to show up at work, in relationships, and under stress. Give Honesty-Humility real attention: it is what this instrument adds over Big Five and it predicts exploitation, entitlement, and integrity-relevant behavior.
4. **Profile interactions.** Two to four notable combinations across factors (for example low Honesty-Humility with high eXtraversion, or high Emotionality with low Agreeableness) and what the interplay tends to mean. This is where the report earns "detailed": single-trait readouts miss how traits combine.
5. **Reflection prompts.** A few open questions the user can sit with, tied to their specific results.
6. **Caveats and how to read this.** Self-report captures self-image on one day, not fixed truth. Bands describe the taker's own answer pattern, not a percentile against the population (this preliminary IPIP-HEXACO set has no official norms). Facet scales are short (10 items) and the trimmed final HEXACO scales are not published in the public domain, so facet readings are indicative, not precise. Traits are continua, not types. Mood and context shift answers. This is not a clinical or diagnostic instrument.

## Principles

- **Faithful instrument.** Use the exact items and keying from the reference file. Do not improvise, drop, or trim items to a shorter form; there is no public-domain short version and validity depends on it.
- **Honesty-Humility is the point.** Give it full weight in scoring and in the report rather than treating it as a footnote.
- **Specific over generic.** A good report reads like it is about this person's answers. Cite the answer patterns and facet splits that drove each band rather than reciting textbook trait blurbs.
