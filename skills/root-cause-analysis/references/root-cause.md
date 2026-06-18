# Root-cause analysis: fishbone, 5 Whys, verification

Root-cause analysis pairs two tools. The Ishikawa fishbone enumerates the possible causes of an effect across every category, so the search is broad and nothing is skipped. The 5 Whys drills a chosen cause deep, so the search reaches the origin and not a midpoint. Used together they cover both the breadth and the depth that either alone misses.

## The fish head: state the effect

The head of the fishbone is the effect, stated precisely. A precise head names **what** the problem is, **where** it occurs, **when** it occurs, and its **magnitude**, quantified wherever data exists.

- Loose head: "soldering problems", "the app is slow", "customers are unhappy".
- Precise head: "solder voids on connector J3, second shift only, ~8% of boards since week 12"; "checkout API p95 latency rose from 200ms to 1.8s after the 3.4 release"; "first-contact resolution on billing calls fell from 78% to 61% in Q2".

A loose head produces a loose analysis: the categories fill with vague causes that cannot be tested. Sharpen the head before drawing any bones.

## The bones: cause categories

The bones of the fishbone are cause **categories**, not individual causes. Categories force the analysis to look everywhere, including the places no one suspected. Pick the set that fits the domain.

### Default: the 6 Ms (manufacturing and operations)

| Category | Covers | Probes |
|---|---|---|
| **People** (Manpower) | who does the work | training, skill, staffing, fatigue, handoffs, communication, incentives |
| **Machine** (Equipment) | tools, hardware, systems | wear, calibration drift, capacity, configuration, version, faults |
| **Method** (Process) | how the work is done | procedure, sequence, standards, recent process changes, missing steps |
| **Material** | inputs and components | supplier change, batch variation, spec mismatch, contamination, storage |
| **Measurement** | how the effect is observed | gauge error, sampling, definition changes, instrument calibration, data quality |
| **Environment** (Mother Nature) | the conditions around the work | temperature, humidity, load, time of day, location, external events |

Default to the 6 Ms unless the effect has no physical product.

### Service variant: the 4 Ps and 8 Ps

For service, process, and administrative problems use the 4 Ps: **People, Process, Place, Policy**. Expand to the 8 Ps where useful: add **Product, Promotion, Price, Procedures**. Use the set that maps cleanly onto the effect; do not force physical categories onto a service problem or vice versa.

### Choosing and using the set

Pick one set and name it. The categories are scaffolding, not a straitjacket: if a real cause does not fit any bone, add a category rather than discarding the cause. The goal is coverage, so scan every category before committing to any single chain.

## The 5 Whys: drilling to the root

For each strong candidate cause, ask "why does this happen?" and answer; then ask "why?" of that answer; repeat. Roughly five iterations reaches the root in most problems, but five is a guideline, not a rule. Stop when you reach a **root cause**:

- A root cause is one that, **if removed, prevents recurrence** of the effect.
- A root cause is one you can **actually act on**. A chain that bottoms out at "the laws of physics" or "the economy" has gone too far; back up to the deepest cause within your control.

A proximate cause is a symptom one level up. "The board failed" → "a solder joint cracked" → "the reflow profile was wrong" → "the profile was changed without re-qualification" → "there is no change-control gate on reflow profiles". Stopping at "the solder joint cracked" treats a symptom; the actionable root is the missing change-control gate.

**A why-chain can branch.** More than one cause can operate at a level. If two answers to a "why" are both true and both contribute, follow both forks; do not force the chain into a single line. A branching chain is more honest than a tidy linear one.

## Verification: correlation is not causation

A fishbone lists possible causes; a why-chain proposes one. Neither proves anything. Test each claimed root cause before concluding:

1. **Timeline.** Did the cause precede the effect? Did the effect start when the cause appeared (the reflow profile changed in week 12; the voids started in week 12)? A cause that postdates the effect is disqualified.
2. **Removal.** Would removing the cause remove the effect? Where possible, test it: revert the change, swap the batch, recalibrate, and see whether the effect stops.
3. **Data.** Is there evidence, not just a plausible story? Pull logs, measurements, incident records, control charts. A cause with no supporting data is a hypothesis, label it so.
4. **Mechanism.** Is there a coherent mechanism by which this cause produces this effect? A correlation with no mechanism is suspect.

**Root versus contributing causes.** A root cause is the origin; removing it stops recurrence. A contributing cause worsens or enables the effect but is not its source (removing it reduces severity but the problem still occurs). Classify each verified cause as one or the other; aim countermeasures primarily at the roots.

## Classic failure modes, and the guards against them

- **Stopping at the symptom.** The analysis ends at the proximate cause and the team fixes that, so the problem recurs from the same untouched root. *Guard:* keep asking "why" until removal prevents recurrence; verify with the removal test.
- **Single-cause bias / first-guess fixation.** The first plausible cause captures the whole analysis and the other categories are never examined. *Guard:* scan all categories in the fishbone before drilling any chain; the fan-out exists to defeat this.
- **Assigning blame instead of finding system causes.** The chain stops at "operator error" or "the vendor failed", which names a person, not a fixable cause. *Guard:* ask why the system permitted the error; push past the person to the method, machine, measurement, or environment that allowed it.
- **The 5 Whys collapsing into one unverified linear guess.** Five confident steps feel rigorous but are a single untested story. *Guard:* branch the chain where it branches, and verify each claimed root against timeline, data, removal, and mechanism before calling it the cause.

The countermeasure for a verified root cause should remove that root, not soothe the symptom. Each recommendation names the specific root it eliminates, and names what to check after acting: does the recurrence stop.
