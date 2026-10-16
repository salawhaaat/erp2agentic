---
title: Week 4 - RPA, the Tactical Integration Layer
type: week-summary
tags: [week-summary, week4, module2, rpa]
description: Catch-up summary of Week 4 (Sep 25): what RPA is, the three candidate tests, attended vs unattended, bot economics, and the Thermo Fisher and Bailey Hydraulics cases.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w4/W04_RPA_StudyNote.md
  - id: slides
    resource: raw/data/markdown/course-weeks/w4/W04_RPA_LN_Slides_v1.md
---
# Week 4: RPA, the Tactical Integration Layer

Module 2, The Automation Ladder, Friday Sep 25, 2026. Readings: [[W04_RPA_StudyNote|study note]], [[W04_RPA_LN_Slides_v1|slides]]. Previous: [[Week-3-Lab-1-Diagnose-and-Map]]. Next: [[Week-5-Scaling-RPA-and-CoE]]. Capstone output: [[RPA-Candidate-Scan-Sweetgreen]].

## The one-paragraph version

RPA is software that operates existing applications through their user interface, "working the screens, not the plumbing". That is both its appeal (it bridges systems never integrated, fast and cheap) and its weakness (it breaks when a screen changes). This week is still diagnosis: you scan the Lab 1 map for steps worth automating. The build comes in Lab 2.

## Key points

- **Three ways to take a human out of the loop:** traditional back-end automation (plumbing, via APIs), RPA (surface, via screens), and AI (judgment). See [[RPA vs Traditional Automation vs AI]].
- **Process mindset first.** Ask whether the step should exist at all, then automate the stable, rules-based residue. RPA is the "then automate" half of [[Obliterate Then Automate]].
- **Three tests for a candidate** ([[RPA Candidate Criteria]]): repetitive, rules-based, stable.
- **Attended vs unattended.** Attended bots run beside a person who stays ready to take over. Unattended bots run alone on a schedule or queue. "Rules-based" does not mean "no human needed": a bot follows a wrong rule with full confidence.
- **Economics.** A bot turns a variable labour cost into a near-zero marginal cost. Example: 3 minutes times 500 per day is 25 hours a day, 3 to 4 people. That is also a person's hours, so "redeployed to higher-value work" is sometimes real and sometimes a convenient story.
- **Where the repetitive work comes from:** the batch-push planning layer (MRP, S&OP). The overnight run throws off exceptions that people firefight each morning. RPA makes that cheaper without changing the rhythm.
- **Market (Deloitte 2022, 479 executives):** about 74% already run RPA, about 31 to 32% cost reduction, payback of roughly 16 to 22 months. Top scaling barriers are process fragmentation, vision, IT readiness, and resistance to change, none of them technology.

## Cases

- **[[Thermo Fisher Scientific]].** Reps were the integration between nine screens. RPA plus OCR took over order entry and routed ambiguous exceptions to a human. Call hold times fell about 27% (Customer) and cash flow accelerated (Cash).
- **[[Bailey Hydraulics]].** NetSuite's native integration cut the financial close from 20 days to 3. Plumbing removed "move data between screens" work before any bot was needed. Check what integration already owns before pointing a bot at a seam.

## Why it matters later

The brittleness warning returns in Week 5 as the first reason programmes stall. The deliverable is the RPA-candidate scan, which Lab 2 builds.
