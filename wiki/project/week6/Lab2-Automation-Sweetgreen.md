---
title: Lab 2 Automation (Sweetgreen)
type: deliverable
tags: [deliverable, week6, lab2, automation, make, sweetgreen]
description: The D2 availability-check automation built and tested in Make, with the three-route outcome, what broke along the way, and an illustrative ROI.
company: Sweetgreen
due: Week 6 lab (Fri Oct 9, 2026)
feeds: ["Board Memo §4 — Automation Journey", "Storyboard S6/S7"]
sources:
  - id: postmortem
    resource: raw/data/markdown/team-drive/lab2/Sweetgreen_Lab2_Postmortem.md
    title: Lab 2 postmortem
  - id: evidence
    resource: raw/data/markdown/team-drive/lab2/Sweetgreen_Lab2_Live_Evidence.md
    title: Live Make run evidence
  - id: guide
    resource: raw/data/markdown/team-drive/lab2/Sweetgreen_CP_DP_Lab2_Group_Guide.md
    title: CP and DP group guide
  - id: slides
    resource: raw/data/markdown/team-drive/lab2/Sweetgreen_Lab2_Board_Slides.md
    title: Board slides S3-S7
---
# Lab 2 Automation (Sweetgreen)

Builds the rules-based candidate that [[RPA-Candidate-Scan-Sweetgreen]] picked: the D2 availability check from [[Lab1-Process-Map-Sweetgreen]]. Course reading: [[W06_Lab2_Automate_StudyNote_v1|Week 6 study note]] and [[W06_Lab2_Automate_LN_Slides_v1|lecture slides]]. Terms: [[Control Point]], [[Decision Point]], [[RPA Candidate Criteria]].

## What was built

A five-module Make scenario: Search Rows reads `CheckQueue`, a Router sends each order to one of three Add a Row modules, and all three write to an `AutoActions` audit sheet.

| Route | Rule | Next action recorded |
|---|---|---|
| APPROVE | Current availability = 1, status NEW, no prior exception, positive line count equal to matched count, KITCHEN source, source age 0 to 60 min | Preparation, audit recommendation only |
| STAFF_REVIEW | Current availability = 0, or BLOCKED status, or prior exception = 1 | Shift lead holds the order at CP2 and assesses D3 recovery |
| DATA_REVIEW | Everything else | Integration owner repairs the input and re-runs D2 |

Staff holds win when an operational flag and a data problem coexist. The scenario is inactive and writes audit rows only. Nothing was sent, released or paid.

## What broke

Seven unique synthetic orders: two normal (H1, H2) and five problem cases (B1 unavailable stock, B2 blocked re-entry, B3 missing availability, B4 stale source, B5 unmatched item).

1. The original cached-availability rule approved four problem cases and silently dropped B3.
2. Adding a Router alone changed nothing. The rules were wrong, not the routing.
3. A guarded version caught all five, but lumped them into one generic REVIEW.
4. The final `three-outcomes-v3` rule separates staff judgment problems from data repair problems. One run (`THREE_OUTCOMES_01`) gave 2 approvals, 2 staff reviews and 3 data reviews.

The log holds 30 rows because tests were repeated. Seven is the unique order count.

## Control points and decisions touched

D2 is implemented for availability only. CP2 is logged in part (case IDs, field values, proposed owner role, next action). D3 and CP3 consent stay human. CP4 to CP6 are outside this automation. See the full mapping in the [[Sweetgreen_CP_DP_Lab2_Group_Guide|group guide]].

## Illustrative ROI

Assumptions: 660 orders a month, 20% exceptions, 45 s manual check, 10 s routine oversight, 15 s extra per exception, $24/hour, 4 build hours, 1 maintenance hour a month. Baseline labor $726, after-automation labor $616, upkeep $24, so $86 a month of capacity value against a $96 build. Payback is 1.12 months. None of these inputs are measured, and the figure should be re-estimated for the expanded design. Passing the tests shows routing works, not that money is saved.

## Limits

Frozen historical sandbox, not a live kitchen feed. The 60-minute freshness limit is illustrative. Owner roles are proposed, not verified Sweetgreen assignments. Duplicate protection, schema validation, reviewer assignment and closure, and consent capture are future work.

## Source material

Raw transcriptions live in `raw/data/markdown/team-drive/lab2/`: [[Sweetgreen_Lab2_Postmortem]], [[Sweetgreen_Lab2_Live_Evidence]], [[Sweetgreen_CP_DP_Lab2_Group_Guide]], [[Sweetgreen_Lab2_Board_Slides]]. These came from the team's Google Drive folder as text only, so the original PDFs, `.pptx`, `.zip` and Make screenshot are not in the vault.
