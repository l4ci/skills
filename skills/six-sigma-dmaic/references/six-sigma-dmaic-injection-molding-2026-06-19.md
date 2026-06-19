# DMAIC: Injection-Molding Phone-Case Line

> _Illustrative example output for the `six-sigma-dmaic` skill. This molding line is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Process:** Injection-molding cell producing TPU/PC phone cases (the molding cell only, not downstream assembly).
- **Date:** 2026-06-19
- **Project owner:** Second-shift line lead (Marisol R.); sponsor is the plant quality manager.
- **Data source:** MES scrap log (per-shift, per-reason), 12 weeks pulled for baseline.

---

## 1. Define

### Problem statement

Visible cosmetic defects (flash and short shots) on the phone-case molding line have risen from roughly 3% of units scrapped (Q2 2025) to about 8% (trailing 12 weeks ending 2026-06-13), measured at the molding cell's outfeed inspection. The increase is sustained, not a single bad lot.

*No presumed cause and no solution is stated in the problem.* The earlier draft, "8% scrap because the molds are worn", had a cause baked in; it was stripped. Mold wear is a hypothesis for Analyze, not a premise.

### Goal and target

Return the molding-cell cosmetic scrap rate to **3% or below** within the project window, and hold it there for at least four consecutive weeks under a control plan. Stretch: ≤2%.

### Scope

- **Start of scope:** resin loaded at the hopper of the molding cell.
- **End of scope:** part placed on the outfeed conveyor after the molding-cell visual check.
- **Out of scope:** assembly, printing/decoration, packaging, resin procurement.

### Customer and CTQs

Customer is the internal retail brand, which specifies **zero visible cosmetic defects** on shipped cases. CTQs for the molding cell:

| CTQ | Requirement | How a defect shows |
|---|---|---|
| No flash | No excess material at the parting line / vents | Thin fin or web on edge |
| Complete fill (no short shot) | Full part geometry, all corners/bosses formed | Missing/under-filled corner or button cutout |
| Surface finish | No sink marks, no flow lines in cosmetic zones | Visible dimple or streak |

Flash and short shots are the two reasons driving the rise; surface finish is stable and treated as secondary.

### SIPOC

| Suppliers | Inputs | Process | Outputs | Customers |
|---|---|---|---|---|
| Resin vendor; masterbatch vendor; tooling shop; maintenance | TPU/PC resin + colorant; mold tool; machine (clamp/inject/cool); operator setup | Dry → load → inject → pack/hold → cool → eject → visual check | Molded case (pass) or scrap (flash/short) | Assembly cell → retail brand |

### Gate: Define

**Is the problem clear, measurable, and worth solving?** Yes. The defect is defined, the rise is quantified against a baseline period, scope is bounded to the molding cell, and at ~8% scrap on a high-volume line the cost of poor quality clearly justifies the project. No solution is presumed. **Gate passed.**

---

## 2. Measure

### Defect and metric definition

- **Defect (unit):** any case scrapped at the molding-cell visual check for **flash** or **short shot**. (Surface-finish scrap is logged separately and excluded from the project metric.)
- **Primary metric:** cosmetic scrap rate = (flash + short-shot scrap units) ÷ total units molded, per shift.
- **Opportunity definition (for DPMO):** 2 cosmetic opportunities per unit (flash, fill). Baseline ≈ **40,000 DPMO** (~3.3σ).

### Data-collection plan

Twelve weeks of existing MES scrap records pulled (3 shifts × 7 days). Each scrap event already carries: timestamp, shift, machine ID (cell runs 4 presses, M1–M4), mold/cavity, resin lot, and operator-entered reason code. Added for the project: a one-week confirmation count where QA re-inspected scrap to validate reason codes.

### Measurement-system check (can we trust the numbers?)

The reason codes are **operator-entered**, so the system was sanity-checked before trusting it:

- QA re-inspected 300 logged scrap parts. Reason-code agreement with QA: **flash 96%, short shot 91%**, with the main confusion being short shots mis-tagged as "other." Agreement is adequate to proceed; "other" is treated cautiously.
- Total-units denominator comes from the machine cycle counter, independently verified against the day's good-part tally: within 0.4%.

Verdict: the metric is trustworthy enough for baselining. The known weak spot (the "other" bucket) is flagged for Analyze.

### Baseline and variation

| Reason | Share of scrap | Approx. scrap rate |
|---|---|---|
| Flash | 58% | 4.6% |
| Short shot | 31% | 2.5% |
| Other (surface, handling) | 11% | 0.9% |
| **Cosmetic total (flash + short)** | **89%** | **7.1–8.0%** |

Variation is **not uniform.** Two patterns stand out in the baseline and are carried into Analyze as leads, not conclusions:

- **By machine:** M3 runs ~13% cosmetic scrap; M1/M2/M4 run ~5–6%. M3 is an outlier.
- **By shift:** night shift runs ~2 points higher than day, concentrated in the first two hours.

### Gate: Measure

**Do we trust the baseline?** Yes. The metric is defined, the measurement system was checked (code agreement ≥91% on the two relevant defects, denominator verified), and a baseline with its variation (machine and shift signals) is established. **Gate passed.**

---

## 3. Analyze (parallel root causes)

Four analyst lenses were run in parallel, each returning candidate causes with reasoning. Pooled and deduped below, then each was **tested against the MES data** with the line lead. Only causes the evidence supports are kept.

### Candidate causes (pooled from the parallel lenses)

| Lens | Candidate cause |
|---|---|
| Equipment | C1: M3 clamp tonnage drifting low → mold opens slightly under injection pressure → flash |
| Equipment | C2: Worn parting-line surface on the M3 tool → flash |
| Materials | C3: Resin moisture (inadequate drying) → short shots / splay |
| Materials | C4: Regrind ratio crept up → inconsistent fill |
| Process / method | C5: No standardized startup warm-up → cold-tool short shots at shift start |
| Process / method | C6: Hold pressure/time set per-operator, not per-spec → fill variation |
| People | C7: Night-shift operators less trained on M3 setup |
| Environment | C8: Plant humidity swing affecting resin at the hopper |
| Measurement | C9: "Other" bucket hiding mis-tagged short shots (from Measure) |

### Data tests applied

| Cause | Test against data | Result |
|---|---|---|
| C1 (clamp tonnage low) | Pulled M3 clamp-tonnage logs; cross-checked flash events | **Supported.** M3 tonnage reads 8–11% below setpoint; flash on M3 correlates with the low-tonnage windows. |
| C2 (worn parting line) | Tooling inspection + flash pattern by cavity | **Partly.** M3 tool shows mild parting-line wear, but flash is general across cavities, pointing more to clamp force (C1) than localized wear. Kept as secondary. |
| C3 (resin moisture) | Dryer dew-point logs vs. short-shot timing | **Not supported.** Dew point in spec throughout; no correlation. Rejected. |
| C4 (regrind ratio) | Batch records | **Not supported.** Regrind held at 15% per spec; no drift. Rejected. |
| C5 (no warm-up standard) | Short shots vs. time-since-shift-start | **Supported.** Short shots spike in the first ~90 min of each shift, worst on night shift after the idle gap. Cold-tool startup is real. |
| C6 (per-operator hold settings) | Setup-sheet audit vs. machine setpoints | **Supported (contributing).** Hold pressure varied ±12% between operators on the same mold; tighter on day shift. |
| C7 (night training) | Scrap by operator/shift | **Re-attributed.** The night-shift signal is explained by C1 (M3) + C5 (cold start), not operator skill per se. Not a standalone root cause. |
| C8 (plant humidity) | Same dew-point logic as C3 | **Not supported.** Rejected. |
| C9 ("other" mis-tags) | QA re-inspection from Measure | **Confirmed measurement artifact, not a process cause.** ~30% of "other" was short shots → true short-shot share slightly higher. Adjusts the data, not the cause list. |

### Proven root causes (the vital few)

1. **C1: M3 clamp tonnage running below setpoint**, letting the mold breathe open under injection pressure. Primary driver of the flash excess (and most of the machine-level outlier).
2. **C5, No standardized cold-start warm-up procedure**, producing short shots in the opening ~90 minutes of each shift, worst on night shift.
3. **C6, Operator-to-operator variation in hold pressure/time** (contributing, secondary), widening fill variation.

C2 (mild tool wear) is logged as a watch item. C3, C4, C7, C8 are rejected against data.

### Gate: Analyze

**Are the root causes proven, not merely plausible?** Yes, C1, C5, and C6 each pass a data test (tonnage logs, time-since-start correlation, setup-sheet audit), and the four most "plausible-sounding" alternatives (moisture, regrind, humidity, night-training) were **rejected by the data.** This is the gate DMAIC most often fails; it was passed on evidence, not assertion. **Gate passed.**

---

## 4. Improve

### Solution options (targeting proven causes)

| Targets | Option | Impact | Feasibility |
|---|---|---|---|
| C1 | Recalibrate M3 clamp, fix tonnage-drift cause (worn pressure sensor / hydraulic), add tonnage alarm | High | High (maintenance window) |
| C1/C2 | Refurbish M3 parting line | Med | Low (tool out of service, cost): deferred |
| C5 | Standard warm-up: dummy-shot cycle + tool-temp confirm before first good part each shift | High | High |
| C6 | Lock hold pressure/time per mold in machine recipe; remove operator discretion | Med-High | High |
| C6 | Operator retrain on setup sheet | Low-Med | High |

### Selection

Chosen for the pilot: the high-impact / high-feasibility set:

- **Recalibrate M3 clamp + add a tonnage low-alarm** (C1).
- **Standard cold-start warm-up procedure** (C5).
- **Lock hold pressure/time in the machine recipe** (C6).

Parting-line refurbishment (C2) deferred as a watch item; recalibration is expected to resolve most of the flash without taking the tool offline.

### Pilot design

- **Where:** M3 only (the outlier), all shifts.
- **Duration:** 3 weeks.
- **Measure of success:** M3 cosmetic scrap drops from ~13% toward the ≤3% target, with the first-90-minutes short-shot spike eliminated. No regression on M1/M2/M4.

### Pilot result (against the metric)

| Metric | Pre-pilot (M3) | Pilot (M3) |
|---|---|---|
| Cosmetic scrap rate | 13.1% | **3.4%** |
| Flash share | 9.0% | 1.9% |
| Short-shot share | 3.8% | 1.3% |
| First-90-min short-shot spike | Present every shift | Gone (within normal run) |

Cell-wide projected scrap if rolled to all presses: ~7.4% → **~3.0%**. The change moved the metric, confirmed by data. Cleared for rollout to M1/M2/M4 with the same recipe lock and warm-up standard.

### Gate: Improve

**Does the pilot move the metric?** Yes: M3 cosmetic scrap fell 13.1% → 3.4% over three weeks with the startup spike eliminated and no regression elsewhere. Confirmed with data before recommending rollout. **Gate passed.**

---

## 5. Control

### Control plan

| Item | Control |
|---|---|
| Clamp tonnage (C1) | Standing **low-tonnage alarm** on all presses; auto-flag below 5% of setpoint. Tonnage on the daily maintenance check. |
| Cold-start (C5) | Warm-up procedure added to the **shift-start SOP**; tool-temp confirmation logged before first good part. |
| Hold settings (C6) | Hold pressure/time **locked in the machine recipe**, password-protected; changes require lead sign-off. |
| Tool wear (C2 watch) | Quarterly parting-line inspection on M3. |

### Monitoring and response rules

- **Control chart:** weekly p-chart of cosmetic scrap rate per press, with control limits set from the post-pilot data.
- **Reason-code quality:** monthly QA re-inspection of a scrap sample to keep code agreement ≥90% (closes the old "other" gap from Measure).
- **Response rules:**
  - Single point above the upper control limit → line lead investigates that shift's tonnage + warm-up log same day.
  - Two consecutive weeks trending up, or any press back above 5% → reopen Analyze on that press; do not just re-tune.

### Owner handover

Process owner: **second-shift line lead (Marisol R.).** Holds the SOP, the p-chart, and the response rules; reports the weekly scrap number to the quality manager. Project team steps back after the four-week hold is confirmed.

### Gate: Control

**Will the gain hold without the project team?** Yes: the three root-cause fixes are embedded in equipment (alarm), procedure (SOP), and the locked recipe rather than depending on people remembering; monitoring with response rules and a named owner is in place. **Gate passed (pending the four-week hold confirmation).**

---

## 6. Phase gates: record

| Phase | Gate question | Answered |
|---|---|---|
| Define | Problem clear, measurable, worth solving? | Yes: defect defined, ~8% vs. 3% baseline, scope bounded, no presumed solution. |
| Measure | Do we trust the baseline? | Yes: code agreement ≥91% on flash/short, denominator verified, baseline + variation established. |
| Analyze | Root causes proven, not plausible? | Yes: C1/C5/C6 pass data tests; moisture/regrind/humidity/training rejected by data. |
| Improve | Does the pilot work? | Yes: M3 13.1% → 3.4% over 3 weeks, confirmed by data. |
| Control | Will the gain hold without the team? | Yes: alarm + SOP + locked recipe + p-chart + owner; pending 4-week hold. |

---

## 7. Caveats

- Conclusions are only as good as the data and the measurement system behind them. The reason-code agreement was adequate (≥91% on the two relevant defects) but not perfect; the monthly re-inspection rule exists to keep it honest.
- Verified root causes **reduce, not eliminate**, the chance of a wrong fix. C2 (tool wear) was deliberately deferred, not dismissed; if scrap creeps back on M3 specifically, it is the first thing to revisit.
- The pilot proved the fix on **M3 only**. Rollout to M1/M2/M4 assumes the same root causes apply there; the per-press p-chart is what will confirm or refute that assumption.
- A gain holds only if Control is real. The verdict above is provisional until the four-week hold is observed under the control plan.
- All figures here are illustrative for documentation purposes and were not researched.
