# Force Field Analysis: Four-Day Week for Support

> _Illustrative example output for the `force-field-analysis` skill. This support team and its figures are fictional; every number, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Change analyzed:** Move the 30-person customer-support team to a four-day, 32-hour week, no drop in pay, no drop in coverage, by Q3 (target go-live 2026-09-01).
- **Context:** Agents are burning out and attrition is high; finance worries about Friday coverage gaps; one team lead has piloted compressed hours informally; the CEO is open but wants proof response times won't suffer.
- **Date:** 2026-06-19.
- **Framework:** Kurt Lewin's force field analysis treats the status quo as an equilibrium held by driving forces (pushing toward the change) and restraining forces (holding the status quo). The field below is a starting read, not a fixed verdict, it shifts as the change proceeds, and acting on it changes it.

---

## 1. Verdict

**Feasible by Q3, but only if the coverage restrainer is dismantled first, not if the change is driven through on urgency alone.** The driving side is genuinely strong: attrition is bleeding the team, the people most affected want the change, and an informal pilot already exists to build on. But the field is held in place by one binding restrainer, the unmodelled Friday coverage gap that finance and the CEO are anchored on, and that single barrier blocks the change regardless of how the totals read. The leverage is to *solve coverage on paper and in a measured pilot* so the restrainer shrinks, rather than to push harder on burnout urgency, which would only provoke finance to push back harder. Totals come out 16 driving against 14 restraining, but the net read is not the arithmetic: weaken the coverage restrainer and the rest of the field tips decisively toward go-live.

---

## 2. The scored force field

```
DRIVING (toward four-day week)          →  ←  RESTRAINING (holding the status quo)
Attrition & burnout cost ........ 5      |     Friday coverage gap (unmodelled) ... 5
Agent demand for change ......... 4      |     Finance scepticism / cost risk ..... 4
Existing informal pilot ......... 3      |     CEO needs response-time proof ...... 3
Recruiting / employer brand ..... 2      |     Scheduling & tooling rework ......... 2
CEO openness .................... 2      |
----                                     |     ----
total 16                                 |     total 14
```

Totals: **16 driving / 14 restraining, gap +2 toward the change.** Read this as "leaning feasible, held by one binding barrier," not "feasible because 16 > 14." The +2 evaporates the moment the magnitude-5 coverage restrainer is left unaddressed.

---

## 3. The forces

### Driving forces (toward the change)

| Force | Push | Lens | Strength | Conf | Rationale / evidence |
|---|---|---|---|---|---|
| Attrition & burnout cost | Status quo is actively expensive | People / Org | 5 | High | Support attrition ran ~34% over the trailing 12 months vs. a ~15% company norm; replacement cost est. ~$22k/agent fully loaded. The change directly targets the stated cause. On its own enough to carry the case. |
| Agent demand for the change | The affected people want it | People | 4 | High | Internal pulse survey: 27 of 30 agents rank a four-day week as their #1 retention lever. The people who must change behaviour are pulling toward it, not resisting: rare and load-bearing. |
| Existing informal pilot | A proof point already exists | Org / Technical | 3 | Med | One team lead has run compressed hours for ~6 agents for two quarters with no measured CSAT drop. Real but small-sample and informal; strengthens the case without settling the coverage question. |
| Recruiting / employer-brand pull | Easier to hire and retain | External / People | 2 | Med | A four-day week is a visible differentiator in the support hiring market; plausibly lifts applicant volume, but the effect is diffuse and not the reason to act now. |
| CEO openness | Top cover is available | Org | 2 | Med | CEO is "open but wants proof." A permissive, not an active, driver: it removes a blocker more than it pushes, and it is conditional on the coverage/response-time evidence. |

### Restraining forces (holding the status quo)

| Force | Resist | Lens | Strength | Conf | Rationale / evidence |
|---|---|---|---|---|---|
| Friday coverage gap (unmodelled) | Coverage may drop on the lost day | Org / Technical | 5 | High | Friday currently carries ~19% of weekly ticket volume. No staggered-rota model has been built showing the same coverage on 32 hours. This is the binding restrainer: until it's solved, neither finance nor the CEO can say yes. Capable of blocking the change alone. |
| Finance scepticism / cost risk | Fears hidden cost of backfill | Org | 4 | High | Finance models the change as needing 4–6 extra heads to hold coverage (~$130–195k/yr), which "no drop in pay or coverage" appears to require. The fear is of unbudgeted backfill, and it's the loudest organizational objection. |
| CEO needs response-time proof | Won't approve without evidence | People / Org | 3 | Med | CEO's approval is explicitly gated on proof that first-response and resolution times hold. A real condition, but a satisfiable one: it points straight at the pilot that would also shrink the coverage restrainer. |
| Scheduling & tooling rework | Rotas and tooling must change | Technical | 2 | Med | WFM scheduling, on-call, and SLA dashboards need reconfiguring for staggered four-day rotas. Real work, but bounded and one-time: a drag, not a wall. |

---

## 4. Net field

**Binding restrainer:** the **unmodelled Friday coverage gap (5).** Friday's ~19% volume share has no demonstrated 32-hour staffing plan behind it. This is the load-bearing objection beneath both the finance fear (it implies extra heads) and the CEO's proof condition (response times). Solve coverage credibly and you collapse much of the restraining column at once; leave it unsolved and the change does not move whatever the totals say.

**Load-bearing drivers:** **attrition/burnout cost (5)** and **agent demand (4).** The first makes the status quo expensive enough that doing nothing is itself a decision with a price tag; the second means the people who must change their working patterns are pulling with the change rather than against it: so there is no people-side restrainer to fight, which is unusual and valuable.

**What the balance means:** the field is *leaning* feasible (+2) but is held by a single magnitude-5 barrier. This is precisely the case Lewin warns is misread by the totals: a change facing one binding restrainer is blocked even when the drivers outweigh it on paper. The situation will **not move on its own**, and it will **resist being pushed** harder on urgency. It can move with one targeted intervention against the coverage restrainer.

---

## 5. Leverage and moves

Leading with restrainers to weaken (the durable route), then drivers to strengthen second.

**Weaken the restrainers (do these first):**

1. **Build the staggered-rota coverage model on paper, before anything else (targets the 5).** Show, in the WFM tool, that two overlapping four-day rotas hold the same Friday and weekly coverage on 32 hours per agent, with the existing headcount. This is the single highest-leverage move: it directly shrinks the binding restrainer and, by doing so, defuses both the finance fear (no extra heads → no unbudgeted cost) and the CEO's response-time worry. Low cost, high impact, blocks nothing downstream. **Do this first.**
2. **Run a time-boxed, instrumented pilot, then let the data answer finance and the CEO (targets the 4 and the 3).** Extend the team lead's informal pilot into a measured 8-week trial across two squads, tracking first-response time, resolution time, CSAT, and Friday SLA against the control. The pilot converts the CEO's "prove it" condition from a blocker into a satisfiable test, and gives finance real coverage data instead of a worst-case head-count assumption. It also upgrades the informal-pilot driver from a 3 toward a 4.
3. **Pre-commit a kill/scale criterion with finance (shrinks the cost-risk 4).** Agree in advance the thresholds (e.g., response time within X%, Friday SLA held, no CSAT drop) at which the change scales, and at which it stops. Finance resists an open-ended cost commitment; a bounded, reversible pilot with explicit exit criteria removes the open-endedness that drives the scepticism.
4. **Scope the scheduling/tooling rework as a one-time setup task (clears the 2).** Name an owner and a two-week window for the WFM, on-call, and SLA-dashboard reconfiguration so it stops being a vague drag and becomes a closed checklist item.

**Strengthen the drivers (second, and only the cheap ones):**

5. **Make the attrition cost legible to finance (sharpens the load-bearing 5).** Put the ~34% attrition rate and ~$22k/agent replacement cost in the same model finance uses for the backfill fear, so the status-quo cost sits beside the change cost. This reframes "what does the four-day week cost?" as "what does *not* changing cost?", without adding top-down pressure.

**Do not** reach first for more urgency from the CEO or louder burnout messaging. The people side is already pulling with the change; the equilibrium is held on the *organizational/technical* side (coverage, cost, proof). Pushing harder on urgency raises tension against finance and provokes counter-pressure on exactly the cost axis where it is strongest, fragile change that snaps back the first bad-coverage Friday.

**Judgment on the shift:** the equilibrium can realistically be moved by Q3. The binding restrainer is solvable on paper and provable in a pilot, the cost fear is downstream of it, the proof condition is satisfiable by the same pilot, and there is no people-side resistance to overcome. Sequence: model coverage (move 1) → instrumented pilot with pre-agreed criteria (moves 2–3) → tooling setup (move 4) → go-live if criteria clear. If the coverage model cannot be made to hold on existing headcount, the honest read flips: the change then *does* require the 4–6 backfill heads finance fears, and "no drop in pay or coverage at no extra cost" was never feasible, better to surface that in week one of move 1 than after a launch.

---

## 6. Caveats

- This field is a **starting read, not a fixed verdict.** It shifts as the change proceeds: a successful pilot neutralizes the coverage restrainer and re-scores half the column, and acting on the field changes it.
- **Scores are informed judgment, not measurement.** The medium-confidence forces (informal pilot, recruiting pull, tooling rework) are the ones most worth replacing with hard data before committing, and the pilot in move 2 is what produces it.
- **The net read is not the arithmetic.** The +2 driving margin does not make the change feasible; the magnitude-5 coverage restrainer being unsolved makes it blocked. One binding restrainer overrides the totals.
- A long driver column against a short restrainer column would have signalled a lazy restrainer hunt, not an easy change. Here both sides were hunted across all four lenses; the restraining side is shorter only because the people lens yielded no genuine restrainer (the agents want the change).
- All figures here are illustrative for documentation purposes and were not researched.
