---
title: Order and Payment Process Map (Sweetgreen)
tags: [deliverable, week3, lab1, diagram, sweetgreen]
---

# Order and Payment Process Map (Sweetgreen)

> Diagram only. Diagnostic points, the three-point table, and the write-up live in [[Lab1-Process-Map-Sweetgreen]] — this note exists so the diagram can be embedded and edited on its own.
>
> **Post-curveball.** Nodes `IK` and `V` and the edges around them were added to absorb the curveball: for Infinite Kitchen stores, the kitchen system is owned and operated by Wonder, not Sweetgreen, since the December 2025 divestiture. See [[Lab1-Process-Map-Sweetgreen]] for the full reasoning.

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
        IK{"Infinite Kitchen store? (kitchen system is Wonder-owned since Dec 2025)"}
        V{"②b Wonder-owned system confirms capacity and ingredient availability, in sync?"}
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
    E -->|Yes| F --> G --> IK
    E -->|No| N --> END1

    IK -->|No: traditional make-line| H
    IK -->|Yes: query Wonder-owned kitchen system, crosses a company boundary| V
    V -->|Yes: synced and available| H
    V -->|"No: stale sync, capacity limit, or vendor system unavailable (CURVEBALL)"| Q

    H --> I
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
    class IK,V curveball;
```

**Legend:** ★ control point (where data is born/committed) · ①②③ the three diagnostic points · shaded blue = control point, amber = diagnostic point, red = exception-handling node, **shaded purple = added to absorb the curveball** (the Wonder-owned Infinite Kitchen system boundary).
