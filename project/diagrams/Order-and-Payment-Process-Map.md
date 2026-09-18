---
title: Order and Payment Process Map (Sweetgreen)
tags: [deliverable, week3, lab1, diagram, sweetgreen]
---

# Order and Payment Process Map (Sweetgreen)

> Diagram only. Diagnostic points, the three-point table, and the write-up live in [[Lab1-Process-Map-Sweetgreen]] — this note exists so the diagram can be embedded and edited on its own.
>
> **Post-curveball.** Node `STALE` and its edges were added to absorb the curveball: deck card #3, "nightly batch, not real time." Availability data at decision ② now comes from two sources, a live system and a nightly legacy cache, and they don't always agree. See [[Lab1-Process-Map-Sweetgreen]] for the full reasoning and the data that confirms this is the curveball actually modeled in the sandbox.
>
> An annotated, presentation-ready version of this map (control-point IDs, decision labels, lab markers) is at `assets/Order-and-Payment-Process-Map-Annotated.png`.

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
        STALE{"Does live availability match last night's cached snapshot?"}
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
    E -->|Yes| F --> G --> H --> STALE
    E -->|No| N --> END1

    STALE -->|Yes: sources agree| I
    STALE -->|"No: nightly cache is stale, disagrees with live system (CURVEBALL)"| Q

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
    classDef curveball fill:#f3e8ff,stroke:#7e22ce,color:#3b0764;

    class F,X,Y,Y4,W control;
    class I,S diagnostic;
    class L,Q,T exception;
    class STALE curveball;
```

**Legend:** ★ control point (where data is born/committed) · ①②③ the three diagnostic points · shaded blue = control point, amber = diagnostic point, red = exception-handling node, **shaded purple = added to absorb the curveball** (live vs. nightly-cached availability freshness check).

## Annotated reference (pre-curveball state)

Presentation-ready version with control-point IDs (CP1–CP6), decision labels (D1–D3), and the friction chain overlaid, generated before the curveball was absorbed into the mermaid source above. Control points and decisions map onto the tables in [[Lab1-Process-Map-Sweetgreen]].

![[Order-and-Payment-Process-Map-Annotated.png]]

A diagram-only crop (no side panel of CP/D reference text) is at `assets/Order-and-Payment-Process-Map-Diagram-Only.png` — this is the version used on slide S5 of `project/Board-Presentation-Sweetgreen.pptx`, since the full annotated page's reference text is illegible at slide scale and duplicates the tables above.

![[Order-and-Payment-Process-Map-Diagram-Only.png]]
