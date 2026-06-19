# Digital Maturity Assessment: Meridian Mutual

> _Illustrative example output for the `digital-maturity-assessment` skill. Meridian Mutual is a fictional company; every figure, name, and claim below is invented to demonstrate the report's shape, not researched. Do not cite these numbers._

- **Organization:** Meridian Mutual, a 1,200-person regional property-and-casualty insurer.
- **Target ambition:** Reach **level 4 (Managed)** on **Customer Experience** and **Data and Analytics** within three years; the remaining five dimensions may sit at **level 3 (Connecting)**.
- **Date:** 2026-06-19
- **Context:** A 90-year-old core policy administration system, a mobile claims app live for ~14 months, a data-warehouse project stalled at pilot, no product owners, and an executive team that still signs off on every production release.
- **Scoring basis:** Scores reflect **what is in production and in behavior**, not what is planned, piloted, or in a deck. Where evidence was thin, the gap is flagged rather than scored on aspiration.

---

## 1. Maturity profile

The shape is the finding. The simple average (≈2.1) is reported only to be set aside: it hides a profile that runs from a near-leading claims app down to a core-system and culture floor that caps everything above it.

| # | Dimension | Current | Target | Gap | Confidence |
|---|---|:---:|:---:|:---:|:---:|
| 1 | Strategy and leadership | 2: Emerging | 3 | **−1** | High |
| 2 | Customer experience | 3: Connecting | **4** | **−1** | High |
| 3 | Technology and architecture | 2: Emerging | 3 | **−1** | High |
| 4 | Data and analytics | 1: Nascent | **4** | **−3** | High |
| 5 | Operations and process | 2: Emerging | 3 | **−1** | Medium |
| 6 | People and culture | 2: Emerging | 3 | **−1** | High |
| 7 | Innovation and ecosystem | 2: Emerging | 3 | **−1** | Medium |

```
Profile (current ●  / target ○)

Strategy & leadership   ●───○ · · ·   2 → 3
Customer experience     · · ●───○ ·   3 → 4
Technology & arch.      ●───○ · · ·   2 → 3
Data & analytics        ●───────○ ·   1 → 4   ← the chasm
Operations & process    ●───○ · · ·   2 → 3
People & culture        ●───○ · · ·   2 → 3
Innovation & ecosystem  ●───○ · · ·   2 → 3
                        1   2   3   4   5
```

**Read of the profile.** Customer experience sits a level above the rest, lifted almost entirely by one product (the claims app). Data and analytics sits a level below the rest, at a true Nascent floor. The two dimensions Meridian most wants at level 4 are its highest and its lowest: and the lowest, Data, is the one that determines whether the highest can actually reach 4. Everything else clusters at Emerging (2), held there by the core system and a release process that runs through the executive team.

---

## 2. Per-dimension detail

### 2.1 Strategy and leadership: Level 2 (Emerging), target 3, gap −1: confidence High

**Evidence.** A board-approved "digital ambition" exists on paper and the claims app was funded as a visible bet. But there is no standing digital governance forum, no multi-year funded roadmap, and investment is approved project-by-project. The decisive signal: the executive team personally signs off every production release, leadership is engaged but operating as a control gate, not as a delegating sponsor.

**What holds it here.** Digital is treated as a portfolio of approved projects, not an integrated capability with owned outcomes. There is sponsorship but no governance; ambition but no coordinated investment mechanism.

**What level 3 requires.** A defined, funded digital strategy coordinated across the business; a governance body that sets priorities and tolerances; and delegation of release decisions to accountable owners so leadership shapes direction instead of gating throughput.

### 2.2 Customer experience: Level 3 (Connecting), target 4, gap −1: confidence High

**Evidence.** The mobile claims app has been live ~14 months: customers file first-notice-of-loss, upload photos, and track status; ~38% of claims now start in-app, and claims NPS rose ~12 points for app users. This is a genuine, coordinated digital channel in production, clearly above Emerging. But it stops at claims. New-business quoting and policy servicing (endorsements, renewals, billing) remain phone-, agent-, and paper-driven, and there is no personalization because the underlying customer data is not unified (see Data).

**What holds it here.** One excellent journey, not an integrated experience. Without unified customer data there is no personalization, no proactive servicing, and no single view across the policy lifecycle, the things that separate Connecting (3) from Managed (4).

**What level 4 requires.** Digital servicing extended beyond claims to quote, bind, and policy management; a unified customer view feeding personalization and proactive outreach; and journeys measured and governed end-to-end. **This target is gated by Data and analytics**: CX cannot reach 4 while customer data sits at level 1.

### 2.3 Technology and architecture: Level 2 (Emerging), target 3, gap −1: confidence High

**Evidence.** The 90-year-old core policy administration system is a mainframe-era monolith of record. The claims app is a modern cloud front-end, but it integrates to the core through nightly batch files and a thin layer of brittle point-to-point connectors, not a managed API layer. There is no integration platform, no real-time eventing, and changes to the core require specialist contractors and long lead times.

**What holds it here.** A two-speed estate: a modern edge bolted to an unchangeable center via batch. Integration is point-to-point and fragile; the core's pace of change is measured in quarters.

**What level 3 requires.** A deliberate, coordinated integration approach, an API/eventing layer that decouples modern channels from the core (a "strangler" pattern around the monolith), so new digital services can read and write core data in near-real-time without each one cutting a new brittle connection.

### 2.4 Data and analytics: Level 1 (Nascent), target 4, gap −3: confidence High

**Evidence.** The data-warehouse project has been **stalled at pilot** for over a year. Reporting runs on extracts into spreadsheets; claims, policy, and billing data live in separate systems with no common customer or policy key; there is no data governance, no defined ownership, and no production analytics or ML in decisions. Underwriting and pricing decisions are expertise-and-rules driven, not data-driven. This is ad hoc and reactive, a true level 1.

**What holds it here.** No foundation: no integrated, governed, trustworthy data layer, so there is nothing for analytics to stand on. The stalled warehouse is the symptom; the cause is no owner, no governance, and no integration path off the siloed source systems.

**What the target (4) requires, and why the gap is −3.** Moving from Nascent to Managed is three full levels and the single largest move in this assessment. It requires: a governed, integrated data platform (revive and finish the warehouse with clear ownership); a common customer/policy key across claims, policy, and billing; defined data quality and stewardship; and analytics actually used in production decisions (servicing, pricing, claims triage). **This is the binding gap of the whole assessment**: it caps Customer experience and starves Innovation.

### 2.5 Operations and process: Level 2 (Emerging), target 3, gap −1: confidence Medium

**Evidence.** The digital-claims team ships iteratively and has automated parts of the claims intake flow. Elsewhere, core processes (underwriting, endorsements, renewals) are manual, paper-heavy, and unchanged. Process improvement is local to the one digital team, not an organizational practice. Confidence is Medium: detail beyond the claims flow was thin and would need process-level evidence to firm up.

**What holds it here.** Agility exists in one pocket and nowhere else; there is no continuous-improvement practice spanning the business, and the core processes are bound to the unchangeable core system.

**What level 3 requires.** A coordinated digitize-and-automate approach across the main operational processes, and process-improvement disciplines applied beyond the single digital team.

### 2.6 People and culture: Level 2 (Emerging), target 3, gap −1: confidence High

**Evidence.** A small modern digital team (~25 people) exists and works in an agile way, but it is an island. **There are no product owners**: the clearest cultural signal: work is project-managed and accountability for outcomes is diffuse. The executive release sign-off reflects a low-trust, control-oriented operating culture. Outside the digital team, the workforce is long-tenured and skilled in insurance, not in digital ways of working, and change appetite is cautious.

**What holds it here.** Digital capability and a change-friendly culture are confined to one team; the broader organization lacks the roles (product owners), the skills, and the delegated authority that level 3 assumes.

**What level 3 requires.** Establish product ownership with real decision authority; spread digital ways of working and skills beyond the one team; and shift leadership from gating releases to setting outcomes and trusting owners to deliver them.

### 2.7 Innovation and ecosystem: Level 2 (Emerging), target 3, gap −1: confidence Medium

**Evidence.** The claims app shows Meridian can ship something new, and there have been early conversations with insurtech partners and a telematics vendor. But there is no repeatable mechanism to experiment, fund, and scale ideas, and no production partner/platform integration. Innovation has happened once, as a project, not as a capability. Confidence Medium given limited evidence on the partner pipeline.

**What holds it here.** No repeatable experiment-to-scale process and no ecosystem integration; innovation depends on one-off executive bets. It is also starved by Data, most insurtech value (telematics, fraud, automated triage) needs the data foundation that does not yet exist.

**What level 3 requires.** A deliberate, coordinated innovation approach, a light funnel to test and scale ideas, and at least one production partner/platform integration that creates value.

---

## 3. Binding gaps and imbalances

The profile is not a flat shortfall to be closed evenly. Three structural facts govern it:

**A. Data and analytics is the binding gap (−3).** It is the lowest dimension, it carries the largest gap to target, and it is upstream of the two ambitions Meridian most cares about. Customer experience cannot reach its level-4 target without unified, governed customer data; Innovation cannot reach 3 without a data foundation to build on. **Data is not one of seven parallel workstreams, it is the constraint the others depend on.** Sequencing anything ahead of it wastes spend.

**B. The classic imbalance, reversed.** The textbook pattern is strong technology stranded behind weak people and culture. Meridian shows a sharper variant: a **strong customer-facing product (CX at 3) stranded behind a Nascent data layer (1) and a batch-only integration to a 90-year-old core (Tech at 2).** The claims app is already running ahead of what the foundation can support; pushing CX toward 4 before Data and Tech catch up will produce a more sophisticated front-end writing into a foundation that cannot personalize, cannot serve in real time, and cannot extend past claims.

**C. People and culture caps the rate of change.** No product owners and executive sign-off on every release mean that even fully funded technical work will throttle at the governance gate. The absence of product ownership (level 2 People) limits how fast every other dimension can move. It is a low-cost gap to close and it unblocks throughput everywhere, which is why it leads the roadmap despite not being a stated target dimension.

**The dependency chain:** People/governance (frees throughput) → Data (the foundation) → Technology integration (the pipe to the core) → Customer experience and Innovation (what the foundation enables). The two target dimensions sit at the **end** of the chain, not the start.

---

## 4. Roadmap

Sequenced to attack the binding constraint first. The error to avoid is funding Customer-experience features (the visible target) before the Data foundation and the integration layer exist to support them.

### Quick wins (0–6 months): unblock throughput, stop the bleeding

1. **Appoint product owners and delegate release authority (People, Strategy).** Name owners for claims, servicing, and the data platform; move routine production releases off the executive desk to a defined release standard. Lowest cost, highest leverage, it raises the ceiling on every other move. Targets People 2→3 and removes the executive gate.
2. **Unstall the data-warehouse pilot with an owner and a governance mandate (Data).** The pilot is stalled for lack of ownership, not technology. Assign a data owner, define a minimal governance model, and set a common customer/policy key as the first deliverable. This is the first step of the −3 climb.
3. **Stand up a basic integration capability around the claims-app boundary (Technology).** Replace the most brittle batch/point-to-point connectors with a small managed API layer where the app already touches the core, a beachhead for the strangler pattern, proving the approach before scaling it.

### Longer plays (6–36 months): build the foundation, then the target dimensions

4. **Build the governed, integrated data platform to Managed (Data, the −3 climb).** Finish the warehouse, unify claims/policy/billing on the common key, establish stewardship and quality, and put analytics into at least one production decision (claims triage or servicing). This is the multi-year spine of the whole program; **CX-4 and Innovation-3 are blocked until this lands.**
5. **Extend the integration layer to decouple the core (Technology 2→3).** Grow the API/eventing layer into a deliberate strangler around the monolith so digital services read and write core data in near-real-time. Sequenced alongside the data platform, they share the same plumbing.
6. **Extend digital servicing past claims and turn on personalization (Customer experience 3→4).** Only after Data and Tech can support it: bring quote/bind and policy servicing into digital channels, build the unified customer view, and add personalization and proactive outreach. This is the stated target, deliberately placed late because it depends on 4 and 5.
7. **Spread agile ways of working and a light innovation funnel (Operations, People, Innovation to 3).** Take the claims team's practices organization-wide, automate core operational processes, and stand up a repeatable experiment-to-scale mechanism with one production partner integration (telematics is the natural first candidate once data exists).
8. **Mature governance into a standing digital strategy function (Strategy 2→3).** Convert project-by-project funding into a coordinated, funded roadmap with a governance body, the structure that holds the gains.

**Sequencing logic:** quick wins free throughput (1) and start the foundation (2, 3); longer plays complete the foundation (4, 5) and only then deliver the two target dimensions (6) and broaden the rest (7, 8).

---

## 5. Verdict

**Overall maturity: low-Emerging (≈2), but the average is the wrong lens.** Meridian is a level-2 organization with one level-3 bright spot (the claims app) sitting on a level-1 data foundation. The single number to act on is not the 2.1 average, it is the **−3 gap on Data and analytics**, because that one dimension gates both of the level-4 ambitions and starves innovation.

**The three moves that matter most:** (1) appoint product owners and get the executive team out of the release path, the cheapest move and the one that unlocks the pace of everything else; (2) revive the data-warehouse pilot under clear ownership and build it into a governed, integrated platform, the multi-year spine; (3) build an integration layer that decouples digital channels from the 90-year-old core, so the front-end can finally read and write in real time.

**Is the three-year target realistic?** The level-3 targets on five dimensions are achievable in the window. The two level-4 targets are the harder question. **Customer experience to 4 is realistic only if it is sequenced after the data and integration work, and that ordering is the whole game.** Data to 4 is a −3 climb and the most ambitious goal here; three years is tight but feasible *if* it starts now, gets a real owner, and is not deprioritized behind more visible CX features. The risk is not capability, it is the temptation to keep shipping app features (visible, popular) while the foundation stays at level 1. If Meridian funds the foundation first and the front-end second, the target is reachable. If it does the reverse, it will arrive at year three with a better claims app and the same Nascent data layer underneath it.

---

## 6. Caveats

- Scores reflect the **evidence available** for this assessment and are **judgment, not certification.** Operations/process and Innovation/ecosystem are Medium-confidence and would firm up with process-level and partner-pipeline evidence.
- **Maturity is not an end in itself.** These scores are read against Meridian's own target (4 on CX and Data, 3 elsewhere), not against level 5. Level 5 on any dimension would be over-investment relative to the stated ambition.
- **The lagging dimension governs realized value, not the average.** Data at level 1 caps what the level-3 claims app can actually deliver; the program succeeds or fails on whether the foundation rises, regardless of how the average moves.
- All figures, metrics, and findings here are **illustrative for documentation purposes** and were not researched.
