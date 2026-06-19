# tosca-problem-definition

Sharpens a vague problem into a crisp, solvable one before any solving starts. It uses TOSCA, the problem-definition framework from *Bulletproof Problem Solving* (Charles Conn and Robert McLean): Trouble, Owner, Success criteria, Constraints, Actors. A well-defined problem is half-solved, and most wasted analysis comes from solving the wrong problem precisely.

The skill runs as a guided interview. It walks through each of the five elements with sharp questions, and it challenges weak answers rather than accepting them: a symptom gets pushed to its root, a solution hiding inside the problem gets stripped out, vague success criteria are forced into a metric and a date, and each constraint is marked as real or merely assumed. Before finalizing, three critic subagents stress-test the framing in parallel for the classic failure modes. The output is a saved markdown brief with a single crisp problem statement and the structured TOSCA behind it.

This skill frames the problem; it does not solve it. Run it upstream of the analysis and strategy skills in this collection.

## Starting

**You provide:** nothing structured; just the fuzzy problem in your own words, and it interviews you through the five TOSCA elements. Something like "help me frame this problem with TOSCA."

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the framework, questions, pitfalls, and problem-statement criteria are in [references/tosca.md](references/tosca.md).
