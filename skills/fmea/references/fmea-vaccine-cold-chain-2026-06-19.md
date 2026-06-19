# FMEA: Vaccine Cold-Chain Delivery: Regional Depot to Rural Clinics

> _Illustrative example output for the `fmea` skill. The cold-chain process, incident history, and organization are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Subject:** End-to-end cold-chain process delivering temperature-sensitive vaccines (2–8 °C) from the regional depot to rural clinics.
- **Boundary:** Starts at **depot dispatch** (vaccine pulled from depot cold room into the packing area). Ends at **clinic refrigerator handover** (vials accepted and placed in the clinic fridge). Manufacturing/upstream supply, and in-clinic administration after handover, are **assumed reliable and out of scope.** The depot cold room itself is assumed in-spec at the moment of pull.
- **Type:** Process FMEA (PFMEA), units are process steps.
- **Date:** 2026-06-19
- **Framework note:** FMEA scores each failure mode on three anchored 1–10 scales, computes RPN = S × O × D and Criticality = S × O, ranks, and forces an action onto every prioritized mode that reduces S, O, or D.

### Scales (anchors, abbreviated)

- **Severity (S):** 1 none · 4–5 moderate loss of function · 6–7 major loss/cost · 8 primary function lost, regulatory warning · 9 hazardous **with** warning (safety/regulatory) · 10 hazardous **without** warning.
- **Occurrence (O):** 1 essentially never · 2–3 low/isolated · 4–6 occasional · 7–8 repeated/poorly controlled · 9–10 frequent/almost certain.
- **Detection (D, inverted, low is good):** 1 poka-yoke certain catch · 2–3 robust/automated · 4–6 checks exist but miss · 7–8 weak/manual/sampled · 9–10 remote/none.

### Action threshold

The regulator requires documented risk controls before launch, so the bar is set conservatively:

- **Threshold:** any mode with **RPN ≥ 100** requires a documented action.
- **Severity override:** any mode with **S ≥ 9** requires an action **regardless of RPN**: patient-safety and regulatory failures are never "low priority" on the strength of a detection control alone.

---

## 1. Verdict

The dominant risk is **silent thermal excursion**: vaccine that has gone out of the 2–8 °C band but is administered anyway because nobody knows. Three of the top four modes share this signature, a **failed cooler-box seal (RPN 280)**, **coolant packs conditioned wrong so they freeze the vaccine (RPN 252)**, and **transit excursion that goes unrecorded between manual log points (RPN 224)**. All three carry **S = 9**: a vaccine that has frozen or cooked is inert, and a clinic that cannot prove the chain held must discard stock and may breach the regulator's documentation requirement, with no warning to the nurse drawing the dose.

The current process leans almost entirely on **manual detection**: clinics log fridge temps by hand, transit has no continuous record, which is exactly the wrong lever: detection catches a failure it does not prevent, and a manual check that runs twice a day cannot catch an excursion that happens between checks. The seal failure that caused both spoilage incidents last year is still controlled only by a visual check at packing.

The headline actions therefore attack **O and D with prevention-grade controls**, not more paperwork:

1. **Single-use electronic freeze/heat indicator inside every cooler box** (poka-yoke), turns a silent excursion into a visible, irreversible flag at handover. Cuts D on the three top modes from 7–8 to 2.
2. **Pre-conditioned coolant packs with a conditioning checklist and a phase-change (not hard-frozen) pack**: removes the freeze-the-vaccine cause. Cuts O on the conditioning mode from 7 to 3 and S from 9 to 7 (freeze no longer reaches the vaccine).
3. **Replace the reusable seal with a tamper-evident single-use closure plus a 2-second seal-seat check**: attacks the exact cause of last year's two incidents. Cuts O from 5 to 2.

These three actions move the worst-ranked modes from RPN 280/252/224 down to target RPNs of **40/63/28** respectively.

---

## 2. The FMEA table

One row per failure mode, sorted by current RPN. **Bold S** marks the S ≥ 9 override. Criticality = S × O.

| # | Step / function | Failure mode | Effect(s) | S | Cause(s) | O | Current controls | D | RPN | Crit | Recommended action | Target RPN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Packing & seal (contain cold) | Cooler-box seal fails; box loses thermal integrity | Vaccine warms above 8 °C in transit; inert dose given, no warning; stock discard + regulatory exposure | **9** | Reusable gasket degrades/misseated | 5 | Visual seal check at packing (manual) | 7 | **280** | 45 | **D→** electronic excursion indicator in box; **O→** single-use tamper-evident closure | 40 |
| 2 | Coolant conditioning | Packs too cold (hard-frozen) freeze the vaccine | Vaccine frozen → permanently inert; no warning at point of use | **9** | Packs taken straight from freezer, not conditioned to phase-change temp | 7 | Informal "let them sit" rule, no timer/checklist | 4 | **252** | 63 | **O→** conditioning checklist + phase-change packs; **S→** packs can't reach freezing temp | 63 |
| 3 | Transit temperature monitoring | Excursion occurs and goes unrecorded between manual readings | Chain integrity unprovable; either discard good stock or ship suspect stock | **9** | No continuous logger; readings only at load/unload | 4 | Manual temp note at dispatch and arrival | 8 | **224** | 36 | **D→** continuous data-logger per box, alarmed | 28 |
| 4 | Clinic fridge transfer | Box left out of fridge too long at handover | Vaccine warms during the gap; cumulative time-out-of-fridge breach | 7 | Busy clinic, no defined transfer-time limit | 6 | None specific; nurse judgment | 6 | 252 | 42 | **O→** 5-minute transfer SOP + door-open timer; **D→** indicator (action 1) carries through | 56 |
| 5 | Clinic fridge storage (to acceptance) | Clinic fridge itself out of range at handover | Vaccine placed into an already-warm/cold fridge; excursion continues | 8 | Old/un-serviced clinic fridge; no min/max alarm | 4 | Manual twice-daily fridge log | 7 | 224 | 32 | **D→** min/max alarm thermometer; **O→** fridge service schedule | 32 |
| 6 | Depot dispatch (pull & stage) | Wrong product/quantity pulled; vaccine staged warm too long | Delay warms vaccine; wrong stock to wrong clinic | 6 | Manual pick, no scan; staging area uncontrolled temp | 5 | Paper picklist, supervisor spot-check | 6 | 180 | 30 | **O→** barcode pick-verify; **D→** staging-area temp alarm | 48 |
| 7 | Packing & seal | Under-packing: too few coolant packs for route duration | Temp drifts up on long rural routes; partial excursion | 7 | Pack count not matched to route length | 4 | Standard pack count regardless of route | 6 | 168 | 28 | **O→** route-length pack table; **D→** indicator (action 1) | 42 |
| 8 | Transit | Delivery delayed beyond cooler-box hold time | Hold time exceeded; whole box excursion | 7 | Vehicle breakdown, weather, route detour | 4 | Driver phone contact, no hold-time spec | 6 | 168 | 28 | **D→** logger alarm + hold-time spec on box label; **O→** backup-vehicle plan | 42 |
| 9 | Coolant conditioning | Packs too warm; insufficient cooling capacity | Slow warm-up; sub-clinical excursion on long routes | 6 | Over-conditioned / left out too long | 5 | Same informal rule as mode 2 | 5 | 150 | 30 | **O→** conditioning checklist (action 2) | 54 |
| 10 | Clinic fridge transfer | Handover documentation not completed | No record of chain integrity at acceptance; regulatory gap | 8 | Manual paper log, busy clinic, optional sign-off | 4 | Paper handover form | 7 | 224 | 32 | **D→** mandatory indicator-read + digital sign-off | 32 |
| 11 | Depot dispatch | Vaccine pulled outside the 2–8 °C band (cold room edge) | Excursion starts before the box is even sealed | 8 | Pulling from a poorly-mixed cold-room shelf | 2 | Cold-room mapping (boundary-assumed in-spec) | 5 | 80 | 16 | **D→** pre-pack temp spot-read (override: S=8 <9, monitor) | 48 |
| 12 | Transit | Box physically damaged / crushed in vehicle | Insulation compromised; localized excursion | 5 | Poor load securing, stacking | 3 | Driver loading guidance (informal) | 5 | 75 | 15 | **O→** load-securing SOP; below threshold, batch with SOP rollout | 36 |

**Threshold line (RPN ≥ 100):** modes 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 are above threshold and require action. Modes 11 and 12 fall below RPN 100 but **mode 11 carries S = 8**: close to the override line and worth a cheap detection control, batched in. No mode below threshold carries S ≥ 9.

**Severity-override flags (S ≥ 9):** modes 1, 2, 3. All three already clear the RPN threshold, so the override changes no priorities here: but it is the reason none of them can be "closed" by a detection control alone; each carries a prevention action (O or S) as well.

---

## 3. Per-unit detail

### Step 1: Depot dispatch (pull & stage) · *confidence: medium*

The boundary assumes the cold room is in-spec, so the live risks are at the *interface*: pulling the wrong stock (mode 6, RPN 180) and pulling from a marginal shelf edge (mode 11, RPN 80). Occurrence on the pick error (O = 5) reflects a fully manual paper pick with only a spot-check. Mode 11's O = 2 is low because the cold room is assumed reliable per boundary; its S = 8 is high because an excursion that starts pre-seal is invisible to everything downstream. Confidence is medium, no incident history here, scores are anchored to process design rather than data.

### Step 2: Coolant conditioning · *confidence: high*

The most dangerous single step. Hard-frozen packs against vaccine vials is the classic cold-chain own-goal: the freeze excursion (mode 2) is **as damaging as heat and far more likely**, because the failure is a missing step, not a rare event. O = 7 reflects that there is no timer, no checklist, only an informal "let them sit" habit, repeated, poorly controlled. S = 9 because a frozen vaccine is permanently inert with no warning. D = 4 is moderate only because a hard-frozen pack is sometimes visible at packing. This step earns its high confidence: freeze damage from un-conditioned packs is a well-documented mechanism, not a guess.

### Step 3: Packing & seal · *confidence: high*

Houses the incident-history mode. The seal failure (mode 1, RPN 280) is the **highest-RPN row in the analysis** and is the direct lineage of last year's two spoilage incidents traced to a failed cooler-box seal. O = 5 (occasional, reusable gasket degrades) and D = 7 (visual check at packing is manual and easily passed by a seated-but-degraded seal) are anchored to that history, hence high confidence. Under-packing (mode 7) and the seal share the same weak detection: nothing inside the box reports the consequence.

### Step 4: Transit · *confidence: medium*

Three modes (3, 8, 12) share the same root gap: **no continuous record between the manual dispatch and arrival readings.** Mode 3 (RPN 224, S = 9) is the marquee, an excursion can occur and resolve entirely between two manual touchpoints, leaving the chain unprovable. O = 4 is moderate (excursions are occasional, not constant), but D = 8 is the analysis's worst detection score: a reading taken only at the endpoints cannot see the middle. Confidence is medium; transit duration and ambient variability on rural routes are estimated, not measured.

### Step 5: Clinic fridge transfer · *confidence: medium*

The handover gap (mode 4, RPN 252) and the documentation gap (mode 10, RPN 224) both stem from a busy clinic with no defined transfer-time limit and an optional paper sign-off. Mode 10 carries S = 8 because an undocumented handover is a **regulatory** failure independent of whether the vaccine is actually good, the regulator requires the record. O = 4 to 6 reflects predictable human-factors pressure in understaffed clinics.

### Step 6: Clinic fridge storage (to acceptance) · *confidence: medium*

Mode 5 (RPN 224): placing good vaccine into an already-out-of-range clinic fridge. The clinic fridge sits just inside the boundary (up to acceptance). S = 8, O = 4 (old un-serviced units are occasional), D = 7 because the only control is the **manual twice-daily log named in the context**: strong on paper, blind between readings.

---

## 4. Action plan

Prioritized by current RPN, with the override modes carrying a prevention action even where a detection action also helps. Owner placeholders are `[OWNER]`. Prevention (S, O) is preferred over detection (D) wherever both were available, noted per action.

| Pri | Mode(s) | Action | Lever | Why this lever | Before → Target RPN | Owner |
|---|---|---|---|---|---|---|
| **A1** | 1, 3, 4, 7, 8 | **Single-use electronic freeze/heat excursion indicator inside every cooler box**, read and recorded at handover | **D** (1→cause), poka-yoke | Turns every silent excursion across packing and transit into one irreversible, visible flag at the fridge door. One control covers five modes. Detection here is justified because it makes an *otherwise invisible* failure visible at the safety-critical moment | 280 → 40 (mode 1) | `[OWNER]` |
| **A2** | 2, 9 | **Conditioning checklist + phase-change (not hard-frozen) coolant packs** | **O** + **S** | Prevention beats detection: removes the freeze cause (O 7→3) *and* changes the design so packs physically can't reach a vaccine-freezing temperature (S 9→7). The strongest action in the plan: it lowers two terms | 252 → 63 (mode 2) | `[OWNER]` |
| **A3** | 1 | **Replace reusable seal with single-use tamper-evident closure + 2-sec seal-seat confirmation** | **O** | Attacks the exact cause of last year's two incidents: a degraded/misseated reusable gasket. Removes the reuse-degradation mechanism entirely (O 5→2) | combines with A1 → 40 | `[OWNER]` |
| **A4** | 3, 8 | **Continuous alarmed data-logger per box; hold-time spec printed on box label** | **D** + **O** | Closes the transit blind spot; the hold-time spec plus a backup-vehicle plan reduces the delay cause (O on mode 8) | 224 → 28 (mode 3) | `[OWNER]` |
| **A5** | 4, 10 | **5-minute transfer SOP + door-open timer; mandatory indicator-read & digital handover sign-off** | **O** + **D** | Bounds the human-factors gap and converts the optional paper form into a required digital record: directly satisfies the regulator's documentation control | 252 → 56 (mode 4); 224 → 32 (mode 10) | `[OWNER]` |
| **A6** | 5 | **Min/max alarm thermometer in every clinic fridge + quarterly fridge service schedule** | **D** + **O** | The manual twice-daily log is blind between readings; an alarm catches excursions continuously and the service schedule reduces the out-of-range cause | 224 → 32 | `[OWNER]` |
| **A7** | 6 | **Barcode pick-verify at dispatch + staging-area temp alarm** | **O** + **D** | Error-proofs the manual pick and bounds staging warm-up | 180 → 48 | `[OWNER]` |
| **A8** | 7 | **Route-length-keyed coolant pack-count table** | **O** | Matches cooling capacity to route duration; removes the one-size pack count | 168 → 42 | `[OWNER]` |
| **A9** | 11, 12 | **Pre-pack temp spot-read; load-securing SOP** (batched, below threshold) | **D** + **O** | Cheap controls bundled into the SOP rollout; mode 11 monitored for its S = 8 | 80 → 48; 75 → 36 | `[OWNER]` |

**Why detection still appears on the override modes:** A1 is a detection control, yet it lands on three S ≥ 9 modes. It is justified *only because it is paired with prevention*: A2 lowers the freeze cause and A3 removes the seal cause. The indicator is the safety net that makes a residual excursion visible at the point of use; it is not the primary defense. Per the framework, a low D on a high-S mode is fragile on its own, so prevention carries the weight and detection backs it up.

**Net effect:** the three override modes drop from RPN 280 / 252 / 224 to **40 / 63 / 28**, and every above-threshold mode lands below 100 in its target state.

---

## 5. Caveats

- **RPN is ordinal, not arithmetic.** Modes 3, 5, and 10 all sit at current RPN 224 but are **not the same risk**: mode 3 is (S9, O4, D8), a safety item reached through weak detection; mode 5 is (S8, O4, D7); mode 10 is (S8, O4, D7), a regulatory documentation item. The tie was broken by severity, then criticality, putting mode 3 first. Equal RPNs from different triples are not equivalent and were not treated as such.
- **Severity can override the number.** Modes 1–3 carry S = 9 and would warrant action even had their RPNs fallen below 100. Mode 11 (S = 8, RPN 80) sits below threshold but is flagged and monitored precisely so it is not lost to RPN tunnel vision.
- **Detection scores reflect today's controls and decay.** The D values assume the named current controls (visual seal check, manual fridge log, endpoint temp notes) keep running as described. The moment a clinic stops logging twice daily, those D scores are stale and the real risk is higher than the table shows. The plan deliberately replaces fragile manual detection (A1, A4, A6) rather than adding more of it.
- **The analysis only covers enumerated modes.** A failure nobody listed is invisible to this FMEA. Plausible un-scored modes, power loss at the depot cold room (excluded by boundary), counterfeit/expired stock, driver tampering, were left out by scope, not because they are impossible. Revisit the boundary if any of those become live.
- **Scores are calibrated judgment, not measurement.** Modes anchored to the two real incidents (mode 1) and to documented freeze mechanics (mode 2) carry high confidence; transit and clinic-side scores are medium-confidence estimates that should be replaced with logger data once the loggers from A4 are in the field. The target RPNs are projections of where each action should land, not guaranteed outcomes, they require post-implementation re-scoring to confirm.
- **All figures here are illustrative for documentation purposes and were not researched.**
