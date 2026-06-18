# Jobs to Be Done: framework, four forces, and opportunity scoring

People do not want a product. They want to make progress in a struggling moment. They "hire" a solution to get a job done, and "fire" it when something does the job better. The unit of analysis is the **job in a circumstance**, not the customer's demographics and not the product.

"People don't want a quarter-inch drill, they want a quarter-inch hole" — and really, they want the progress the hole enables (a shelf, a hung picture, a finished room). The job is solution-agnostic and stable over time; products and technologies come and go. A drill, a hook, an adhesive strip, and a handyman all compete for the same hole.

A job is anchored to a circumstance: **when [situation], a person struggling to make some progress.** Two people with identical demographics can have different jobs in different moments; one person can have different jobs at different moments. Profile the circumstance, not the person.

## The three dimensions of a job

Every job has three dimensions at once. Most analyses see only the first and miss the switch that the other two drive.

1. **Functional.** The practical task to accomplish — the objective, measurable work. "Get a hole in the wall." "Get to the meeting on time." This is the dimension products are usually designed for.
2. **Emotional.** How the person wants to feel, or to stop feeling, while making progress. Reassurance, control, confidence, relief from anxiety or guilt. "Feel competent doing my own repairs rather than helpless."
3. **Social.** How the person wants to be perceived by others. Status, belonging, being seen as responsible, modern, or capable. "Look like the kind of parent who keeps a tidy home."

Plus the **circumstance / trigger**: the situation that creates the struggle and starts the hunt for a solution. The trigger is the moment the job becomes active and worth acting on.

## Desired outcomes

The customer measures whether a job was done well by **outcomes**, not by features. Outcomes are stable, solution-agnostic, and measurable. Phrase each as an **outcome statement** with four parts:

> **direction + metric + object of control + context**

- "**Minimize** the **time it takes to** **detect a leak** **when the appliance is unattended**."
- "**Reduce** the **likelihood that** **the hole is off-center** **when drilling into tile**."
- "**Increase** the **number of** **guests served** **without reheating food**."

Direction is *minimize* or *increase* (or *reduce the likelihood / time / number*). A good outcome statement contains no solution. If you can point at a product in it, rewrite it.

## Competing solutions

What does the person hire today? List the full set, not just direct rivals:

- **Direct competitors** in the same category.
- **Indirect / cross-category** solutions that do the same job a different way (a drill versus a handyman versus a removable hook).
- **Workarounds** the person cobbles together (a nail and a hammer, a spreadsheet, a manual checklist). Workarounds are the loudest signal of an underserved job.
- **Nonconsumption** — doing nothing, putting up with the problem, or abandoning the job. Often the largest competitor and the one most overlooked. The real competition is rarely just the named rivals; it is whatever the person does *instead*, including nothing.

## The four forces of progress

A switch from the old way to a new solution happens only when the forces pushing toward change beat the forces holding the person in place.

| | Drives the switch | Resists the switch |
|---|---|---|
| **Tied to the present** | **Push** of the situation: the pain, frustration, and triggering event that make the current way intolerable | **Habit** of the present: comfort with what works today, switching cost, inertia, "good enough" |
| **Tied to the new** | **Pull** of the new solution: the attraction of the new way, the better outcome it promises | **Anxiety** of the new: uncertainty, fear it won't work, learning cost, risk of looking foolish |

A switch occurs only when **Push + Pull > Anxiety + Habit**. Most product thinking pours energy into Pull (features, messaging) and ignores the two resisting forces. To win a switch you can also reduce Anxiety (guarantees, trials, onboarding) and loosen Habit (migration help, switching incentives). Map all four for the job, not just the attractive ones.

## The job story

Capture the job in one line that names situation, motivation, and expected outcome — and names no solution:

> **When [situation], I want to [motivation], so I can [expected outcome].**

Example: "When I notice water pooling under the sink late at night, I want to know whether it's urgent, so I can decide whether to call a plumber now or wait until morning."

If the sentence contains your product, it is a feature story, not a job story. Rewrite it solution-free.

## Opportunity scoring (ODI)

Rank desired outcomes to find where to focus. For each outcome, gather two ratings (typically 1–10, from the customer, not from the team):

- **Importance**: how important is this outcome to the customer.
- **Satisfaction**: how well are current solutions delivering it today.

The opportunity is highest where importance is high and satisfaction is low — the **underserved** outcomes.

> **Opportunity = Importance + max(Importance − Satisfaction, 0)**

The `max(…, 0)` term ignores overserved outcomes (where satisfaction already exceeds importance) rather than rewarding them. Sort outcomes by opportunity score:

- **High importance, low satisfaction → underserved.** The opportunity. Build here.
- **High importance, high satisfaction → served.** Table stakes; match, don't over-invest.
- **Low importance → ignore**, whatever the satisfaction. Overserved outcomes (low importance, high satisfaction) are candidates to *stop* investing in.

## Classic failure modes to guard against

- **Confusing the job with your product.** The job is solution-agnostic and stable; your product is one current way to get it done. If your "job" mentions your product or category, you have described a feature, not a job, and you are blind to the real competition.
- **Thinking in demographics, not circumstances.** "Women aged 35–50" is not a job. The same person hires different solutions in different moments. Anchor every job to a situation and a trigger.
- **Ignoring the emotional and social dimensions.** Functional-only analysis explains what the product does but not why people switch. The emotional and social jobs are usually what tips Push and Pull over the line.
- **Naming only direct competitors.** Missing workarounds and nonconsumption means missing the largest part of the market and the strongest evidence of an underserved job.
- **Outcome statements that hide a solution.** "Make the app faster" names a solution. "Minimize the time it takes to confirm the payment cleared" names an outcome.
