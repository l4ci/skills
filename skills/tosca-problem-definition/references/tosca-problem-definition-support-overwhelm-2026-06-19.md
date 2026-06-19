# TOSCA brief: Support team overwhelm

> _Illustrative example output for the `tosca-problem-definition` skill. The company and its support operation are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

**Date:** 2026-06-19
**Raw problem, in the owner's words:** "Customer support is overwhelmed and tickets keep piling up."

---

## Problem statement

> **How can the VP of Customer Experience cut the support backlog from ~1,400 open tickets to under 300 and bring median first-response time back under 8 business hours within the next quarter (by 2026-09-30), without adding headcount beyond the two reqs already approved and without degrading the current 4.4/5 CSAT?**

This is the headline deliverable. It is specific (a named backlog and response-time gap), measurable and time-bound (1,400→<300, median FRT <8h, by Q3 close), decision-oriented (it serves the VP's staffing-and-process decision), answerable (an issue tree can resolve it), and free of an embedded solution, it does *not* say "hire more agents" or "buy a chatbot," both of which surfaced during the interview as candidate answers, not as the problem.

---

## TOSCA brief

### Trouble

The felt pain is "swamped," but the interview pushed past it. "Overwhelmed" and "tickets piling up" are symptoms. The underlying gap:

- **Inflow has outrun throughput since the April release.** Daily ticket inflow rose from ~180 to ~310 after the v4 billing redesign shipped in April; agent throughput stayed flat at ~190/day. The backlog is the integral of that gap, it grows ~120 tickets/day and now sits at ~1,400 open, oldest at 19 days.
- **A large share is self-inflicted and repetitive.** A first-pass tag audit suggests ~40% of new tickets are billing-confusion tickets traceable to the v4 change (unclear proration, a relabeled invoice line). These are not "more demand", they are a defect leaking into support.

Why now, not later: the oldest tickets are aging past the 14-day mark where CSAT collapses, the two approved reqs won't onboard for 6–8 weeks, and the Q3 board review reports a support SLA the team is now missing. Doing nothing means the backlog crosses ~2,500 and FRT past 24h before new hires are productive.

**Root vs. symptom:** "Support is overwhelmed" was reframed to *a post-release defect is generating ~40% of inflow while throughput is structurally capped*, solving that removes the symptom; throwing bodies at the symptom does not.

### Owner

- **Owner: Priya Raman, VP Customer Experience.** Owns the support SLA, the support budget, and the two open reqs. Accountable to the COO for the Q3 SLA number.
- **What she values:** protecting CSAT (her board-facing metric) first, then SLA recovery, then cost, in that order. She will not trade CSAT for a faster but worse backlog burn-down.
- **Authority check:** Priya can reallocate agent time, approve overtime, and prioritize the two reqs. She *cannot* unilaterally force the Billing/Product team to fix the v4 defect, that is the single most important limit on her authority and the reason Product appears as a potential blocker under Actors.

### Success criteria

| Dimension | Metric | Target | By |
|---|---|---|---|
| Backlog | Open tickets | < 300 | 2026-09-30 |
| Responsiveness | Median first-response time | < 8 business hours | 2026-09-30 |
| Quality (guardrail) | CSAT | ≥ 4.4 / 5 (no degradation) | maintained throughout |
| Cost (bound) | Net new headcount | ≤ 2 (already approved) | n/a |

**Trade-off named:** backlog burn-down and CSAT pull against each other: the fastest way to clear tickets (terse, templated mass-closes) tanks satisfaction. Priya's stated priority is CSAT-protected burn-down, so CSAT is a hard guardrail, not a target to optimize. Speed serves the backlog goal *only up to* the CSAT floor.

### Constraints

| Constraint | Real or assumed | Note |
|---|---|---|
| ≤ 2 net new hires this quarter | **Real** | Budget locked for Q3; finance confirmed no further reqs. |
| New hires not productive for 6–8 weeks | **Real** | Onboarding + tooling access is a fixed lead time. |
| Cannot degrade CSAT below 4.4 | **Real** | Owner's hard guardrail; board-reported. |
| "We can't touch the v4 billing flow this quarter" | **Assumed** | Stated as fixed, but never tested with Product. A defect fix or even an in-app clarification could remove ~40% of inflow: challenging this is the highest-leverage move. Flagged for resolution. |
| "Chatbot/automation is the only scalable answer" | **Assumed** | This is a smuggled solution, not a constraint. Stripped out; logged as a hypothesis to test, not a boundary. |
| Current tooling (Zendesk + macros) stays | **Assumed** | Treated as fixed by habit; macro/triage reconfiguration is likely available within the quarter. |

### Actors

| Actor | Interest | Can block? |
|---|---|---|
| Priya Raman (VP CX) | Hit SLA, protect CSAT, stay in budget | Owner: drives |
| Support agents (team of 11) | Sustainable load, not punished for backlog they didn't cause | Low: but morale/attrition risk if mishandled |
| Product / Billing lead (Marco) | Protect the v4 roadmap; reluctant to reopen shipped work | **Yes**: controls the defect fix that drives ~40% of inflow |
| COO | Q3 SLA number for the board | No, but sets the deadline pressure |
| Customers (esp. billing-confused cohort) | Clear invoices, fast answers | No: but their tickets *are* the inflow |
| Finance | Hold the headcount line | Indirect: owns the budget constraint |

The interview initially omitted Product/Billing entirely. Surfacing Marco as a blocker is the brief's most consequential addition: the root cause sits in a team the owner cannot command.

---

## Open questions

1. **Is the ~40% billing-confusion share real?** The tag audit was first-pass. A clean sample of 200 recent tickets should confirm the proportion before betting the plan on a defect fix.
2. **Will Product fix or clarify the v4 flow this quarter?** Unresolved. If no, the plan must lean harder on triage/deflection; if yes, the inflow problem largely dissolves. This is the pivot variable.
3. **What is the true sustainable throughput per agent at the CSAT floor?** ~190/day is observed, but it's unclear whether that's a ceiling or a function of current triage chaos.
4. **Are any of the backlog's oldest tickets already lost?** Some 19-day tickets may be auto-resolvable (customer churned/self-served), which would shrink the real backlog before any work.

---

## Stress-test notes

Three critic subagents reviewed the draft TOSCA in parallel. The strongest challenges and their resolution:

- **Critic A (root & solution):** Flagged that "tickets keep piling up" was being treated as the problem when it is an *output*; and that "scalable automation" had crept into the constraints as if it were a boundary. **Resolved:** Trouble reframed to the inflow-vs-throughput gap with the v4 defect as the named root; the automation assumption was stripped from Constraints and demoted to a hypothesis.
- **Critic B (owner & success):** Challenged whether "reduce the backlog" was measurable (it wasn't: no number, no date) and warned that backlog speed silently conflicts with CSAT. **Resolved:** Success criteria given explicit targets and a deadline; the CSAT/speed trade-off was named and CSAT set as a hard guardrail with the owner's priority stated.
- **Critic C (constraints & actors):** Caught the missing blocker, the draft had no Product/Billing actor, despite the root cause living there, and questioned whether "can't touch v4" and "tooling is fixed" were real or assumed. **Resolved:** Marco/Product added as a blocking actor; both constraints re-marked as assumed and routed to Open Questions 1–2.

One challenge left open: whether Product will actually act (Open Question 2). The framing is honest that the owner cannot force this, which is itself a finding.

---

## Suggested next step

Build an **issue tree** off the problem statement, splitting the backlog gap into its two MECE drivers: *reduce inflow* (fix/clarify v4, deflect repetitive billing tickets) and *raise throughput* (triage, macros, temporary reallocation, the two new hires once productive). Size each branch against the <300 / <8h targets before committing, and resolve Open Question 2 with Product first, since the inflow branch is worthless if the defect can't be touched. Hand the tree to a solving method (hypothesis testing or the relevant strategy skill); do not start staffing changes until the inflow share is confirmed.

---

## Caveats

- TOSCA frames the problem; it does not solve it. This brief defines *what to work on*, not the fix.
- The brief is only as good as the owner's honesty about constraints and success. Two load-bearing numbers (the ~40% billing share, the throughput ceiling) are still estimates, see Open Questions.
- If the situation shifts, Product commits to a v4 fix, a third req opens, CSAT priority changes, revisit the framing before continuing. A stale problem definition quietly steers good analysis at the wrong target.
- All figures here are illustrative for documentation purposes and were not researched.
