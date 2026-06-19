# ocean-personality-test

Conducts the Big Five personality test (OCEAN: Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism) as a conversation, then scores it and writes a detailed markdown report.

It uses the public-domain 50-item [IPIP Big-Five Factor Markers](https://ipip.ori.org/New_IPIP-50-item-scale.htm) (Goldberg, 1992), ten items per dimension, rated on a 1-to-5 scale. The skill runs the questionnaire in the user's own language, scores each dimension into a total and a band, and produces a report with a summary table, a deep dive per dimension, notable trait interactions, reflection prompts, and clear caveats.

This is a non-clinical self-report questionnaire, not a diagnostic tool.

## Starting

**You provide:** nothing; it administers the 50-item questionnaire and you answer as you go. Something like "Give me the Big Five personality test".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the item bank, keying, and scoring rules are in [references/items.md](references/items.md).
