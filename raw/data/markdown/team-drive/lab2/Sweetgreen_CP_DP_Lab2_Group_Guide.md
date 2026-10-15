---
title: Sweetgreen CP & DP Lab 2 Group Guide
type: team-source
tags: [lab2, sweetgreen, control-point, decision-point, team-drive]
description: Team's two-page reference mapping the six control points and three decision points onto the Lab 2 Make automation.
sources:
  - id: drive-guide
    resource: "Google Drive: IE-GY 9113B Team 4 / Sweetgreen Lab 2 - Final Materials - 2026-10-06 / Sweetgreen_CP_DP_Lab2_Group_Guide.pdf"
---
# Sweetgreen CP & DP Lab 2 Group Guide

Text transcription of a team PDF (6 October 2026), read through the Drive connector. The original PDF was not downloaded (private file).

Group reference, Lab 1 process map and Lab 2 automation.

**Control point (CP):** where an important fact is recorded. **Decision point (DP):** where the process chooses a route. The map labels the three highlighted routing decisions D1-D3.

## The six control points

| ID | Control point | What it records / when it applies |
|---|---|---|
| CP1 | Confirmed order | After acceptance: order ID, accepted items/customizations, payment authorization reference, promised pickup time. |
| CP2 | Fulfillment issue | When preparation is blocked: exception ID, order/item, reason, check time, source timestamp, assigned owner. |
| CP3 | Agreed changes | After customer agreement: original and revised items, consent, agreement time, revised ETA. Recheck before preparation. |
| CP4 | Completed handoff | After collection: order ID, completed status, handoff time. Kitchen readiness and customer collection are distinct events. |
| CP5 | Cancellation / payment status | After cancellation: reason, cancellation time, payment reference, whether payment was captured or only authorized. |
| CP6 | Payment resolution | After provider confirmation: refund or authorization-void outcome, amount, transaction reference, resolution time. |

## The three highlighted routing decisions

| ID | Question | Routes |
|---|---|---|
| D1 | Was the order accepted? | Yes: confirm the order (CP1). No: notify the customer and end. |
| D2 | Can the order be prepared as specified? | Yes: prepare. No: record an issue (CP2). Checks cover availability and supported customizations; Lab 2 implements only the availability portion. |
| D3 | Which recovery option is agreed? | Staff assess feasible options; the customer chooses a change (CP3), cancellation (CP5), or hold/escalation. |

These describe the designed process. Some fields are proposed controls, not fields currently logged in the sandbox. The full map also retains quality-check and payment-captured gateways.

## Where they fit in Lab 2

Focus is D2: automate the availability check for an already accepted order.

CP1: confirmed order, then D2: availability check, then prepare OR CP2: log an issue.

| Point | Role in Lab 2 |
|---|---|
| D1 + CP1 | Upstream context: establish the accepted order and the items to check. The Make scenario does not accept orders or take payment. |
| D2 | Implemented: check current availability, status, prior exceptions, item match and source freshness. Approve passing cases; route operational exceptions to STAFF_REVIEW and remaining failures to DATA_REVIEW. |
| CP2 | Partial logging implemented: STAFF_REVIEW and DATA_REVIEW rows preserve case/order IDs, field values, a proposed owner role and next-action instructions. Assignment, resolution tracking and customer contact remain human/future work. |
| D3 + CP3 | Human recovery: staff and customer agree on a feasible change, then record consent and the revised specification before rechecking. Not automated. |
| CP4 | Downstream: record collection after successful preparation. Outside this automation. |
| CP5 + CP6 | Cancellation branch: record cancellation/payment status, then confirm refund or void. Outside this automation. |

## What actually happened in Make

Five modules: Search Rows, Router, then Approve order, Staff recovery review, or Data repair review. All three actions write to AutoActions. The approval filter requires current stock, NEW status, no prior exception, complete positive item matching and a KITCHEN source aged 0-60 minutes. These are sandbox audit rows, not real kitchen or payment actions.

Lab 1 supplied the sandbox and diagnosis. Lab 2 prepared seven unique test orders: two normal and five problem cases (unavailable stock, blocked order, missing value, stale source, unmatched item). The latest run produced 2 approvals, 2 staff reviews and 3 data reviews. AutoActions preserves 30 results because tests were repeated. Seven was the team's testing choice.

## Routing decisions are not diagnostic markers

1. Worst friction: correction/remake/recheck loop.
2. Rules-based automation candidate: D2.
3. Human-judgment candidate: D3, informed by staff assessment.

Status: scenario inactive. Routing checks and a review fallback are tested in Make. Live kitchen data, duplicate protection and review closure remain future work. The freshness limit is illustrative. All test data is synthetic; nothing has been submitted.

Basis: the team's annotated Order and Payment process map and control definitions; `W06_Lab2_Automate_StudyNote_v1.pdf` §§3-4; original, guarded-v2 and three-outcomes-v3 live Make tests (6 October 2026).
