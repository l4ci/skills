# Scenario Planning: On-Prem Product Line, 2026-2036

> _Illustrative example output for the `scenario-planning` skill. The company, market, and every figure, name, regulation, and claim below are invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Focal question:** How should our mid-market data-infrastructure company position its on-prem product line over the next ten years, given the shift to cloud?
- **Entity:** A mid-market data-infrastructure vendor (~$140M ARR, ~55% from a self-managed on-prem database/streaming stack, the rest from a younger managed cloud SaaS).
- **Horizon:** Ten years (2026-2036).
- **Date:** 2026-06-19.
- **Method:** 2x2 critical-uncertainties method (GBN / Royal Dutch Shell tradition; Schwartz, *The Art of the Long View*). These are four plausible futures to prepare for, **not forecasts**, and none carries a probability. The deliverable is the strategy and signposts, not the four stories.
- **Decision it feeds:** A board call on whether to fund continued on-prem R&D, and at what level.

---

## 1. The 2x2 at a glance

**Axis A, Where regulated data is allowed to live:** *Sovereignty-bound* (law and procurement force data inside controlled, often on-prem or national-cloud, perimeters) ←→ *Cloud-permissive* (regulators accept hyperscaler controls; data flows freely to public cloud).

**Axis B, Where the control plane runs:** *Operator-managed* (customers still want to run and tune the infrastructure themselves) ←→ *Vendor-managed* (customers offload operations entirely to a managed/serverless control plane, regardless of where bytes physically sit).

```
                         OPERATOR-MANAGED control plane
                                    |
            FORTRESS RACKS          |        SOVEREIGN AS-A-SERVICE
   (sovereignty-bound x operator)   |   (sovereignty-bound x vendor-managed)
   on-prem renaissance; you run it  |   data stays home, vendor runs it
                                    |
   SOVEREIGNTY-BOUND ---------------+--------------- CLOUD-PERMISSIVE
                                    |
            THE LONG TAIL           |        OPEN SKIES
   (cloud-permissive x operator)    |   (cloud-permissive x vendor-managed)
   on-prem shrinks to a legacy niche|   full hyperscaler/serverless default
                                    |
                         VENDOR-MANAGED control plane
```

| Scenario | One line | On-prem verdict |
|---|---|---|
| **Fortress Racks** | Sovereignty law hardens and customers still insist on running it themselves: on-prem is strategic again. | **Invest** |
| **Sovereign as-a-Service** | Data must stay home, but customers want it operated for them: the future is sovereign managed, not racks-you-tune. | **Transform** (on-prem control plane, vendor-operated) |
| **The Long Tail** | Cloud is permitted everywhere yet a stubborn operator base remains: on-prem becomes a profitable, shrinking annuity. | **Harvest** |
| **Open Skies** | Cloud-permissive and fully vendor-managed: serverless hyperscaler default; on-prem collapses to a rump. | **Exit / wind down** |

**Read in two minutes:** the on-prem decision turns on two independent questions: *will regulation keep forcing data into controlled perimeters?* and *will customers keep wanting to operate infrastructure themselves?* On-prem R&D is clearly worth funding in **Fortress Racks**, clearly not in **Open Skies**, and in the two off-diagonal worlds the answer is "yes, but rebuilt" (**Sovereign as-a-Service**) or "yes, but milked, not grown" (**The Long Tail**). The robust play funds the parts that pay off in three of four worlds; the bet on classic operator-run on-prem is the one piece that only survives Fortress Racks.

---

## 2. Axes and forces

### The two axes (critical uncertainties)

Both score high-impact / high-uncertainty against the focal question, and they are independent, neither tells you the other.

- **Axis A, Data-residency regime (sovereignty-bound ←→ cloud-permissive).** *Impact 5:* it directly governs whether regulated mid-market buyers (finance, health, public sector, ~60% of the on-prem book) are even permitted to use public cloud. *Uncertainty 5:* the regulatory pendulum genuinely could swing either way over ten years; data-sovereignty statutes are proliferating in some jurisdictions while broad cloud-adequacy frameworks expand in others. Reasonable people disagree on the 2036 end-state.

- **Axis B, Operating model (operator-managed ←→ vendor-managed).** *Impact 5:* it determines whether the product is "software you run" or "a service we run," which is a different company, cost structure, and R&D roadmap. *Uncertainty 4-5:* the secular drift is toward managed/serverless, but a real counter-current (cost control, lock-in fear, FinOps discipline, repatriation) keeps the operator pole alive. Where it lands in ten years is open.

**Independence check:** knowing data must stay on-prem (sovereignty-bound) does *not* tell you who operates it, a vendor can run a managed control plane inside a customer's own datacenter or national cloud (that is the Sovereign-as-a-Service quadrant precisely). And a cloud-permissive world still contains operators who choose to self-manage for cost (The Long Tail). The poles cross cleanly into four non-empty, qualitatively different worlds; the 2x2 does not collapse.

### Predetermined elements (shared backdrop in every scenario)

High-impact, low-uncertainty trends already in motion. All four scenarios inherit these:

- **AI/ML workloads become the dominant driver of new data-infrastructure spend.** Vector, retrieval, and feature-store demand keeps rising in every world; the only question is *where* it runs, which is what the axes settle.
- **Compute and energy costs stay structurally elevated and volatile.** GPU scarcity and power constraints make the run-it-anywhere economics matter; cheap, abundant compute is not coming back this decade.
- **Consolidation continues among data-infra vendors.** M&A and platform bundling persist; a sub-scale mid-market vendor is acquisition bait in any world.
- **Skilled operations talent stays scarce and expensive.** The labor pressure that pushes buyers toward managed services exists in all four, it just gets overwhelmed by other forces in the operator-managed worlds.
- **Security/breach risk and audit burden keep rising.** Compliance overhead grows regardless of where data lives.

### Forces considered and set aside

- **General macro/recession cycle**: high uncertainty but it moves all four worlds together (an event, not a structural axis); shifts timing, not the end-state. *Background to monitor.*
- **Open-source erosion of commercial licenses**: real but lower direct impact on the *positioning* question than the two axes; a secondary wildcard feeding the Long-Tail signposts.
- **Quantum / post-quantum crypto disruption**: high uncertainty, low near-horizon impact on this decision. *Secondary wildcard, watch-list only.*
- **Geopolitical fragmentation of the internet ("splinternet")**: important, but it largely expresses *through* Axis A (data residency) rather than as a separate cross.

---

## 3. The four scenarios

### 3.1 Fortress Racks: *sovereignty-bound × operator-managed*

**Confidence: Medium-High.** Internally tight; rests on regulation hardening, which is the genuinely uncertain leg.

**The path here.** Between 2027 and 2031 a cluster of data-localization statutes and sector rules (a tightened financial-data residency directive, a public-sector "no-foreign-cloud" procurement mandate, a health-data sovereignty act) lands in the company's core markets. A high-profile hyperscaler outage and two cross-border subpoena incidents harden boards against public cloud for regulated workloads. Simultaneously, a 2029-2030 wave of cloud-bill shock and FinOps backlash keeps the *operator* instinct alive: CIOs decide that if data has to stay home anyway, they will run it themselves and own the cost line. Repatriation projects become budget-line items.

**What it looks like in 2036.** Regulated mid-market buyers run controlled, often air-gapped or national-cloud estates and staff them with (scarce, expensive) platform teams. AI workloads run on-prem on owned or co-located GPU, the predetermined AI-demand surge lands *inside the perimeter*. On-prem is not legacy; it is where the strategic, regulated workloads live. Vendors who kept a credible self-managed product with strong AI primitives win premium contracts.

**Implications.** This is the world the on-prem line was built for. Funding continued on-prem R&D, especially on-prem AI/vector serving, hardened security, and sovereign-deployment tooling, is straightforwardly correct. The risk is *under*-investing and ceding the renaissance to a more committed competitor.

### 3.2 Sovereign as-a-Service: *sovereignty-bound × vendor-managed*

**Confidence: Medium.** The most strategically interesting world and the one current strategy least fits.

**The path here.** Sovereignty rules harden exactly as in Fortress Racks, but the operations talent shortage and the managed-service habit win the operating-model question. Customers conclude: *the data must stay home, but we refuse to run the plumbing.* Hyperscalers and sovereign-cloud providers roll out "data-stays-in-country, we-operate-it" offerings; a managed control plane runs the customer's regulated data inside their own datacenter or a certified national cloud. By 2032 "sovereign managed" is the dominant procurement shape for regulated mid-market.

**What it looks like in 2036.** Bytes sit in controlled perimeters; nobody on the customer side touches a config file. The product that wins is a vendor-operated control plane that can deploy *into* customer-controlled environments (BYOC, on-prem operator, sovereign-cloud regions) with full remote operation, patching, and SLA. Classic "ship them software and a manual" on-prem is dying even though physical on-prem locations persist.

**Implications.** On-prem as a *location* survives; on-prem as an *operating model* does not. The decision is not "fund on-prem yes/no" but "**transform** on-prem into a vendor-operated, deploy-anywhere control plane." This world rewards the company's nascent managed-cloud muscle pointed at sovereign deployment, and punishes pure self-managed R&D.

### 3.3 The Long Tail: *cloud-permissive × operator-managed*

**Confidence: Medium-High.** Closest to a straight-line extrapolation of today; well-grounded.

**The path here.** Broad cloud-adequacy frameworks expand through 2028-2030; regulators get comfortable with hyperscaler controls and residency stops being a hard blocker. Most new workloads go to public cloud. But a durable minority, cost-sensitive heavy-compute users, latency-critical edge/industrial, and lock-in-averse engineering-led shops, keep running their own infrastructure, helped by persistently high cloud bills (a predetermined element). On-prem stops growing but does not die; it becomes a stable, high-margin annuity serving a shrinking, sticky base.

**What it looks like in 2036.** New logos overwhelmingly start in cloud. The on-prem installed base renews reliably, pays well, and demands little new feature work beyond security and compatibility. It is a cash cow with a slow decline curve, not a growth engine.

**Implications.** **Harvest.** Fund on-prem at maintenance level, security, compliance, AI-compatibility shims to keep the base from churning, but stop building it as a growth bet and redirect new-feature R&D to cloud. Over-investing here burns money chasing a market that is consolidating into a niche; abandoning it abruptly throws away a profitable annuity and annoys reference customers.

### 3.4 Open Skies: *cloud-permissive × vendor-managed*

**Confidence: High.** The clearest, most internally consistent world, and the most uncomfortable.

**The path here.** Cloud-adequacy wins on the regulatory axis *and* serverless/managed wins on the operating axis. By the early 2030s, mid-market buyers default to fully managed, serverless data infrastructure on the major clouds; the AI-spend surge (predetermined) lands almost entirely on hyperscaler-native managed services. Operating your own data infrastructure becomes an eccentric choice, like running your own email server. Vendor consolidation (predetermined) folds independent on-prem players into platform suites or winds them down.

**What it looks like in 2036.** On-prem revenue is a rump, a few regulated holdouts and legacy contracts, declining fast. The company's value, if any, is in its managed-cloud SaaS and whatever differentiated IP can ride on hyperscaler marketplaces.

**Implications.** **Exit / wind down** on-prem. Funding continued on-prem R&D in this world is value-destroying. This is the challenging scenario the current strategy would not survive: 55% of ARR is in a structurally dying line. The board needs a written answer for what the company *is* if Open Skies arrives.

---

## 4. Strategy

### Robust moves (sensible in all four worlds: fund these now, no bet required)

1. **Build the data engine to be deploy-target-agnostic.** Invest in a single codebase that can run on-prem (operator), as a vendor-managed control plane inside customer environments (BYOC/sovereign), and as serverless cloud, selected by config, not by fork. *This is the highest-leverage robust move:* it is exactly the capability that wins Fortress Racks, Sovereign-as-a-Service, **and** Open Skies, and it lets you harvest gracefully in The Long Tail. It converts the binary "on-prem yes/no" into a portability investment that pays off everywhere.
2. **Make AI/vector/retrieval workloads first-class everywhere.** The AI-spend surge is predetermined; capturing it regardless of *where* it runs is robust. Win the workload, stay neutral on the location.
3. **Invest in security, compliance, and audit tooling.** Breach risk and audit burden rise in all four worlds; this is table-stakes that also defends the installed base in the harvest world.
4. **Strengthen FinOps / cost-transparency tooling.** Elevated, volatile compute cost is predetermined; helping customers see and control spend sells in every scenario and is the wedge for repatriation conversations if they come.
5. **Protect and grow the managed-cloud SaaS line.** It is the survival asset in Open Skies and the foundation of the control plane in Sovereign-as-a-Service. No world penalizes a stronger managed product.

### Contingent moves (prepare now, trigger on a signpost: do not commit yet)

| Move | Triggered if… | Tied to | Trigger signpost |
|---|---|---|---|
| **Double down on hardened self-managed on-prem + on-prem AI serving** (premium sovereign-deployment SKU) | sovereignty hardens **and** operator instinct holds | Fortress Racks | Localization statutes pass in 2+ core markets **and** repatriation deal count rises |
| **Build the vendor-operated sovereign control plane** (managed-into-customer-environment) | sovereignty hardens **and** managed wins | Sovereign-as-a-Service | Localization statutes pass **and** "sovereign managed" RFP language appears |
| **Shift on-prem to maintenance-mode annuity; freeze new on-prem features** | cloud is permitted but operators persist | The Long Tail | Cloud-adequacy expands **and** on-prem renewal rate stays high while new on-prem logos fall |
| **Pre-plan the on-prem wind-down / EOL roadmap and customer-migration path** | cloud permitted **and** managed wins | Open Skies | Cloud-adequacy expands **and** new on-prem bookings drop below a kill-threshold for 2+ quarters |

The structure: a thick layer of portability-and-workload investment that holds across all four, plus four cheap options held ready, each wired to a discriminating signpost. Notice three contingent moves build *on* the robust deploy-agnostic engine: buying the option early is cheap precisely because the robust investment already exists.

---

## 5. Signposts (monitoring dashboard)

Observable, discriminating, leading indicators. Each points toward one or two scenarios and away from the others.

| Signpost | Points toward | Why it discriminates |
|---|---|---|
| **Data-localization / sovereignty statutes pass in core markets** (financial, health, or public-sector residency mandates) | Fortress Racks + Sovereign-as-a-Service (Axis A → sovereignty-bound) | Resolves Axis A toward the sovereign poles; absence over 3-4 years points to cloud-permissive |
| **Broad cloud-adequacy frameworks expand / hyperscaler controls accepted by regulators** | The Long Tail + Open Skies (Axis A → cloud-permissive) | The mirror of the above; the two are mutually exclusive on the residency axis |
| **"Sovereign managed" appears as RFP/procurement language** (data-home, vendor-operated) | Sovereign-as-a-Service | Discriminates Axis B *within* the sovereign world: racks-you-run (Fortress) vs. operated-for-you |
| **Repatriation / cloud-exit deal volume vs. cloud-migration volume** | rising repatriation → operator poles (Fortress + Long Tail); falling → vendor-managed poles | Reads Axis B directly; a leading indicator from analyst deal trackers |
| **Hyperscaler serverless data-infra revenue growth rate** | Open Skies (and Sovereign-as-a-Service): vendor-managed pole | Accelerating serverless adoption is the signature of the vendor-managed worlds |
| **On-prem renewal rate vs. new on-prem logo count** (internal) | high renewal + falling new logos → The Long Tail; both falling → Open Skies | The earliest internal read on whether harvesting or winding down is the live world |
| **Cloud spend as a board-level cost concern / FinOps backlash intensity** | operator poles (Fortress + Long Tail) | Cost backlash keeps the self-managed instinct alive; its fading favors vendor-managed |
| **Competitor M&A: independent on-prem vendors acquired or shut down** | Open Skies (consolidation overwhelming the niche) | Distinguishes a dying niche (Open Skies) from a stable annuity (Long Tail) |

Watch the two Axis-A signposts first: they split the board into the left (sovereign) and right (cloud-permissive) halves and settle whether on-prem-as-location has a future at all. The Axis-B signposts (RFP language, repatriation volume, serverless growth, FinOps intensity) then resolve *which* on-prem strategy within each half.

---

## 6. Caveats

- **These are plausible futures to prepare for, not predictions.** None carries a probability. The point is robustness across all four, not a guess at which arrives, and explicitly preparing for Open Skies, the world current strategy would not survive.
- **The set is only as good as the two axes.** If data-residency regime and operating model turn out correlated in a way this analysis missed (e.g., sovereignty law *always* forces self-management), two quadrants thin out and the 2x2 weakens. The independence test passed here, but revisit it as the regulatory picture clears.
- **The value is in the strategy and signposts, not the stories.** The four narratives exist to generate the robust/contingent moves and the watch list. The deliverable is "fund the portable engine and AI workloads now, hold four options, watch the eight signposts", not the four names.
- **Scenarios are a thinking tool, to be revisited as forces shift.** The predetermined elements (AI demand, compute cost, consolidation, talent scarcity) are assumptions, not certainties; if any breaks, rerun. Re-examine at least at each board cycle, and immediately if a top signpost fires.
- **All figures, regulations, and market dynamics here are illustrative for documentation and were not researched.**
