---
title: Sweetgreen Lab 1 Final Annotated Map (team submission, 24 Sep 2026)
type: reference
tags: [reference, lab1, sweetgreen, graded]
---

# Sweetgreen | Annotated Order and Payment Process (Final, 24 Sep 2026)

> Markdown transcription of `Sweetgreen-Lab1-Final-Annotated-Map.pdf` (the pdf, with the actual diagram image, sits next to this file's PDF counterpart in `raw/data/pdf/sweetgreen-lab1-evidence/`). This is the team's graded checkpoint-final submission. Its content was folded into [[Lab1-Process-Map-Sweetgreen]] (control register, friction chain, diagnosis) at the time; this page preserves the document's own text and structure for reference. Local review copy, 18 September 2026 baseline, revised 24 September 2026 — no upload or submission of this specific file; process and causal claims require validation with restaurant staff.

## Page 1 — Annotated order and payment process

Diagram: BPMN swimlane map with lanes Customer, Ordering and Payment Systems, Kitchen and Pickup Staff, Staff Handling Exceptions. Control points CP1–CP6, decisions D1–D3, diagnostic markers ①②③. See [[Order-and-Payment-Process-Map]] for the vault's living version of this diagram (Mermaid + a hand-built swimlane image).

### Control points — ★ new authoritative facts

- **CP1 · Confirmed order** — Order ID, accepted items/customizations and promise become the fulfillment reference.
- **CP2 · Fulfillment issue recorded** — Create an exception record when an unavailable item, unsupported request or uncorrectable meal blocks the order.
- **CP3 · Agreed order changes** — Record the new specification and customer consent before kitchen re-entry.
- **CP4 · Order completion** — Record successful collection/completion against the order ID.
- **CP5 · Cancellation and payment status** — Record cancellation and whether payment was captured or only authorized.
- **CP6 · Payment resolution** — Record the refund or authorization-void outcome, amount and transaction reference.

### Three routing decisions

- **D1 · Order accepted?** Route to confirmed order or notify customer / end. Payment approval and order acceptance criteria must be explicit.
- **D2 · Can the order be prepared as specified?** ② Stable rules / Lab 2: check ingredient availability and supported customizations. Yes → prepare; no → exception handling. Freshness of the availability input must be checked.
- **D3 · Which recovery route is agreed?** ③ Judgment / Lab 3: staff assess feasible options and the customer consents. Route to agreed change, cancellation or hold/escalation. The "Customer's choice?" diamond carries this branch; staff judgment occurs in the preceding assessment.

### The three lab markers

- **① Worst friction:** the hold → correction/remake → recheck loop, including escalation when correction cannot finish. Tags: Quality, Time, Cost and Frustration.
- **② Rules target:** D2.
- **③ Judgment target:** the D3 recovery branch, informed by staff assessment.

> The lab requires three diagnostic markers; only two must sit on decision points. Retain your additional quality-check and payment-captured gateways: they remain necessary routing choices. (This is the checkpoint feedback [[Lab1-Process-Map-Sweetgreen]]'s "Checkpoint feedback" section responds to.)

### Friction chain

Operations: accepted specification and kitchen feasibility disagree → order held/rejected → manual customer contact and recovery → kitchen re-entry / repeat checking → Customer: pickup promise missed and uncertainty increases → Cash: staff capacity consumed and refunds reduce receipts.

### Board-level consequence

Six of 30 synthetic orders require exception recovery, consuming $44 in modeled labor capacity and refunds. 60 labor minutes × $0.40/min + $20 refunds = $44. Those six orders are ready an average of 18.7 minutes late.

This is an illustration from the earlier sandbox, not measured Sweetgreen performance. The $28 partial-prep waste is excluded because the map checks availability before preparation. The meal-error remake branch is a suspected friction; its separate cost has not been seeded or measured.

## Page 2 — Section 3: Process diagnosis

*Order acceptance to pickup | Lab 1 | 24 September 2026*

### Diagnosis and process boundary

Working hypothesis: the ordering channel can accept a meal that the kitchen cannot fulfill as specified. The process spans acceptance, availability checking, preparation, quality checking, pickup and exception/payment resolution. The lecture curveball, "nightly batch, not real time," makes a stale availability snapshot the testable failure mechanism. This is a classroom scenario, not evidence of Sweetgreen's actual update cadence.

### Specific control points and three diagnostic markers

Each control point now specifies its trigger, proposed owner, fields and downstream use in the map's control register. CP1 binds the accepted specification and pickup promise to an order ID; CP2 logs the blocked item, reason and exception ID; CP3 versions the agreed replacement with consent/time; CP4 records collection/time; CP5 records cancellation and capture status; CP6 links a refund or void to the payment reference.

1. **Worst friction:** correction/remake and repeat checking (Quality, Time, Cost, Frustration).
2. **Rules / Lab 2:** D2 availability and supported-customization check.
3. **Judgment / Lab 3:** staff recovery assessment and customer choice at D3.

### Friction chain: Operations to Customer to Cash

Stale availability → false acceptance → kitchen exception and held work → manual customer contact and agreed recovery → kitchen re-entry and later readiness → staff capacity consumed and refunds reducing receipts. Availability failure before prep and meal-quality failure after prep are separate branches; the sandbox quantifies the former only.

### Board-level consequence

In the synthetic 30-order sample, **6 orders (20%)** need exception recovery. They consume **60 extra staff minutes** at an assumed $24/hour ($24 of capacity) and **$20 in goodwill refunds**: **$44 total**, or $7.33 per affected order. Their combined lateness is **112 order-minutes**, averaging **18.7 minutes** each. The earlier $28 partial-prep waste is excluded because the final map checks availability before preparation. Labor capacity is not necessarily incremental payroll. These are modeled exposure figures, not observed performance, annual forecasts or guaranteed savings.

### Lab 2 candidate and board implication

Automate D2 first: read the accepted order and authoritative availability, check item/customization feasibility and freshness, then route to preparation or a recorded exception. Stale or unknown input requires review. Preserve order IDs and repeat-safe logging. Demonstrate the cached-source failure, then add the freshness safeguard. In Lab 3, assist D3 with urgency, prep ETA, queue impact and customer constraints; staff review and the customer consents. Validate the real workflow and baseline before piloting. The board-level opportunity is more reliable pickup promises with less avoidable recovery work.

**Basis:** supplied Order and Payment diagram; W3 Lab 1 lecture/study note; Sweetgreen context briefs; synthetic sandbox. Checkpoint feedback addressed: make control points more specific. Proposed owners and internal data contracts require restaurant validation.
