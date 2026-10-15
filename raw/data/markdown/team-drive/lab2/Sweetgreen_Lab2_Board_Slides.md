---
title: Sweetgreen Lab 2 Board Slides (S3-S7)
type: team-source
tags: [lab2, sweetgreen, board-presentation, team-drive]
description: Text of the team's Lab 2 board-deck excerpt, slides S3 to S7, with live Make results on S6 and S7.
sources:
  - id: drive-slides
    resource: "Google Drive: IE-GY 9113B Team 4 / Sweetgreen Lab 2 - Final Materials - 2026-10-06 / Sweetgreen_Lab2_Board_Slides.pptx"
---
# Sweetgreen Lab 2 Board Slides (S3-S7)

Text extraction of a teammate's `.pptx` (6 October 2026), read through the Drive connector. Slide visuals and speaker notes are not reproduced; the original `.pptx` was not downloaded (private file). Excerpt in the supplied course template. S3-S5 retain the prior diagnosis; S6-S7 contain observed live Make results.

Title slide: "Reliable kitchen availability before automated order handling", Lab 2 live tests, 6 October 2026.

## S3. Context & backbone (Memo §2)

Order-to-pickup reliability is the primary operations thread. Project scope: order to pickup. Model basis: functional hypothesis. Evidence: synthetic sandbox.
- Order capture and payment establish the accepted specification.
- Kitchen availability determines whether staff can fulfill it.
- Customer recovery updates the order and payment records.
- Working archetype: common process, locally managed exceptions.

The handoff depends on shared order IDs, accepted item details and a trustworthy kitchen availability timestamp. Architecture and operating-model claims require validation with restaurant staff. This is a functional project hypothesis, not a verified description of Sweetgreen's internal applications.

## S4. The strategic problem (Memo §2)

A confirmed order can conflict with kitchen availability.

| Lab 1 sample | Modeled impact | Late readiness |
|---|---|---|
| 6 exceptions / 30 orders | $44 labor + refunds | 18.7 min / exception |

- Cached availability can approve an item the kitchen cannot make.
- Staff must hold the order, contact the customer and repeat checks.
- The pickup promise slips while recovery consumes staff capacity.
- Assembly automation still needs a reliable fulfillment decision.

Board consequence: unresolved data disagreement can erode service reliability and consume the capacity automation is meant to release. Notes: six synthetic exceptions consume 60 modeled recovery minutes at $0.40/minute ($24) plus $20 refunds, total $44; they total 112 late-ready order-minutes, mean 18.7. The sample is seeded, not a population estimate. Waste from partial preparation is not counted because the mapped availability check precedes preparation.

## S5. Backbone diagnosis (Memo §3)

Condensed Lab 1 process with control points and diagnostic markers.
1. Correction / remake loop: worst friction.
2. D2 availability: rules-based target.
3. D3 recovery: human judgment.

Friction chain: availability conflict causes a hold, customer recovery and repeat checks. Late pickup and recovery costs follow. Flow: D1 accepted? (CP1 order spec), D2 feasible? (availability), prepare and quality check, pickup (CP4 complete). On "No": hold (CP2 issue log), D3 recovery (customer choice, CP3 change, consent, recheck D2). Cancel path: CP5 cancellation/payment state and CP6 refund/void record.

## S6. Automation opportunity (Memo §4)

Lab 1 identified D2 availability. Lab 2 builds and tests the automation.
- Tested in Make: positive item match, current availability, source age 0-60 min, NEW status with no exception, staff and data review.
- Remaining: live feed and deduplication.
- First: check every original line against kitchen availability. Now: log every failed approval check for human review.
- Human-led: D3 recovery, consent and customization feasibility.
- The first build writes a recommendation to an audit sheet. Five modules: Search Rows, Router and three audit writers.
- The 60-minute freshness limit is illustrative. Live use needs approved limits and duplicate protection.

Speaker notes carry the full run detail (seven orders H1/H2/B1-B5, run `THREE_OUTCOMES_01`, rule `three-outcomes-v3`, routing logic, 30 log rows across repeated tests, historical failures, ROI assumptions). These match the [[Sweetgreen_Lab2_Postmortem|postmortem]] and [[Sweetgreen_Lab2_Live_Evidence|live evidence]] pages.

## S7. Automation journey (Memo §4)

Lab 2 tests: seven unique orders, two normal and five problem cases.
- Original rule: four false approvals and one silent drop.
- Current run: 2 approvals, 2 staff reviews, 3 data reviews. Seven orders, seven final decisions.
- 30 log rows include repeated tests of the same seven orders.
- Illustrative ROI: $726 baseline minus $616 labor and $24 upkeep = $86/month capacity value. $96 build; 1.12-month payback.
- ROI inputs are unmeasured. Guarded routing passed seven sandbox cases; production controls remain incomplete.
