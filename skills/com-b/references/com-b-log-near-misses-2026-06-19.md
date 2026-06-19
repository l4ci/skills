# COM-B: Field engineers logging safety near-misses

> _Illustrative example output for the `com-b` skill. The wind-turbine service operator, its engineers, and its app are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Behaviour diagnosed:** Field engineers log every safety near-miss in the mobile app, before leaving the site, on the day it happens.
- **Actor:** The 240 field engineers servicing wind-turbine sites, mostly working solo or in pairs.
- **Context:** Logging dropped ~70% after the paper form was retired; a reminder-email campaign three months ago changed nothing; a fix is needed before the Q3 safety audit.
- **Date:** 2026-06-19
- **Framework note:** This is COM-B (Michie, van Stralen & West) with the Behaviour Change Wheel. COM-B diagnoses *one specific behaviour by one specific actor*, not a safety culture, not the app, not the engineering org. Everything below is anchored to the single action above.

---

## 1. The behaviour

**Who:** A field engineer on the wind-turbine maintenance crew (population of 240, predominantly lone or paired working, dispersed across remote on- and offshore-adjacent sites).

**What:** Records a near-miss, an unplanned event that could have caused harm but did not, as a structured entry in the new mobile app.

**When:** Before leaving the site, on the same day the event occurred.

**Where:** At the turbine site, frequently at height, often in poor connectivity, frequently with gloves on and PPE up.

This is the concrete action every component is judged against. The implicit "should" version of the behaviour ("engineers care about safety") is *not* the unit of analysis; the logging action is.

---

## 2. Verdict

**The binding constraint is Opportunity, specifically Physical Opportunity, not Motivation.** The behaviour collapsed the moment the *tool* changed (paper form retired), not when anyone's attitude changed. The new app demands data entry at the worst possible moment and place: gloved hands, height, dead signal, and the strong pull to descend and move to the next job. A second, reinforcing barrier sits in Psychological Capability (the app's flow is unclear and the definition of "near-miss" is fuzzy). Motivation is broadly intact, the email campaign proved that, by moving the needle zero. You cannot persuade your way past a 4-minute form on a phone you can't see through a fogged visor with no bars.

| Sub-component | Verdict | Severity | Confidence |
|---|---|---|---|
| Physical capability | Sufficient |: | High |
| Psychological capability | Barrier | Medium | Medium |
| **Physical opportunity** | **Barrier** | **High** | **High** |
| Social opportunity | Barrier | Low–Medium | Medium |
| Reflective motivation | Sufficient (mostly) |: | Medium |
| Automatic motivation | Barrier | Low–Medium | Medium |

**Rolled up to the three components:** Capability: partial barrier (psychological). **Opportunity, the binding constraint (physical).** Motivation, broadly sufficient, with a minor automatic drag.

---

## 3. Component scan

### Capability

**Physical capability, Sufficient.** *(Confidence: High)*
- *Evidence (fact):* The engineers are already trained to operate phones/tablets for work orders, parts lookup, and time entry; tapping a form is not a physical-skill gap.
- *Evidence (fact):* They logged near-misses reliably on the paper form for years, they are physically capable of the *recording* act.
- *Interactions:* Their physical capability to use a phone is real but is throttled by Physical Opportunity, gloves, height, glare, and a fogged visor turn a trivial tap into a fiddly one. The skill exists; the conditions to exercise it do not.

**Psychological capability, Barrier.** *(Severity: Medium, Confidence: Medium)*
- *Evidence (fact):* The app routes near-miss entry through a 6-screen flow originally designed for full incident reports; engineers report not knowing which path is the "quick" one.
- *Evidence (assumption):* The definition of "near-miss" is under-specified for these workers, when in doubt whether an event "counts," the cognitively cheap default is not to log. (Plausible from the dropoff pattern, not measured.)
- *Evidence (fact):* There was app training at rollout, but it was a single remote session; retention across 240 dispersed lone workers is thin.
- *Interactions:* This compounds Physical Opportunity. A long, ambiguous flow is survivable at a desk; on a turbine in bad light it becomes the reason to defer "until later," which becomes never.

### Opportunity

**Physical opportunity, Barrier. THE BINDING CONSTRAINT.** *(Severity: High, Confidence: High)*
- *Evidence (fact):* Connectivity at many sites is poor; the app appears to require (or is believed to require) a live connection to submit, so an on-site attempt fails or stalls, training the engineer not to try.
- *Evidence (fact):* The moment of the near-miss is the *worst* moment to enter data: at height, gloved, PPE up, hands occupied, daylight glare on the screen.
- *Evidence (fact):* The strong competing cue is "get down, secure the site, drive to the next job." Logging competes with that and loses; the paper form won because it lived in the cab and took 30 seconds at the end of the day.
- *Evidence (assumption):* No offline draft / no end-of-day batch entry path exists or is discoverable. (Inferred from the symptom; verify in the build.)
- *Interactions:* This is the gate. It throttles the engineers' real physical and psychological capability and overrides their intact motivation. Remove this and the behaviour can flow; leave it and no amount of persuasion or training restores logging.

**Social opportunity, Barrier.** *(Severity: Low–Medium, Confidence: Medium)*
- *Evidence (assumption):* Lone/paired working means there is rarely a peer or supervisor present to model or prompt logging at the moment it matters, the social cue the paper form's end-of-day handover used to carry is gone.
- *Evidence (assumption):* If "no one else is logging either," a descriptive norm of *not* logging can set in quickly after a tool change. (Likely given the 70% drop; not surveyed.)
- *Interactions:* Reinforces the physical barrier. Weak social prompting means nothing reminds the engineer in the absence of a system cue.

### Motivation

**Reflective motivation, Sufficient (mostly).** *(Confidence: Medium)*
- *Evidence (fact):* The reminder-email campaign, pure reflective-motivation lever, produced no measurable change. If intention were the gap, a credible appeal would have moved it; it did not.
- *Evidence (assumption):* Safety-critical engineers in this trade generally believe near-miss reporting matters; the value is not in dispute, the *act* is blocked. (Reasonable, not measured.)
- *Interactions:* Intact motivation is precisely why the motivation reflex is the wrong place to spend. Willing people are being stopped by the world, not their will.

**Automatic motivation, Barrier.** *(Severity: Low–Medium, Confidence: Medium)*
- *Evidence (fact):* The paper form was a *habit* tied to an end-of-day ritual; retiring it broke the cue-response loop, and no new habit has replaced it.
- *Evidence (assumption):* A failed/stalled submit on poor signal is a small punishment that trains avoidance, each failure makes the next attempt less likely. (Plausible reinforcement mechanism.)
- *Interactions:* Downstream of Physical Opportunity. Fix the friction and the negative reinforcement stops; pair it with a new cue and a habit can re-form.

---

## 4. Diagnosis and interventions

### The binding constraint

The behaviour stopped when the **tool and its physical demands** changed, not when anyone's beliefs changed. **Physical Opportunity is the binding constraint** (severity High): the app requires data entry at height, gloved, in glare, on poor signal, against a strong competing pull to descend and move on, and likely fails to submit offline. Psychological Capability (ambiguous flow, fuzzy "near-miss" definition) is the reinforcing secondary barrier; Social Opportunity and Automatic Motivation are minor drags downstream of the same friction.

### The motivation reflex: checked explicitly

The obvious framing, and the org's first move, was *motivation*: a reminder-email campaign. **It is the classic, expensive error, and the evidence refutes it.** The campaign changed nothing, which is exactly what COM-B predicts when you push motivation at an opportunity gap. The engineers are willing; they are *prevented*. Any further "remind / encourage / re-train on why safety matters" spend will produce the same null result. **The gap is Opportunity, not Motivation.** Say it plainly to whoever owns the Q3 audit remediation.

### Mapping constraints to intervention functions

Read deficit → function (not the reverse):

| Binding constraint | Function(s) per the mapping | Rejected & why |
|---|---|---|
| Physical opportunity (primary) | **Environmental restructuring**, **Enablement** | Not Persuasion/Incentivisation: those address motivation, which is intact |
| Psychological capability (secondary) | **Enablement**, **Education**, **Training** | Education alone is insufficient; the flow must be *changed*, not just explained |
| Social opportunity (minor) | **Modelling**, **Environmental restructuring** |: |
| Automatic motivation (minor) | **Environmental restructuring** (new cue) | Coercion is overkill and would corrode willing reporting |

### Targeted interventions (for these engineers, this app, this context)

**Primary: close the physical-opportunity gap (do these first):**

1. **Offline-first capture with auto-sync (Environmental restructuring + Enablement).** Let the engineer save a near-miss with no signal; the app queues it and submits when connectivity returns. This single change removes the stall-and-give-up loop that is training avoidance. *Highest-leverage fix; everything else is secondary to it.*
2. **A 2-tap "quick near-miss" path (Enablement).** Strip the entry to: category, one-line description, optional photo, done, under 30 seconds, gloved-hand-sized targets, high-contrast for glare. Defer the full incident-report flow to a later "add detail" prompt. Restore the *speed* the paper form had.
3. **Sanctioned end-of-day batch logging in the cab (Environmental restructuring).** Explicitly permit logging at the truck after descent rather than at height. This re-creates the paper form's winning ritual, a calmer moment and place, without pretending engineers will tap forms on a ladder.

**Secondary, close the psychological-capability gap (do alongside):**

4. **Embed a one-line "what counts as a near-miss" prompt at the point of entry (Education + Enablement).** Put 3 examples in the app at the moment of logging, not in a training deck no one revisits. Kill the "does this even count?" hesitation that produces silent non-logging.

**Tertiary, re-form the cue and norm (do after friction is gone):**

5. **A reliable end-of-job cue (Environmental restructuring → Automatic motivation).** Trigger a logging prompt on job-completion/clock-out in the same app, rebuilding the habit loop the paper form used to own.
6. **Lightweight modelling/feedback (Modelling + Social opportunity).** Share anonymised "near-miss of the week" learnings back to crews so logging visibly feeds something, restoring a reporting norm among lone workers.

### Secondary constraint waiting behind the binding one

Once friction falls and volume returns, the next barrier surfaces in **Psychological Capability + Social Opportunity**: consistency of *what* gets logged and whether the influx is triaged and fed back. If reports pour in but nothing visibly happens with them, Reflective and Automatic Motivation will erode ("why bother, it goes into a void"). Pair the friction fix with a closed feedback loop, or the recovery will fade after the Q3 audit.

---

## 5. Caveats

- COM-B diagnoses **one specific behaviour at a point in time**: same-day on-site near-miss logging by field engineers, not the org's safety culture, not the app as a product, not reporting behaviour in general.
- The mapping to intervention functions **narrows the field; it does not guarantee** a chosen intervention works. Offline capture is the right *class* of fix, but its execution (latency, sync reliability, UI under glare) still has to be got right.
- Several assessments are marked **assumption**: the "near-miss" definition ambiguity, the descriptive-norm drift, the failed-submit reinforcement. These are the cheapest things to verify before the build: a 30-minute ride-along with two engineers would confirm or kill most of them.
- **Removing the binding constraint may unmask the masked one.** Restoring volume can expose a triage-and-feedback gap that current low volume hides. Watch for it.
- All figures here are illustrative for documentation purposes and were not researched.
