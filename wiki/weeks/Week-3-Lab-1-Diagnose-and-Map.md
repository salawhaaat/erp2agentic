---
title: Week 3 - Lab 1 Diagnose and Map
type: week-summary
tags: [week-summary, week3, lab1, module1]
description: Catch-up summary of Lab 1 (Sep 18): map the real process, mark three diagnostic points, absorb a curveball, build a sandbox, and write a one-page diagnosis.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w3/IE-GY-9113B_Lab1_StudyNote.md
  - id: lecture-notes
    resource: raw/data/markdown/course-weeks/w3/W3_Lab1_Lecture-Notes.md
---
# Week 3: Lab 1, Diagnose and Map a Process

Module 1 lab, Friday Sep 18, 2026, 8:00 to 10:30. Readings: [[IE-GY-9113B_Lab1_StudyNote|study note]], [[W3_Lab1_Lecture-Notes|lecture notes]]. Previous: [[Week-2-Failure-to-Leverage]]. Next: [[Week-4-RPA]]. Capstone outputs: [[Lab1-Prework-Sweetgreen]], [[Lab1-Process-Map-Sweetgreen]].

## The one-paragraph version

A build session, not a lecture. You arrive with a research brief (gated: no brief, no lab). You map the **real** process in BPMN, find a causal chain of frictions, absorb a curveball, build a synthetic data sandbox, and present. The output becomes board deck slide S5 and the evidence for Board Memo §3.

## The four moves

1. **Map the real process.** Mark ★ [[Control Point|control points]], name every ◆ [[Decision Point|decision point]], and trace the rejection and rework path, where the cost hides.
2. **Mark three diagnostic points:**
   - the worst friction (tag with a Four Lens)
   - a **stable-rules** decision point, which is the Lab 2 automation target
   - a **judgment** decision point, which is the Lab 3 agent target
3. **Take a curveball.** Pick a card that changes reality: hidden legacy system, acquired parallel data, nightly batch instead of real time, an undocumented manual reconciliation, a vendor that only takes email or FTP. Revise the map and diagnosis.
4. **Generate the data last,** then verify every planted flaw survived. An LLM will often helpfully clean them away.

## What good looks like

- **Find a chain, not a pain:** at least 3 causally linked frictions across at least 2 [[Three Threads|threads]], ending in a board-level consequence. "Invoices go out late" is a symptom. A chain shows how one friction causes the next.
- The Citi Bike worked example: a demand forecast is recorded but never consumed, so rebalancing is reactive, riders hit empty docks, and about 1 in 7 tasks enters rework. It is a mirror, not a template.
- **Anti-patterns:** a pain instead of a chain, and mapping the solution instead of reality (a suspiciously clean map has no rejection path).

> [!info]- Chain-skeleton library (6 shapes)
> Inventory-to-cash, procurement blind spot, multi-system reconciliation, returns and credit leakage, quote-to-onboard drag, service-to-churn. Each is a causal shape to test your chain against, not a menu to copy. Detail in the study note §6.

## Deliverables

Sandbox (Airtable or Sheets), annotated map (★ ◆, rejection path, three points), and a one-page diagnosis (chain, consequence, prize). Submitted Monday.

## Why it matters later

The stable-rules decision point becomes the [[RPA Candidate Criteria|RPA candidate]] in Week 4 and the Make build in [[Week-6-Lab-2-Automate]]. The judgment point becomes the Lab 3 agent. Ethics thread: what is the human doing at the judgment step, and should it be automated at all?
