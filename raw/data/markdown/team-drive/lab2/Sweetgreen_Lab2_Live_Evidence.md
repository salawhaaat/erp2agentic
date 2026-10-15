---
title: Sweetgreen Lab 2 Live Evidence
type: team-source
tags: [lab2, sweetgreen, make, evidence, team-drive]
description: Three-page evidence pack from the live Make run THREE_OUTCOMES_01, with the seven test orders and the AutoActions log walkthrough.
sources:
  - id: drive-evidence
    resource: "Google Drive: IE-GY 9113B Team 4 / Sweetgreen Lab 2 - Final Materials - 2026-10-06 / Sweetgreen_Lab2_Live_Evidence.pdf"
---
# Sweetgreen Lab 2 Live Evidence

Text transcription of a team PDF (6 October 2026), read through the Drive connector. The embedded Make screenshot is not reproduced; the original PDF was not downloaded (private file).

## Page 1: Lab 2, three outcomes in one run

Scenario: Sweetgreen D2 availability check. Sandbox: Sweetgreen Lab 2 Sandbox. Rule `three-outcomes-v3`. Inactive. Audit-only outputs.

Actual Make screenshot: Search Rows, Router and three named output modules. One combined run produced 2 approvals, 2 staff reviews and 3 data reviews. `THREE_OUTCOMES_01` output timestamps: 22:39:07-08 UTC on 6 October 2026. Readback: AutoActions rows 25-31.

**Historical evidence preserved.** The CSV contains 30 output rows. Rows 2-11 retain naive tests; rows 12-18 the initial guarded tests; rows 19-24 additional happy-case replays. Rows 25-31 are the current seven-case demonstration. Repeated tests are not additional unique orders.

## Page 2: Decisions, ownership and next steps

| Cases | Observed route | Recorded next action |
|---|---|---|
| H1 / H2 | APPROVE | Preparation after remaining customization checks; audit recommendation only |
| B1 / B2 | STAFF_REVIEW | Shift lead checks stock, holds order at CP2 and assesses D3 recovery; CP3 consent before changes |
| B3 / B4 / B5 | DATA_REVIEW | Integration owner repairs missing/stale/unmatched inputs, then reevaluates D2 |

**Routing and precedence.** Approval requires current availability = 1, NEW status, no prior exception, positive line count equal to matched count, KITCHEN source, and a present source age between 0 and 60 minutes. Staff review matches current availability = 0 OR BLOCKED status OR prior exception = 1. All remaining cases go to the data-review fallback. Staff holds take priority when an operational flag and a data problem coexist.

**Reproduction.** Search Rows: CheckQueue, headers Yes, A-Z, formatted values/timestamps, `test_group` Text Matches pattern `^(HAPPY|BREAK)$`, limit 7. All actions append to AutoActions with `run_label` THREE_OUTCOMES_01 and `rule_version` three-outcomes-v3. Change the run label before another test. The saved configuration includes both groups, so all three routes can be demonstrated in one Run once.

**What this adds.** The earlier fallback grouped every problem into REVIEW. The current workflow separates a fulfillment problem needing staff/customer judgment from a data problem needing repair. No extra module is needed per test row; modules represent actions. Five modules give the complete three-outcome demonstration.

**Scope and remaining work.** The input is a frozen historical sandbox, not a live kitchen feed. The 60-minute limit is illustrative. Owner roles and next actions are instructions, not notifications or completed work. Duplicate protection, full schema/ID validation, reviewer assignment/closure and consent capture remain future work. Seven selected cases reached the expected route exactly once. The test does not establish complete production coverage. An unexpected status or other unmatched case also reaches DATA_REVIEW. No messages, real order release, payments or coursework submissions occurred.

## Page 3: Test orders and the AutoActions log

Lab 1 provided the process map, diagnosis and Gemini sandbox. Lab 2 prepared a seven-order test set to exercise the D2 availability automation. Seven is the chosen test count. The tests use synthetic classroom data.

| Case / order | Test purpose | Latest decision |
|---|---|---|
| H1 / O007 | Normal single-item order | APPROVE |
| H2 / O025 | Normal two-item order | APPROVE |
| B1 / O001 | Unavailable stock despite cached availability | STAFF_REVIEW |
| B2 / O002 | Blocked order with a prior exception | STAFF_REVIEW |
| B3 / O008 | Missing availability value | DATA_REVIEW |
| B4 / O009 | Source age 670 minutes, above the 60-minute limit | DATA_REVIEW |
| B5 / O010 | Zero matched items out of one expected | DATA_REVIEW |

**AutoActions top to bottom.**
- Rows 2-3: original normal test, two correct approvals.
- Rows 4-7: original problem test, four false approvals. B3 produced no row.
- Rows 8-11: adding a Router alone repeated the same failures.
- Rows 12-16: stronger checks sent all five problem cases to REVIEW.
- Rows 17-18: both normal orders still passed the stronger checks.
- Rows 19-24: three further replays of the same two normal orders.
- Rows 25-31: current combined run, seven orders and seven results.

**Row columns.** A identifies the test run. B-D identify case, order and items. E is the event identifier (does not prevent duplicates). F is the decision and G the reason and next step. H-I are source and evaluation times in the September sample. J is the rule version. K is the actual October time Make wrote the row.

Seven unique orders, 30 logged outputs: repeated runs add rows. Earlier failures remain visible as evidence. Logging a next step does not notify staff or complete the work.

Links in the original: the Make scenario (us2.make.com, scenario 6536204) and the AutoActions Google Sheet.
