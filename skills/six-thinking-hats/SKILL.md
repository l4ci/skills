---
name: six-thinking-hats
description: Use when the user wants to examine an idea, plan, or decision from every angle, run a structured deliberation, or break an adversarial deadlock using Edward de Bono's Six Thinking Hats. Defines a focus question with the Blue hat, fans out five parallel subagents that each look at that question in one strict mode (White facts, Red feelings, Black caution, Yellow benefits, Green creativity), then synthesizes them into a Blue-hat conclusion with concrete actions, the emotional read, and which risks must be mitigated versus which ideas neutralize them. Triggers include "six thinking hats", "de Bono", "look at this from all angles", "parallel thinking", "structured deliberation".
---

# six-thinking-hats

Runs Edward de Bono's Six Thinking Hats: examines a topic in six modes (White facts, Red feelings, Black caution, Yellow benefits, Green creativity, Blue process control) so everyone looks in the same direction at once instead of arguing across directions. Catches the failure where deliberation becomes a fight and the topic is never seen from every angle.

The six hats, their strict discipline, the failure modes, and the suggested sequence live in [references/six-hats.md](references/six-hats.md). Load that file before facilitating, and hold each hat strictly in its lane.

## When to use

The user wants to evaluate an idea, plan, or decision from all sides, run a structured deliberation, or break a deadlock where people are talking past each other. The unit is one focus question examined in full. Distinguish from a pre-mortem, which looks only at how something fails (the Black hat alone), and from a weighted decision matrix, which scores defined options against criteria. If there is a single clear question, use this; if the user is choosing among several options on known criteria, a scoring method fits better.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **TOPIC** (required): the idea, plan, or decision to examine. Push for one focus question. If the topic is broad or tangled, narrow it to a single question with the Blue hat in Stage 1 before fanning out.
- **CONTEXT** (optional): the stakes, the people affected, the decision the session should inform, and any constraints. Shapes the focus question, the hat sequence, and the framing of the synthesis, not the discipline of each hat.

## Orchestration map

```
Stage 1  Blue (open)    ── 1 agent, inline ──────────────────────┐  (set the focus question, sequence, success)
Stage 2  Five hats      ── 5 subagents IN PARALLEL ──────────────┤  (White, Red, Black, Yellow, Green)
Stage 3  Blue (close)   ── 1 agent, needs all 5 ─────────────────┘  (integrate, weigh, conclude, act)
```

## Stage 1: Blue hat, open (INLINE)

Before dispatching anything, do the Blue hat's opening work yourself:

1. **Focus question.** State the one question the session will examine, precisely. If the TOPIC is broad, narrow it with one or two questions to the user first. Everything downstream looks at this question.
2. **Sequence.** Pick the hat order for how the synthesis will reason, keyed to purpose (see the reference file). The five substantive hats still run in parallel; the sequence governs how the Blue hat orders and weighs them.
3. **Success.** Say what a good outcome looks like, and confirm the conclusion is genuinely open, not a foregone decision the hats are being run to ratify.

## Stage 2: Five hats (PARALLEL)

Dispatch five subagents at once, one per substantive hat: White, Red, Black, Yellow, Green. Give each the shared framing plus its hat's discipline from the reference file. All five look at the same focus question simultaneously, each confined to its own mode.

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their hat in real evidence where the hat allows (White and Black especially; Red is exempt by design).

**Shared framing (send to every hat):**

> Examine this focus question in one mode only: **[FOCUS QUESTION]**. You are wearing the **[HAT]** hat. Stay strictly in its discipline; do not stray into another hat's mode. [Insert the hat's row and discipline from the reference file.] Then return:
> - **Findings**: the specific points your hat surfaces about this question, each as a tight, concrete claim
> - **Evidence**: what grounds each point (figures, sources, named specifics), or, for the Red hat, simply the feeling stated plainly with no justification
> - **Weight**: which of your points matter most, and why
> - **Confidence**: high, medium, or low, lowered where evidence was thin (the Red hat reports intensity of feeling instead)
>
> Context: [CONTEXT]

Assign the five hats from the reference file. The Black hat must return logical, specific risks, not free-floating negativity; the Yellow hat must name the mechanism behind each benefit; the Green hat generates without judging and is told the Black hat's job is covered elsewhere so it need not pre-criticize its own ideas. Collect all five structured results before continuing. Re-dispatch any hat that fails rather than synthesizing with a gap.

## Stage 3: Blue hat, close (SEQUENTIAL, needs all 5)

One agent puts the Blue hat back on and integrates across the five:

1. **Integrate.** Lay the five hats side by side in the chosen sequence. Where do they agree, and where does one hat's finding directly answer another's (a Green idea that neutralizes a Black risk, a White fact that deflates a Yellow benefit)?
2. **Weigh.** Which findings carry real weight and which are minor? Do not let the volume of risks decide the outcome on its own; set them against the Yellow value and the Green routes around them.
3. **The emotional read.** Surface what the Red hat flagged. A strong gut reaction is data even when no Black-hat argument backs it; name it and say how much it should move the decision.
4. **Risks: must-mitigate vs neutralized.** Sort the Black-hat risks into those that must be mitigated before proceeding and those a Green-hat idea already addresses. Pair each surviving risk with its mitigation or mark it open.
5. **Conclusion and actions.** Reach a clear conclusion on the focus question, or state plainly what is unresolved and why. List the concrete next actions that follow.

## Report structure

Write a thorough markdown report and save it to `six-thinking-hats-<topic-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The focus question examined, the context if given, the hat sequence used, the date, and a one-line note on the framework.
2. **Verdict.** The Blue-hat conclusion on the focus question in a few sentences, with the emotional read and the one or two findings that most drive it called out up front.
3. **The six hats.** Each hat in the chosen sequence, with its findings, evidence, and weight. Keep each hat strictly in its mode so the report stays scannable by direction.
4. **Synthesis.** Integration across the hats, the weighing, the Red-hat emotional read, and the risks sorted into must-mitigate versus neutralized.
5. **Conclusion and actions.** The decision or open question, and the concrete next actions.
6. **Caveats.** Six Hats opens a question across modes of thought; it does not score options against criteria or guarantee the chosen path is right. The hats reflect the information and intuitions available at the session, not a forecast. A clear conclusion means the question was examined from every angle, not that the outcome is certain.

## Principles

- **One mode at a time.** A risk smuggled into the facts, or a critique smuggled into an idea, breaks the method. Separate the hat from the thinker: the same subject can be argued for under Yellow and against under Black without contradiction.
- **Force Yellow and Green around Black.** Caution is the default mode and will dominate if unchecked. Every risk gets a fair search for value and a way past it before it decides anything.
- **Red is data, not noise.** Feelings get a legitimate, unjustified slot so they stop contaminating the rational hats. Weigh the gut read in the synthesis rather than dismissing it.
- **Keep the outcome open.** Do not run the hats to ratify a decision already made.
