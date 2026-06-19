# Design Thinking: Patient Discharge Experience

> _Illustrative example output for the `design-thinking` skill. The hospital, its patients, and its staff are fictional; every figure, quote, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

## 1. Header

- **Challenge:** Redesign how patients leave the hospital after surgery so they understand their aftercare.
- **Intended users:** Recovering inpatients aged 60+ on a surgical ward, and the family members or friends collecting them.
- **Date:** 2026-06-19
- **Context carried in:** 30-day post-discharge readmission rate sits at 18.4%, above the regional average of ~14%. We hold 11 discharge-nurse interviews but no patient-side research. Budget is tight, no new staff headcount, prototypes must be near-zero-cost.

---

## 2. Empathy

We synthesized the existing nurse interviews and then ran a small, cheap patient-side pass (8 bedside conversations across two wards, 4 family members in the pickup loop, 1 ride-along to a patient's home the morning after discharge). Captured against say / do / think / feel. **Evidence** is what we observed or heard directly; **Assumption** is what we are inferring and have not yet confirmed with a patient.

### What users say, do, think, feel

| Quadrant | Observation | Status |
|---|---|---|
| **Say** | "They went through the sheet so fast. I nodded because I just wanted to go home." (patient, 71) | Evidence |
| **Say** | "Nobody told me which pills replaced the ones I already take." (patient, 68) | Evidence |
| **Do** | Patients pocket the discharge folder unread; 3 of 8 could not locate it the next morning. | Evidence |
| **Do** | Discharge teaching happens at the moment of departure, when the family car is already waiting. | Evidence |
| **Do** | Family members photograph the wound-care instructions on their phones: the paper is distrusted as "losable." | Evidence |
| **Think** | Patients believe "the hospital will call if something is wrong": they treat discharge as the end, not a handoff. | Evidence |
| **Feel** | Relief to leave dominates everything; cognitive load is at its peak exactly when teaching is delivered. | Evidence |
| **Feel** | Family collectors feel responsible but uninformed: "I'm the one doing the care and I wasn't in the room." | Evidence |
| **Think** | Patients may under-report confusion to avoid delaying their own discharge. | Assumption |
| **Feel** | Anxiety about "bothering" clinicians suppresses follow-up phone calls in the first 72 hours. | Assumption |

### Needs and insights

- **Need:** Patients need aftercare they can act on *after the adrenaline of leaving has worn off*: because the teaching moment (departure) is the worst possible time to absorb instructions.
- **Need:** The family collector needs to be a first-class recipient of the information, because they, not the patient, often perform the actual aftercare.
- **Need:** Patients need a low-friction way to ask a question in the first 72 hours, because the silence is read as "everything is fine," and the readmission spike lives in that window.
- **Insight:** The discharge folder is an artifact of the hospital's process, not a tool for the patient. It is optimized for being handed over, not for being used at home at 6 a.m.

### Empathy gaps still open

- No data on what actually happens in the first 72 hours at home (the ride-along was one household).
- The two "Feel/Think" assumptions above are unconfirmed and load-bearing for the framing.

---

## 3. Point-of-view and How Might We

**Point-of-view (primary):**
> A recovering 60+ surgical patient and their family collector need aftercare information they can absorb and act on *after* leaving, because it is delivered at the one moment they are least able to take it in, the rush of going home, and the silence afterward is mistaken for safety.

**How Might We questions** (opening the space, not prescribing the answer):

1. HMW deliver aftercare teaching *before* the relief-of-leaving moment, while the patient can still absorb it?
2. HMW make the family collector a deliberate part of the handoff rather than a bystander in the corridor?
3. HMW turn the first-72-hours silence into a low-effort, two-way channel patients feel allowed to use?
4. HMW make the take-home aftercare artifact something patients actually reach for at home?

*Confirmed with the user before ideating.* HMW #1 and #3 were judged highest-leverage against the readmission metric; #2 and #4 carried forward as supporting.

---

## 4. Ideas

### Divergence (parallel idea generation)

Five idea-generator passes ran in parallel, each given the four HMW questions and a different lens. Pooled raw count: 41 ideas. Selected sample below.

| Lens | Representative ideas |
|---|---|
| **Analogous domains** (aviation pre-flight, restaurant order-back) | "Teach-back" read-aloud where the patient repeats instructions in their own words; pre-discharge "boarding pass" checklist; a pharmacist "order-back" of the new vs. old medication list |
| **Extreme users** (a patient with no family, a patient with dementia) | A single laminated one-page "fridge sheet" with three red-flag symptoms; a designated phone buddy assigned at admission; pictogram-only instructions |
| **Opposite-of-obvious** (don't add information: remove it) | Cut the folder to one page; replace teaching at departure with teaching the day *before*; a single phone number that beats the whole folder |
| **Constraint removal** (pretend budget and staffing are unlimited) | A nurse home-visit at 48 hours; an app with a recovery timeline; an AI follow-up call: *flagged as out-of-budget, kept for stripped-down variants* |
| **Existing-tech recombination** (use what the ward already has) | SMS check-in from the existing appointment-reminder system; reuse the ward whiteboard for a discharge-day countdown; a QR code on the wristband linking to a 90-second aftercare video |

### Convergence

Clustered the 41 into six themes (timing, the collector, the 72-hour channel, the artifact, teach-back, red-flag triage). Removed duplicates. Selected **three** to prototype, each chosen because it is cheap, attacks a high-leverage HMW, and tests a distinct assumption:

1. **The "day-before" teach-back** (HMW #1, #2): move teaching to the evening before discharge and have the patient *and* collector repeat it back. Tests whether timing, not content, is the problem.
2. **The one-page fridge sheet** (HMW #4), replace the folder with a single laminated red-flag-symptom sheet. Tests whether the artifact is the failure.
3. **The 72-hour SMS check-in** (HMW #3), a single "Reply 1 if all OK, 2 if you have a question" text at 48 hours, riding the existing reminder system. Tests whether the silence can be broken cheaply, and whether it's read as permission to ask.

*Deferred:* home-visits and an app (over budget); pictogram-only sheet (kept as a fallback if literacy turns out to be the blocker).

---

## 5. Prototypes

All three are deliberately rough and near-zero-cost.

| # | Prototype | Form (rough on purpose) | What it is meant to learn | Open question |
|---|---|---|---|---|
| 1 | Day-before teach-back | A script on an index card + a checklist the nurse runs the evening before, role-played first with staff | Does earlier timing improve absorption, and can the family collector be present a day ahead? | Is the bottleneck *when* we teach, or *what* we teach? |
| 2 | Fridge sheet | A single hand-drawn A4 page: 3 red-flag symptoms, "who to call," new-vs-old meds box. Printed, not designed. | Will patients actually reach for a one-pager at home when they ignored the folder? | Is the artifact the failure, or the moment? |
| 3 | 72-hour SMS check-in | A manual text sent from a ward phone (faking the automated system) at 48h | Do patients reply? Does a reply-2 surface real problems before they become readmissions? | Is the silence "fine" or "afraid to bother anyone"? |

---

## 6. Tests and learnings

Each prototype was put in front of real users seeking *disconfirmation*. Pre-set failure criteria stated below.

### Prototype 1: Day-before teach-back
- **Setup:** 6 patients, 5 with a family collector present the evening before. Observed the teach-back; asked nothing leading.
- **Would count as failure:** patients can't recall instructions next morning no better than the folder group.
- **Result:** 5 of 6 correctly stated their two red-flag symptoms the next morning, vs. an informal baseline of ~1 in 8. **Did not fail.** But: getting the collector there a day early worked only 2 of 5 times: logistics, not willingness.
- **Disconfirmed:** the assumption that *content* was the core problem. Timing dominated.

### Prototype 2: Fridge sheet
- **Setup:** Given to 7 patients at discharge; ride-along + phone follow-up at 48h.
- **Would count as failure:** sheet is lost or unread like the folder.
- **Result:** 6 of 7 had the sheet visible at home (fridge or bedside) at 48h. Two patients said the new-vs-old meds box was the single most useful thing they'd received. **Did not fail.** But two collectors still photographed it "in case", the laminate didn't fully kill the losable-paper fear.
- **Disconfirmed:** that patients won't engage with any paper. They will, if it's one page and load-bearing.

### Prototype 3: 72-hour SMS check-in
- **Setup:** Manual texts to 9 discharged patients at 48h.
- **Would count as failure:** low reply rate, or replies that surface nothing actionable.
- **Result:** 7 of 9 replied. 3 sent "reply 2", one was an early wound-infection sign that triggered a same-day clinic call *instead of* an ED visit. **Strong signal.** But one patient replied "1 (all OK)" and was readmitted the next day, a single text under-detects, and "1" may mean "I don't want to bother you," confirming the earlier assumption.
- **Disconfirmed:** that patients won't use a digital channel. Partly confirmed the "afraid to bother" assumption, a binary reply hides it.

---

## 7. Loop log

| Iteration | Mode worked | What we learned | Sends work back to |
|---|---|---|---|
| 1 | Empathize → Define | Teaching lands at peak cognitive overload; the collector is excluded; silence reads as safety | Define (framed POV + 4 HMW) |
| 2 | Ideate → Prototype → Test | Timing beats content (P1); a one-page artifact is used (P2); SMS breaks the silence but a binary reply hides fear (P3) |: |
| 3 | Test → **Define** | P3's "1 = I'm fine OR I'm afraid to bother you" ambiguity means HMW #3 was under-framed. Reframe: not "break the silence" but "make asking feel permitted and safe." | **Define** (sharpen HMW #3) |
| 4 | Test → **Empathize** | Collector-logistics failure in P1 is a real-world constraint we never researched. Need to understand the collector's day before redesigning the handoff. | **Empathize** (collector-side research) |
| 5 | Test → **Prototype** | P1 + P2 combine well; next prototype merges day-before teach-back *with* the fridge sheet as its teach-back script, and replaces P3's binary SMS with an open "How's recovery going?" prompt. | **Prototype** (combined v2) |

**Current state:** the work is mid-loop, not finished. Two threads diverge from the same round of testing: one back to Define (sharpen the asking-is-safe framing) and one back to Empathize (the collector's logistics). The next prototype is a merged teach-back-plus-sheet with an open-text SMS.

---

## 8. Caveats

- Design Thinking surfaces **desirable** solutions. Viability (does the SMS check-in scale without adding nurse load?) and feasibility (can the appointment-reminder system actually send and triage replies?) are untested and need separate validation before any rollout.
- Insights are only as good as the realness of the user contact behind them. This pass rests on **8 patient conversations and 1 ride-along**: directionally useful, not statistically sound. The two unconfirmed empathy assumptions (under-reporting confusion; fear of bothering staff) are load-bearing and only partially confirmed by P3.
- The readmission numbers here are illustrative for documentation and were not researched. A real engagement would tie prototype results to an actual readmission-rate measurement over a defined cohort and window.
- Progress is **learning, not stage completion.** Two of three prototypes "succeeded," yet the loop sent work backward, not forward, that is the method working.
