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
* **Tools:** Two only: read the order row, write a recommendation row. Gemini at low temperature. Builder still open (leaning Make).
* **Never:** Silent substitutions, allergy guesses, refunds, sending messages, or writing to the order system.

## Sprint 2: Reflect and stopping rule

* **Reflect:** Daily check of each pick against the shift lead's override and the outcome (pickup promise kept, goodwill refund), split by case difficulty. The failure to watch for is a drift to "always cheapest" or "always cancel."
* **Stop:** Hands off to a person on a missing or stale field, a diet flag, a close call, or instructions in the customer's text. A circuit breaker trips after 3 overrides in a row *(proposed)*. The shift lead pulls it per case and the ops manager per store.

## Open

1. Builder choice and justification.
2. Is 3 in a row the right breaker, or a rolling rate?
3. Value tag: Customer only, or also Cash Management?
