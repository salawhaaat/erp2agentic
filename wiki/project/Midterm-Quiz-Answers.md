---
title: Midterm Quiz Answers (Quizz 1)
type: deliverable
tags: [deliverable, quiz, midterm, sweetgreen]
description: The three Quizz 1 (Mid Term) questions with the answers submitted, written as short paragraphs.
sources:
  - id: w2
    resource: raw/data/markdown/course-weeks/w2/W02_FailureToLeverage_StudyNote_v6.md
  - id: w5
    resource: raw/data/markdown/course-weeks/w5/W05_ScalingRPA_CoE_StudyNote_v2.md
---
# Midterm Quiz Answers (Quizz 1)

IE-GY 9113B, due Oct 14, 2026, 11:59 PM. Related: [[Leverage Gap]], [[Obliterate Then Automate]], [[RPA Candidate Criteria]], [[RPA-Candidate-Scan-Sweetgreen]], [[Lab2-Automation-Sweetgreen]].

## Question 1

**Distinguish failure to leverage from implementation failure, and explain why automating a broken process makes things worse. Name the principle that fixes it and what it requires you to do first.**

An implementation failure means the system does not work, for example it crashes or never goes live. A failure to leverage means the system works, but the business gets no value because the process behind it was never fixed. Automating a broken process makes things worse, since it just runs the same bad steps faster and locks the problem in. The fix is "obliterate, then automate." It requires us to redesign the process first, where value is created or lost, and only then automate what is left.

## Question 2

**Give the three criteria that make a step a good RPA candidate, then describe one step from your own project that looks automatable but fails one criterion, and say which.**

A good RPA candidate is repetitive, rules-based, and stable. In our Sweetgreen project, D3 (choosing a recovery option for a blocked order) looks automatable because it happens often and uses structured data. However, it fails the rules-based test, since staff must judge customer urgency and wait time, and the customer must agree to the change. D2, the availability check, passes all three, so we automated that one in Lab 2.

## Question 3

**RPA works but doesn't scale. Explain one reason it stalls as it grows and what a Center of Excellence does about it; then, from your Lab 2 automation, name one failure mode and the human-oversight control it implies.**

RPA stalls because bots are brittle. When a screen changes the bot breaks, and with hundreds of bots, fixing them takes more time than building new ones. A Center of Excellence fixes this by owning the standards, tracking every bot, and handling maintenance. In Lab 2, the failure mode was bad or stale input data, because our first rule approved four problem orders. The control it implies is human review: staff review for operational problems and data review for bad inputs, plus an audit log of every decision.
