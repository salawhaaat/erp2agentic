---
title: Midterm Quiz Answers (Quizz 1)
type: deliverable
tags: [deliverable, quiz, midterm, sweetgreen]
description: Short keyword answers to the three Quizz 1 (Mid Term) questions, tied to Sweetgreen and Lab 2.
sources:
  - id: w2
    resource: raw/data/markdown/course-weeks/w2/W02_FailureToLeverage_StudyNote_v6.md
  - id: w5
    resource: raw/data/markdown/course-weeks/w5/W05_ScalingRPA_CoE_StudyNote_v2.md
---
# Midterm Quiz Answers (Quizz 1)

Due Oct 14, 2026, 11:59 PM. Concepts: [[Leverage Gap]], [[Obliterate Then Automate]], [[RPA Candidate Criteria]]. Evidence: [[RPA-Candidate-Scan-Sweetgreen]], [[Lab2-Automation-Sweetgreen]].

## Q1. Failure to leverage vs implementation failure; the principle

- **Implementation failure:** the system does not work. It crashes, loses data, or never goes live. Everyone sees it.
- **Failure to leverage:** the system works, but the value never arrives because the process was never redesigned. Quieter and far more common (Gartner: most ERP projects miss business-case goals).
- **Why automating a broken process is worse:** it gives a faster broken process. It locks in bad steps, scales errors, and makes the process harder to change later ("paving the cow path"). Examples: Nike (2000), Birmingham Oracle (2023).
- **Principle:** *Obliterate, then automate* (Hammer).
- **What it requires first:** redesign the process from a blank sheet before automating. Ask whether the step should exist at all. Focus redesign where value is created or destroyed (Four Lenses) and adopt the standard elsewhere.

## Q2. Three RPA criteria; a step that fails one

- **Three criteria:** repetitive (high, recurring volume), rules-based (explicit logic, no judgment), stable (process and screens rarely change). A step must pass all three.
- **My project (Sweetgreen):** D3, choosing the recovery option after an order is blocked. It looks automatable because it recurs and uses structured order data.
- **Fails:** *rules-based*. Staff weigh customer urgency, ETA and queue impact, and the customer must give consent (CP3). That is human judgment, so D3 is an AI or human target, not RPA.
- **Contrast:** D2, the availability check, passes all three and became the Lab 2 automation.

## Q3. Why RPA stalls at scale; CoE; Lab 2 failure mode

- **Why it stalls:** bots are brittle. A screen or system changes and the bot breaks. At hundreds of bots, maintenance grows faster than new work (also bot sprawl: unowned shadow automations).
- **What a Center of Excellence does:** one central team owns standards, bot ownership and registry, monitoring, maintenance, and governance, so bots stay alive and nobody builds shadow bots.
- **Lab 2 failure mode:** bad or stale input data. The first rule approved four problem orders (unavailable stock, blocked, stale source, unmatched item) and silently dropped one (missing availability value).
- **Human-oversight control it implies:** a review queue instead of auto-approve. Staff review (shift lead holds the order at CP2) and data review (integration owner repairs input), plus a 0 to 60 minute source-freshness check and an audit log. Humans keep D3 and consent (CP3).
