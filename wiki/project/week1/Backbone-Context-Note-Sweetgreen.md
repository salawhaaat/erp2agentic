---
type: deliverable
tags: [deliverable, week1, backbone-context-note, sweetgreen]
company: Sweetgreen
due: Week 2
feeds: ["Board Memo §2", "Storyboard S1/S3"]
---
# Backbone-Context Note — Sweetgreen

> Homework seed for [[Context-and-Diagnosis-Brief-Sweetgreen|the Week 2 context-and-diagnosis brief]]. Follows the six-move read taught in the [[W1_IntegrationBackbone_Slides_v3|Week 1 slides]] (Chipotle worked example).

## 1 · Get the context — RESEARCHED

Sweetgreen is a fast-casual restaurant company selling customizable salads, bowls, wraps, and protein plates through in-store and digital channels (app, website, in-store kiosk/POS, and third-party delivery platforms).

- **Digital mix:** digital channels generated **61.8%** of total revenue in FY2025, and climbed further to **66.3%** in Q2 2026 (owned-digital alone: 38.8%, up from 33.4% YoY) — digital ordering is central to the operating model and still growing as a share of demand, not a side channel.
- **Customers:** individual consumers ordering for pickup or delivery, largely urban/suburban fast-casual diners.
- **Primary thread:** **Operations & Supply Chain** (kitchen throughput, ingredient/menu availability), with **Customer** a close second (order accuracy, promised-time reliability). Cash is affected mainly as a downstream consequence (refunds, waste), not the primary leak — though FY2025 net loss widened to $(134.1)M from $(90.4)M and same-store sales fell in 2025-2026, so Cash pressure is intensifying (source: FY2025 10-K, Q2 2026 earnings release).

## 2 · Name the backbone — RESEARCHED (sourced, updated Sep 2026)

No single public ERP is named, but the backbone is now confirmed as a **stitched SaaS stack**, sourced from a Sweetgreen Systems Engineer (New Restaurant Openings) job posting, published vendor case studies, and the FY2025 10-K:

- **Ordering channels:** app, web, kiosk, **Olo** (third-party/online ordering integration layer)
- **Payment processing / authorization**
- **POS / restaurant order-management system: PAR Brink** — confirmed via the New Restaurant Openings systems-engineer role, which explicitly lists "configuring the POS/QSR stack (PAR Brink), payments, loyalty, inventory, Salesforce and their integrations" as part of every new-store build-out
- **Kitchen execution — two formats, now run by two different owners:**
  - Traditional make-line
  - **Infinite Kitchen** — as of the FY2025 10-K, Sweetgreen **sold the Infinite Kitchen technology and related assets to Wonder in December 2025**, keeping "a non-exclusive, perpetual, irrevocable, royalty-free license back." Wonder now sells Infinite Kitchen units back to Sweetgreen long-term and provides commissioning, support, and maintenance. 30 of 281 restaurants ran Infinite Kitchen units at FY2025 year-end, with guidance for ~half of the ~13 planned FY2026 openings to feature it.
- **Inventory, labor/scheduling, operations execution: Crunchtime** — Sweetgreen is a named Crunchtime customer (inaugural Ops Excellence Award; 2024 labor-and-scheduling case study)
- **CRM / loyalty: Salesforce** (same job posting)
- Fulfillment (pickup / delivery handoff)
- Refunds and financial reporting / revenue recognition

**Single source of truth:** still not named as one system. But the stack is now legible as **Olo (ordering) → PAR Brink (POS/order intake) → Crunchtime (inventory/kitchen ops) + Wonder (Infinite Kitchen hardware/software, external vendor) → Salesforce (loyalty/CRM)** — five to six separate vendor systems that must agree on menu availability, order status, and kitchen capacity in real time. The Infinite Kitchen divestiture *sharpens* the original leverage-gap hypothesis: for ~30 stores, the channel→kitchen handoff now crosses a **company boundary** (Sweetgreen ordering/POS layer → Wonder-owned kitchen system), not just a systems boundary. This is a materially different risk profile than "two internal formats," and should be reflected in Move 6 and the diagnosis brief.

> [!info]- Sourcing for this section
> - FY2025 10-K (filed 2026-02-27): [sg-20251228.htm](https://www.sec.gov/Archives/edgar/data/1477815/000162828026012520/sg-20251228.htm) — Infinite Kitchen/Wonder divestiture, restaurant count, financials
> - Q2 2026 earnings release (8-K ex99.1, filed 2026-08-06): [q226sweetgreenearningsrele.htm](https://www.sec.gov/Archives/edgar/data/1477815/000162828026054324/q226sweetgreenearningsrele.htm) — digital mix, same-store sales, guidance
> - Systems Engineer II, New Restaurant Openings job posting (careers.sweetgreen.com, via freehire.me) — PAR Brink, Olo, Salesforce, inventory/loyalty integrations at store build-out
> - Crunchtime customer case study/press: [Ops Excellence Award](https://www.crunchtime.com/press/sweetgreen-wins-crunchtimes-inaugural-ops-excellence-awards), [2024 Labor & Scheduling case study (PDF)](https://www.crunchtime.com/hubfs/Case%20Studies/Sweetgreen_Crunchtime%20Labor%20and%20Scheduling_202402.pdf?hsLang=en)
> - Restaurant Technology News on the Wonder divestiture: [Sweetgreen Sells Restaurant Robotics Arm to Wonder](https://restauranttechnologynews.com/2025/11/sweetgreen-sells-restaurant-robotics-arm-to-wonder-while-continuing-infinite-kitchen-expansion/)

## 3 · Place it — TIER/SCOPE ASSUMED

- **Archetype:** large multi-unit restaurant operator — closest to the **large-enterprise archetype**, scaled down from a single-vertical (food-service) angle rather than a generalist platform. Confirmed at **281 restaurants across 24 states + D.C.** as of FY2025 year-end (10-K).
- **Cloud/on-prem:** cloud-based ordering and payment stack (typical for the sector); store-level kitchen systems on a mix of cloud (PAR Brink, Crunchtime, Olo, Salesforce) and local POS/kitchen hardware, plus Wonder-owned Infinite Kitchen hardware/software at ~30 stores.
- **Generalist/vertical:** **vertical** — purpose-built for restaurant/food-service operations, not a horizontal platform.
- **Tier:** Tier I/II confirmed — named platforms are PAR Brink (POS), Olo (online ordering), Crunchtime (inventory/labor/ops), Salesforce (CRM/loyalty), per the New Restaurant Openings systems-engineer job posting.

## 4 · Trace one flow — Order-to-Cash (O2C)

```
Customer places order (app / web / kiosk / Olo-routed 3rd-party)
        ↓
Payment authorized  ★ CONTROL POINT (the order record is born — fact now owned)
        ↓
Order enters PAR Brink POS / order-management system
        ↓
Kitchen receives order — traditional line OR Infinite Kitchen  ◆ DECISION POINT
   (which format handles it, and does it have current stock to fulfil the customization?)
        ↓
   ├─ Traditional line: Crunchtime-tracked inventory, Sweetgreen-operated crew
   └─ Infinite Kitchen: Wonder-owned hardware/software (external vendor,           ◆ SECOND DECISION POINT
      post-Dec-2025 divestiture) — does the Sweetgreen order record and the        (systems boundary now
      Wonder kitchen system agree on stock and status in real time?                 a company boundary)
        ↓
Meal prepared
        ↓
Order verified and packed
        ↓
Pickup or delivery
        ↓
Transaction completed / revenue recorded
```

- **★ Control point:** payment authorization — this is where the order becomes a committed, owned fact the rest of the process must honor.
- **◆ Decision point:** kitchen-format and availability routing — whether the order's customization and promised time can actually be honored by the format and capacity it lands on.
- **◆ Second decision point (new, post-Dec-2025):** for the ~30 Infinite Kitchen stores, the handoff now crosses from Sweetgreen's own systems (PAR Brink/Olo) into a system owned and operated by **Wonder**, a separate company. Sweetgreen holds only a license-back, not operational control of that system — raising the stakes on whether order/status data genuinely round-trips in real time, or whether this is now an inter-company integration risk rather than a purely internal one.

## 5 · Classify the operating model

Using Ross & Weill's two questions (standardization × integration):

- **Standardization:** high — Sweetgreen runs a common menu and process discipline across company-operated stores.
- **Integration:** *mixed, now confirmed structurally fragmented* — five to six named vendor systems (Olo, PAR Brink, Crunchtime, Salesforce, plus Wonder for Infinite Kitchen) must all share the same order truth. The degree to which they actually stay synchronized in real time is still not confirmed, but the fragmentation itself — including a hard company boundary at ~30 Infinite Kitchen stores — is no longer a guess.

**Working classification: Unification stance (high standardization, high intended integration)** — but the intended integration is likely stronger on paper than in practice at the channel↔kitchen handoff, which is exactly where Move 6 names the gap. The Wonder divestiture makes this harder, not easier, to achieve: real-time integration across a company boundary requires a vendor contract and API commitment, not just an internal engineering decision.

## 6 · Name the leverage gap

> Sweetgreen's backbone fails to fully leverage digital order data **at the handoff between ordering channels and kitchen execution** — a handoff that, for Infinite Kitchen stores, now crosses into a system owned by a separate company (Wonder, since Dec 2025). Inconsistent visibility into customization, item availability, kitchen capacity, and order status can create delays, exceptions, remakes, and an inconsistent customer experience — a leak on the **Operations** and **Customer** threads, with **Cash** absorbing the downstream cost (waste, refunds, extra labor, and — per FY2025/Q2 2026 results — a widening net loss and falling same-store sales that raise the cost of getting this wrong).

---
**Carried forward into:** [[Context-and-Diagnosis-Brief-Sweetgreen]] · [[Lab1-Prework-Sweetgreen]]
**Legend:** researched fact (green in slides) vs. labelled assumption (gold in slides) — sections above are marked accordingly. As of Sep 2026, Moves 1–4 are sourced from the FY2025 10-K, Q2 2026 earnings release, and a Sweetgreen careers posting (see callout in Move 2); remaining unconfirmed items are the degree of real-time data synchronization across vendors and any single system of record for operational truth.
