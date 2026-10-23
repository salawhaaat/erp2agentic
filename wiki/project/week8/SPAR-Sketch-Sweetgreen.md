---
title: Week 8 Breakout - SPAR Sketch for the D3 Recovery Agent (Sweetgreen)
type: deliverable
tags: [deliverable, week8, spar, agent-design, sweetgreen, breakout]
company: Sweetgreen
due: Week 8 breakout (Fri Oct 23, 2026), finish tonight; walk into Lab 3 with it
feeds: ["Board Memo §5 - Agent Design and Governance", "Storyboard S8", "Lab 3 build"]
description: Short breakout version of the SPAR sketch for the D3 recovery agent: agent definition, Reflect, and stopping rule.
sources:
  - id: slides
    resource: raw/data/markdown/course-weeks/w8/W08_SPAR_LN_Slides.md
  - id: scan
    resource: wiki/project/week4/RPA-Candidate-Scan-Sweetgreen.md
---
# Week 8 Breakout: SPAR Sketch for the D3 Recovery Agent

Short version for the breakout. Full draft and Board Memo §5 seed: [[SPAR-Sketch-Sweetgreen-Full]]. Framework: [[SPAR Framework]]. The step is D3 from [[RPA-Candidate-Scan-Sweetgreen]]; its trigger is the STAFF_REVIEW route from [[Lab2-Automation-Sweetgreen]]. Entity: [[Sweetgreen]]. Figures marked *(proposed)* are design choices, not measurements.

## Sprint 1: Define the agent

* **Agent:** Recommends, never decides, how to fix a Sweetgreen order that hit a stockout (swap, partial change, cancel, or hold). Advisor to the shift lead, only for orders Lab 2 flagged for staff review.
* **Sense / Plan / Act:** Reads one order row. Weighs urgency against prep time, queue and customer constraints. Writes a ranked pick with a one-line reason and the rejected option, and drafts the customer message without sending it.
* **Tools:** Two only: read the order row, write a recommendation row. Gemini at low temperature. Builder: Make. Two narrow tools keep the agent read-only on the live order system, so the worst it can do is write a bad recommendation that a person can see and override.
* **Must not touch:** the order system (read-only), customer messages (draft only), refunds, and allergy decisions (human only).

## Sprint 2: Reflect and stopping rule

* **Reflect:** Daily check of each pick against the shift lead's override and the outcome (pickup promise kept, goodwill refund), split by case difficulty. The failure to watch for is a drift to "always cheapest" or "always cancel."
* **Stop:** Hands off to a person on a missing or stale field, a diet flag, a close call, or instructions in the customer's text. A circuit breaker trips after 3 overrides in a row *(proposed)*, plus a rolling override rate on hard cases as the slow drift signal. The shift lead pulls it per case and the ops manager per store.

## Decided

* **Builder:** Make. Alternatives noted: Zapier Central (bigger ecosystem, not needed) and Flowise (self-hosted, needs setup and possibly faculty approval).
* **Breaker:** Two ways to switch the agent off. Fast: three overrides in a row by the shift lead, because something is clearly broken. Slow: the share of hard cases the shift lead overrides keeps creeping up over the days, because the agent is quietly getting worse. Exact numbers set in Lab 3.
* **Value tag:** Customer primary, Cash Management secondary through fewer goodwill refunds. Savings stay modelled exposure.

## Board Memo §5: Agent Design and Governance

Sweetgreen's D3 recovery decision is the one step on the order-to-cash map where a rule runs out, so we propose a recommender, not a decider. For an order the availability check flags, the agent weighs customer urgency, prep time, queue impact and the customer's constraints, then writes a ranked pick, a one-line reason and a draft message for the shift lead. It has two tools, read the order row and write a recommendation row, and we would build it in Make for continuity with Lab 2. It cannot send messages, issue refunds or write to the order system, and the customer's consent stays human.

Each day we compare every pick with the shift lead's override and the outcome, split by case difficulty, to catch a quiet drift toward "always cheapest" or "always cancel." The agent escalates on a diet flag, missing field, close call or embedded instruction. Two signals stop it: a circuit breaker after three overrides in a row for sudden failure, and a rolling override rate on hard cases for slow drift. The shift lead can pull it per case and the ops manager per store.

The value lands mainly on Customers, with a secondary effect on Cash Management through fewer goodwill refunds. Savings are modelled exposure ($44 across six of thirty synthetic orders), not a promise.
