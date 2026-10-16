---
title: Week 6 - Lab 2 Automate the Repeatable Part
type: week-summary
tags: [week-summary, week6, lab2, module2]
description: Catch-up summary of Lab 2 (Oct 9): build a Make automation at home, break it on a seeded flaw, name the oversight, and present with ROI.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w6/W06_Lab2_Automate_StudyNote_v1.md
  - id: slides
    resource: raw/data/markdown/course-weeks/w6/W06_Lab2_Automate_LN_Slides_v1.md
---
# Week 6: Lab 2, Automate the Repeatable Part

Module 2 lab, Friday Oct 9, 2026, 8:00 to 10:30. Readings: [[W06_Lab2_Automate_StudyNote_v1|study note]], [[W06_Lab2_Automate_LN_Slides_v1|slides]]. Previous: [[Week-5-Scaling-RPA-and-CoE]]. Capstone output: [[Lab2-Automation-Sweetgreen]].

## The one-paragraph version

You stop diagnosing and build. You automate the stable-rules decision point from Lab 1, then **break it on purpose** using the flaws you seeded. The honest map of where a rules-based bot needs a human is the point, not a working demo. Lab 2 completes Milestone 1 and carries you from Board Memo §3 into §4.

## How it ran

- **Build at home, refine in class.** Lab 1's in-class build was rushed, so the first pass moved to pre-work. Arriving with nothing is the one thing you can't do. If stuck, bring the specific error and a sketch of candidate, trigger, rule, and mappings.
- **Gate at the door:** a built (or attempted) Make scenario, and the board deck current through S5.
- **Session:** gate check, industry guest, work block (refine, break, harden, ROI), then a 7-minute show and 3-minute feedback with a guest on the board.

## The build

Shape is always **trigger, condition, action**, connecting at least two systems:
1. Read System 1 (your Lab 1 sandbox in Sheets or Airtable).
2. Router or Filter encoding your exact rule, with every case decided.
3. Write System 2 (Gmail, Slack, or a second sheet).

Make free-tier notes: about 1,000 credits a month, 2 active scenarios, scheduled trigger at most every 15 minutes (use "Run once"). Create the Connection first, since half of first-build snags are there. Stack-flexible: AWS Step Functions plus EventBridge or a custom stack is fine by approval.

## Presentation (7 minutes)

| Part | Time |
|---|---|
| S3 to S5, story so far | about 2 min |
| S6, the automation (happy path) | about 1.5 min |
| S7, where it broke and the oversight it implies | about 2 min |
| S7, ROI and thread | about 1.5 min |

## The lesson

**The break is a governance finding, not a bug.** Every edge case the bot shipped confidently is a place a human belongs. That edge case is the judgment step that becomes the Lab 3 agent. Ethics thread: what do the limits of rules say, and what do we risk removing the human at scale?

## Deliverables and logistics

- Post to the team workspace that day: a screenshot of the working workflow plus a one-page post-mortem (what you built, where it broke, oversight, simple ROI).
- **Quiz 1** (Modules 1 and 2): applied, open materials, about 45 to 60 min, then a 15-minute 1:1 booked within 10 days of submitting. See [[Midterm-Quiz-Answers]].
- Next: Module 3, Week 7, From RPA to Intelligent Automation.
