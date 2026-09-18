---
title: Lab 1 Process Map — Order and Payment (Sweetgreen)
tags: [deliverable, week3, lab1, process-map, sweetgreen]
company: Sweetgreen
due: Week 3 Lab 1 (Fri Sep 18, 2026)
feeds: ["Board Memo §3 — Integration Backbone Assessment", "Storyboard S5"]
---

# Lab 1 Process Map — Order and Payment (Sweetgreen)

> The in-class BPMN build from [[W3_Lab1_Lecture-Notes|Lab 1]], move ① ("Map the real process") and ② ("Mark three diagnostic points"), applied to [[Lab1-Prework-Sweetgreen|the pre-work reality brief]]'s core thesis: the handoff between digital ordering and kitchen execution. Status: map + three diagnostic points done; **curveball exercise (move ③) in progress** — see open thread below.

## The annotated map

```mermaid
flowchart TD
    subgraph Customer["Customer"]
        A([Start])
        B["Select store, items, and customizations"]
        C["Submit pickup order"]
        R{"Customer's choice?"}
        Z["Collect order"]
    end

    subgraph Systems["Ordering and Payment Systems"]
        D["Process payment and order acceptance"]
        E{"Order accepted?"}
        F["★ Record confirmed order and specifications"]
        G["Send order to kitchen"]
        X["★ Record agreed order changes"]
        Y["★ Record cancellation and payment status"]
        Y1{"Payment already captured?"}
        Y2["Process refund"]
        Y3["Void authorization if applicable"]
        Y4["★ Record payment resolution"]
        W["★ Record order completion"]
        N["Notify customer that order was not accepted"]
        END1([Order not placed])
        END2([Order canceled])
        END3([Order completed])
    end

    subgraph Kitchen["Kitchen and Pickup Staff"]
        H["Review order specifications and availability"]
        I{"② Can the order be prepared as specified?"}
        J["Prepare meal"]
        K{"Does the meal match the confirmed order?"}
        L["① Hold incorrect meal and identify mismatch"]
        M["Correct or remake meal as required"]
        O["Pack and mark order ready for pickup"]
        P["Verify pickup order and hand over meal"]
    end

    subgraph Exceptions["Staff Handling Exceptions"]
        Q["Hold order and record fulfillment issue"]
        S["③ Assess feasible options and contact customer"]
        T["Keep order on hold and escalate to shift manager"]
    end

    A --> B --> C --> D --> E
    E -->|Yes| F --> G --> H --> I
    E -->|No| N --> END1

    I -->|Yes| J --> K
    I -->|No: unavailable item or unsupported request| Q
    Q --> S --> R

    R -->|Agrees to a feasible change| X
    X -->|Re-enter kitchen review| H
    R -->|Requests cancellation| Y
    R -->|No agreement or no response| T
    T -->|Further review or contact| S

    K -->|Yes| O --> P --> Z --> W --> END3
    K -->|No| L --> M
    M -->|Rework: check again| K
    M -->|Cannot complete correction| Q

    Y --> Y1
    Y1 -->|Yes| Y2 --> Y4
    Y1 -->|No| Y3 --> Y4
    Y4 --> END2

    classDef control fill:#e8f2ff,stroke:#2563eb,color:#172554;
    classDef diagnostic fill:#fff3d6,stroke:#b7791f,color:#422006;
    classDef exception fill:#fde8e8,stroke:#c53030,color:#450a0a;

    class F,X,Y,Y4,W control;
    class I,S diagnostic;
    class L,Q,T exception;
```

**Legend:** ★ control point (where data is born/committed) · ①②③ the three diagnostic points · shaded blue = control point, amber = diagnostic point, red = exception-handling node.

## The three diagnostic points

| # | Point | Type | Lens tag | Routes to |
|---|---|---|---|---|
| ① | Hold incorrect meal and identify mismatch (`L`) | Worst friction — the rework loop when the finished meal doesn't match the confirmed order | Quality / Operations & Supply Chain | — |
| ② | Can the order be prepared as specified? (`I`) | Stable-rules decision point — availability/feasibility check against a known ruleset | Operations & Supply Chain | **Lab 2 (Make)** — automate first |
| ③ | Assess feasible options and contact customer (`S`) | Judgment decision point — no clean rule for which substitution/compromise to offer, or when to escalate vs. hold | Customer | **Lab 3 (Relevance AI)** |

## Why this map matches the capstone thesis

This directly operationalizes the throughline from [[Backbone-Context-Note-Sweetgreen]] and [[Context-and-Diagnosis-Brief-Sweetgreen]]: the backbone's weakest point is the handoff between digital ordering and kitchen execution. On this map that handoff is literally the arrow from `G` (send order to kitchen) into `H`/`I` (kitchen review and feasibility check) — and it's exactly where the process forks into the worst-friction rework loop (①) and the judgment-heavy exception path (②→③→`Q`/`S`/`T`/`R`). The rejection/rework path (`Q → S → R` and `M → K` loop) is where — per the lecture notes' anti-pattern warning — "the cost hides"; this map has one, so it reflects the real process rather than the idealized one.

This also lines up with the primary-source evidence gathered in [[research/Sweetgreen-Public-Research|the public research log]]: the CEO's own order-accuracy math (§1) and the two independently-sourced kiosk/ordering-friction incidents (§4, §6) both point at the same seam this map isolates — the point where a digitally-placed order meets kitchen execution capacity and either holds together or doesn't.

## Open thread — curveball exercise (Lab 1 move ③, in progress)

Not yet resolved. Per [[W3_Lab1_Lecture-Notes]], next step is to pick one curveball from the deck and revise this map/diagnosis to absorb it — usually by adding a new rejection path or changing how an existing decision point behaves. Candidates most relevant to this map, given the confirmed backbone (Olo → PAR Brink → Crunchtime + Wonder-owned Infinite Kitchen → Salesforce):

- **#1 Hidden legacy system** or **#3 Nightly batch, not real time** — plausible given store-level menu/availability data may not sync in real time to the ordering layer, which would directly stress decision point ② (feasibility check running on stale availability data).
- **#2 Acquisition's parallel data** — less obviously applicable (no recent acquisition in the confirmed backbone) unless framed around the Wonder divestiture creating a *second* system of record for Infinite-Kitchen stores.
- **#6 The compliance hold** — plausible via food-safety/allergen sign-off, but weaker fit to the digital-ordering thesis than #1/#3.

Decide and record here once chosen; then update the map above to show the new/changed path.
