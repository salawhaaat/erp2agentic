---
title: Lab 3 Final Flow, Order to Outcome (v7)
type: diagram
tags: [diagram, week9, lab3, make, sweetgreen, customer-journey]
company: Sweetgreen
description: Final flowchart of the v7 recovery workflow, one overview for the slide and one detailed version with module-level steps.
related: ["[[Lab3-Governed-Recovery-Agent]]"]
---
# Lab 3 Final Flow, Order to Outcome (v7)

Supersedes the earlier journey draft. All steps shown as built are in the v7 blueprints and not yet run in Make.

## Overview (for the slide)

Red diamonds are code checks (no model). Yellow boxes are Gemini. Green boxes are rows the workflow writes. Bold circles are the only places a person decides. Dotted lines are the scheduled follow-up.

![[Lab3-Final-Flow-Overview.png]]

## Detailed

Adds the three scenarios, the sheet tabs, the kill switch, the Reflect loop and the parts not built yet (orange dashed: checkout-time swap offer outside Make, sending the offer by email or SMS, the weekly review).

![[Lab3-Final-Flow-Detailed.png]]

> [!example]- Mermaid source, overview
> ```mermaid
> %%{init: {"flowchart": {"nodeSpacing": 35, "rankSpacing": 55, "curve": "basis", "useMaxWidth": false}, "themeVariables": {"fontSize": "18px"}} }%%
> flowchart TD
>     O([Order has an out-of-stock item]) --> G{"CODE GUARDRAILS<br/>allergen, odd text,<br/>conflicting or stale stock,<br/>bad deadline"}
>
>     G -->|"unsafe or unclear"| D["Staff row<br/>+ Gemini brief"] --> H1((Shift lead<br/>decides))
>     G -->|"no replacement fits"| C["Refund request<br/>+ Gemini apology"]
>     G -->|"clean"| P["Gemini picks replacement<br/>from approved list only"] --> V{"Code: pick<br/>in the list?"}
>     V -->|no| H1
>     V -->|yes| OF["Offer sent<br/>to customer"]
>
>     OF --> R{"Customer replies<br/>code checks: real,<br/>unexpired offer?"}
>     R -->|"no match or odd text"| H1
>     R -->|SWAP| L{"Code: replacement<br/>still in stock now?"}
>     L -->|gone| H1
>     L -->|yes| SW["Swap confirmed"] --> KO([Kitchen makes<br/>swapped order])
>     R -->|WAIT| W["Wait confirmed"]
>     R -->|DECLINE| RQ["Refund request"]
>
>     OF -.->|"no reply"| T{"Scheduled sweeper<br/>checks what is due"}
>     W -.->|"restock time"| T
>     T -->|"offer expired"| RQ
>     T -->|"item is back"| KO2([Kitchen makes<br/>original order])
>     T -->|"still out"| RQ
>
>     C --> CAP{"Code: order value<br/>at or under $15?"}
>     RQ --> CAP
>     CAP -->|yes| AU["Auto-approved<br/>by rule"] --> RF([Customer<br/>refunded])
>     CAP -->|no| FIN((Finance<br/>approves)) --> RF
>
>     classDef gem fill:#fef9c3,stroke:#a16207,color:#000;
>     classDef code fill:#fee2e2,stroke:#b91c1c,color:#000;
>     classDef human fill:#fff,stroke:#000,stroke-width:4px,color:#000;
>     classDef ok fill:#dcfce7,stroke:#15803d,color:#000;
>     class D,C,P gem; class G,V,L,CAP,T,R code; class H1,FIN human; class SW,AU,W,RQ,OF ok;
>
> ```

> [!example]- Mermaid source, detailed
> ```mermaid
> %%{init: {"flowchart": {"nodeSpacing": 28, "rankSpacing": 46, "curve": "basis"}} }%%
> flowchart TD
>     O([Customer places order]) --> CO["Checkout stock check<br/>offer in-stock swaps before paying<br/>(outside Make, not built)"]:::future
>     CO --> Q[("CheckQueue row")]
>     Q --> S1{"S1 stock check<br/>cached vs current"}
>
>     S1 -->|"available, clean"| AP["Approve order"]:::s1 --> KA([Kitchen prepares])
>     S1 -->|"stale or unmatched"| DR["Data repair row"]:::s1 --> HS((Staff))
>     S1 -->|"stockout, blocked,<br/>prior exception"| KS{"Kill switch<br/>3 REJECTs in 24h?"}:::guard
>     KS -->|"OFF: AI paused"| HS
>     KS -->|ON| GR{"Fixed guardrails, no model<br/>allergen blank or flagged<br/>instruction-like note<br/>fresh conflicting stock<br/>stale source, bad deadline"}:::guard
>
>     GR -->|"any hit: Path D"| PD["Staff row written first"]:::s1 --> GB["Gemini brief for the lead<br/>suggested action, main risk,<br/>draft message"]:::gem --> HL((Shift lead decides))
>     GR -->|"no approved candidate<br/>or restock too late: Path C"| PC["Refund request queued first"]:::s1
>     GR -->|"clean: Path A or B"| CL[("candidate_list from Menu<br/>same category, in stock,<br/>allergen NONE")]:::sheet
>
>     PC --> GM["Gemini writes apology<br/>template as fallback"]:::gem
>     PC --> CAP{"order value<br/>at or under cap $15?"}:::guard
>     CAP -->|yes| AA["AUTO_APPROVED<br/>approved_by RULE_CAP"]:::s1 --> RF([Refund])
>     CAP -->|no| FIN((Finance approves)) --> RF
>
>     CL --> GP["Gemini picks ONE item<br/>from the list only<br/>temp 0.1, swap or swap+wait"]:::gem
>     GP --> PG{"Guard: pick text is<br/>inside candidate_list?"}:::guard
>     PG -->|no| HS
>     PG -->|yes| OF["CUSTOMER_OFFER row<br/>expires 10 min (B) or 60 min (A)"]:::s1
>     OF --> SD["Send offer by email or SMS<br/>sheet row only today"]:::future
>
>     SD --> CR{{"Customer replies<br/>Customer Response tab"}}
>     CR --> S2{"S2: reply matches an<br/>unexpired offer, clean text?"}:::s2
>     S2 -->|"no match, expired,<br/>instruction-like text"| HS
>     S2 -->|ACCEPT_SWAP| RC{"Live re-check:<br/>item still in Menu stock?"}:::guard
>     RC -->|gone| HS
>     RC -->|in stock| SW["SWAP_CONFIRMED row<br/>change request for kitchen"]:::s2 --> KS2([Kitchen prepares swapped order])
>     S2 -->|WAIT_RESTOCK| WC["WAIT_CONFIRMED row"]:::s2
>     S2 -->|"DECLINE or NO_REPLY"| RQ["Refund request queued"]:::s2 --> CAP
>
>     OF -.->|"no reply by expiry"| FQ[("Follow-up Queue<br/>self-emptying tab")]:::sheet
>     WC -.->|"restock time reached"| FQ
>     FQ --> S3{"S3 sweeper"}:::s3
>     S3 -->|"TIMEOUT"| RQ
>     S3 -->|"RESTOCK_DUE, item back"| RS["RESTOCK_CONFIRMED"]:::s3 --> KS3([Kitchen prepares original order])
>     S3 -->|"RESTOCK_DUE, still out"| RQ
>
>     RF -.-> RE["Reflect: decline rate and reason,<br/>rating after pickup, reversal rate on path D"]:::future
>     HL -.-> RE
>     RE -.-> WR((Weekly review:<br/>person approves rule<br/>and prompt changes))
>
>     classDef s1 fill:#dcfce7,stroke:#15803d,color:#000;
>     classDef s2 fill:#dbeafe,stroke:#1d4ed8,color:#000;
>     classDef s3 fill:#ede9fe,stroke:#6d28d9,color:#000;
>     classDef gem fill:#fef9c3,stroke:#a16207,color:#000;
>     classDef guard fill:#fee2e2,stroke:#b91c1c,color:#000;
>     classDef sheet fill:#f1f5f9,stroke:#475569,color:#000;
>     classDef future fill:#fed7aa,stroke:#c2410c,stroke-dasharray: 5 3,color:#000;
>     class HS,HL,FIN,WR human;
>     classDef human fill:#fff,stroke:#000,stroke-width:2px,color:#000;
>
> ```
