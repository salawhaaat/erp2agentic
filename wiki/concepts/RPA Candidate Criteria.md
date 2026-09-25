---
title: RPA Candidate Criteria
type: concept
tags: [concept]
---

# RPA Candidate Criteria

The three tests a step must pass to be worth automating with a bot (Robotic Process Automation): **repetitive** (high, recurring volume, so a bot's fixed cost is spread across enough transactions), **rules-based** (every case decided by explicit, complete logic, no point where a human must exercise judgment), and **stable** (the process and the screens it runs on rarely change, since RPA drives screens and breaks when they move). A step must pass all three, or it is not a candidate — it routes instead to a [[Decision Point|judgment decision point]] (AI target) or back to redesign ([[Obliterate Then Automate]]).

**Introduced:** [[W04_RPA_StudyNote|Week 4 study note]], "Three Tests for a Good Candidate."

**Anchored exemplars from the readings:** [[Thermo Fisher Scientific]]'s order-entry automation (millions of repetitive, rules-based transactions a year) vs. [[Bailey Hydraulics]], where native NetSuite integration removed the "move data between screens" task before any bot was needed — see [[W04_RPA_StudyNote]]'s case sections, and [[RPA vs Traditional Automation vs AI]] for the full three-way comparison this test set is built on.

**Applied in this capstone:**
- [[RPA-Candidate-Scan-Sweetgreen|RPA-candidate scan (Sweetgreen)]] — the full three-test walkthrough across the Lab 1 map. D2 (feasibility/freshness check) passes all three and is the Lab 2 target. D1, the quality gate at `K` (see [[Control Point]] for why it stayed a routing decision, not a new control point), and the stock-accuracy root cause each fail at least one test and are rejected with reasons.
- [[Lab1-Process-Map-Sweetgreen|Lab 1 process map]] — the stable-rules [[Decision Point]] (D2) this filter selects is the same one marked as diagnostic point ② in Lab 1, before the criteria had a name.

**Why it matters for the capstone:** Board Memo §4 is, structurally, this filter run against your company's process map and written up — two or three real candidates, plus an honest account of what was rejected and why.
