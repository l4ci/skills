# Tuckman Diagnosis: Platform Engineering Squad

> _Illustrative example output for the `tuckman` skill. This team is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Team:** The eight-person platform engineering squad formed by merging the former API team (4) and infrastructure team (4).
- **Date:** 2026-06-19
- **Context:** Merged three weeks ago. A new lead promoted from the API side now runs a team that includes the former infra lead as an individual contributor. Standups have stretched from 15 to 40+ minutes with open disagreement, mostly over who owns the on-call rotation and which team's runbooks win. Decisions are made in the room and then quietly ignored.
- **Framework note:** This applies Bruce Tuckman's stages of group development (Forming, Storming, Norming, Performing, Adjourning). A stage is a diagnosis of where the team sits *right now*, not a fixed trait, and a recent change in shape can drop a team back.

---

## Verdict

**The team is in Storming, having regressed there from the two predecessor teams' prior maturity when the merge reset the group three weeks ago.** Two groups that each knew their own roles, norms, and on-call patterns were fused into one team that shares none of them, and the friction is now surfacing openly: contested ownership, a challenged new leader, and decisions that do not stick. This is not dysfunction, it is the necessary work of the stage. The single most important move is for the new lead to **stop letting on-call ownership be re-litigated every standup and instead facilitate one decision-making process that produces a written, owned conflict resolution**, because the blocker is not the disagreement itself but that nothing the team decides becomes binding.

Note the regression up front: the high apparent "experience" of the members masks that *as a team* this group is three weeks old.

| Stage | Match (1–5) | Confidence |
|---|---|---|
| Forming | 2 | High |
| **Storming** | **5** | **High** |
| Norming | 2 | Medium |
| Performing | 1 | High |
| Adjourning | 1 | High |

---

## Stage assessment

### Forming: Match 2 (High)

**Evidence.** The team *did* pass through a compressed Forming at the merge: the new lead announced the combined charter and that the squad now owns the full platform surface. The orientation phase was real but brief.

**Counter-evidence.** The defining Forming markers are absent now. Members are not polite, tentative, or conflict-avoidant; they are openly contesting each other in standup. They are not waiting on the leader for direction: they are challenging his authority. The eight people are seasoned engineers who skipped most of the "anxious newcomer" behavior because none of them are new to the work, only to each other.

**Regression signal.** None into Forming. The team moved *through* Forming quickly and is now past it.

### Storming: Match 5 (High)

**Evidence.**
- *Conflict and friction, surfacing openly*, standups have tripled in length with open disagreement (marker: "conflict and friction… contest the goal, the approach, and each other").
- *Jockeying for position and contesting ownership*, the fight over who owns the on-call rotation and whose runbooks are authoritative is a direct contest of roles and approach.
- *Challenging authority*, a new lead drawn from one of the two merged sides, with the other side's former lead now a peer IC, is a textbook authority challenge; the infra contingent has not accepted his mandate.
- *Cliques forming*, the API-origin and infra-origin members still cluster, each defending their prior way of working.

**Counter-evidence.** Almost none. The one mild softener: conflict is being voiced rather than suppressed, which is healthier than a silent stall and means the team is doing Storming's work out loud rather than avoiding it.

**Regression signal.** Strong. The merge (new members + new leader + new combined goal, all at once) is exactly the trigger Tuckman names for dropping a team back. Two previously-functioning groups regressed into a single Storming team three weeks ago.

### Norming: Match 2 (Medium)

**Evidence.** Each *predecessor* team had norms; fragments survive (each side still runs its own runbooks competently).

**Counter-evidence.** No *shared* norms exist. The clearest tell is that decisions do not stick, the hallmark of Norming is that the team agrees on how it operates and then self-corrects to hold the line. This team agrees in the room and then reverts. There is no shared on-call process, no agreed feedback culture, no settled roles. Confidence is Medium only because "quiet agreement that doesn't stick" can be misread as early Norming; it is not, it is unfinished Storming.

**Regression signal.** N/A, the team has not reached Norming as a unit to regress from.

### Performing: Match 1 (High)

**Evidence.** None. Individuals are high-performing; the *team* is not.

**Counter-evidence.** Performing requires self-organization, autonomous conflict resolution, and delivery with little oversight. This team cannot resolve its own on-call dispute without the conflict reopening daily, and it has produced no joint delivery yet. The individual seniority is a trap here: do not mistake competent people for a performing team.

### Adjourning: Match 1 (High)

**Evidence.** None. This team is forming up, not winding down. No disengagement, no task conclusion, no transition out.

**Counter-evidence.** Entirely inapplicable. (Worth a single line only because the framework runs all five.)

---

## Diagnosis

**Current stage: Storming, reached by regression.** The match scores and the evidence agree without tension, this is a clean Storming read, and the only reason to slow down is to make sure the regression is named so the team isn't held to the maturity of its two parents. It is not: as a *team*, it is three weeks old and in the hardest stage.

**Regression.** Confirmed. The trigger is the merge itself, new members, a new leader, and a new combined goal landing simultaneously, the strongest possible regression event in Tuckman's model. The team fell from "two teams each near Norming/Performing" to "one team in Storming." Diagnose from Storming, not from where either predecessor team used to be.

**Leadership focus the stage needs: Coach, and there is a mismatch.** Storming needs a leader who surfaces conflict and normalizes it, builds the processes for making decisions and handling disagreement, builds trust across the old factions, and keeps everyone anchored to the shared goal. The likely current failure mode, given that decisions are made in standup and then ignored, is a lead who is *chairing debate* but not *closing it into binding process*. Letting the on-call argument recur daily is suppression-by-exhaustion, not coaching. The new lead also carries an authority deficit with the infra side that pure facilitation won't fix; he needs to coach *and* visibly partner with the former infra lead so that side's expertise is enfranchised rather than annexed.

**Moves to advance (to Norming):**

1. **Settle on-call once, in writing, with an owner.** Run one decision specifically on the on-call rotation and runbook authority, using an explicit decision method (e.g., the lead decides after a timeboxed input round, or a documented consensus). Write it down, name who owns each rotation, and declare it binding until a scheduled review. The recurring fight ends when one decision becomes real.
2. **Install a decision-making process so the next ten decisions stick.** The on-call dispute is a symptom; the disease is that nothing the team decides holds. Agree how this team makes and records decisions (who decides, how dissent is captured, where it's written) before the next contested call arrives.
3. **Merge the runbooks deliberately, not by conquest.** Assign mixed API+infra pairs to reconcile each contested runbook so neither faction's knowledge is discarded, this builds the cross-faction trust Storming requires.
4. **Co-anchor the leadership.** Have the new lead and the former infra lead jointly own the team charter and the on-call decision, so the infra side sees its expertise enfranchised and the authority challenge drains.
5. **Re-charter the shared goal.** Restate what the *combined* squad is for, so members contest ideas inside a shared purpose rather than defending two legacy identities.

**The blocker.** Decisions don't stick. The team is doing Storming's real work, conflict is open, not buried, which is the healthier failure, but the conflict has no exit because nothing decided becomes binding. Until one hard call (on-call) is made, written, owned, and held, every standup will re-run the same argument and the team cannot reach the agreed-ways-of-working bar that begins Norming. Resolve the *process for deciding*, and the on-call fight resolves with it.

---

## Caveats

- Tuckman is a lens, not a measurement. This locates a stage to match support to it; it does not quantify the team.
- Stages are not strictly linear. A team can sit between two, and, as here, regress when its shape changes. This squad could oscillate between Storming and early Norming for several cycles before settling.
- The diagnosis rests on observed behavior at one moment (week three post-merge) and will shift as the team works through conflict and as its goals firm up. Re-diagnose after the on-call decision lands.
- Locating the stage tells you what support fits, not how long advancing will take. Storming has no fixed duration; coaching shortens it, suppression lengthens it.
- This is the developmental-stage question only. For *why specific behaviors* break the team's results, see five-dysfunctions-of-a-team; for *whether members feel safe to speak up*, see psychological-safety. All figures here are illustrative for documentation and were not researched.
