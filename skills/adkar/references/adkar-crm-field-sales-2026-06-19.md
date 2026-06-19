# ADKAR: Field Sales CRM Adoption

> _Illustrative example output for the `adkar` skill. The CRM rollout described here is fictional; every figure, name, quote, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Change:** Moving the 120-person field sales team off spreadsheets onto Salesforce, assessed six weeks after go-live.
- **Unit making it:** Field Sales division of a mid-market B2B software company.
- **Affected groups:** Field sales reps (~120), regional sales managers (~14), sales-ops support team (~6).
- **Date:** 2026-06-19
- **Cut used:** One subagent per element, assessed across all three groups (the default). The groups are distinct but not so divergent that a per-group cut was needed.
- **Note:** ADKAR assesses *individual* change, scored per affected group; this is a snapshot at six weeks post-go-live, not a forecast, and the barrier points will move as the change progresses. Re-assess.

---

## 1. Verdict

Three groups, three different barrier points, which is exactly why a single org-wide adoption number ("31% logging into Salesforce weekly") tells you nothing actionable.

- **Field sales reps are stuck at Desire (2).** They understand why the CRM exists; they do not want to use it. A failed rollout two years ago left them cynical, and nothing in their week rewards pipeline hygiene. Training them harder is the wrong move.
- **Regional sales managers are stuck at Desire (3) too, but for a different reason: their incentives actively oppose the change.** They are paid on closed deals, not pipeline accuracy, so they tolerate reps skipping the CRM. Their Knowledge gap (3) sits behind the Desire one and is provisional.
- **Sales-ops support is stuck at Knowledge (3).** They want it and understand why, but they were trained on the vanilla tool, not the customized org and the field workflows they now have to support.

**Scorecard** (1 Absent · 2 Weak · 3 Partial · 4 Strong · 5 Achieved). The **barrier cell**: first element scoring ≤3, read left to right, is marked **【 】**. Scores to the right of a barrier are provisional.

| Group | Awareness | Desire | Knowledge | Ability | Reinforcement |
|---|---|---|---|---|---|
| Field sales reps | 4 | **【2】** | 3 | 2 | 1 |
| Regional sales managers | 4 | **【3】** | 3 | 3 | 2 |
| Sales-ops support | 4 | 4 | **【3】** | 3 | 2 |

The pattern: **Awareness is solved everywhere; the program is failing on the people-side blocks it left to no one.** Desire and Reinforcement were treated as project-team deliverables, and the project team cannot supply them.

---

## 2. Per-group sections

### Field sales reps (~120)

**Barrier point: Desire (2).** Reps know why the company wants the CRM and many could even pass a Salesforce quiz: but they will not engage, and the scores after Desire (Knowledge 3, Ability 2, Reinforcement 1) are provisional until that changes.

**Why it holds.** Two compounding reasons, both about cost-to-me, not understanding:
1. **Burned once already.** The 2024 CRM attempt was abandoned after reps had migrated data into it; many lost a quarter of pipeline notes. The lived lesson was "corporate tools waste my time and then disappear." This is rational cynicism, not irrational resistance, it is information about a trust gap.
2. **It is pure overhead in their week.** A rep's day is rewarded by booked meetings and closed deals. Logging activity into Salesforce after each call adds ~30–40 minutes of admin that produces nothing they are measured on. The personal case for change has never been made; the personal cost is obvious and daily.

| Element | Score | Evidence | Gap | Conf |
|---|---|---|---|---|
| Awareness | 4 | Launch town hall and a clear deck explained the "single pipeline view" rationale; reps can restate it in interviews ("leadership can't forecast off 120 spreadsheets") | Minor: the risk of *not* changing was framed as a leadership problem, not a rep problem | Med |
| **Desire** | **2** | 31% weekly login; reps openly say "I'll use it when the last one didn't get killed"; no manager-led conversations addressing the 2024 history | The personal case is absent, the 2024 trust breach is unaddressed, and the admin cost is unmitigated | High |
| Knowledge | 3 | Two-hour group training delivered to all reps pre-go-live; job aids exist on the intranet | Generic tool training, not "how your day changes"; delivered before any Desire, so it did not stick | Med |
| Ability | 2 | The minority who log in fumble basic flows; no observed proficiency at speed under real call volume | Provisional: can't separate "can't" from "won't"; little hands-on practice or coaching during ramp | Low |
| Reinforcement | 1 | Nothing recognizes or rewards CRM use; old spreadsheets still accepted in deal reviews | No reinforcement at all; the old way still works and carries no cost | High |

**Interventions, sequenced from the barrier:**

1. **Desire first: owner: regional managers, sponsored by the VP Sales.** Manager-led 1:1s that *name the 2024 failure out loud* and state what is different this time (executive commitment, no migration cliff, a rollback guarantee). Surface each rep's actual fear (lost notes, wasted time) and answer it. This is not a project-team job.
2. **Desire, owner: VP Sales (sponsor).** Cut the admin cost that makes resistance rational: commit to mobile/voice logging and kill at least one redundant existing report so net admin time does not rise. Make the personal case ("the rep with clean pipeline gets first claim on inbound leads").
3. **Then Knowledge, owner: sales-ops + project team.** Re-deliver training as *role-specific* "your Tuesday on the new system," not a tool tour, and only after Desire work has started, otherwise it won't stick again.
4. **Then Ability, owner: managers + sales-ops.** Side-by-side coaching on real deals during the next two pipeline cycles; protect ramp time.
5. **Then Reinforcement, owner: VP Sales + managers** (see cross-group; this is shared and currently absent everywhere).

### Regional sales managers (~14)

**Barrier point: Desire (3).** Managers understand the change and could mostly use the tool, but they are passively non-committal, they tolerate reps skipping the CRM rather than enforcing it. Knowledge (3) and the blocks after are provisional behind this.

**Why it holds.** **Their comp plan rewards the opposite of what the change needs.** Managers are paid on their region's closed bookings, not on pipeline accuracy or CRM adoption. Chasing reps on hygiene costs them goodwill with the team they depend on for revenue and buys them nothing on their own scorecard. They are not resisting loudly; they are quietly optimizing for how they are paid. This is the single most fixable barrier in the whole change, because it is structural, not emotional.

| Element | Score | Evidence | Gap | Conf |
|---|---|---|---|---|
| Awareness | 4 | Managers were briefed ahead of reps and articulate the forecasting rationale well | Minor | Med |
| **Desire** | **3** | Mixed: a few champion it, most tolerate non-use; none have made CRM adoption a team expectation; comp plan unchanged | Incentives oppose the change; no sponsor ask landed on managers specifically | High |
| Knowledge | 3 | Same generic training as reps; managers don't know how to *coach* CRM use or read the new pipeline dashboards | Provisional: no manager-specific enablement on leading the change, only on the tool | Med |
| Ability | 3 | Can navigate the tool; have not demonstrated coaching reps or running a pipeline review off Salesforce | Provisional: no practice at the *managing-the-change* behaviors | Low |
| Reinforcement | 2 | Nothing rewards them for driving adoption; deal reviews still run off rep spreadsheets | Their own incentives and the review process both reinforce the old way | High |

**Interventions, sequenced from the barrier:**

1. **Desire first: owner: VP Sales (sponsor), with HR/Comp.** Change what managers are measured on: add a pipeline-accuracy / adoption component to the manager scorecard for the next two quarters. Until the comp plan moves, every other manager intervention pushes against the money. Make the explicit sponsor ask: "driving your team's adoption is your job, and here is how it now counts."
2. **Then Knowledge, owner: sales-ops.** Manager-specific enablement: how to run a pipeline review *only* from Salesforce, how to coach a reluctant rep, how to read the dashboards. Time after the Desire/comp change.
3. **Then Ability, owner: sales-ops + VP Sales.** Mandate that the weekly regional pipeline review is run off Salesforce, nothing else accepted, forced practice in real conditions.
4. **Then Reinforcement, shared (see cross-group).**

### Sales-ops support team (~6)

**Barrier point: Knowledge (3).** This group cleared Awareness and Desire, they asked for the CRM and want it to work, but they are stuck on knowing how to support the *customized* org and field workflows.

**Why it holds.** **They were trained on out-of-the-box Salesforce, then handed a heavily customized implementation.** The org has custom objects, a bespoke quoting flow, and field-specific automation that no standard training covered. When reps hit a wall, sales-ops can't always answer, which feeds the reps' "this tool wastes my time" Desire problem, so this Knowledge gap is also a hidden tax on the reps' barrier.

| Element | Score | Evidence | Gap | Conf |
|---|---|---|---|---|
| Awareness | 4 | They championed the project internally; fully understand the why | None material | High |
| Desire | 4 | Actively engaged, want the rollout to succeed, advocate to reps | Minor: morale dipping as they field questions they can't answer | High |
| **Knowledge** | **3** | Standard admin training only; no documentation of the custom build; the implementation partner has rolled off | Deep knowledge of the customized org, field workflows, and edge cases is missing | High |
| Ability | 3 | Handle routine resets and access requests; stall on custom-object and quoting issues | Provisional: limited by the Knowledge gap, not by aptitude or willingness | Med |
| Reinforcement | 2 | No structured feedback loop from rep issues back into config fixes or doc updates | Provisional: knowledge gaps recur because nothing captures and closes them | Med |

**Interventions, sequenced from the barrier:**

1. **Knowledge first: owner: project team.** Knowledge-transfer sessions on the *custom* build (objects, quoting flow, automation) before the implementation partner is fully gone; produce a config runbook. This is a project-team deliverable and is genuinely theirs to own.
2. **Then Ability, owner: project team + sales-ops lead.** Shadow the partner on live tickets for the remaining engagement; build a triage playbook for the recurring custom-object issues.
3. **Then Reinforcement, owner: sales-ops lead.** A standing loop that turns recurring rep tickets into config fixes and doc updates, so the same gap isn't relearned monthly.

---

## 3. Cross-group synthesis

**The dominant gap is Desire, and it is the program's leverage point.** Two of three groups are barricaded there, and the third group's Knowledge gap is partly *caused* by an unsupported tool that worsens the reps' Desire problem. The change does not have an Awareness problem (every group scores 4) and it does not fundamentally have a Knowledge problem, yet the only intervention the program has run so far is **training**, which is Knowledge. That is the classic and expensive ADKAR error: jumping to the visible, schedulable block while the real barrier sits one block earlier.

**Where leverage concentrates: the managers' comp plan.** The single highest-leverage move is changing what regional managers are measured on. Today the comp plan, the deal-review process, and the surviving spreadsheets all reinforce the *old* way, so managers tolerate non-use, reps see no cost to non-use, and adoption stalls. Move the manager scorecard and you convert 14 managers from passive tolerators into the people who close the reps' Desire gap on the ground. Reinforcement (rewarding the new, ending the old) is the binding constraint underneath Desire for both the reps and the managers, and it currently belongs to no one.

**The group needing its own track: sales-ops support.** Their barrier is Knowledge of the custom build, not Desire, and it is owned by the project team on a hard clock, the implementation partner is rolling off. This track runs in parallel and must not wait for the Desire work; if sales-ops can't answer rep questions, the reps' Desire problem gets worse.

---

## 4. Sequenced plan

What to **start**, **re-time**, and **stop**, ordered so earlier blocks are secured before later ones:

**Start now (the actual barriers):**
- **Change the regional-manager scorecard** to include pipeline accuracy / adoption (VP Sales + Comp). Unblocks managers' Desire; nothing else for managers works until this moves.
- **Manager-led 1:1s with reps that name the 2024 failure** and state what's different (managers, sponsored by VP Sales). Unblocks reps' Desire.
- **Cut the rep admin cost**: mobile/voice logging, retire one redundant report (VP Sales). Removes the cost that makes rep resistance rational.
- **Custom-build knowledge transfer to sales-ops** before the partner leaves (project team). Independent track, hard deadline.
- **Visible sponsor re-engagement** (VP Sales). The sponsor going quiet after launch is itself a Desire signal across all groups; re-establish presence.

**Re-time (right block, wrong moment):**
- **Re-deliver rep training as role-specific**: but only *after* the Desire 1:1s have started. Delivering it now repeats the mistake of training people who don't yet want the change.
- **Manager enablement on coaching/dashboards**: after the comp change lands.

**Stop (running ahead of a barrier):**
- **Stop accepting spreadsheets in deal reviews and pushing more generic training as the primary lever.** Both are Knowledge/Ability-era moves while two groups sit at Desire. More training on an unwanted change produces capable non-adopters.
- **Stop treating Desire and Reinforcement as project-team tasks.** They belong to the sponsor and the managers; the project team has been left holding blocks it structurally cannot deliver.

**Then, once Desire is moving:** work reps' Knowledge → Ability, managers' Knowledge → Ability, and finally **build Reinforcement everywhere** (recognition for clean pipeline, adoption in the manager scorecard, a regression metric, end the spreadsheet fallback), currently the weakest column on the board and the reason any early win would decay.

---

## 5. Caveats

- ADKAR is a snapshot of **individual readiness**, not a forecast. This is the picture at six weeks post-go-live; barrier points move (reps clearing Desire may then stall on Ability), so re-assess on a cycle rather than acting on this read indefinitely.
- The scores are **informed judgment, not measurement.** The reps' Ability (2) and the managers' Knowledge/Ability (3/3) are explicitly low-confidence because, behind an unresolved Desire barrier, you cannot cleanly separate "can't" from "won't." Treat all post-barrier scores as provisional.
- ADKAR addresses the **people side only.** It does not cover the organizational steps of leading the change (see `kotter-change`, a quiet sponsor and misaligned incentives are also Kotter problems) or the project/technical plan (the custom-build documentation gap is a delivery issue surfacing as a Knowledge barrier).
- Mapping who the three groups are, and who sponsors and influences them, pairs with `stakeholder-analysis`.
- All figures, quotes, and history here are illustrative for documentation purposes and were not researched.
