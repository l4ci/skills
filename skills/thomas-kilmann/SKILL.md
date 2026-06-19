---
name: thomas-kilmann
description: Use when the user has a specific conflict, disagreement, or dispute to navigate and needs to decide how to handle it. Diagnoses the situation along assertiveness and cooperativeness, then fans out five parallel analyst subagents (one per conflict mode) to score how well each fits this situation, and synthesizes a primary mode and fallback with concrete words and actions, flagging when the user's habitual default is mismatched. Triggers include "Thomas-Kilmann", "TKI", "conflict mode", "how should I handle this conflict", "competing collaborating compromising avoiding accommodating".
---

# thomas-kilmann

Runs the Thomas-Kilmann Conflict Mode Instrument to choose how to handle a specific conflict. Conflict-handling behavior varies on two axes, assertiveness (concern for your own goals) and cooperativeness (concern for the other party's), producing five modes: Competing, Collaborating, Compromising, Avoiding, and Accommodating. Catches the failure of defaulting to your habit; no mode is best, so match the mode to THIS situation.

The two axes, the five modes, the situational factors, and the pitfalls live in [references/thomas-kilmann.md](references/thomas-kilmann.md). Load that file before analyzing.

## When to use

The user faces a concrete conflict, disagreement, or dispute and is deciding how to approach it. The unit of analysis is one situation between defined parties, not a personality assessment and not a general communication style. Pairs with negotiation-prep when the chosen mode is collaborating or compromising and a deal must be worked, and with stakeholder-analysis when the conflict spans several parties with different stakes. Do not use it to type people; use it to choose an approach for this conflict.

## Language

Conduct the session and write the report in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of the output language.

## Inputs

- **CONFLICT** (required): the dispute to navigate: the parties, what each side wants, and what is at stake. If this is vague, narrow it with one or two questions before analyzing.
- **CONTEXT** (optional): the power balance, how much the relationship matters, time pressure, the history and trust between the parties, and the user's own habitual conflict style. Shapes which modes fit and lets the synthesis flag a mismatched default.

## Orchestration map

```
Stage 1  Situation     ── inline ─────────────────────────────┐  (parties, stakes, power, relationship, time)
Stage 2  Mode Fit      ── 5 analyst subagents IN PARALLEL ─────┤  (each scores its mode's fit to this situation)
Stage 3  Synthesis     ── 1 agent, needs all 5 ────────────────┘  (primary mode, fallback, what to say and do)
```

## Stage 1: Situation (INLINE)

Before dispatching anyone, fix the facts that decide which modes fit. State, from CONFLICT and CONTEXT: the parties and what each wants; the stakes for the user and the stakes for the other party; the power balance; how much the ongoing relationship matters versus this one outcome; the time pressure; and the trust and history. If the user named their habitual conflict style, record it for the mismatch check in Stage 3. Where a factor is unknown, name it as unknown rather than guessing.

## Stage 2: Mode Fit (PARALLEL)

Dispatch five analyst subagents at once, one per conflict mode. Give each the shared framing plus its mode's description, fits, and overuse/underuse risks from the reference file.

**Shared framing (send to each analyst):**

> Evaluate one conflict-handling mode against this specific situation. Conflict: **[CONFLICT]**. Situational factors: [the Stage 1 facts, stakes for each side, power balance, relationship importance, time pressure, trust and history]. Your mode is **[MODE]**: [its description, when it fits, and its overuse/underuse risks from the reference file]. Judge fit to THIS situation only; do not argue the mode is generally good or bad. Then return:
> - **Fit assessment**: how well this mode suits these exact factors, factor by factor
> - **Pros**: what choosing this mode would gain here
> - **Cons**: what it would cost or risk here, including the relevant overuse or underuse risk
> - **Likely outcome**: the realistic result if the user handled the conflict this way
> - **Fit score**: high, medium, or low, with one line of justification tied to the factors
> - **Concrete move**: if this mode were chosen, the opening thing to say or do
>
> Context: [CONTEXT]

Tell each subagent its final message is the return value: structured data, not prose for a human. Subagents should use available retrieval tools to ground their assessment in real evidence where the conflict involves verifiable facts. Assign the five modes from the reference file: Competing, Collaborating, Compromising, Avoiding, and Accommodating. Collect all five structured results before continuing. Re-dispatch any analyst that fails rather than synthesizing with a gap.

## Stage 3: Synthesis (SEQUENTIAL, needs all 5)

One agent compares the five fit assessments and reaches a recommendation:

1. **Rank by fit.** Order the five modes by fit score against the Stage 1 factors. Name why the top mode wins and the bottom modes lose, in terms of the situational factors, not preference.
2. **Primary and fallback.** Recommend the primary mode and a fallback for if it stalls or the other party will not engage (collaboration falling back to compromising, competing against bad faith falling back to avoiding, and so on).
3. **What to say and do.** Translate the primary mode into concrete moves: how to open, what to ask for, what to concede or hold, and how to read whether to switch to the fallback.
4. **Default mismatch.** If the user named a habitual style and it differs from the recommended mode, say so plainly: name the habit, name the gap, and name what the situation demands instead.

## Report structure

Write a thorough markdown report and save it to `thomas-kilmann-<subject-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location.

1. **Header.** The conflict analyzed, the parties, the context if given, the date, and a one-line note that no mode is universally best and the instrument chooses an approach for a situation, not a personality.
2. **Verdict.** The recommended primary mode and fallback in a few sentences, with a table: each of the five modes, its fit score, and a one-line reason.
3. **The situation.** The Stage 1 factors laid out, with unknowns flagged.
4. **Mode fit.** Each of the five modes: fit, pros, cons, likely outcome, and its concrete move.
5. **Recommendation.** Primary and fallback, what to say and do, and the default-mismatch flag if it applies.
6. **Caveats.** The TKI describes behavior in a situation, not a fixed personality; the recommendation is only as good as the situational facts, several of which may be assumed or unknown; the other party will respond and may shift the situation mid-conflict; and choosing the right mode does not guarantee the outcome, only the soundest approach to it.

## Principles

- **Match the situation, not the habit.** The recommendation follows from the stakes, power, relationship, and time, not from what the user usually does. Flag the gap when they differ.
- **No mode is best.** Every mode wins somewhere and loses elsewhere. Reject any pull toward a universal favorite, especially chronic collaborating or chronic avoiding.
- **Read power and time honestly.** A collaborative ideal is worthless without leverage or time. Ground the choice in the real constraints.
- **Always name a fallback.** Conflicts move; the other party gets a vote. A primary mode without a fallback is a plan that breaks on first contact.
