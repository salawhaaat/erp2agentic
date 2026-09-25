---
title: Order and Payment Process Map (Sweetgreen)
type: diagram
tags: [deliverable, week3, lab1, diagram, sweetgreen]
---

# Order and Payment Process Map (Sweetgreen)

> Diagnostic points, the three-point table, and the write-up live in [[Lab1-Process-Map-Sweetgreen]] — this note exists so the diagram can be embedded and edited on its own.
>
> **Post-curveball.** A freshness gate (`STALE` in the full-detail source) was added to absorb the curveball: deck card #3, "nightly batch, not real time." Availability data at decision ② now comes from two sources, a live system and a nightly legacy cache, and they don't always agree. See [[Lab1-Process-Map-Sweetgreen]] for the full reasoning and the data that confirms this is the curveball actually modeled in the sandbox.
>
> **Post-checkpoint (final, Sep 24).** The guest lecturer's suggestion to add a quality control point was considered and not taken: the checkpoint feedback actually acted on was to make the six existing control points (CP1–CP6) more specific (trigger, owner, fields, downstream use), not to add a seventh. The quality check and the payment-captured check stay routing gateways, not control points — see [[Lab1-Process-Map-Sweetgreen]] for the reasoning and the control register.

## Swimlane view (primary)

**Sweetgreen order & payment flow.** Rendered image, built to match the course's own worked-example style (the Citi Bike annotated process map from the Week 3 lecture notes): ★ control point (data is born), ◆ decision point (routing choice), red dashed = rejection/rework path, ⚡ = value leak (Four Lenses). Mermaid's `subgraph`-based swimlanes reordered unpredictably around this process's back-edges and produced an unreadable tangle in both Obsidian and a direct render, so this is a hand-built SVG (source: `assets/Order-and-Payment-Swimlane.svg`) rendered to PNG, not a live Mermaid block.

![[Order-and-Payment-Swimlane.png]]

**Reading it:** the recovery loop (agrees to change → re-enter kitchen review) and the quality-rework loop (reject → rework → re-serve late) are both drawn as red dashed curves, matching the course's own rejection-path convention. `Feasible?` (D2, kitchen row) is the RPA target, Lab 2. `Recovery agreed?` (D3, exceptions row) is the AI-agent target, Lab 3. `Matches order?` failing is where ① (the worst-friction rework loop) surfaces. Every ★ node is a control point from the register in [[Lab1-Process-Map-Sweetgreen]]; the quality gate and the payment-captured check stay plain ◆ decisions, deliberately not control points (see that note's "Checkpoint feedback" section).

## Full detail (BPMN)

> [!example]- Every step, every gate, every control point — the source of truth the swimlane view above summarizes
> Flat left-to-right, not `subgraph` lanes — same reason as the swimlane image above. Colored by role (blue = control point, amber = ② stable-rules diagnostic, red = ① worst friction / exception node, purple = curveball-added freshness gate) instead of physical lane grouping.
> ```mermaid
> flowchart LR
>     A([Start]) --> B["Select store, items, and customizations"] --> C["Submit pickup order"] --> D["Process payment and order acceptance"] --> E{"Order accepted?"}
>
>     E -->|Yes| F["★ Record confirmed order and specifications"] --> G["Send order to kitchen"] --> H["Review order specifications and availability"] --> STALE{"Does live availability match last night's cached snapshot?"}
>     E -->|No| N["Notify customer that order was not accepted"] --> END1([Order not placed])
>
>     STALE -->|Yes: sources agree| I{"② Can the order be prepared as specified?"}
>     STALE -->|"No: nightly cache is stale, disagrees with live system (CURVEBALL)"| Q["Hold order and record fulfillment issue"]
>
>     I -->|Yes| J["Prepare meal"] --> K{"Does the meal match the confirmed order?"}
>     I -->|No: unavailable item or unsupported request| Q
>
>     K -->|Yes| O["Pack and mark order ready for pickup"] --> P["Verify pickup order and hand over meal"] --> Z["Collect order"] --> W["★ Record order completion"] --> END3([Order completed])
>     K -->|No| L["① Hold incorrect meal and identify mismatch"] --> M["Correct or remake meal as required"]
>     M -->|Rework: check again| K
>     M -->|Cannot complete correction| Q
>
>     Q --> S["③ Assess feasible options and contact customer"] --> R{"Customer's choice?"}
>     S -->|escalate| T["Keep order on hold and escalate to shift manager"] --> R
>
>     R -->|Agrees to a feasible change| X["★ Record agreed order changes"] --> H
>     R -->|Requests cancellation| Y["★ Record cancellation and payment status"] --> Y1{"Payment already captured?"}
>     R -->|No agreement or no response| T
>
>     Y1 -->|Yes| Y2["Process refund"] --> Y4["★ Record payment resolution"] --> END2([Order canceled])
>     Y1 -->|No| Y3["Void authorization if applicable"] --> Y4
>
>     classDef control fill:#e8f2ff,stroke:#2563eb,color:#172554;
>     classDef diagnostic fill:#fff3d6,stroke:#b7791f,color:#422006;
>     classDef exception fill:#fde8e8,stroke:#c53030,color:#450a0a;
>     classDef curveball fill:#f3e8ff,stroke:#7e22ce,color:#3b0764;
>
>     class F,X,Y,Y4,W control;
>     class I,S diagnostic;
>     class L,Q,T exception;
>     class STALE curveball;
> ```
>
> **Legend:** ★ control point (where data is born/committed) · ①②③ the three diagnostic points · shaded blue = control point, amber = diagnostic point, red = exception-handling node, shaded purple = added to absorb the curveball (live vs. nightly-cached availability freshness check). `K` (quality check) and `Y1` (payment captured) are routing gateways deliberately kept as decisions, not control points — see the reasoning in [[Lab1-Process-Map-Sweetgreen]].

## Superseded assets

Two presentation-ready PNGs (`Order-and-Payment-Process-Map-Annotated.png`, a full annotated page with a CP/D reference panel, and `Order-and-Payment-Process-Map-Diagram-Only.png`, a diagram-only crop used on slide S5 of `wiki/project/shared/Board-Presentation-Sweetgreen.pptx`) were generated 18 Sep 2026, before the curveball was absorbed into the map. Removed 25 Sep 2026: the [[Order-and-Payment-Swimlane|swimlane view]] above is the current, accurate, presentation-ready diagram now, and keeping a pre-curveball screenshot around risked someone citing stale control-point/decision labels. **Note:** the deck's own slide S5 still has the old diagram image baked into it (PNGs embed as binary data in a `.pptx`, deleting the standalone file doesn't touch that) — re-export the swimlane image into that slide the next time the deck is touched.
