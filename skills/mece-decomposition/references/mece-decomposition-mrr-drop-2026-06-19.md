# MECE Issue Tree: Q2 MRR Drop

> _Illustrative example output for the `mece-decomposition` skill. The SaaS company and its revenue figures are fictional; every number, segment, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Subject:** A 14% quarter-over-quarter drop in monthly recurring revenue (MRR) for a B2B project-management SaaS.
- **Purpose:** Diagnose the drop so each branch can be handed to an owner to investigate.
- **Date:** 2026-06-19

---

## 1. The cut

**Top-level logic: algebraic decomposition of the MRR movement equation.**

MRR is a number, and the question is why that number fell. When the target is a quantity, the algebraic cut is MECE by construction and ties every branch to an arithmetic that can be measured. Ending MRR is exactly the starting MRR plus everything that added revenue minus everything that removed it:

```
Ending MRR = Starting MRR
           + New MRR            (revenue from accounts that were not paying last quarter)
           + Expansion MRR      (existing accounts paying more)
           − Contraction MRR    (existing accounts paying less, still active)
           − Churned MRR        (accounts that left entirely)
```

The drop must live in one or more of these four flows. There is no fifth place for a dollar to go, which is what makes the cut clean. Each flow is independently ownable: new-business, customer-success/expansion, and retention each map to a different team, which is exactly what the purpose asks for.

**Why it beat the alternatives:** a *segment* cut (by plan tier, geography, industry) tells you *where* the drop is but not *what kind* of movement it is, and the same lost dollar can sit in two segments at once unless you fix a single attribute, fragile ME. A *process/funnel* cut (awareness → trial → paid → renewal) explains new-business weakness well but cannot represent expansion or contraction inside an existing account, leaving a gap (failed CE). The algebraic cut subsumes both: segment and funnel become the *second-level* logics applied inside each flow, where they are clean.

---

## 2. The tree

Each node states the single logic used to split it.

- **Q2 MRR drop (−14% QoQ)**: *split by MRR-movement flow (algebraic)*
  - **1. New MRR shortfall** *(less new revenue added than the prior quarter)*, *split by acquisition funnel stage (process)*
    - 1.1 Top of funnel, fewer qualified leads (demand-gen spend, channel mix, market softness)
    - 1.2 Conversion, same leads, lower trial→paid or opportunity→close rate (sales capacity, pricing objections, product fit)
    - 1.3 Deal size, same number of new logos, smaller average contract value (downsell at point of sale, tier mix shift)
  - **2. Expansion MRR shortfall** *(existing accounts grew less than before)*, *split by expansion mechanism (component)*
    - 2.1 Seat expansion, fewer net new seats added per account (slower customer headcount growth, adoption stall)
    - 2.2 Tier/upsell, fewer upgrades to higher plans (weaker upsell motion, feature gating less compelling)
    - 2.3 Add-on/usage, lower attach of paid add-ons or usage-metered revenue
  - **3. Contraction MRR** *(active accounts paying less than last quarter)*, *split by reason for downgrade (cause)*
    - 3.1 Seat reductions, accounts removing users (customer layoffs, lower utilization)
    - 3.2 Plan downgrades, accounts moving to a cheaper tier (value perception, budget pressure)
    - 3.3 Discount/renegotiation, same plan, lower price after renewal negotiation
  - **4. Churned MRR** *(accounts that left entirely)*, *split by churn driver (cause)*
    - 4.1 Involuntary churn, failed payments, expired cards, dunning gaps (collections problem, not a satisfaction problem)
    - 4.2 Voluntary, product/value, left because the product underdelivered (missing features, reliability, poor onboarding)
    - 4.3 Voluntary, external, left for reasons outside the product (company shut down, acquired, switched to a competitor on price)

Depth stops at level 2 because that is where a branch becomes an investigation a single owner can run. Going deeper (e.g., splitting 1.1 by channel) is the *owner's* first task, not the tree's job.

---

## 3. MECE check

**Level 1 (the four flows).** Passes ME: every dollar of MRR change is, by the identity above, either added (new, expansion) or removed (contraction, churn), a single dollar cannot be two of these in the same period. Passes CE: the four flows plus starting MRR reconstruct ending MRR exactly; there is no unaccounted movement. No "Other" branch is needed or allowed here, the algebra forbids a remainder.

**Level 2, branch 1 (funnel stages).** ME holds because the stages are sequential and a shortfall is attributed to the stage where the rate fell, not double-counted downstream. CE holds: leads × conversion × deal size is the full arithmetic of new MRR; nothing else produces a new dollar.

**Level 2, branch 2 (expansion mechanisms).** Seat / tier / add-on are the three distinct ways an existing account's bill rises in this product; they do not overlap (a seat is not a tier is not an add-on) and together they exhaust expansion. Approximate-ME note: a tier upgrade that *bundles* extra seats could touch 2.1 and 2.2, resolve by booking such moves to the line item the billing system records, not by judgment.

**Level 2, branches 3 and 4 (reasons / drivers).** Contraction splits cleanly into the three billing actions that reduce an active account's charge (fewer seats, cheaper tier, negotiated discount). Churn splits first on the binary *involuntary vs. voluntary* (payment failure vs. a decision to leave), then voluntary on *product vs. external* cause. The involuntary/voluntary binary is MECE by logic; the product/external split within voluntary is approximate, a customer can leave for a mix of reasons, so assign by the *primary* reason captured at cancellation. This is the one place ME is judgment, not arithmetic, and it is flagged.

---

## 4. Alternatives considered

- **Segment cut (by plan tier / industry / region).** Rejected as the *top* level: it locates the drop geographically but conflates movement types, and a churned enterprise account in the US sits in three segments at once unless one attribute is fixed, weak ME. Kept in reserve as a *cross-cut* to run inside whichever flow turns out largest.
- **Funnel/process cut (awareness → paid → renewal).** Rejected at the top because it cannot represent expansion or contraction within a live account, those dollars fall through the funnel's gaps (failed CE). Adopted instead as the level-2 logic inside the New MRR branch, where it is exactly right.
- **Hypothesis-driven cut (e.g., "it's the competitor's new pricing").** Rejected because solution-shaped branches bias what gets investigated and risk missing the real driver. The algebraic tree stays neutral; hypotheses belong *inside* a branch once the data points there.

---

## 5. How to use it

Pull the actual dollar figure for each level-1 flow first, this immediately tells you whether the −14% is an *acquisition* problem (branch 1), a *growth* problem (branch 2), or a *retention* problem (branches 3+4), and stops three teams from investigating in parallel when only one flow moved.

| Branch | Owner | First question to answer |
|---|---|---|
| 1. New MRR | VP Sales / Demand Gen | Which funnel stage's rate fell vs. last quarter: leads, conversion, or deal size? |
| 2. Expansion MRR | Customer Success / CS Ops | Did net seats per account slow, or did upsell stall? |
| 3. Contraction MRR | Customer Success / RevOps | What share of downgrades is layoffs (3.1) vs. value-driven downgrade (3.2)? |
| 4. Churned MRR | Retention / Billing | What share of churned MRR is involuntary (4.1, a billing fix) vs. voluntary? |

Sequence: **size the four flows → assign the dominant flow's branch to its owner → that owner runs the level-2 split with real data.** Each owner's branch is self-contained, so the investigations don't collide.

---

## 6. Caveats

- A tree structures the diagnosis; it does not perform it. The −14% is allocated here into ownable buckets, but the *cause* still has to be found by measuring each flow.
- The cut is MECE *relative to the stated scope*: the MRR-movement identity over one quarter. A different purpose (e.g., "which customer segment is least healthy?") would call for the segment cut as the top level instead.
- Level-1 is MECE by arithmetic and beyond dispute. The approximate-ME spots are flagged in §3: the seat-bundled tier upgrade (2.1/2.2) and the product-vs-external churn reason (4.2/4.3). Resolve both by a recording convention (book to the system-of-record line item; assign churn to the primary cancellation reason) rather than pretending the overlap doesn't exist.
- All figures and segments here are illustrative for documentation purposes and were not researched.
