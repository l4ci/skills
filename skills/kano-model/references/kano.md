# The Kano Model: categories, evaluation table, and decay

Noriaki Kano's model classifies product features by the relationship between how well a feature is delivered and how satisfied the customer is. Not all features are equal: some are expected and only punish you when missing, some reward you in proportion to how well you do them, and a few delight precisely because no one expected them. The model exists to stop you from spending equally on all three.

## The five categories (plus questionable)

- **MUST-BE (Basic, dissatisfier).** Expected. Absence causes strong dissatisfaction; presence adds nothing because the customer assumes it. These are table stakes. Doing them better than expected buys no extra satisfaction; failing them sinks the product regardless of everything else. A hotel room that is clean; a car that starts; a login that works.
- **ONE-DIMENSIONAL (Performance, satisfier).** Satisfaction rises roughly linearly with how well the feature is delivered. More is better. These are what customers explicitly ask for, compare on, and will pay more for. Fuel economy, download speed, battery life, price.
- **ATTRACTIVE (Delighter, exciter).** Unexpected. Presence delights and differentiates; absence causes no dissatisfaction because it was never expected. The source of competitive advantage and word of mouth. Customers cannot ask for these because they do not know to want them yet.
- **INDIFFERENT.** Presence or absence makes no difference to satisfaction. The customer does not care. Building these wastes effort; do not invest.
- **REVERSE.** Presence actively causes dissatisfaction; this segment would rather not have the feature. Over-engineering, unwanted complexity, defaults that fight the user. More is worse.
- **QUESTIONABLE.** A contradictory answer pair (the customer claims to both like its presence and like its absence, or expects it and dislikes it). Not a real category: it signals a badly phrased question, a misunderstood feature, or a respondent who was not paying attention. Re-ask, do not classify.

## Evaluation method: the paired question

Each feature is evaluated with two questions answered on the same 5-point scale:

- **Functional question:** "How do you feel if the feature is present (or done well)?"
- **Dysfunctional question:** "How do you feel if the feature is absent (or done poorly)?"

The five answer options for each question:

1. I like it
2. I expect it
3. I'm neutral
4. I can tolerate it
5. I dislike it

The pair of answers maps to a category through the Kano evaluation table. The dysfunctional answer is what discriminates: liking a feature's presence means little until you know whether its absence is tolerated (Attractive) or hated (Must-be or One-dimensional).

## The Kano evaluation table

Rows are the **functional** answer (feature present). Columns are the **dysfunctional** answer (feature absent). The cell gives the category: **M** must-be, **O** one-dimensional, **A** attractive, **I** indifferent, **R** reverse, **Q** questionable.

| Functional ↓ / Dysfunctional → | Like | Expect | Neutral | Tolerate | Dislike |
|---|---|---|---|---|---|
| **Like**     | Q | A | A | A | O |
| **Expect**   | R | I | I | I | M |
| **Neutral**  | R | I | I | I | M |
| **Tolerate** | R | I | I | I | M |
| **Dislike**  | R | R | R | R | Q |

How to read the key cells:

- **Like present / Dislike absent → O.** They want it there and hate it gone: classic performance feature.
- **Like present / Neutral or Tolerate absent → A.** They enjoy it but do not miss it: a delighter.
- **Expect present / Dislike absent → M.** They take presence for granted and punish absence: must-be.
- Anything **Neutral/Tolerate present and Neutral/Tolerate/Expect absent → I.** Nobody cares: indifferent.
- **Dislike present (any absence) → R.** They actively do not want it: reverse.
- The two diagonal extremes (**Like/Like**, **Dislike/Dislike**) → Q: contradictory, re-ask.

## The satisfaction curve

Plot customer satisfaction (vertical) against how well a feature is implemented (horizontal, from absent to fully delivered). The three live categories trace three different curves:

- **Must-be:** a flat, low curve that climbs steeply out of deep dissatisfaction at the left and then plateaus. Below the neutral line even when fully delivered. You can only avoid pain here, not create satisfaction. Diminishing returns set in immediately.
- **One-dimensional:** a straight diagonal through the origin. Absent gives dissatisfaction, fully delivered gives satisfaction, and every increment in between moves the needle. Effort converts directly to satisfaction.
- **Attractive:** a curve that sits flat near the neutral line on the left (absence is fine) and rises steeply to high satisfaction on the right (presence delights). Accelerating returns: the better you do it, the more disproportionate the delight.

Indifferent features are a flat horizontal line on the neutral axis. Reverse features slope downward: satisfaction falls as the feature is added.

## Decay over time

Categories are not fixed. They migrate downward as expectations rise:

> Attractive → One-dimensional → Must-be

Today's delighter becomes tomorrow's performance feature and eventually a baseline must-be. A once-novel capability (a rear-view camera, free shipping, dark mode, a phone that unlocks by face) starts as a surprise that wins customers, becomes something buyers compare and demand, and ends as something whose absence is unthinkable. Competitors copy delighters, and customers acclimate; the half-life of a delighter is short.

Two consequences:

1. A classification is a snapshot. Re-run it as the market moves. The must-be list grows over time; the attractive list must be continually refilled.
2. Plan a pipeline of delighters, not a single hit. The differentiation you build this year is the table stakes you must still meet next year.

## Categories vary by segment

The same feature can be must-be for one segment, attractive for another, and reverse for a third. A power user delights in configurability that a novice experiences as unwanted complexity (reverse). Enterprise buyers treat audit logging as must-be; consumers are indifferent to it. Never classify a feature in the abstract: always name the segment first, and expect a feature to land in different categories across segments. A feature that is reverse for your core segment should not ship to them even if it delights a fringe.

## Classic failure modes to guard against

- **Chasing delighters while a must-be is missing.** The single most damaging error. A missing or broken must-be sinks the product no matter how many delighters you pile on, because the must-be curve bottoms out in deep dissatisfaction that no amount of delight offsets. Cover every must-be before you spend a cent on an exciter.
- **Treating every feature as performance ("more features = better").** Most roadmaps implicitly assume linear satisfaction for everything. But must-bes have a ceiling (over-delivering buys nothing), indifferent features return zero, and reverse features cost you. Only genuine one-dimensional features reward "more."
- **Ignoring decay.** Classifying once and never revisiting leaves you defending last year's delighters as if they still differentiate, while a quietly-promoted must-be goes unmet.
- **Ignoring segment differences.** A single blended classification hides that a feature delights one segment and repels another. Average satisfaction is a fiction; ship to segments, not to the mean.
- **Reading the functional answer alone.** "Customers said they like it" is not a category. Only the functional/dysfunctional pair, run through the table, distinguishes a delighter from a must-be from an indifferent feature.
