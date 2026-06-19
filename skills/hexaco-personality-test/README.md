# hexaco-personality-test

Conducts the HEXACO personality test (Honesty-Humility, Emotionality, eXtraversion, Agreeableness, Conscientiousness, Openness to Experience) as a conversation, then scores it and writes a detailed markdown report.

HEXACO is the Big Five plus a sixth factor, **Honesty-Humility** (sincerity, fairness, greed-avoidance, modesty), which OCEAN does not measure and which predicts integrity-relevant behavior such as exploitation and entitlement. Its Emotionality and Agreeableness factors are also rotated relative to Big Five Neuroticism and Agreeableness. For the classic five-factor test, see [ocean-personality-test](../ocean-personality-test/).

It uses the public-domain 240-item [IPIP-HEXACO scales](https://ipip.ori.org/newHEXACO_PI_key.htm) (Ashton, Lee, & Goldberg, 2007), six factors of four facets each, ten items per facet, rated on a 1-to-5 accuracy scale. The IPIP is in the public domain and free for any use, so the items ship in this repository. The skill runs the questionnaire in the user's own language, scores each factor and facet into a mean and a band, and produces a report with a summary table, a per-factor deep dive with facet breakdowns, notable trait interactions, reflection prompts, and clear caveats.

It is the long form (240 items, roughly 30 to 40 minutes); there is no public-domain short version. For a quicker read, the 50-item OCEAN test is the faster five-factor alternative, though it cannot measure Honesty-Humility.

This is a non-clinical self-report questionnaire, not a diagnostic tool.

## Starting

**You provide:** nothing; it interviews you, presenting the 240 items in batches and scoring your answers. Say something like "give me a HEXACO test".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the item bank, keying, and scoring rules are in [references/items.md](references/items.md), which cites the public-domain source.
