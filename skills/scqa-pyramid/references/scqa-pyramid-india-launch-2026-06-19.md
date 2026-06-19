# SCQA & Pyramid: Pause the India Launch

> _Illustrative example output for the `scqa-pyramid` skill. The India launch, its dates, and every figure below are fictional and invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Message:** Pause the India market launch until H2, three of the four go-live preconditions have failed, and shipping in March means shipping broken.
- **Audience:** The executive team, who greenlit the India launch last quarter and expect it live by March.
- **Format:** One-page executive summary (direct ordering, answer first).
- **Date:** 2026-06-19

---

## 1. The SCQA introduction

**Situation.** Last quarter we committed to launching in India, our first market outside the EU, with a March go-live. The thesis still holds: it is the largest underpenetrated market in our segment, and we have the product and the budget to enter it.

**Complication.** Three of the four conditions we set for a launch-ready market have failed in the run-up. Localization is six weeks behind. Our payments partner failed its compliance review and cannot process live transactions. And customer acquisition cost in the pilot came in at 3x the model, the unit economics that justified the entry do not yet exist.

**Question.** Do we hold the March date, or do we move it?

**Answer.** Move it to H2. Launching in March means launching without working payments, without a localized product, and at economics that lose money on every customer, a worse outcome for the India thesis than a clean launch one quarter later.

---

## 2. The pyramid

The headline deliverable: the governing thought on top, the key line beneath it, evidence under each point.

```
GOVERNING THOUGHT
  Pause the India launch to H2, the March date now ships a broken
  product at losing economics, and a clean H2 launch protects the thesis
  we already approved.

  KEY LINE  (inductive, three reasons of the same kind: launch-readiness
             gates that have failed; ordered by degree, hardest blocker first)

  1. We cannot legally take payment in March.
       - Payments partner failed its compliance review on 2026-06-02; no
         live transaction processing until it re-certifies or we re-contract.
       - Re-certification path is 8–10 weeks (partner's own estimate).
       - Alternative provider integration is a ~12-week build; neither path
         clears March. Without payments there is no revenue and no launch.

  2. The product is not localized for the market in March.
       - Localization is 6 weeks behind plan; current finish date is mid-April.
       - Untranslated checkout and support flows in the pilot drove a measured
         spike in drop-off and support tickets.
       - Shipping the half-localized build burns first-impression goodwill in
         a market where we have no brand equity to spend.

  3. The economics that justified entry do not hold at the March CAC.
       - Pilot CAC came in at 3x the approved model.
       - At 3x, payback runs past the LTV ceiling in the business case, every
         acquired customer is currently unprofitable.
       - The CAC overrun traces partly to (1) and (2): broken payments and a
         rough product depress conversion, inflating cost per paying customer.

  WHY PAUSE RATHER THAN PUSH HARDER:  the three blockers compound, fixing
  CAC depends on fixing payments and localization first, so no amount of
  March spend buys a good March launch. A quarter of runway buys all three.
```

**Grouping type.** The key line is **inductive**: three reasons of one kind, failed launch-readiness gates, joined by "and," not "therefore." They are ordered by **degree** (hardest, most absolute blocker first): payments is a binary legal stop, localization is a quality failure, CAC is an economics failure that partly follows from the first two.

---

## 3. The prose version (one-page exec summary)

**Recommendation: move the India launch from March to H2.**

We committed last quarter to entering India by March, and the strategic case is unchanged, it remains the largest underpenetrated market in our segment, and it is still ours to win. But three of the four conditions we set for a launch-ready market have failed in the run-up, and each one alone would be enough to pull the date. Together they mean a March launch ships a product we cannot take payment for, in a language our customers don't fully read, to customers we lose money on.

**First, we cannot legally take payment in March.** Our payments partner failed its compliance review on June 2 and cannot process live transactions. Re-certification is an 8–10 week path by the partner's own estimate; standing up an alternative provider is a ~12-week build. Neither clears March. There is no version of a launch without working payments.

**Second, the product is not localized.** Localization is six weeks behind, finishing in mid-April at the earliest. The pilot already showed what the half-translated build does: drop-off and support load both spiked on the untranslated checkout and support flows. In a market where we have no brand to fall back on, a rough first impression is expensive and hard to undo.

**Third, the economics don't hold yet.** Pilot CAC came in at 3x our model, past the payback ceiling in the approved business case, which means every customer we acquire today loses money. Part of that overrun is downstream of the first two problems: broken payments and an unpolished product suppress conversion, which inflates cost per paying customer.

**These blockers compound, which is why the answer is pause, not push.** Fixing CAC depends on first fixing payments and localization, so no amount of additional March spend buys a good March launch, it buys a more expensive bad one. Moving to H2 gives us the one quarter needed to clear all three gates and enter the market the way the board approved: clean. We are not walking back the India decision. We are protecting it from a launch date that would damage it.

**Ask:** approve the move to an H2 go-live, with re-cleared payments, completed localization, and a CAC within model as the explicit conditions to launch.

---

## 4. Framing note

Three SCQA framings were generated in parallel before this one was chosen.

- **Framing A, "Why is the launch slipping?" (status-update frame).** Situation: we're heading to a March launch. Complication: things are behind. Answer: here's the recovery plan. *Rejected*, it answers an operational question ("how do we catch up?") the analysis can't actually support, because the payments blocker has no March-clearing path. It would commit us to a date we will miss again.
- **Framing B, "Is India still the right market?" (strategy frame).** Situation: we entered India for the growth. Complication: the pilot underperformed. Question: should we still do this? *Rejected*, it raises a question the execs are not asking. They greenlit the strategy last quarter; relitigating it invites the wrong debate and undersells a thesis that is still sound. The problem is timing, not the market.
- **Framing C, "Do we hold the date or move it?" (timing frame).** **Chosen.** This is the question the exec team actually has: they approved a launch and expect it in March, so their live Complication is "the date is at risk." The Answer, move to H2, is one their three readiness gates can defend directly, and it keeps the conversation on the decision they own (the date) rather than the one they already settled (the market).

The Situation and Answer were kept from Framing C; the urgency framing of the Complication borrowed the concrete blocker language from Framing A. The **direct ordering (A-S-C-Q)** was chosen over the standard S-C-Q-A because this reader already feels the tension and wants the bottom line first.

---

## 5. Logic check

- **Summarize, not label.** The governing thought states the combined message ("a March launch ships broken at losing economics; H2 protects the thesis"), not a topic ("India launch status"). Each key-line point is a complete claim, "we cannot legally take payment in March", not a heading like "payments."
- **One kind per grouping.** The key line is a clean inductive set: three failed readiness gates, joined by "and," no "therefore" smuggled in, no step or example mixed among the reasons.
- **MECE.** The three points cover the distinct ways a launch can be not-ready, legal/operational (payments), product (localization), financial (CAC), without overlap, and the obvious objection ("then push harder for March") is answered by the compounding note rather than left as a gap.
- **On the vertical line.** The governing thought raises "why pause?"; the key line answers with three reasons. Each reason raises "how do you know?"; the evidence answers with dates, the 3x figure, and the build estimates. No level drifts to a question its parent didn't raise.

---

## 6. Caveats

- The pyramid structures and communicates the recommendation; it does not generate the underlying analysis. The strength of this summary rests on the readiness data behind it, the compliance result, the localization plan, and the pilot CAC, not on the outline.
- A framing is right only relative to a stated audience. For the *board* (rather than the exec team), the live Question might be "is India still the right bet?", Framing B, and the pyramid would be rebuilt around that.
- If the evidence could not support "move to H2", for example if payments had a real March-clearing path, the fix would be more analysis, not a sharper outline. The structure makes a sound case legible; it cannot make a weak case strong.
- All figures here are illustrative for documentation purposes and were not researched.
