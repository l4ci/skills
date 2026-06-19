# storm-research

Stanford published a research method in 2024 called STORM (Synthesis of Topic Outlines through Retrieval and Multi-perspective Question Asking), peer-reviewed at NAACL 2024 ([Shao et al.](https://aclanthology.org/2024.naacl-long.347/)). In their evaluation, human raters judged more of STORM's articles to be well-organized, a 25% absolute increase over a retrieval-augmented baseline, with 10% broader coverage. Stanford also runs a free demo at [storm.genie.stanford.edu](https://storm.genie.stanford.edu), which requires a free account to use.

This skill replicates that method inside an agent and runs it in parallel. It fans out five expert perspectives as independent subagents that each do their own retrieval, maps where they contradict, synthesizes a briefing, and then peer-reviews the result with a panel of independent critics that assign confidence scores and name the gaps.

## Starting

**You provide:** the topic to research (and, optionally, who the insight is for). Something like "Do a STORM-style deep research briefing on whether GLP-1 drugs cut cardiovascular risk independent of weight loss".

See [references/example.md](references/example.md) for a worked example.

The skill itself lives in [SKILL.md](SKILL.md).
