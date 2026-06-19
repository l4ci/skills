# Six Thinking Hats: Dropping the Free Tier

> _Illustrative example output for the `six-thinking-hats` skill. The SaaS company is fictional; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

## Header

- **Focus question:** Should we remove the free tier of our project-management SaaS and move everyone to a 14-day trial instead?
- **Context:** Free users are 70% of signups but under 2% convert; support load from free accounts is heavy; the board wants margin improvement this year; sales fears losing the top-of-funnel.
- **Sequence used:** Blue (open) → White → Green → Yellow → Black → Red → Blue (close). White first to fix the numbers; Green early so alternatives appear before judgment hardens; Yellow before Black so the margin upside gets a fair hearing; Black to stress-test the funnel risk; Red near the end to surface the gut read.
- **Date:** 2026-06-19
- **Framework:** Edward de Bono's Six Thinking Hats. Five substantive hats (White, Red, Black, Yellow, Green) examined the one focus question in parallel, each strictly in its own mode; this Blue-hat pass integrates them. The method opens a question from every angle; it does not score options or forecast the outcome.

---

## Verdict

**Do not drop the free tier outright. Replace it with a tightly capped "forever-free" floor plus a 14-day full-feature trial, a hybrid, not a kill.** The two findings that drive this: (White) the free tier is the source of roughly 55% of paid conversions through team-invite virality, so deleting it removes the channel that feeds the very trials we'd be switching to; and (Black) a hard cutover risks a one-time churn and review-bombing event that could cost more in trust than the support savings recover in a year.

The emotional read is split and worth naming: Finance feels relief at the idea ("we are subsidising people who will never pay"), while Sales and Support feel dread for opposite reasons, Sales fears the funnel collapses, Support quietly hopes it does. That divergence is itself a signal that a blunt all-or-nothing move is the wrong shape. The Green hat's capped-floor idea neutralises the largest Black risk while still capturing most of the margin the board wants.

---

## The six hats

### White: Information (Confidence: medium-high)

**Findings**
- Free users are ~70% of new signups; free-to-paid conversion is ~1.8%.
- ~55% of *paid* accounts trace their origin to a free user who invited teammates (team-invite virality), per attribution tagging on the last four quarters.
- Free accounts generate ~40% of inbound support tickets while contributing 0% of revenue; estimated fully-loaded support cost ~$420K/year.
- A 14-day trial model is the dominant pattern among five named competitors; only one retains a free tier.
- **Data we do NOT have:** how many of the 55% virality conversions would still occur under a *trial* (i.e., would the inviter convert before inviting?); price elasticity of the converting 1.8% if forced to decide in 14 days; churn delta from existing free users who would be sunset.

**Evidence:** internal billing and attribution dashboards (medium confidence, attribution is last-touch and overstates the converting event); support cost-allocation model (lower confidence, fully-loaded cost is estimated, not measured).

**Weight:** The 55% virality origin and the unknown trial-substitution rate are the load-bearing facts. The support cost is real but an order of magnitude smaller than the revenue the funnel produces, so it cannot drive the decision alone.

### Green: Creativity (Confidence: n/a: generative)

**Findings (ideas, not judged)**
- **Capped forever-free floor:** keep free but cap it hard (e.g., 1 project, 3 seats, 30-day history). Preserves virality; strips the heavy users driving support cost.
- **Trial-on-top:** every new account starts a 14-day full-feature trial, then drops to the capped floor rather than to nothing. No one is ever locked out.
- **Self-serve support wall:** free tier gets community forum + docs only; live support is a paid feature. Cuts the 40% ticket load without removing the tier.
- **Virality-gated upgrade:** unlock an extra free seat for each teammate invited, turning the cost centre into an acquisition engine.
- **Usage-metered free:** free until X automation-runs/month, then trial-to-paid prompt. Aligns cost with value extracted.
- **Reverse trial:** start everyone on the paid plan free for 14 days, downgrade to capped-free automatically, the trial *is* the onboarding.

**Weight:** The capped forever-free floor and trial-on-top combine into the strongest single move; the self-serve support wall is the cheapest independent win regardless of the tier decision.

### Yellow: Benefits (Confidence: medium)

**Findings**
- **Margin lift via support relief:** removing or capping the heaviest free accounts cuts the ~$420K support line and frees engineering from free-tier-only bug triage, the mechanism is fewer low-value tickets, not higher prices.
- **Higher-intent funnel:** a 14-day trial forces a decision while the user is engaged, compressing the sales cycle; the mechanism is loss-aversion at trial expiry, which converts better than an open-ended free tier where urgency never arrives.
- **Cleaner positioning:** an all-paid (or paid-floor) base lets the product signal "serious tool for serious teams," supporting a price increase later.
- **Board optics:** a visible margin-structure change this year satisfies the board's stated goal and buys runway/trust for the next raise.

**Weight:** The support-relief margin lift is the most defensible benefit because the mechanism is direct and the cost is already measured. The trial-conversion uplift is real but speculative until tested, it assumes trial intent exceeds free-tier inertia, which the White hat flagged as unmeasured.

### Black: Caution (Confidence: high)

**Findings (logical, specific risks)**
- **Funnel collapse:** if ~55% of paid accounts originate from free virality, removing free removes the top-of-funnel that *feeds* the trial; trials don't generate themselves. A 14-day clock on a cold visitor converts far worse than a teammate already invited into a live project.
- **One-time churn + reputation event:** sunsetting existing free users triggers a coordinated backlash, review bombing on G2/Capterra, social posts, "they took away free", that depresses new signups for 1–2 quarters. The trust cost can exceed the support savings.
- **Trial-to-paid cliff:** 14 days is short for a tool that earns value only after a team adopts a workflow; many trials expire before the "aha," dropping conversion below today's 1.8%.
- **Competitive gift:** the one named competitor that keeps a free tier becomes the default fallback for displaced users, we hand them our funnel.
- **Support savings overstated:** much of the 40% ticket load may migrate to paid trials (now motivated, demanding users), not vanish.

**Weight:** The funnel-collapse risk is decisive, it attacks the revenue engine, not a cost line. The reputation event is high-likelihood and hard to reverse. The other three are real but secondary.

### Red: Feelings (Intensity reported, not justified)

**Findings (feelings, stated plainly)**
- **Finance:** strong relief, "we've been subsidising freeloaders; it feels overdue to stop." (high intensity)
- **Sales:** sharp anxiety, "this feels like sawing off the branch we sit on." (high intensity)
- **Support:** quiet, slightly guilty hope that it happens, "I'm tired of free-tier tickets." (medium intensity)
- **Product/founder gut:** unease at being seen as the company that *took something away*; a sense it would feel hostile to the early community. (medium-high intensity)
- **Engineering:** mild indifference leaning positive, "fewer edge cases to support." (low intensity)

**Weight:** The founder's "hostile to the community" unease and Sales' branch-sawing anxiety are the loudest and most aligned with the Black hat's hard evidence, when gut and logic point the same way, weight it heavily.

---

## Synthesis

**Integration.** Laid side by side, the hats converge more than they conflict. White establishes that the free tier is not merely a cost, it is the origin of most paid revenue via virality. Black sharpens that into the funnel-collapse risk. Green offers a direct escape: a *capped* free floor preserves virality while removing the heavy accounts that create the support cost Yellow wants gone. Yellow's strongest benefit (support relief) survives intact under the capped-floor idea; its weaker benefit (trial-conversion uplift) sits on an unmeasured assumption White already flagged. Red shows the organisation is not neutral, relief vs. dread along department lines, which argues against a blunt, irreversible move.

The pivotal interaction: **Green's capped forever-free floor directly neutralises Black's two largest risks.** Keeping a (hard-capped) free tier preserves the team-invite virality that feeds conversions, and never locking existing users out defuses the reputation/review-bombing event. The decision therefore is not "free vs. trial" but "uncapped free vs. capped free + trial."

**Weighing.** Five Black risks vs. four Yellow benefits, but volume doesn't decide. One Black risk (funnel collapse) outweighs all four Yellow benefits combined, because it threatens revenue while they trim cost. The single most actionable Yellow benefit (support relief) is fully achievable *without* taking the risk, via capping and a support wall. So the rational move is the one that banks the cheap win and routes around the expensive risk.

**The emotional read.** Finance's relief is real but is reacting to the cost line, not the revenue line, the gut that "feels overdue" is looking at half the picture White surfaced. Sales' and the founder's dread aligns with the hard evidence and should move the decision: a hard kill *feels* hostile because it *is* funnel-hostile. Weight the dread; discount the relief until it accounts for the virality data.

**Risks: must-mitigate vs. neutralized.**

| Black risk | Status | Mitigation / neutralizer |
|---|---|---|
| Funnel collapse (lose virality) | **Neutralized** | Green capped forever-free floor keeps team-invite virality alive |
| Reputation / review-bombing event | **Neutralized** | Never lock existing users out; migrate them to the capped floor, not to nothing |
| Trial-to-paid 14-day cliff | **Must mitigate** | Extend to 21 days for team accounts; trigger trial only after first real workflow action, not at signup |
| Competitor catches displaced users | **Must mitigate** | The capped floor means few users are displaced; monitor competitor signup mentions in churn surveys |
| Support savings overstated | **Must mitigate** | Implement the self-serve support wall independently; measure ticket deflection before claiming the margin in the board deck |

---

## Conclusion and actions

**Conclusion.** The answer to "should we remove the free tier and move to a 14-day trial?" is **no, not as a clean removal: replace it with a capped forever-free floor plus a full-feature trial on top.** This captures the support-cost margin the board wants while preserving the virality engine that produces ~55% of paid revenue, and it avoids the reputation event a hard sunset would trigger. The question is resolved on the substance; the remaining unknowns are conversion-rate magnitudes, not direction.

**Next actions:**
1. **Design the capped free floor** (1 project / 3 seats / 30-day history) and the trial-on-top flow; never auto-lock existing users, migrate them to the floor. *(Owner: Product, 2 weeks)*
2. **Ship the self-serve support wall** (community + docs for free; live support paid) independently of the tier change, and measure ticket deflection for one month before booking the margin. *(Owner: Support, 4 weeks)*
3. **Run a trial-length and trigger A/B test** (14 vs. 21 days; trial-at-signup vs. trial-after-first-action) on a new-signup cohort to settle the conversion-cliff unknown White flagged. *(Owner: Growth, 6 weeks)*
4. **Instrument virality substitution:** measure how many trial conversions originate from invites vs. cold visitors, to confirm the floor is preserving the funnel. *(Owner: Data, ongoing)*
5. **Bring the hybrid to the board** framed as a measured margin move with the funnel protected, not a free-tier kill, pre-empts the "we lost top-of-funnel" objection. *(Owner: Founder, next board cycle)*

---

## Caveats

- Six Hats opens this question across modes of thought; it does not score the hybrid against a pure-trial or status-quo option on weighted criteria, nor guarantee the chosen path is right. If the board wants a head-to-head scoring of three pricing models, use a decision matrix next.
- The hats reflect the information and intuitions available at this session, the converting-cohort and support-cost figures are estimates, and the trial-conversion uplift is an untested assumption. A clear conclusion means the question was examined from every angle, not that the outcome is certain.
- All figures, departments, and feelings here are illustrative for documentation purposes and were not researched.
