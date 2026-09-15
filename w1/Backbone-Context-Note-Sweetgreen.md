---
tags: [deliverable, week1, backbone-context-note, sweetgreen]
company: Sweetgreen
due: Week 2
feeds: ["Board Memo §2", "Storyboard S1/S3"]
---

# Backbone-Context Note — Sweetgreen

> Homework seed for [[Context-and-Diagnosis-Brief-Sweetgreen|the Week 2 context-and-diagnosis brief]]. Follows the six-move read taught in the [[W1_IntegrationBackbone_Slides_v3|Week 1 slides]] (Chipotle worked example).

## 1 · Get the context — RESEARCHED

Sweetgreen is a fast-casual restaurant company selling customizable salads, bowls, wraps, and protein plates through in-store and digital channels (app, website, in-store kiosk/POS, and third-party delivery platforms).

- **Digital mix:** digital channels generated **61.8%** of total revenue in FY2025 — digital ordering is central to the operating model, not a side channel.
- **Customers:** individual consumers ordering for pickup or delivery, largely urban/suburban fast-casual diners.
- **Primary thread:** **Operations & Supply Chain** (kitchen throughput, ingredient/menu availability), with **Customer** a close second (order accuracy, promised-time reliability). Cash is affected mainly as a downstream consequence (refunds, waste), not the primary leak.

## 2 · Name the backbone — STACK ASSUMED (labelled)

No single public ERP is named; the backbone is most likely a **stitched SaaS stack**, not one unified system:

- Ordering channels (app, web, kiosk, third-party delivery platforms)
- Payment processing / authorization
- Restaurant order-management system (routes the order into the kitchen)
- Kitchen execution — either a traditional make-line or an **Infinite Kitchen** (automated) location
- Fulfillment (pickup / delivery handoff)
- Refunds and financial reporting / revenue recognition

**Single source of truth:** not confirmed publicly. The best current guess is that financial reporting (the general ledger) is the one place all channels ultimately reconcile to — but *operational* truth (menu availability, order status, kitchen capacity) is likely distributed across channel- and store-level systems, which is exactly the kind of gap this course flags as a leverage risk. This is a **first-pass hypothesis**, not a confirmed fact.

## 3 · Place it — TIER/SCOPE ASSUMED

- **Archetype:** large multi-unit restaurant operator — closest to the **large-enterprise archetype**, scaled down from a single-vertical (food-service) angle rather than a generalist platform.
- **Cloud/on-prem:** cloud-based ordering and payment stack (typical for the sector); store-level kitchen systems likely on a mix of cloud and local POS hardware.
- **Generalist/vertical:** **vertical** — purpose-built for restaurant/food-service operations, not a horizontal platform.
- **Tier:** Tier I/II for a public multi-unit operator of Sweetgreen's scale; to confirm, check job ads for named platforms (POS vendor, delivery-integration middleware).

## 4 · Trace one flow — Order-to-Cash (O2C)

```
Customer places order (app / web / kiosk / 3rd-party)
        ↓
Payment authorized  ★ CONTROL POINT (the order record is born — fact now owned)
        ↓
Order enters restaurant order-management system
        ↓
Kitchen receives order — traditional line OR Infinite Kitchen  ◆ DECISION POINT
   (which format handles it, and does it have current stock to fulfil the customization?)
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

## 5 · Classify the operating model

Using Ross & Weill's two questions (standardization × integration):

- **Standardization:** high — Sweetgreen runs a common menu and process discipline across company-operated stores.
- **Integration:** *mixed/uncertain* — digital channels, delivery platforms, and two different kitchen formats (traditional vs. Infinite Kitchen) must all share the same order truth, but the degree to which they actually do is unconfirmed.

**Working classification: Unification stance (high standardization, high intended integration)** — but the intended integration is likely stronger on paper than in practice at the channel↔kitchen handoff, which is exactly where Move 6 names the gap.

## 6 · Name the leverage gap

> Sweetgreen's backbone may fail to fully leverage digital order data **at the handoff between ordering channels and kitchen execution**. Inconsistent visibility into customization, item availability, kitchen capacity, and order status can create delays, exceptions, remakes, and an inconsistent customer experience — a leak on the **Operations** and **Customer** threads, with **Cash** absorbing the downstream cost (waste, refunds, extra labor).

---
**Carried forward into:** [[Context-and-Diagnosis-Brief-Sweetgreen]] · [[Lab1-Prework-Sweetgreen]]
**Legend:** researched fact (green in slides) vs. labelled assumption (gold in slides) — sections above are marked accordingly; assumptions must be validated against real sourcing (job ads, investor materials, careers pages) before the board memo is finalized.
