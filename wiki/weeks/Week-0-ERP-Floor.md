---
title: Week 0 - The ERP Floor
type: week-summary
tags: [week-summary, week0, module1]
description: Catch-up summary of the optional pre-course primer on what an ERP is, how ERPs differ, and basic BPMN vocabulary.
sources:
  - id: primer
    resource: raw/data/markdown/course-weeks/w0/W0_ERPFloor_Course Primer.md
---
# Week 0: The ERP Floor (optional primer)

Module 1, The Integration Foundation. Optional and ungraded. Full reading: [[W0_ERPFloor_Course Primer|primer]]. Next: [[Week-1-Integration-Backbone]].

## The one-paragraph version

A company's data is scattered across many systems that cannot see each other, so a fragmented system landscape means a fragmented company. An enterprise system (ERP) fixes this with one shared database that every function reads from and writes to. The rule of thumb is **one entry, many updates**: a single order should update inventory, scheduling, the ledger, and commissions without anyone re-keying it.

## Key points

- **Four data zones** an ERP spans: financial, human capital, operations and logistics, commercial.
- **ERPs differ along three lines** that cut across the four [[Four Archetypes]]:

| Dimension | Options |
|---|---|
| Deployment | on-premise, cloud, hybrid |
| Scope | generalist (horizontal) or industry-specific (vertical) |
| Market tier | Tier I (about $750M+ revenue), Tier II, Tier III |

- **The software rarely breaks, the business around it does.** Past ERP failures were business-transformation decisions treated as technology purchases. The contrast case is a chemicals subsidiary where a routine order took 4 days and 7 handoffs for about 4 hours of work. It succeeded because leadership "stressed the enterprise, not the system" and redesigned the organization alongside the install.
- **Why a 1998 argument opens an AI course.** Davenport (1998) argued the same thing agents now repeat: an agent senses and acts through the shared data model, so layering agents on a fragmented backbone makes it act on bad data faster. McKinsey (Jan 2026) notes AI budgets rising while spend on the ERP layer falls.
- **BPMN vocabulary:** event, task, gateway, sequence flow, swimlane. The gateway is what the course calls a [[Decision Point]]. Lab 1 also marks [[Control Point|control points]].

## Why it matters later

It sets the vocabulary for [[Week-1-Integration-Backbone]] and the process-mapping work in [[Week-3-Lab-1-Diagnose-and-Map|Lab 1]].
