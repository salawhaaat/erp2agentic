---
title: Week 1 - The Integration Backbone
type: week-summary
tags: [week-summary, week1, module1]
description: Catch-up summary of Week 1 (Sep 4): the backbone as single source of truth, control and decision points, operating models, and why a working backbone still fails to pay.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w1/W01_IntegrationBackbone_StudyNote_PB14.md
  - id: slides
    resource: raw/data/markdown/course-weeks/w1/W1_IntegrationBackbone_Slides_v3.md
---
# Week 1: The Integration Backbone

Module 1, Friday Sep 4, 2026. Readings: [[W01_IntegrationBackbone_StudyNote_PB14|study note]], [[W1_IntegrationBackbone_Slides_v3|slides]]. Previous: [[Week-0-ERP-Floor]]. Next: [[Week-2-Failure-to-Leverage]]. Capstone output: [[Backbone-Context-Note-Sweetgreen]].

## The one-paragraph version

The course climbs four stages: integrate, automate, make intelligent, make agentic. Everything sits on the first. The backbone is a **single source of truth** (one authoritative record per fact) that also **enforces the process** that creates the truth. It is table stakes, not the prize. The real question is why a backbone that works technically so often fails to pay, which is the [[Leverage Gap]].

## Key points

- **Two flows** touch almost every integration: Order-to-Cash (O2C) and Procure-to-Pay (P2P).
- **[[Control Point|Control points]]** are where data is born (PO issued, credit approved, invoice posted). **[[Decision Point|Decision points]]** are where work is routed. The costly case is rejection, which sends work back for manual rework.
- **Backbone shapes:** a single ERP or a multi-SaaS stack, bought packaged or custom. In practice it is a hub with satellite apps, never one system for everything.
- **Four operating models** (Ross and Weill), sorted by standardization and integration: Diversification, Coordination, Replication, Unification. Classifying the company here is the core of Board Memo §3.
- **The foundation frees you.** Digitizing the core makes each process less flexible but the company more agile. About a third of firms had done it and enjoyed higher profit, faster time to market, and about 25% lower IT cost. Symptoms of its absence include people spending their days carrying data between systems.
- **The leverage gap.** Gartner projects over 70% of recent ERP initiatives will miss their original business goals by 2027. Westerman et al. studied 400+ traditional firms: winners paired digital capability with leadership capability, not bigger spend.
- **[[Four Lenses]] preview:** Frustration, Time, Cost, Quality (taught fully in Week 2).
- **[[Three Threads]]:** Customer, Operations and Supply Chain, Cash Management.

## Cases

- **NYU Bobst Library / Jaggaer migration.** The library's homegrown invoice workflow bypassed central procurement (2014 to 2021). An audit pushed a move to iBuy (live Jan 1, 2022), which restored central visibility. But iBuy and the library system aren't integrated, so staff now double-enter every purchase, costing about ten extra work-weeks a year. The seam moved, it didn't vanish.
- **Lidl / SAP eLWIS.** About €500M, started 2011, abandoned 2018. Enterprise-scale version of the same lesson.

## Why it matters later

Weeks 2, 4, and 5 all return to the leverage gap. The control and decision point vocabulary is what Lab 1 maps and what the Lab 2 build targets.
