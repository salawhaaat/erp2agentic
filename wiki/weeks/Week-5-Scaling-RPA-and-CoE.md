---
title: Week 5 - Scaling RPA and the Center of Excellence
type: week-summary
tags: [week-summary, week5, module2, rpa, coe]
description: Catch-up summary of Week 5 (Oct 2): four reasons RPA programmes stall at scale, the Center of Excellence and its five functions, the scale mindset, human-in-the-loop, and the Telefonica O2 case.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w5/W05_ScalingRPA_CoE_StudyNote_v2.md
  - id: slides
    resource: raw/data/markdown/course-weeks/w5/W05_ScalingRPA_CoE_LN_Slides_v1.md
---
# Week 5: Scaling RPA and the Center of Excellence

Module 2, Friday Oct 2, 2026. Readings: [[W05_ScalingRPA_CoE_StudyNote_v2|study note]], [[W05_ScalingRPA_CoE_LN_Slides_v1|slides]]. Previous: [[Week-4-RPA]]. Next: [[Week-6-Lab-2-Automate]]. Concept page: [[Center of Excellence]].

## The one-paragraph version

A pilot proves the logic, not the programme. Ten bots is a demo, a thousand is an operation, and the same fragility that made one bot cheap makes a thousand expensive. The organisational answer is a **Center of Excellence (CoE)**. Scaling is an operating-model decision (who owns it, who builds it, whose budget) before it is a technology decision.

## Four ways programmes break at scale

| Failure mode | What goes wrong | Telefonica O2 example |
|---|---|---|
| Selector instability | A routine update moves a screen element, the bot's address stops resolving, and it fails silently or loudly | A bot shipped duplicate iPhones because it lacked the common sense a clerk supplies |
| Integration drift | Dozens of systems evolve independently under hundreds of bots, so maintenance grows faster than bot count | 15 processes across many systems |
| Infrastructure brittleness | The pilot platform buckles under load | Lead VM fine at about 20 robots, collapsed at about 80, about 16 weeks to re-engineer |
| Bot sprawl | Unowned shadow automations: fragmentation with bots on top | The pilot tripped the company's fraud alarms because IT wasn't involved |

The first three need engineering discipline. The fourth needs an organisation.

## The CoE

A small permanent team that governs how automation is done. Five functions: governance and standards, intake and review, bot ownership and monitoring, enablement and training, infrastructure and platform. Details in [[Center of Excellence]].

- It sits between the business (demand, process knowledge) and IT (platform, identity, security).
- It governs, it does not build everything. Citizen development is a complement that only works under a CoE.
- **Accountability is relocated, not removed.** If a bot is silently wrong for weeks, the CoE's ownership and monitoring function is where the answer lives (the week's ethics thread).

## Mindset

- **Scarcity** hoards experts. One specialist team would take 80+ years to automate everything (Tella et al.).
- **Scale** removes the dam and installs guardrails, so more people build safely. CoE shifts from automation factory to steward.
- Shadow IT is a symptom of a closed or slow sanctioned path. Prevent it by building a better-lit path, not by policing.

## Human in the loop

"Rules-based" does not mean "no human needed". Route to a person whenever the cost of the bot being confidently wrong exceeds the cost of a human touch:
- ambiguous edge cases
- high-value or irreversible actions
- anything a silent error could ruin over weeks

Tella's three approaches: task-based, straight-through processing, orchestration. Mature designs keep people where judgment lives. Westerman et al.: standardizing can empower rather than deskill. A CoE is a hard-to-copy capability; a pile of bots is not.

## Cases

- **Telefonica O2** (Lacity and Willcocks, 2016): independent, peer-reviewed. 2-week proof of concept, then 20, 75, and 160+ robots, 15 core processes, about 35% of back-office transactions, run by 3 in-house developers reassigned from the Back Office. About 10-month payback for RPA versus about 3 years for the BPM alternative, with the gap coming from resourcing. Chase-up calls fell over 80%.
- **Orange Spain "Robot Factory"**: UiPath vendor marketing. Same growth arc, but treat every figure as a vendor claim. The skill being practised is reading a vendor case against an independent one.

## Deliverable

Your CoE and operating-model section: five functions, the ownership model, human checkpoints, and a simple ROI line. Feeds Board Memo §4 and slide S7. Prep for next week: create a Make account. Discussion Forum 1 replies were due Sat Oct 3.
