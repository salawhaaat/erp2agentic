---
title: Sweetgreen Lab 2 Postmortem
type: team-source
tags: [lab2, sweetgreen, postmortem, roi, team-drive]
description: One-page postmortem of the D2 availability automation, covering what broke, how the rules evolved, human oversight and an illustrative ROI.
sources:
  - id: drive-postmortem
    resource: "Google Drive: IE-GY 9113B Team 4 / Sweetgreen Lab 2 - Final Materials - 2026-10-06 / Sweetgreen_Lab2_Postmortem.pdf"
---
# Lab 2 postmortem: D2 availability check

Text transcription of a team PDF (6 October 2026), read through the Drive connector. The original PDF was not downloaded (private file).

Five modules, three outcomes. Tested 6 October 2026. Synthetic classroom data. Scenario 6536204 remains inactive and writes only audit rows. Nothing submitted.

Lab 1 supplied the sandbox and D2 diagnosis. Lab 2 prepared seven unique test orders: two normal cases and five problem cases. Seven was a test-design choice.

## What we built

Search Rows reads CheckQueue. A Router directs each case to one of three Add a Row modules: Approve order, Staff recovery review, or Data repair review. All write to AutoActions. The automation covers D2 availability and partial CP2 exception logging.

Approval requires current availability = 1, NEW status, no prior exception, positive line count equal to matched count, KITCHEN source, and a present source age between 0 and 60 minutes. Staff review matches current availability = 0 OR BLOCKED status OR prior exception = 1. All remaining cases go to the data-review fallback. Staff holds take priority when an operational flag and a data problem coexist.

## What broke and how the design evolved

The original cached-availability rule approved both normal cases but incorrectly approved B1 (unavailable stock), B2 (blocked re-entry), B4 (stale source) and B5 (incomplete match). B3 (missing availability) produced no output. A single-route Router preserved these failures. A later guarded version approved two normal cases and recorded all five breaks as generic REVIEW.

Current live run: `THREE_OUTCOMES_01`, `three-outcomes-v3`. At 22:39:07-08 UTC, H1/H2 received APPROVE; B1/B2 STAFF_REVIEW; B3/B4/B5 DATA_REVIEW. Independent readback confirmed exactly seven rows, one per case (AutoActions rows 25-31). Every route executed in one combined run. The log preserves 30 outputs across repeat tests of these seven orders.

## Human oversight

Staff review: shift lead holds the order at CP2, verifies stock and assesses recovery at D3. Customer consent must be recorded at CP3 before changes or re-entry. Data review: integration owner repairs missing values, refreshes stale data or reconciles item matches before reevaluating D2. These are proposed roles, not verified Sweetgreen assignments.

The input is a frozen historical sandbox, not a live kitchen feed. The 60-minute limit is illustrative. Owner roles and next actions are instructions, not notifications or completed work. Duplicate protection, full schema/ID validation, reviewer assignment/closure and consent capture remain future work.

## ROI and board consequence

Illustrative assumptions: 660 orders/month, 20% exceptions, 45-second manual checks, 10-second routine oversight, 15 extra seconds per exception, 10-minute recovery, $24/hour, 4 build hours and 1 maintenance hour/month. $726 baseline labor minus $616 after labor and $24 upkeep gives $86/month capacity value; a $96 build implies 1.12-month payback. Re-estimate actual build effort and costs for this expanded design. Recovery and refunds remain unchanged. Test success demonstrates routing, not financial savings.

Evidence: `THREE_OUTCOMES_01` audit rows and the Make screenshot. Historical original run IDs: 31d22325594c41d3a0ab667a8e081e4e and b014b84095f54197bc5241ffe2c60d40. Sources: Lab 1 Gemini sandbox and the W06 Lab 2 study note.
