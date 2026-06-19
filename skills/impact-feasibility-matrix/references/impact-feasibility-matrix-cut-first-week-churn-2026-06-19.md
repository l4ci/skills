# Impact vs. Feasibility: Q3 Backlog Prioritization

> _Illustrative example output for the `impact-feasibility-matrix` skill. The product, squad, and backlog are fictional; every score, figure, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Objective:** Cut first-week churn for new B2B accounts.
- **Date:** 2026-06-19
- **Options scored:** SSO login, dark mode, a public API, in-app onboarding tour, GDPR data-export tool, Slack integration, mobile push notifications.
- **Context:** One product squad of five engineers, a single quarter. The public API depends on the auth refactor shipping first.

### Calibrated axes

Every option is judged on the same anchored scale.

**Impact** = how much the option reduces the share of new B2B accounts that go dark in their first seven days. The known first-week failure modes are: friction at signup/login, no clear "first value" moment, and the account never reaching the tool inside its existing workflow.

| Score | Impact (on first-week churn) |
|---|---|
| 5 | Directly removes a top-3 first-week drop-off cause for most new accounts |
| 4 | Removes a drop-off cause for a large segment, or a strong second-order effect |
| 3 | Plausibly helps activation but not aimed at the first-week window |
| 2 | Minor or indirect effect on new-account retention |
| 1 | No credible link to first-week churn |

**Feasibility** = how readily this squad can ship it inside one quarter, accounting for effort, cost, technical risk, and dependencies. High feasibility = low effort and low risk.

| Score | Feasibility (5 eng, 1 quarter) |
|---|---|
| 5 | Days of work, no dependency, low risk |
| 4 | 1–2 weeks, well-understood, minor unknowns |
| 3 | 3–5 weeks, some risk or one dependency |
| 2 | Most of the quarter, real technical risk or a hard dependency |
| 1 | Exceeds the quarter or carries severe risk/dependency |

---

## 1. The matrix

|  | **Low feasibility →** | **→ High feasibility** |
|---|---|---|
| **High impact ↑** | **Major projects**<br>· SSO login (I4 / F2)<br>· Public API (I3→ down-ranked, see note) | **Quick wins**<br>· In-app onboarding tour (I5 / F4)<br>· Slack integration (I4 / F4) |
| **Low impact ↓** | **Thankless tasks**<br>· _(none)_ | **Fill-ins**<br>· Dark mode (I2 / F5)<br>· Mobile push notifications (I3 / F3)<br>· GDPR data-export tool (I2 / F3) |

The public API sits high on raw enthusiasm but scores low on *this* objective and is gated behind the auth refactor; it lands as a major project for the roadmap, not this quarter. See the dependency note in §4.

---

## 2. Scored options

| Option | Impact | Feasibility | Quadrant | Dependencies | Confidence |
|---|---|---|---|---|---|
| In-app onboarding tour | 5 | 4 | Quick win | none | High |
| Slack integration | 4 | 4 | Quick win | none | Medium |
| SSO login | 4 | 2 | Major project | none (but IdP variance is the risk) | Medium |
| Mobile push notifications | 3 | 3 | Fill-in | none | Low |
| Public API | 3 | 2 | Major project | **auth refactor must ship first** | Medium |
| GDPR data-export tool | 2 | 3 | Fill-in | none | High |
| Dark mode | 2 | 5 | Fill-in | none | High |

*Recalibration note (Stage 2):* the public API scorer returned Impact 4, framing it as a growth lever. Adjusted to **3**: it expands the ceiling for *integration partners and power users*, not for new B2B accounts in their first week, which is the stated objective. Without the recalibration it would have masqueraded as a quick win. SSO feasibility was returned as 3 by an optimistic scorer; revised down to **2** because "SSO" in B2B means SAML *plus* per-customer IdP quirks (Okta, Entra, Ping), which is where the time goes.

---

## 3. Quadrant detail

### Quick wins (do first)

**In-app onboarding tour: I5 / F4.** The single most direct lever on the objective. Today a new account logs in and faces an empty workspace with no guided path to first value; the tour walks them to their first completed action inside week one. Frontend-only, no backend dependency, the squad has the component library. The risk is design quality, not engineering, a bad tour annoys more than it helps, so it ships behind a flag with an instrument-and-iterate loop.

**Slack integration, I4 / F4.** Most new B2B accounts already live in Slack. A "results land where the team already is" notification gives the tool a reason to be opened in week one without the user remembering to come back. Well-trodden OAuth + incoming-webhook pattern, ~1.5 weeks. Confidence is Medium only because the activation lift is assumed from analogy, not measured, worth A/B confirming.

### Major projects (plan and stage, do not start casually)

**SSO login, I4 / F2.** Removes a real first-week wall: B2B buyers frequently *cannot* roll the tool out to their team until SSO exists, so accounts stall before they ever activate. High impact, but feasibility is low because each enterprise IdP is its own integration-and-testing burden. Break it down (SAML core first, then per-IdP hardening) and stage it; do not let it consume the squad mid-quarter.

**Public API, I3 / F2, gated.** Genuinely valuable for the platform, but aimed at the wrong objective for this quarter and blocked behind the auth refactor. Belongs on the roadmap, not the Q3 churn sprint.

### Fill-ins (only with spare capacity)

**Mobile push notifications, I3 / F3.** A plausible re-engagement nudge, but B2B first-week work happens on desktop; push is a weaker channel than Slack for this audience. Low confidence on the impact assumption.

**GDPR data-export tool, I2 / F3.** Low churn impact, but flagged as a possible **strategic must-do**: if it is a contractual/compliance blocker for closing enterprise deals, it overrides the matrix regardless of its score (see §5).

**Dark mode, I2 / F5.** Cheap and popular, with no credible link to first-week churn. The textbook fill-in. The danger is fill-in creep: it *feels* productive and could quietly eat the SSO breakdown time.

### Thankless tasks (drop)

None this round. Every option clears the "worth doing eventually" bar; the discipline here is sequencing, not deletion.

---

## 4. Dependencies

```
auth refactor ──► Public API        (hard: API cannot ship until auth refactor lands)
```

No option that targets the objective depends on another, so the quick wins are free to go first. The one hard dependency (auth refactor → public API) sits entirely inside the down-ranked major project, so it does not perturb the in-quarter sequence, it only confirms the public API is not a Q3 item.

---

## 5. Recommended sequence

1. **In-app onboarding tour first.** Highest impact on the objective, high feasibility, no dependency. Ship behind a flag, instrument the first-week activation funnel, iterate. This is the momentum win.
2. **Slack integration second.** The other quick win. Pairs with the tour: the tour creates first value, Slack pulls the team back to see it. Confirm the activation lift with an A/B test since its impact is assumed.
3. **Begin the SSO breakdown, staged.** Start SAML core now in parallel with a fraction of the squad; do not let it block the quick wins. It removes a real first-week wall but is a multi-sprint effort, plan it, don't lunge at it.
4. **GDPR export, only if it is a deal blocker.** If sales confirms it gates enterprise contracts, promote it above its score (strategic override). Otherwise it waits.
5. **Defer the public API to the roadmap.** Wrong objective for this quarter and gated behind the auth refactor. Revisit once the refactor is scheduled.
6. **Hold mobile push and dark mode as true fill-ins.** Touch them only with genuine spare capacity, and watch for fill-in creep, dark mode is the most likely culprit to quietly displace the SSO work.

**Stop doing:** treating the public API as a near-term churn lever, and letting dark mode's low cost tempt it ahead of the staged SSO work.

---

## 6. Caveats

- Scores are **judgment anchored to a stated definition**, not measurement. Change the objective and the whole ranking moves, dark mode and the public API both look very different under "increase platform stickiness" than under "cut first-week churn".
- **Feasibility is routinely overestimated.** SSO and the public API are the two most likely to run long; both were revised down from their first-pass scores for exactly this reason.
- **Dependencies override quadrant order**: though here the only hard dependency lives inside an already-deferred project, so the in-quarter plan is unaffected.
- **Strategic must-dos and hard constraints override the matrix.** The GDPR export is the live example: a low-impact fill-in by score, but a compliance/contract blocker would force it forward regardless.
- Several impact assumptions (Slack lift, push re-engagement) are **assumed, not validated**. The quick wins ship instrumented so the next round of this exercise runs on data, not analogy.
- All figures here are illustrative for documentation purposes and were not researched.
