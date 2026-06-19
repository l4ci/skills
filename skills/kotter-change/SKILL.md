---
name: kotter-change
description: Use when the user wants to lead an organizational change using Kotter's 8-step model (urgency, coalition, vision, communication, removing barriers, short-term wins, sustaining acceleration, anchoring in culture). Facilitates the eight sequential steps with a gate check per step, uses parallel subagents within a step where useful, and maintains a change plan document. Triggers include "Kotter", "8-step change", "Leading Change", "change management", "drive organizational change", "manage a transformation".
---

# kotter-change

Guides Kotter's 8-step change cycle (John Kotter, *Leading Change*) to lead a real organizational change. Catches the failure where skipping a step creates the illusion of speed but rarely produces a satisfying result.

The eight steps, their gate questions, and the pitfalls live in [references/kotter.md](references/kotter.md). Load that file before facilitating.

## When to use

The user wants to lead a substantial organizational change: a new strategy, a restructuring, a merger integration, a cultural shift, a transformation. Kotter drives the change that mckinsey-7s diagnoses: if 7-S shows the parts pulling in different directions, Kotter is how you move them. ADKAR is the companion lens for the individual side (does each person have the Awareness, Desire, Knowledge, Ability, and Reinforcement to make the change). For a lighter analytical tool that weighs the forces for and against a change before committing to it, prefer force-field-analysis.

## Language

Facilitate and write the document in the language the user is writing in. The reference file is English; keep the framework keyed to it regardless of output language.

## Inputs

- **CHANGE** (required): the change to lead and the organization or unit it affects.
- **CONTEXT** (optional): why now, who holds power, prior change history, and the known sources of resistance.

## How to facilitate

Work step by step. Each step has a gate question that must be answered before the next begins; hold the gate. Record everything in the change plan, and name the current step at each turn.

1. **Create urgency.** Help the user assemble the honest case for why this change must happen now: the threats, the closing windows, the cost of standing still, framed to reach people, not just inform them. Where the evidence comes from several directions, dispatch parallel subagents to surface urgency evidence from different angles (market, customer, financial, competitive, operational), each returning a list of evidence with reasoning rather than prose; pool and sharpen them with the user. Gate: is there enough felt urgency that the people who matter will act, not just nod? Manufactured panic or a single anxious leader does not clear.

2. **Build the guiding coalition.** Help identify who must be on the team for it to have enough power, credibility, and expertise, and check it functions as a team rather than a committee. Gate: does the coalition have enough real power and credibility to drive the change against resistance? If it looks right on the org chart but lacks authority or line leaders, name the gap rather than proceeding.

3. **Form the vision.** Help write a vision that is clear, desirable, feasible, and simple enough to communicate in a few minutes, plus the strategic initiatives that move toward it. Gate: can the vision be explained in a few minutes and leave the listener clear on the direction and willing to follow? A vision that is really a financial target or a detailed plan does not clear.

4. **Communicate the vision.** Help plan how the vision will be communicated constantly and through behavior, not one memo: the channels, the repetition, and how the coalition will model it. Gate: do enough people understand and accept the vision that a volunteer army is forming? If communication is a one-off launch or leaders are behaving against the vision, hold here.

5. **Remove barriers.** Inventory what blocks action: structures, processes, systems, skill gaps, and resistant managers. Where the barriers span lenses, dispatch parallel subagents to inventory them across angles (structure, systems and incentives, skills, and people), each returning candidate barriers with reasoning; pool, dedupe, and prioritize them with the user, then plan the removals. Gate: can people actually act on the vision now? A key barrier left standing (a misaligned incentive, a resistant senior manager) does not clear.

6. **Generate short-term wins.** Help engineer wins that are visible, unambiguous, and clearly tied to the change, and plan to deliver them early. Gate: have real, visible wins been delivered and made clearly attributable to the change? Vague or disputable wins do not clear.

7. **Sustain acceleration.** Help spend the credibility from early wins on bigger, deeper change rather than treating the win as the finish. Gate: is the momentum being used to take on more change, with urgency intact? This gate is where change most often dies; do not let a short-term win be mistaken for victory.

8. **Anchor in culture.** Help connect the new behaviors to the results they produced, reinforce them in norms, and protect them through who gets promoted, so the change outlasts the people who drove it. Gate: are the new ways tied to results, built into norms, and safe in leadership succession? If anchoring is by decree before results made the new way credible, or absent entirely, the change will revert.

## Change plan document

Maintain a markdown document, saved to `kotter-change-<change-slug>-<YYYY-MM-DD>.md` (today's date) in the working directory unless the user names another location:

1. **Header.** The change, the organization or unit, the date, and the sponsor.
2. **Urgency.** The case for why now, the evidence behind it, and the level of felt urgency.
3. **Guiding coalition.** Who is on it, the power and credibility it carries, and how it works as a team.
4. **Vision.** The vision statement, the strategic initiatives, and the few-minute version.
5. **Communication.** The plan to communicate the vision through channels and behavior, and the signs of acceptance.
6. **Barriers.** The inventoried barriers across lenses, the priorities, and the removal plan.
7. **Short-term wins.** The wins engineered, delivered, and tied to the change.
8. **Sustained acceleration.** The bigger changes taken on with the credibility from wins.
9. **Anchoring.** How the change is tied to results, built into norms, and protected in succession.
10. **Step gates.** A short record that each gate question was answered before advancing.
11. **Caveats.** Weak urgency undermines everything built on it; a coalition without real power cannot overcome resistance; declaring victory at the first win is what kills change in its second half; and a change that is not anchored in culture reverts once the drivers leave.

## Principles

- **Hold the gates.** Do not advance a step that has not answered its question.
- **Never skip urgency.** Skipping it to save time is the most common and most fatal mistake.
- **Communicate by behavior.** Leaders modeling the vision carries it; leaders contradicting it kills it. Words alone undercommunicate by orders of magnitude.
- **Anchor before letting go.** Change lasts only when built into norms and into who gets promoted, not when announced as done.
