# Fermi estimate: UK 2026 market for electric cargo bikes sold to last-mile delivery firms

> _Illustrative example output for the `fermi-estimation` skill. The factor values below are reasoned guesses and rough anchors, **not** researched figures. The point of the method is that every assumption is visible and challengeable, so challenge them. Do not cite these numbers._

**Sharpened quantity:** annual revenue, in GBP, from *new* electric cargo bikes sold to UK last-mile delivery companies during calendar 2026. Units: £/year, a flow (not the installed fleet stock). Approach: bottom-up primary chain, top-down proxy as the independent cross-check.

---

## 1. The estimate

**≈ £30 million per year**, plausibly **£12M–£90M**: roughly an order of magnitude wide.

For the decision at hand ("is this a £10M or a £100M opportunity?"): it is a **low-to-mid tens-of-millions** opportunity, comfortably above £10M, but well short of £100M on current assumptions, and sitting nearer the £10M end than the £100M end.

The two independent paths did not fully agree (bottom-up ~£45M, top-down ~£13M); the reconciled central figure of ~£30M reflects that spread, and a bounds check argues against the high end.

---

## 2. The decomposition (primary, bottom-up)

Revenue = (UK last-mile firms) × (fraction adopting cargo bikes) × (bikes bought per adopting firm per year) × (price per bike)

| Factor | Low | Best | High | Basis |
|---|---|---|---|---|
| F1: UK last-mile delivery firms | 3,000 | 5,000 | 8,000 | User-supplied anchor (~5,000); widened for definition fuzziness |
| F2: fraction in cargo-bike-viable areas that adopt | 0.15 | 0.25 | 0.45 | Guess: only dense-urban operators; adoption still early |
| F3: bikes purchased per adopting firm per year | 2 | 6 | 14 | Guess, wide: blends fleet growth + replacement; **dominant uncertainty** |
| F4: price per fleet-grade e-cargo bike (£) | 4,000 | 6,000 | 9,000 | User-supplied anchor (~£6,000) |
| **Result (£/yr)** | **~£3.6M** | **~£45M** | **~£450M** | product |

Central: 5,000 × 0.25 × 6 × £6,000 = **£45M**.

The naive low×low and high×high bounds (£3.6M–£450M) overstate the spread: they assume every factor hits its extreme at once. Propagating the uncertainties in log space (combining the relative ranges in quadrature) gives an honest **~£13M–£160M** band around the bottom-up £45M. Reconciliation with the second path (below) pulls the central figure down to ~£30M and the working band to **£12M–£90M**.

---

## 3. What it rests on

Three load-bearing factors, in order of how much they move the answer:

1. **Bikes per firm per year (F3)**: a genuine guess spanning 2–14. This single factor's width dominates the entire estimate's uncertainty (see §5).
2. **Adoption fraction (F2)**: how many of the ~5,000 firms operate where a cargo bike actually beats a van. A guess, not measured.
3. **Price (F4)**: the firmest factor; the £6,000 anchor is solid, and its ±50% range barely moves the result.

F1 (firm count) is anchored but its *definition* is soft: "last-mile delivery firm" ranges from a one-rider courier to DPD. F2 partly corrects for this by filtering to viable adopters.

---

## 4. The dominant uncertainty

**Bikes purchased per adopting firm per year (F3).** Its relative range (×/÷ ~2.6) is wider than any other factor's, so it controls the band's width, tightening F1, F2, or F4 would barely narrow the answer.

**The one measurement that would shrink the band most:** an actual figure for annual *unit* sales of commercial e-cargo bikes to UK delivery fleets (e.g. a Bicycle Association or cargo-bike trade-body statistic). That single number collapses F1×F2×F3 into one observed quantity and would likely tighten the estimate from ~1 order of magnitude to within 2×.

---

## 5. Cross-check

**Second path (top-down proxy)**: start from the whole UK cargo-bike market and carve out the delivery-fleet slice:

| Factor | Best | Basis |
|---|---|---|
| Total UK cargo-bike units sold/yr (all segments) | 9,000 | Guess across consumer, family, trades, fleet |
| × electric fraction | 0.70 | Most fleet/commercial units are electric |
| × share to last-mile delivery fleets | 0.35 | Rest is family/consumer/trades |
| × price (£) | 6,000 | Same anchor |
| **= revenue** | **~£13M** | 9,000 × 0.70 × 0.35 × 6,000 |

The two paths land at **£45M (bottom-up)** and **£13M (top-down)**: a ~3.4× gap, just over the width of one order of magnitude. They agree on the *order* (tens of millions) but not the figure. The gap **is** the finding: it hinges on whether you trust per-firm purchasing (bottom-up) or total-market size (top-down). Splitting the difference, weighted slightly toward the more constrained top-down view, gives the reconciled **~£30M**.

**Bounds check.** If the *entire* UK cargo-bike market (all segments) is on the order of £60–100M/yr, then a £45M delivery-only figure would be most of the whole market: implausible, since families and trades are a large share. This ceiling argues the bottom-up £45M is high and supports pulling the central estimate down toward £30M or below. Floor: visible fleet deployments (parcel carriers, grocery micro-hubs) put it clearly above a few £M. The estimate sits comfortably inside both bounds.

---

## 6. Confidence and caveats

- **Order of magnitude: fairly confident.** This is a tens-of-millions market, not single-digit millions and not hundreds of millions. That answers the stated decision.
- **The figure within that range: low confidence**, driven almost entirely by F3 and the total-market size. Treat ±3× as honest.
- A Fermi estimate is auditable, not authoritative: it is built to be *attacked one factor at a time*. The numbers here are illustrative for documentation and were not researched, replace F3 and the top-down total with real trade figures before any real decision.
