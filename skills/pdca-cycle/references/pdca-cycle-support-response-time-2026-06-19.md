# PDCA: Support first-response time

> _Illustrative example output for the `pdca-cycle` skill. The support team, ticket volumes, and figures below are fictional; every name and number is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Focus:** First-response time on support tickets is averaging 9 hours; target is under 4.
- **Date:** 2026-06-19
- **Context:** Four-person support team, tickets via Zendesk, no triage rota today, response-time stats available per week.

---

## Cycle 1: Morning triage rota

### Plan

- **Objective:** Cut the weekly median first-response time from ~9h toward the <4h target, without adding headcount.
- **Current situation (just enough to act):** Tickets sit untouched overnight and pile up by morning. With no rota, all four agents dip into the same queue ad hoc, so the oldest tickets are not anyone's job and slip until someone happens to grab them. The lag is mostly at the *front* of the day, not throughout it.
- **The change:** Introduce a daily morning triage rota. One named agent owns the queue 08:00–11:00, working strictly oldest-first and sending a first response (even a holding reply) to every ticket opened overnight before taking on new same-day work. Rotate the owner daily so it is one person's burden per day, not four people's distraction.
- **Prediction:** Weekly **median** first-response time drops from ~9h to **≤5h** within one week; the overnight backlog (tickets older than 8h at 08:00) clears by ~10:00 each day instead of lingering past noon. We did *not* expect to hit <4h from this change alone.
- **Measure:** Zendesk weekly first-response report, median and 90th-percentile first-response time, plus a count of tickets still unanswered at the 8h mark. One-week run, compared against the prior four-week baseline.

### Do

- Ran the rota for one week (Mon–Fri). Maya, Tom, Priya, and Devin each took one morning slot; Maya took two (five weekdays, four agents).
- Posted the oldest-first rule and a one-line holding-reply template in the team channel.
- **What actually happened:** The rota ran as planned four of five days. **Surprises:**
  - On the Wednesday the owner was pulled into an escalation for ~90 minutes, and the queue regressed that morning, a single absence broke the whole mechanism, because ownership was a single point of failure.
  - The holding-reply template was used more than expected and customers responded well to it; several threads resolved in one round because the holding reply asked the right clarifying question up front.
  - New same-day tickets arriving *after* 11:00 still waited, because the rota only covered the morning.

### Check

- **Results vs. prediction:**
  - Weekly median first-response time fell to **4.8h** (predicted ≤5h), **prediction met.**
  - 90th-percentile fell from ~22h to ~11h, large gain, but still far from target.
  - Overnight backlog cleared by ~10:15 on the four clean days; on the disrupted Wednesday it lingered to ~13:00.
- **Learning, measured against the prediction:** The rota works and roughly hit the predicted median. But the median improvement is fragile (one absence undid a morning) and the *afternoon* is now the dominant source of slow responses, the bottleneck moved rather than disappeared. The holding-reply template was an unplanned win worth keeping regardless of the rota's fate.

### Act

- **Decision: Adjust.** The rota earned its place as the new baseline, but it does not reach <4h on its own and has a single-point-of-failure flaw. Keep it; iterate.
- **Concretely:** Adopt the rota *and* the holding-reply template into standard practice now. Carry two problems into Cycle 2: (a) coverage gaps when the owner is pulled away, and (b) afternoon response lag.
- **New baseline:** Daily morning triage rota (08:00–11:00, oldest-first, holding-reply template) + the holding-reply template as standard for all first responses. Median first-response time ~4.8h.

---

## Cycle 2: Plan only (teed up for the next loop)

- **Objective:** Close the remaining gap to <4h and remove the single-point-of-failure.
- **Candidate change:** Add a named **backup owner** each day (so an escalation does not break triage) and extend coverage with a lighter **afternoon sweep** at 14:00 that clears anything opened since 11:00.
- **Prediction (to be set with the user before running):** median ≤3.5h, 90th-percentile ≤7h, no morning regression on days the primary owner is pulled away.
- **Measure:** same Zendesk weekly report, one-week run against the Cycle 1 baseline.

---

## Running standard

After Cycle 1's adopted changes, the current standardized practice is:

1. **Daily morning triage rota**, 08:00–11:00, one named owner, rotating daily.
2. Owner works the queue **oldest-first** and sends a **first response to every overnight ticket** before taking same-day work.
3. **Holding-reply template** used for all first responses, leading with a clarifying question.

Accumulated gain so far: median first-response time **~9h → ~4.8h** in one cycle. Target <4h not yet reached; pursued in Cycle 2.

---

## Caveats

- PDCA trades depth for speed. One week is a small trial; the 4.8h median holds **in this team's context and that week's ticket mix**, not universally, a holiday week or a product incident could move it.
- The gain sticks only because Act **standardized** the rota and template into the running standard. Had we stopped at "it worked," the improvement would have evaporated by the next busy week.
- The bottleneck **moved** (morning fixed, afternoon now dominant) rather than vanishing, typical of a fast loop, and exactly why Cycle 2 follows rather than declaring victory.
- These figures are illustrative for documentation and were not researched.
