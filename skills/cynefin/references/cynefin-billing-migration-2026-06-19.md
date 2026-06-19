# Cynefin: Billing platform migration to a new payments provider

> _Illustrative example output for the `cynefin` skill. This migration is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

---

## 1. Header

- **Situation:** Replace the payments provider, re-platform billing onto the new provider's stack, and (the unstated hope) lift checkout conversion in the process. Two prior migration plans slipped badly and no one can say exactly why.
- **Context:** A hard regulatory deadline in nine months. A team of six. Two prior attempts that stalled in integration. A CFO who wants a fixed go-live date he can commit to the board.
- **Date:** 2026-06-19
- **Note:** Cynefin is a sense-making *meta-framework*. It tells you what *kind* of problem each part of this is, and therefore how to act and which other tool to reach for. It does not solve the migration. The answer still comes from acting in the way each domain calls for.

---

## 2. Verdict

This is a **mixed portfolio masquerading as a single project plan**, and that disguise is why the last two attempts slipped. The team has been running the whole thing as one Complicated migration, analyze it all up front, produce a Gantt chart, commit to a date, when at least two of its load-bearing pieces are **Complex** (the integration that stalled twice, and the conversion lift) and cannot be planned into existence. Studying them harder is the slow failure mode, and it has already happened twice.

The single most dangerous issue in the portfolio is the one everyone is most confident about: **the old provider's billing still running in production**. It is Clear and quietly trusted, which puts it on the **Clear–Chaotic cliff**: a dual-run cutover or a contract lapse could drop it straight into Chaos with no graceful degradation.

The **fixed go-live date the CFO wants is itself a Disorder issue**: it bundles a Clear deadline, a Complicated compliance scope, and a Complex integration into one promise, so no one can locate where the slip risk lives. It must be broken apart before it can be answered.

| # | Issue | Domain | Action model | Confidence |
|---|---|---|---|---|
| 1 | Hitting the regulatory deadline in 9 months | Clear | Sense → Categorize → Respond | High |
| 2 | Mapping data + compliance scope onto the new provider | Complicated | Sense → Analyze → Respond | High |
| 3 | Integration that stalled twice | **Complex** | Probe → Sense → Respond | High |
| 4 | Will the migration lift checkout conversion | **Complex** | Probe → Sense → Respond | High |
| 5 | Keeping the *old* provider live through cutover | **Clear: on the cliff** | Sense → Categorize → Respond | Medium |
| 6 | The CFO's demand for one fixed go-live date | **Disorder** | Break into parts and classify each | Medium |

**Flags up front:** Issue 5 sits on the cliff. Issue 6 is in Disorder and must be decomposed, not answered. Issues 3 and 4 are the misdiagnosed Complex pair driving the repeat slips.

---

## 3. The portfolio

The mix, laid out by domain:

```
  ORDERED                          UNORDERED
  ┌──────────────────────┐        ┌──────────────────────┐
  │ CLEAR                 │       │ COMPLEX               │
  │  #1 Regulatory date   │       │  #3 Stalled integration│
  │  #5 Old provider live │ ◄cliff│  #4 Conversion lift   │
  │      (on the cliff)   │       │                       │
  ├──────────────────────┤        ├──────────────────────┤
  │ COMPLICATED           │       │ CHAOTIC               │
  │  #2 Data + compliance │       │  (none: yet; #5 lands │
  │      mapping          │       │   here if it falls)   │
  └──────────────────────┘        └──────────────────────┘
            DISORDER (center): #6 "one fixed go-live date"
```

Five issues classified, one (#6) still in Disorder pending decomposition. The center holds the thing the CFO most wants pinned down, which is exactly the part no one can yet locate in a real domain.

---

### Issue 1: Hitting the regulatory deadline in 9 months → **Clear**

**Evidence.** The deadline is a fixed, externally-set date with an unambiguous compliance requirement (the new scheme rules take effect, the old acceptance path is decommissioned). Cause-and-effect is obvious: miss it and the payment rail stops settling. Any reasonable observer agrees on what "done" means and when. A known procedure exists, scope the mandated changes, certify against the scheme, switch on by date.

**Action model.** SENSE the exact mandated requirements → CATEGORIZE against the scheme's certification checklist → RESPOND with the standard compliance program. First concrete move: pull the scheme's official conformance checklist and the decommission notice, confirm the real date and the real minimum scope.

**Practice:** Best practice. There is one right answer, certified by the deadline, and it is the same answer every quarter the scheme runs it.

**Misdiagnosis risk.** Treating the *deadline* as Complex ("we can't really know if we'll make it") imports false uncertainty and invites slippage as a self-fulfilling prophecy. The deadline is fixed and the minimum scope is knowable; the uncertainty lives in issues 3 and 4, not here. Conflating them is precisely the error that produced issue 6.

---

### Issue 2: Mapping data and compliance scope onto the new provider → **Complicated**

**Evidence.** Migrating tokenized card data, stored mandates, subscription schedules, dunning rules and tax logic onto the new provider's data model is solvable, but only by experts who know both schemas, PCI scope, and the SCA/3DS edge cases. There are several defensible mapping strategies (big-bang re-tokenization vs. provider-to-provider token migration vs. re-collection), each with known trade-offs. The relationship between cause and effect is stable, what a payments engineer learns about the mapping today still holds next month.

**Action model.** SENSE the current data model and obligations → ANALYZE the mapping options with payments/PCI expertise → RESPOND with a defensible migration design. First move: stand up a data-mapping spike with one engineer plus the new provider's solutions architect; produce a field-by-field crosswalk and a token-migration feasibility answer.

**Practice:** Good practice. More than one right answer; choose among defensible options on cost/risk, do not chase a single recipe.

**Misdiagnosis risk.** Treating this as Clear, "it's just data migration, follow the runbook", skips the analysis a genuinely Complicated mapping needs and ships the silent data-loss bugs that surface only in production. The opposite error (treating it as Complex and probing endlessly) wastes the deadline budget on a problem that an expert can actually answer in advance.

---

### Issue 3: The integration that stalled twice → **Complex** ⚠ *misdiagnosed*

**Evidence.** Two prior plans stalled in integration and **no one can say why**. That is the signature of Complex, not Complicated: if it were knowable in advance, expert analysis would have caught it the second time, and it didn't. The integration touches many interacting systems, checkout, billing, ledger, fraud, the provider's webhooks and retry semantics, async settlement timing, whose behavior under real load is coherent only in retrospect. Acting on the system (wiring up one path) changes what the next path does. Repeated attempts to plan the integration whole have failed.

**Action model.** PROBE with small, safe-to-fail integration experiments → SENSE which interactions produce the failure mode → RESPOND by amplifying what holds and damping what breaks. First move: build a thin vertical slice, one product, one payment method, sandbox provider, behind a flag, carrying zero real money, and observe webhook ordering, retry, and idempotency behavior end-to-end. Do not plan the whole integration; instrument one path and watch.

**Practice:** Emergent. The integration design that works will reveal itself through the slices; it cannot be specified up front, which is why the two up-front plans slipped.

**Misdiagnosis risk.** This is the core error in the whole project. Treated as **Complicated**: "analyze harder, write a more detailed integration plan", it fails again, slower and more expensively, because the answer is emergent. Two slipped plans are two instances of exactly this misdiagnosis. Treated as Clear ("follow the provider's quickstart") it fails outright on the first real edge case.

---

### Issue 4: Will the re-platform lift checkout conversion → **Complex**

**Evidence.** Conversion is an emergent property of customer behavior interacting with a new flow, new 3DS challenges, new error copy, new latency. You cannot know in advance whether the new provider lifts or *drops* conversion; provider swaps routinely do both. Acting changes the system (the new flow is the new system). Many interacting variables, no stable pre-measurable relationship. The hope that the migration "lifts conversion" is an untested hypothesis riding along on a compliance project.

**Action model.** PROBE with A/B exposure → SENSE the conversion delta on real traffic → RESPOND by amplifying the variants that lift and damping those that don't. First move: define the conversion metric and guardrails *now*, and plan a percentage-ramp (1% → 5% → 25%) on the new provider once issue 3's slice is live, so conversion is measured, not assumed.

**Practice:** Emergent.

**Misdiagnosis risk.** Treating it as Clear ("new provider = better checkout, obviously") bakes an unvalidated revenue assumption into the business case. Treating it as Complicated ("model the conversion lift in a spreadsheet up front") produces a confident number that real traffic will ignore. The danger is *coupling* this Complex bet to the Clear deadline, letting an emergent conversion experiment hold the mandatory compliance cutover hostage.

---

### Issue 5: Keeping the *old* provider live through cutover → **Clear, on the cliff** ⚠

**Evidence.** The existing billing on the old provider is the most stable, best-understood thing in the estate. It works, it settles money, no one touches it. That is precisely the danger. Cause-and-effect is obvious *today*; confidence in it is total; attention has drifted entirely to the new build. A dual-run period, a token-migration cutover, an expiring contract, or a scheme change on the *old* rail can break the settled process all at once, and Clear does not degrade gracefully into Complicated. It falls off the cliff into Chaos (payments stop, no fallback, mid-cutover).

**Action model.** SENSE the live state continuously → CATEGORIZE against known-good → RESPOND with the procedure. But the real work here is **cliff defense**, not routine operation: maintain a tested rollback to the old provider for the entire dual-run window, confirm the old contract outlasts go-live plus a buffer, and alarm on settlement-rate drops.

**Practice:** Best practice, with explicit anti-complacency instrumentation bolted on.

**Misdiagnosis risk.** Treating it as permanently Clear ("the old system is fine, ignore it") is the cliff. The most dangerous issue in any portfolio is the one everyone is most sure is under control; this is that issue. If it falls, it lands in **Chaotic**, and the only move there is act-to-stabilize (roll back, restore settlement) before anything else.

---

### Issue 6: The CFO's demand for one fixed go-live date → **Disorder**

**Evidence.** "Give me one fixed go-live date" cannot be classified as stated, because it bundles three different kinds of cause-and-effect into a single promise: the Clear regulatory deadline (#1, genuinely fixed), the Complicated compliance/data scope (#2, knowable), and the Complex integration (#3, *not* knowable in advance). A fixed date is honest for the first, defensible for the second, and a fiction for the third. No one knows which domain the *date* lives in, which is the definition of Disorder, and the reason it keeps slipping: the slip risk is hidden inside a number that pretends to be Clear.

**The move (no action model, decompose).** Break the date into its parts and classify each:
- The **mandatory compliance cutover** (Clear/Complicated) → can carry a committed date; this is what the CFO actually needs for the board.
- The **integration readiness** (Complex) → cannot carry a fixed date; carries an evidence-based confidence range that tightens as slices land.
- The **conversion lift** (Complex) → must be *decoupled* from go-live entirely; it is a post-cutover experiment, not a launch gate.

Reframe the CFO's question from "what's the date?" to "what's the **committed compliance date** (fixed) and the **integration confidence range** (narrowing weekly as probes report)?" That answer is both honest and board-ready.

**Misdiagnosis risk.** This *is* the misdiagnosis, institutionalized. Forcing the Complex integration under a Clear date is what produced two slipped plans. Answering "yes, here's your fixed date" a third time repeats it. Leaving it in Disorder lets everyone's comfort domain take over, the CFO imposes a date (process), the engineers ask for more analysis, no one probes.

---

## 4. Action and frameworks

The domain-appropriate move and the right tool for each, **in attack order**:

| Order | Issue | Move | Framework / tool to reach for |
|---|---|---|---|
| **1st** | #6 Disorder: the date | Decompose the date into compliance-date (fixed) + integration-confidence-range. Stop the project from being run as one promise. | **tosca-problem-definition** / **mece-decomposition**: split before solving |
| **2nd** | #5 Cliff: old provider | Build and test the rollback; confirm old contract outlasts go-live; alarm on settlement rate. Do this *before* touching cutover. | Operational runbook + SOP, chaos/rollback drill |
| **3rd** | #3 Complex: integration | Ship one thin, money-free vertical slice behind a flag; instrument webhooks/retry/idempotency; let design emerge. **Do not write a bigger plan.** | Experiment design, short feedback loops, feature flags, vertical-slice / tracer-bullet |
| **4th** | #2 Complicated: data mapping | Expert spike: field-by-field crosswalk, token-migration feasibility, PCI scope. Pick among defensible options. | The analytic frameworks: decision tree on migration strategy, expert review |
| **5th** | #1 Clear: deadline | Pull the scheme's conformance checklist; scope the mandated minimum; run the standard compliance program. | Checklist / SOP / standard compliance playbook |
| **last** | #4 Complex: conversion | Decouple from go-live. After cutover, ramp 1%→5%→25% on real traffic and measure. | A/B test, percentage ramp, analytics |

**Why this order.** Disorder first, because until the date is decomposed the whole portfolio is mis-run and every other action inherits the false framing. The cliff second, because an undefended old provider is the catastrophic tail risk and rollback must exist before any cutover. The Complex integration third, because it is the actual schedule driver and the thing that has failed twice: it needs probes running *early* so its confidence range starts narrowing. The Complicated and Clear pieces are real work but are the ones that *can* be planned, so they slot in behind the experiments. Conversion is last and decoupled: it is a bet, not a gate.

**The one-sentence reframe for the CFO:** *You get a committed, fixed compliance cutover date; you get a weekly-narrowing confidence range on integration readiness from live probes; and the conversion lift comes off the launch gate entirely so it can never hold the deadline hostage.*

---

## 5. Movement

What to watch, and what to reclassify when it appears:

- **#3 Integration: Complex → Complicated.** The signal is a **repeatable pattern from the slices**: e.g., "webhook ordering is the failure every time, and this idempotency-key scheme fixes it." When a probe reveals a stable, repeatable relationship, the integration stops being emergent and becomes analyzable. *Then* you can write the detailed plan and commit a date, not before. This is the moment the integration earns a place under issue 1's fixed-date discipline.
- **#4 Conversion: Complex → Complicated, then archive the assumption.** Once the ramp produces a stable measured delta, the conversion question is answered by data and stops being a live experiment. Watch for the variant whose lift holds across two ramp steps.
- **#2 Data mapping: Complicated → Clear.** Once the crosswalk and token-migration path are proven on a slice, the mapping hardens into a repeatable runbook. Re-sort it to Clear and codify the procedure.
- **#5 Old provider: Clear → Chaotic (the cliff).** The warning signals: settlement-rate dip during dual-run, an approaching old-contract expiry, a scheme change on the old rail, or simply *no one looking at it anymore*. If any fires, this issue has fallen, switch immediately to the Chaotic move (act-to-stabilize: roll back, restore settlement, *then* diagnose). The trigger to re-examine is calendar-driven: review the old provider's health and contract every sprint until decommission is fully complete.
- **#6 The date: Disorder → resolved.** Once decomposed (action 1), Disorder shrinks to zero on this axis. Watch for it to *re-form*: if a new pressure (a board ask, a competitor launch) re-bundles the compliance date and the integration bet back into one promise, the situation slides back into Disorder and must be split again.

Tie to context: with six people and nine months, the schedule is dominated by **#3**. The single highest-leverage thing the team can do this week is start the first safe-to-fail integration slice, because that, not another planning cycle, is what converts the Complex unknown into a Complicated knowable and lets the CFO's date stop being a fiction.

---

## 6. Caveats

- Cynefin classifies the *kind* of cause-and-effect to choose an *approach*; it does not produce the migration plan. The answer to the integration still comes from running the probes, not from this report.
- The boundaries between domains are **judgments, not facts**. #5 (old provider) is classified Clear-on-the-cliff but is one missed contract date from Chaotic; #2 (data mapping) could prove Complex if the token migration turns out to have no stable answer. These near-fold placements are working hypotheses, not verdicts.
- The framework guards against misdiagnosis but cannot prevent it where evidence is thin. The two **medium-confidence** placements, #5 (depends on contract/dual-run facts not fully known here) and #6 (Disorder by construction, pending the decomposition), are exactly the ones to revisit first as the situation reveals itself.
- The load-bearing claim of this analysis is that **#3 and #4 are Complex, not Complicated**. If that is wrong, if a payments expert genuinely *can* analyze the integration to a reliable plan in advance, then the right move reverts to better up-front planning. But two slipped plans are strong evidence against that, and the cheap test (start one slice) settles it quickly either way.
- All figures, dates, and team details here are illustrative for documentation purposes and were not researched.
