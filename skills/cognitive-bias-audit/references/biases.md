# Cognitive biases: families, tells, and countermeasures

Biases are systematic, not random. The same pressures bend a decision the same way every time, which is why you cannot introspect them away and why generic awareness ("watch out for bias") changes nothing. What works is auditing a specific decision against known families and installing structural countermeasures into the process.

Each entry below gives the bias, **the tell** (how it actually shows up in a decision's reasoning), and **a countermeasure** (a process change, not an exhortation). A bias counts as *live* only when you can point to the reasoning where it operates. Severity is how much it could distort *this* call; confidence is how sure you are it is operating here.

---

## Belief & evidence

How the decision gathered and weighed information.

| Bias | The tell | Countermeasure |
|---|---|---|
| **Confirmation bias** | Evidence cited all points one way; disconfirming data is absent, dismissed, or never sought. Only supporting sources consulted. | Considering the opposite: assign someone to build the strongest case against. Pre-commit to what evidence would change the call. |
| **Motivated reasoning** | The conclusion serves the reasoner's interest, identity, or prior commitment; the argument was built backward from a wanted answer. | Blind review by someone with no stake. Separate the person who wants the outcome from the person who judges the evidence. |
| **Anchoring** | A first number, estimate, or proposal frames everything after it; the final figure sits suspiciously close to the opening one. | Generate estimates independently before anyone shares one. Anchor on a base rate, not on the first quote. |
| **Availability** | Risks or options are weighted by how easily examples come to mind (recent, vivid, memorable), not by frequency. | Pull actual frequencies. Ask "how often does this really happen?" against data, not memory. |
| **Base-rate neglect** | Specific, vivid detail about this case crowds out the prior probability for cases like it. "This time is different" with no reason why. | Base-rate anchoring and reference-class forecasting: start from the rate for the class, adjust only for evidence that this case truly differs. |

## Confidence & prediction

How the decision estimates outcomes and its own accuracy.

| Bias | The tell | Countermeasure |
|---|---|---|
| **Overconfidence** | Stated certainty exceeds the evidence; ranges are too narrow; no serious account of being wrong. | Calibrated ranges with explicit probabilities. Decision journals to check past confidence against outcomes. |
| **Planning fallacy** | Timeline or cost built bottom-up from the ideal path, ignoring how similar efforts actually went. | Reference-class forecasting: estimate from how comparable projects finished, not from the inside view of this one. |
| **Optimism bias** | Best-case treated as expected case; downside scenarios thin or absent. | Pre-mortem: assume it failed, list why. Force an explicit downside case. |
| **Hindsight bias** | Past outcomes described as "obvious" or "inevitable," distorting what was actually knowable at the time. | Decision journals recording the reasoning and probabilities at the time of the call, before outcomes are known. |

## Attachment & loss

How prior investment and ownership distort the call.

| Bias | The tell | Countermeasure |
|---|---|---|
| **Sunk cost** | Past spend (money, time, effort) cited as a reason to continue; "we've already invested too much to stop." | Decide on future costs and benefits only. Ask: would we start this today, knowing what we now know? |
| **Loss aversion** | Potential losses loom larger than equivalent gains; the option that merely avoids loss is over-weighted. | Reframe symmetrically in both gain and loss terms; pre-committed criteria set before stakes felt. |
| **Status-quo bias** | The current option gets a free pass; alternatives must clear a higher bar to justify any change. | Treat the status quo as one option among several, scored on the same criteria as the rest. |
| **Endowment** | What is already owned or built is valued above its market or replacement worth. | Ask what an outsider with no ownership would pay or choose. |
| **Escalation of commitment** | Doubling down on a failing course to justify earlier choices; new resources chase a defended position. | Pre-committed stop-loss criteria and kill conditions, set before the project, judged by someone uninvolved. |

## Social

How group dynamics and authority shape the call.

| Bias | The tell | Countermeasure |
|---|---|---|
| **Groupthink** | Quick consensus, little recorded dissent, pressure to agree; disagreement treated as disloyalty. | Devil's advocate / red team with a real mandate. Collect views privately before discussion. |
| **Authority bias** | A view carries weight because of who holds it, not the argument behind it. | Blind review; evaluate the argument with the source stripped out. Junior voices first. |
| **Bandwagon** | "Everyone is doing it" or rising adoption stands in for an actual reason. | Demand the first-principles case independent of who else chose it. |
| **Halo effect** | One strong trait (a track record, a brand, a credential) inflates judgment of unrelated qualities. | Score each dimension separately on its own evidence; do not let one carry the rest. |
| **In-group bias** | Ideas, people, or vendors from the in-group are trusted more; outsiders held to a higher bar. | Apply identical criteria regardless of source; blind the origin where possible. |

## Framing & salience

How presentation and the story bend the call.

| Bias | The tell | Countermeasure |
|---|---|---|
| **Framing effect** | The choice flips with how options are worded (gains vs. losses, 90% success vs. 10% failure). | Restate the decision in the opposite frame and check the answer holds. |
| **Recency** | Latest events dominate; older but relevant evidence is discounted. | Weight evidence over a full time window, not just the last data point. |
| **Salience** | A vivid or dramatic factor crowds out duller but more important ones. | List all material factors and weight them deliberately; do not let the loudest win by volume. |
| **Narrative fallacy** | A clean cause-and-effect story is mistaken for the real explanation; messy, conflicting data smoothed over. | Demand the alternative story and the evidence that does not fit the preferred one. |
| **Survivorship bias** | Reasoning from winners or survivors only; the failures that fit the same pattern are invisible. | Find the comparable cases that failed; ask what data is missing because it did not survive. |

---

## Debiasing toolkit

Countermeasures repeat across families because a few structural moves do most of the work. Prescribe these by name, tied to the specific exposure found:

- **Pre-mortem.** Assume the decision failed; work backward to the causes. Surfaces optimism, planning fallacy, overconfidence.
- **Reference-class forecasting / outside view.** Estimate from how comparable cases actually turned out, not from the inside story of this one. Counters base-rate neglect, planning fallacy, optimism.
- **Devil's advocate / red team.** A mandated role to argue the other side. Counters confirmation bias, groupthink.
- **Blind review.** Judge the evidence or option with the source and stakes hidden. Counters authority bias, halo, motivated reasoning, in-group bias.
- **Base-rate anchoring.** Start from the prior probability for the class before adjusting for specifics. Counters base-rate neglect, availability.
- **Decision journals.** Record the reasoning, probabilities, and confidence at the time of the call. Counters hindsight and overconfidence over time.
- **Considering the opposite.** Deliberately build the case against the preferred answer and the conditions under which it is wrong. Counters confirmation bias, narrative fallacy, framing.
- **Pre-committed criteria.** Set the decision rules, weights, and kill conditions before stakes are felt. Counters sunk cost, escalation, loss aversion, status-quo bias.

## How not to misuse the audit

Three failure modes turn a bias audit into theater. Guard against all three:

1. **Bias-spotting theater.** Labeling biases generically with no evidence they operate in this decision. Every flagged bias must quote the actual reasoning where it shows up.
2. **Auditing others, not yourself.** It is easy to find bias in someone else's case and miss it in your own. Apply the families to the reasoning at hand whoever produced it, including the reasoner's own.
3. **Motivated dismissal.** Using "that's just confirmation bias" to wave away a conclusion you simply dislike. A bias label is not a refutation; it identifies where the process is exposed, which then has to be tested, not assumed wrong.
