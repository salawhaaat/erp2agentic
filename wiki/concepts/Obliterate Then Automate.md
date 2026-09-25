---
title: Obliterate Then Automate
type: concept
tags: [concept]
---

# Obliterate Then Automate

Hammer's (1990) cure for the [[Leverage Gap]]: redesign the work from a blank sheet before you automate it, rather than automating the process you already have. Automating a broken process "paves the cow path" — pours concrete over a route that wandered, making it a permanent, efficient way to go nowhere sensible. "Obliterate" is not "redesign everything": concentrate total redesign where value is created or destroyed, and adopt the standard elsewhere.

**Introduced:** [[W02_FailureToLeverage_StudyNote_v6|Week 2]] / [[W2_FailureToLeverage_Lecure Notes_v9|Week 2 lecture notes]] — the cure demonstrated against Nike's ~$100M supply-chain meltdown (2000) and Birmingham's Oracle go-live failure (2023), both of which automated before they obliterated.

**Extended in:** [[W04_RPA_StudyNote|Week 4 study note]], "First Decide the Step Should Exist: The Process Mindset" — the task mindset (bolt a bot onto a tedious step) vs. the process mindset (ask what the whole flow is for, redesign first, then automate the stable, rules-based residue). RPA is explicitly framed as the "then automate" half of this sequence, never a substitute for the "obliterate" half.

**Applied in:**
- [[RPA-Candidate-Scan-Sweetgreen|RPA-candidate scan (Sweetgreen)]] — the stock-accuracy root cause behind the live/cache availability mismatch is rejected as an RPA candidate precisely because it is a redesign job (close the sync gap), not a bot-shaped problem; automating around it would pave the cow path.

**Why it matters for the capstone:** it's the discipline that stops a scan from recommending a bot for every repetitive-looking step. Every "not this — redesign first" line in [[RPA Candidate Criteria|an RPA-candidate scan]] is this principle in action.
