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

An implementation failure is when the system simply does not work. It crashes, loses data, or never goes live, so everyone can see it. A failure to leverage is different, because the system works fine but the business still gets no value from it. This usually happens because the process behind it was never fixed, and it is the more common problem. Automating a broken process makes things worse since the software only runs the same bad steps faster and at bigger scale, which locks the problem in. Nike in 2000 and Birmingham's Oracle go-live in 2023 both made this mistake. The principle that fixes it is "obliterate, then automate." It requires us to redesign the process first, starting from a blank sheet and asking whether each step should exist at all. We focus that redesign where value is created or lost, and only then do we automate what is left.

## Question 2

**Give the three criteria that make a step a good RPA candidate, then describe one step from your own project that looks automatable but fails one criterion, and say which.**

A good RPA candidate must be repetitive, rules-based, and stable. Repetitive means it happens often enough to pay back the cost of building a bot. Rules-based means clear logic decides every case, with no need for judgment. Stable means the process and screens rarely change, because a bot breaks when they do. In our Sweetgreen project, D3 (choosing a recovery option when an order is blocked) looks automatable at first, since it happens often and uses structured order data. However, it fails the rules-based test. Staff have to weigh customer urgency, the new wait time, and queue impact, and the customer must also agree to the change. That takes human judgment, so D3 is not an RPA step. By contrast, D2, the availability check, passes all three tests, which is why we automated it in Lab 2.

## Question 3

**RPA works but doesn't scale. Explain one reason it stalls as it grows and what a Center of Excellence does about it; then, from your Lab 2 automation, name one failure mode and the human-oversight control it implies.**

RPA stalls mainly because bots are brittle. When a screen or system changes, the bot breaks, and once a company has hundreds of bots, fixing them takes more time than building new ones. Bots that nobody owns make this even worse. A Center of Excellence deals with this by acting as one central team that sets standards, owns and tracks every bot, monitors them, and handles maintenance. As a result, bots stay healthy and nobody builds hidden ones. In our Lab 2 automation, the clearest failure mode was bad or stale input data. Our first rule approved four problem orders and silently dropped one with a missing availability value. Because of this, the control we need is human review instead of automatic approval. Orders with an operational problem go to staff review, where the shift lead holds the order, and orders with a data problem go to data review, where the integration owner fixes the input. We also added a freshness check and an audit log, so people can always see what the bot decided and why.
