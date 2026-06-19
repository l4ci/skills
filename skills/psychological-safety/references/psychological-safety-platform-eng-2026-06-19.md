# Psychological Safety: Platform Engineering (Dana's team)

> _Illustrative example output for the `psychological-safety` skill. This team is fictional; every figure, name, episode, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Team:** 7-person platform engineering team led by **Dana**, who runs the on-call rotation and the weekly incident review.
- **Context:** A recent Sev1 outage; leadership wants a blameless retro culture. The team is held to a strict **99.95% uptime SLO**.
- **Date:** 2026-06-19
- **Note:** Psychological safety is a property of the **team climate**, not a trait of any individual. The target is the **learning zone**: high safety paired with high accountability, not a comfortable team.

---

## 1. Verdict

The team sits in the **anxiety zone**: a high, strictly-enforced bar (99.95% SLO) without the safety that would let people surface problems early. The diagnosis is not a vibe, it is the same pattern repeating across dimensions. Bad news travels in 1:1s and never in the room; a junior sat on a known-bad config for two days; incident reviews are a three-voice conversation in a seven-person team. The two weakest dimensions are **voice and speaking up** and **response to mistakes and failure**, and they reinforce each other: because mistakes feel dangerous to own, problems are withheld until they are undeniable.

The good news is the move is clear. The team does not need lower standards; it needs the SLO bar held while making it safe to bring the bad news to the bar. That is the move *up* into learning, not *sideways* into comfort.

| Dimension | Score | Confidence |
|---|---|---|
| Voice and speaking up | **Low** | High |
| Response to mistakes and failure | **Low** | High |
| Help-seeking | Low–Moderate | Medium |
| Inclusion of difference | Moderate | Low |
| Risk-taking and challenge | Low | Medium |

**Zone: Anxiety** (low safety, high accountability). **Weakest: voice, and response to mistakes.**

---

## 2. The climate

Each dimension is scored against Edmondson's seven behavioral markers, judging the team and not any individual, and grounded in what happens when a member takes an interpersonal risk.

### Voice and speaking up: **Low** (confidence: High)

**Read.** Voice in the team's central forum has collapsed to its most senior members. The weekly incident review is the place voice matters most and is exactly where it has gone quiet.

**Evidence.**
- In the **last three incident reviews, only Dana and two seniors spoke.** Four of seven members were silent across all three: not occasional silence, a stable pattern.
- Bad news **surfaces in 1:1s, never in the room.** People have a channel for candor; it is the private one, where the risk of being seen to raise a problem is lowest. The public channel is the one that has shut.
- The split is structural, not personal: the same people who are silent in the review speak in their 1:1s. That is a climate signal, not a set of shy individuals.

**Driving behaviors.** Voice is suppressed because the room rewards being right and the review follows a strict SLO breach. When the cost of saying the wrong thing in front of the group is high and the cost of saying nothing is low, rational members route their concerns to the private channel. Markers most violated: **#2 (tough and sensitive issues can be raised)** and **#4 (safe to take an interpersonal risk)**.

**Gaps.** We have not observed *how* Dana responds in the moment to a concern raised in the room, only that few are raised. The mechanism is inferred from the routing pattern.

### Response to mistakes and failure: **Low** (confidence: High)

**Read.** Mistakes are something to survive privately, not data to be examined together. This is the dimension most directly tied to the SLO and the Sev1.

**Evidence.**
- A **junior who pushed a bad config stayed silent for two days** before admitting it. Two days of exposure on a 99.95% SLO is a long time to sit on a known fault. The delay is the diagnosis: the expected cost of confessing exceeded the cost of hiding and hoping.
- The retro culture is **aspirational, not yet real**: leadership *wants* blameless; the team's behavior says it is not there yet.
- Mistakes route the same way bad news does: privately, late, and only when forced.

**Driving behaviors.** When admitting an error feels more dangerous than the error itself, members hide errors, which is the precise failure mode the anxiety zone produces. Marker most violated: **#1 (mistakes are not held against you)**: the strongest negative-keyed signal, and it is firing.

**Gaps.** We do not know what actually happened to the junior after they admitted the config, whether the response was punitive, neutral, or supportive. That response is the single most load-bearing unknown in this assessment.

### Help-seeking: **Low–Moderate** (confidence: Medium)

**Read.** Help-seeking inherits the same fear as confession: asking for help in the room exposes not-knowing. There is some evidence it happens, but quietly.

**Evidence.**
- The two-day config silence is also a help-seeking failure, the junior did not ask for help unwinding the change either.
- The seniors talk in reviews, which suggests peer-to-peer help exists *among the seniors*; it is the cross-level asking (junior → senior, in public) that appears blocked.

**Driving behaviors.** On a high-SLO team, asking for help can read as admitting you cannot meet the bar. Without explicit normalization, help-seeking concentrates among those already secure enough to do it. Markers touched: **#5 (help is easy to ask for)** and **#7 (unique skills valued and used)**.

**Gaps.** Thin evidence, we have one episode and an inference. Scored a half-step above the weakest dimensions because there is no sign of *active* punishment of help-seeking, only of it not being normalized.

### Inclusion of difference: **Moderate** (confidence: Low)

**Read.** No evidence of rejection or undermining surfaced in the signals; equally, no evidence that diverse views are actively drawn out. Defaulted to moderate because the negative markers are quiet.

**Evidence.**
- No reported episodes of anyone being undermined or rejected for being different (marker #6, #3).
- The silence of the four juniors is *as consistent with* unsurfaced difference as with agreement, we cannot tell whether they disagree silently or have nothing to add.

**Driving behaviors.** None observed. The risk here is latent: a team where difference is never voiced cannot demonstrate that difference is accepted.

**Gaps.** Largest gaps of any dimension, composition, tenure mix, and any history of how dissenting or minority views were received are all unobserved. Confidence is **Low** by construction; this score should be replaced with real signal before acting on it.

### Risk-taking and challenge: **Low** (confidence: Medium)

**Read.** Challenge, pushing back on a decision, a design, or the leader, is largely absent from the observable forum, consistent with the voice collapse.

**Evidence.**
- A three-voice incident review is not a forum where the SLO target, the on-call design, or a senior's root-cause call gets challenged from below.
- Dissent, like bad news, has no public channel here.

**Driving behaviors.** Absence of challenge in a high-stakes, high-accountability setting is far more likely a symptom of low safety (no one risks dissent) than of genuine agreement. Markers: **#2** and **#4**, same as voice.

**Gaps.** We have not observed an actual challenge being made and met, so the score is inferred from the broader silence rather than from a punished-dissent episode.

---

## 3. Placement on the 2x2

| | Low accountability / standards | High accountability / standards |
|---|---|---|
| **High psychological safety** | Comfort zone | Learning & high-performance zone *(the target)* |
| **Low psychological safety** | Apathy zone | **← THIS TEAM: Anxiety zone** |

**Accountability axis: High (justified).** A strict, externally-visible **99.95% uptime SLO**, a formal on-call rotation, and a weekly incident review are real, enforced standards. The bar is unambiguous and the Sev1 made the cost of missing it vivid. Accountability is not the problem and must not be lowered.

**Safety axis, Low (justified).** Four of seven silent across three reviews; bad news confined to 1:1s; a two-day delay in confessing a known-bad config; no observable public challenge. The negative-keyed marker **#1 (mistakes held against you)** is firing on its strongest episode. These are behaviors, not impressions.

**Zone: Anxiety.** High demands without safety produce exactly what is observed, mistakes hidden, help not asked for, voice withdrawn, problems surfacing late and large. The Sev1 may itself be partly a product of this climate: a config that someone sat on for two days is a problem that surfaced late because surfacing it early felt dangerous.

**The move is up, not sideways.** The tempting misuse here is to soften the SLO or go easy in retros and call that "blameless." That would slide the team into comfort and learn nothing. The correct move is to **raise safety while holding the 99.95% bar**: make it safe to bring the bad config to the room *and* still own the SLO.

---

## 4. Prescription

Every move below is checked against the accountability bar: none of them lowers the SLO or softens the standard. They make it safe to meet the standard honestly.

### Leader interventions (Dana): against the three practices

**1. Frame the incident review as a learning problem, not an execution problem.**
Open each review by stating plainly that the systems are complex and interdependent and that *no one person can see the whole failure*, so the review needs every person's piece, especially the juniors who touched the change. Today the review reads as a tribunal where seniors deliver the verdict; reframing it as a joint investigation of a system nobody fully understands changes who is expected to talk. Targets the **voice** and **challenge** dimensions directly.

**2. Acknowledge fallibility, out loud, first.**
Dana should name her own misses before asking anyone else to. "I approved the on-call design that made this page no one, that's on me, and I want to know what else I'm not seeing." A leader who models being wrong on a high-SLO team is the only thing that makes the **#1 marker** (mistakes not held against you) credible. Slogans about "blameless" do nothing; one visible instance of the leader owning a mistake without consequence does more than a quarter of posters.

**3. Model curiosity through genuine inquiry, and call on the silent four.**
Replace "any questions?" (which the four will never answer) with directed, genuine questions: "You were closest to the deploy pipeline, what looked off to you before this fired?" Proactive inquiry creates the *necessity* to speak and signals that their view is expected, not optional. The two-thirds of the team that is silent will not volunteer into a three-voice room; they have to be drawn in, repeatedly, until it is normal.

### Team interventions

- **The config story becomes the founding story, told the right way.** Have the junior (with consent, and only if the original response was not punitive) or Dana narrate the bad-config incident in a review as *what the system let happen*, not what a person did wrong. How that two-day silence is treated, publicly, sets the price of confession for everyone watching. **Thank the person who surfaces the hard thing.**
- **A standing "what nearly went wrong" slot.** Every review reserves time for near-misses and not-yet-failures, explicitly. This pulls bad news out of 1:1s and into the room where the team can act on it early, the direct antidote to late-surfacing problems.
- **Normalize help-seeking structurally.** Make asking for a second pair of eyes on a risky change a *required* step, not a sign of weakness, e.g., a lightweight "pre-mortem ping" before high-risk deploys. When the process expects help-seeking, the junior no longer has to decide whether asking makes them look incapable.
- **Protect dissent visibly.** When someone challenges a senior's root-cause call or the on-call design, Dana names it as the behavior she wants, "that's exactly the kind of push I need", so the person who raises the hard thing is rewarded in front of the room, not just tolerated.

### The accountability check

Every prescription above raises safety **while holding the 99.95% SLO and the on-call standard.** Nothing here excuses the bad config, softens the SLO, or makes the Sev1 acceptable. The aim is precise: a team that meets a strict bar *and* surfaces the problems that threaten it early, the learning zone. If any future move would raise safety by relaxing the standard, it is wrong by construction and should be rejected. Blameless does not mean consequence-free for the system; it means the person can tell the truth about the system without being the consequence.

---

## 5. What to watch

Leading indicators, tied to the markers, that tell the team whether the interventions are working:

- **Voice spread (marker #2, #4).** Number of *distinct* people who speak in the incident review, trending from 3 toward 7. The single cleanest signal.
- **Where bad news first appears (marker #1, #2).** Is the next near-miss raised *in the room* or still only in a 1:1? Migration of bad news from private to public is the core behavior change.
- **Time-to-confession (marker #1).** The next bad change, does it get flagged in minutes, or does someone sit on it for days? The two-day baseline is the number to beat.
- **Help-seeking in the open (marker #5).** Frequency of public "can someone look at this risky change with me" before deploys, especially from juniors.
- **Visible challenge survived (marker #4, #6).** A junior pushes back on a senior or on Dana, and the room (and the challenger's standing) is fine afterward. The first time this happens cleanly is the inflection point.
- **The SLO holds while the above rise.** If safety indicators climb *and* the 99.95% bar stays met, the team is moving into the learning zone. If the bar slips, the move went sideways into comfort, re-check the accountability hold.

---

## 6. Caveats

- Psychological safety is a **team climate read from observable behavior at a moment**, not a fixed trait and not a verdict on any individual. The junior who held the config for two days is not "the problem", the climate that made silence the rational choice is.
- It is **not** niceness, consensus, comfort, or low standards. A blameless retro that lowers the SLO is not safety; it is the comfort-zone trap.
- This assessment is **only as good as its signals.** The inclusion-of-difference score rests on near-zero evidence (confidence Low) and the response-to-mistakes mechanism hinges on one unobserved fact, *what actually happened after the junior admitted the config*. That single fact should be established before acting; a confident-sounding score on thin evidence is a guess.
- Raising safety **enables** high performance; it does not produce it. The 99.95% SLO still has to be met. Accountability holds.
- All names, episodes, and figures here are illustrative for documentation and were not researched.
