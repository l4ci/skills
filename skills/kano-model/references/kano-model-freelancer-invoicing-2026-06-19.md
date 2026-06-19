# Kano Analysis: Solo-Freelancer Invoicing Plan

> _Illustrative example output for the `kano-model` skill. The product, segment, and competitive details are fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Segment:** Solo freelancers on the entry-tier ($12/mo) invoicing plan, one-person service businesses (designers, writers, consultants, contractors) who bill a handful of clients and have no bookkeeper.
- **Features classified:** recurring invoices, automatic late-payment reminders, multi-currency support, built-in time tracker, AI-drafted invoice descriptions, white-label branding.
- **Product / context:** a $12/mo SaaS invoicing tool competing with FreshBooks and Wave. The decision this informs is what to put in the next two quarters of roadmap.
- **Date:** 2026-06-19.
- **Framework note:** this is a *reasoned* Kano classification using competitor offerings, review patterns, and segment behaviour as proxies. It is **not a fielded functional/dysfunctional survey.** The high-stakes calls below should be validated with a real Kano survey before large bets. Categories are keyed to this one segment at this one moment, and they decay.

---

## 1. Verdict

**No must-be is currently missing from the candidate list, but two features in it are already baseline must-bes that competitors ship, so they are non-negotiable table stakes, not roadmap "wins."** Automatic late-payment reminders and recurring invoices are both must-be for this segment: their absence drives strong dissatisfaction and churn, their presence buys no praise. FreshBooks and Wave both have them. Ship them first and stop counting them as differentiators.

**Compete on the one-dimensional feature: white-label branding.** For solo freelancers whose invoice *is* their brand touchpoint with a client, "remove the vendor's logo / add my own" is a satisfier that scales with how cleanly it is done, and it is a known up-sell lever. This is the axis to do better than Wave's bare free tier.

**Back exactly one delighter: AI-drafted invoice descriptions.** It is unexpected at $12/mo, removes a small recurring annoyance (writing line-item prose), and differentiates against incumbents that do not have it yet. Concentrate the delight budget here rather than spreading it.

**Cut the built-in time tracker and treat multi-currency as conditional.** The time tracker is *indifferent* for this segment (most entry-tier freelancers track time elsewhere or bill flat); building it returns little. Multi-currency is *indifferent-to-attractive* and splits hard by sub-segment, must-be for the freelancer with overseas clients, irrelevant for the domestic-only majority. Do not put it in the core build; gate it behind a usage signal.

Riskiest gap: none missing, but the riskiest *mistake available* is shipping the time tracker (indifferent effort sink) or treating reminders/recurring as optional polish when they are the floor.

---

## 2. Classification table

Grouped by category. Confidence is the analyst's, lowered wherever the call rests on reasoning rather than survey data.

### Must-be (M)

| Feature | Functional (present) | Dysfunctional (absent) | Conf | Decay risk |
|---|---|---|---|---|
| Automatic late-payment reminders | Expect | Dislike | High | Already a must-be; stays must-be. No further decay: it is the floor. |
| Recurring invoices | Expect | Dislike | Med-High | Already must-be for retainer-based freelancers; stable. |

### One-dimensional (O)

| Feature | Functional (present) | Dysfunctional (absent) | Conf | Decay risk |
|---|---|---|---|---|
| White-label branding | Like | Dislike | Medium | Slow drift toward must-be over ~2–3 yrs as free tiers add it; still a live satisfier now. |

### Attractive (A)

| Feature | Functional (present) | Dysfunctional (absent) | Conf | Decay risk |
|---|---|---|---|---|
| AI-drafted invoice descriptions | Like | Neutral | Med-Low | Fast decay (~12–18 mo): AI features are being copied across the category quickly; will slide to one-dimensional, then must-be. |

### Indifferent (I)

| Feature | Functional (present) | Dysfunctional (absent) | Conf | Decay risk |
|---|---|---|---|---|
| Built-in time tracker | Neutral | Tolerate | Medium | n/a: indifferent features do not decay into satisfiers for this segment. |
| Multi-currency support | Neutral | Tolerate (domestic majority) | Low | Conditional: must-be for the overseas-client sub-segment; indifferent for the rest. See per-feature note. |

### Reverse (R)

None for this segment. (See segment-sensitivity notes: the time tracker edges toward reverse for the "I bill flat fees and don't want clutter" sub-segment.)

---

## 3. Per-feature detail

### Automatic late-payment reminders: Must-be (High)

- **Functional / dysfunctional:** *Expect present* (a freelancer assumes a billing tool chases overdue invoices, it is why they pay for one over a Word template) / *Dislike absent* (chasing late payers by hand is the single most-cited freelancer pain; its absence would feel like the tool failing at its core job). Expect/Dislike → **M**.
- **Why must-be, not performance:** more elaborate reminder cadences do not raise satisfaction much above "it works"; a freelancer just wants the money chased. The curve plateaus fast, classic must-be.
- **Segment sensitivity:** universal across freelancer sub-segments. Even flat-fee billers want it.
- **Evidence vs. assumed:** FreshBooks and Wave both ship automated reminders on paid tiers (competitor evidence, solid). The *strength* of dissatisfaction on absence is reasoned from review themes ("getting paid on time"), not measured.

### Recurring invoices: Must-be (Med-High)

- **Functional / dysfunctional:** *Expect present* (retainer and subscription-style freelancers assume the tool re-bills automatically) / *Dislike absent* (re-creating the same invoice monthly is exactly the manual toil they bought software to avoid). Expect/Dislike → **M**.
- **Why must-be:** it is a baseline of any modern invoicing tool; presence is unremarkable, absence is a dealbreaker for the retainer cohort.
- **Segment sensitivity:** **must-be** for retainer/subscription freelancers; closer to *indifferent* for the purely project-by-project freelancer who never bills the same thing twice. The retainer cohort is large enough that the blended call is must-be, but this is the feature most worth splitting by sub-segment.
- **Evidence vs. assumed:** competitor parity is documented. The blended category leans on an assumed retainer-cohort share (~40–50%); a survey would sharpen it.

### White-label branding: One-dimensional (Medium)

- **Functional / dysfunctional:** *Like present* (a freelancer's invoice is a client-facing brand surface; their own logo and no vendor mark looks more professional and they value it) / *Dislike absent* (a competitor's logo on *my* invoice to *my* client reads as amateur). Like/Dislike → **O**.
- **Why one-dimensional, not attractive:** satisfaction scales with how complete the branding control is (logo only → colours → full template → custom domain on the pay page). Each increment converts to satisfaction, and it is a feature freelancers explicitly ask for and will pay to unlock, the signature of a performance feature.
- **Segment sensitivity:** strongest for client-facing creative freelancers (designers, agencies-of-one); weaker for back-office contractors who never see their invoice as marketing. Not reverse for anyone here.
- **Evidence vs. assumed:** Wave's free tier carries Wave branding and white-labeling is a known up-sell; FreshBooks gates deeper customization to higher tiers (competitor evidence). That this segment *dislikes* the vendor mark on absence is reasoned, medium confidence.

### AI-drafted invoice descriptions: Attractive (Med-Low)

- **Functional / dysfunctional:** *Like present* (auto-writing tidy line-item descriptions from a few words is a pleasant surprise that saves a small recurring chore) / *Neutral absent* (freelancers do not yet expect AI in a $12 invoicing tool, so its absence costs nothing). Like/Neutral → **A**.
- **Why attractive:** no one is asking for it (delighters are features customers don't know to want), it is not yet table stakes at this price point, and done well it produces a "oh, nice" moment. Accelerating returns, the better the drafts, the more disproportionate the delight.
- **Decay:** fast. AI text features are spreading across the category; expect this to slide to one-dimensional within ~12–18 months and toward must-be after that. Bank the differentiation now and plan its replacement.
- **Segment sensitivity:** delight for the freelancer who hates writing descriptions; edges toward *indifferent* for the one whose line items are always identical (they have a template already).
- **Evidence vs. assumed:** that incumbents at this tier lack it today is the differentiator (competitor evidence). The *strength* of delight is the softest call in this report, lowest confidence; validate before betting the quarter on it as the headline.

### Built-in time tracker: Indifferent (Medium)

- **Functional / dysfunctional:** *Neutral present* (entry-tier freelancers who bill hourly mostly already track time in a dedicated tool or a spreadsheet; an in-app tracker is "fine, I guess") / *Tolerate absent* (they shrug, they have a workflow). Neutral/Tolerate → **I**.
- **Why indifferent, not performance:** the satisfaction needle barely moves either way. A second-rate embedded tracker competes with Toggl-class tools the freelancer already trusts; switching cost makes it a non-event.
- **Segment sensitivity:** for the hourly freelancer with *no* existing tracker it edges toward attractive; for the flat-fee freelancer who finds the tracker UI clutter it edges toward **reverse** (unwanted complexity in a tool they want to stay simple). The blend is indifferent, which is the case *against* building it.
- **Evidence vs. assumed:** the "already track elsewhere" behaviour is reasoned from how the segment works, not surveyed. Medium confidence that the net is indifferent; the spread across sub-segments is the real story.

### Multi-currency support: Indifferent / conditional must-be (Low)

- **Functional / dysfunctional (domestic majority):** *Neutral present* / *Tolerate absent* → **I**. **(overseas-client sub-segment):** *Expect present* / *Dislike absent* → **M**.
- **Why split:** for a freelancer with only domestic clients, currency is invisible. For the freelancer with even one overseas client, billing in the wrong currency is a hard blocker, absence drives them to a competitor outright. There is no single blended category that is honest here; average satisfaction is a fiction.
- **Segment sensitivity:** this is the textbook segment-dependent feature. Gate it behind a signal (client country / "do you invoice abroad?" at onboarding) rather than building it into the universal core.
- **Evidence vs. assumed:** the existence of the overseas sub-segment is certain; its *share* of the entry-tier base is assumed (low confidence) and is exactly what a survey should measure before scoping the build.

---

## 4. The feature set and sequence

### Must-bes to guarantee (table stakes: non-negotiable)

- **Automatic late-payment reminders** and **recurring invoices.** Cover both, adequately, before anything else. A missing must-be sinks the product no matter how good the AI drafting is. These are the floor, not the roadmap headline.

### Performance feature to compete on

- **White-label branding.** Pick this as the satisfaction axis to beat the incumbents on, especially Wave's branded free tier. Invest in *depth* (logo → colours → template → custom pay-page domain) because every increment converts to satisfaction and it is a clean up-sell.

### Delighter to back (exactly one)

- **AI-drafted invoice descriptions.** The single deliberate exciter. Concentrate the delight budget here; do not scatter it. Lead marketing with it while it is still novel.

### Drop

- **Built-in time tracker.** Indifferent for the segment; returns little and risks clutter (reverse) for flat-fee billers. Cut from the core roadmap.

### Avoid shipping to this segment

- Nothing is outright reverse here. But do **not** force the time tracker on flat-fee freelancers (where it edges reverse), if built at all, make it opt-in, never a default surface.

### Conditional

- **Multi-currency support.** Not in the universal core. Gate behind an onboarding signal; build only for the overseas sub-segment once its share is measured.

### Build order

1. **Q-now / first:** confirm and harden the two must-bes (reminders, recurring). Floor must be solid before any exciter ships.
2. **Then:** white-label branding depth, the performance axis to compete on.
3. **Then:** AI-drafted descriptions, the one delighter, shipped while still a surprise.
4. **Deferred / gated:** multi-currency for the overseas sub-segment, pending a usage/share signal.
5. **Dropped:** time tracker.

### Decay timeline

| Feature | Today | ~12–18 mo | ~2–3 yr |
|---|---|---|---|
| AI-drafted descriptions | Attractive (delighter) | One-dimensional (compared, expected) | Must-be (absence unthinkable) |
| White-label branding | One-dimensional | One-dimensional, drifting | Must-be as free tiers add it |
| Reminders / recurring | Must-be | Must-be | Must-be |

Implication: the delighter you ship next quarter (AI drafts) is the table stakes you must still meet next year. **Plan the next delighter now**: a single hit is not a pipeline. Re-run this classification as the market moves; the must-be list only grows.

---

## 5. Caveats

- **Kano is a model of satisfaction, not of cost, effort, or revenue.** It says which features matter to this segment and why: not in what order to build them by ROI. Pair it with RICE to sequence the backlog by score (e.g., the AI drafting delighter may be high-impact but also high-effort; Kano does not weigh that).
- **One segment, one moment.** Every call here is for entry-tier solo freelancers as of 2026-06-19, and the categories decay. Multi-currency and recurring invoices already show how hard the picture splits by sub-segment, average satisfaction is a fiction; ship to segments, not the mean.
- **This is a reasoned proxy, not survey data.** No functional/dysfunctional survey was fielded. The softest calls, the *strength* of delight from AI drafts, the *share* of the overseas and retainer sub-segments, are the ones to validate with a real Kano survey before committing a quarter of roadmap to them.
- **A clean classification describes how features drive satisfaction, not whether the product will succeed.** Covering the must-bes and backing the right delighter is necessary, not sufficient.
- All figures here are illustrative for documentation purposes and were not researched.
