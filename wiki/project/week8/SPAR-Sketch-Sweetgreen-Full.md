---
title: Week 8 Full Draft - SPAR Sketch for the D3 Recovery Agent (Sweetgreen)
type: deliverable
tags: [deliverable, week8, spar, agent-design, sweetgreen, breakout]
company: Sweetgreen
due: Week 8 breakout (Fri Oct 23, 2026), finish tonight; walk into Lab 3 with it
feeds: ["Board Memo §5 - Agent Design and Governance", "Storyboard S8", "Lab 3 build"]
description: Two-sprint SPAR / A.G.E.N.T. sketch of the agent that takes Sweetgreen's D3 judgment step, with where Reflect sits and the stopping rule.
sources:
  - id: slides
    resource: raw/data/markdown/course-weeks/w8/W08_SPAR_LN_Slides.md
  - id: scan
    resource: wiki/project/week4/RPA-Candidate-Scan-Sweetgreen.md
---
# Week 8 Full Draft: SPAR Sketch for the D3 Recovery Agent

Long version kept as the Board Memo §5 source. The in-class breakout version is [[SPAR-Sketch-Sweetgreen]].

Draft for the breakout. Format follows the slides: Sprint 1 defines the agent through Act (A, G, E), Sprint 2 adds the govern half (N, T) with Reflect and the stopping rule. Framework: [[SPAR Framework]], summary in [[Week-8-SPAR-Agent-Architecture]]. The step comes from Week 7: D3, "which recovery route is agreed?", per [[RPA-Candidate-Scan-Sweetgreen]] and [[Lab1-Process-Map-Sweetgreen]]. D2 stayed rules-based in [[Lab2-Automation-Sweetgreen]]; its STAFF_REVIEW route is this agent's trigger. Entity: [[Sweetgreen]].

> Figures marked *(proposed)* are design choices to defend, not measured values. The $44 / 6 of 30 exposure is from the synthetic Lab 1 sandbox.

## Sprint 1: Define the agent (A, G, E)

**Output: one paragraph, goal, what it senses, what it decides, what it acts on.**

> The D3 Recovery Agent recommends, and never decides, how Sweetgreen resolves a digital order that hit an availability exception: substitute, partial change, cancel, or hold for the kitchen. It senses one exception case at a time (the order, the unavailable line, live availability, prep ETA, queue depth, customer urgency, dietary flags, prior exceptions, and the customer's stated constraints). It plans by weighing customer urgency against feasible prep ETA, queue impact and the customer's constraints, and returns a ranked recommendation with a one-line reason and the rejected option. It acts by writing that recommendation to the review sheet for the shift lead and drafting (not sending) the customer message. The customer's consent and the final call stay human.

| A.G.E.N.T. | Our agent |
|---|---|
| **A**gent identity | Goal: propose the recovery route for one exception order inside the pickup promise. Role: recovery advisor to the shift lead. Scope: only orders D2 routed to STAFF_REVIEW. Out of scope: allergy safety, refunds, payment, anything outside the exception queue. |
| **G**ear & brain | Model: Gemini via NYU, low temperature so the same case decides the same way twice. Two tools only: (1) read the exception row, (2) write a recommendation row. Draft-message text is a field of that row, not a send tool. Builder: Make, for continuity with Lab 2 (to be confirmed against the options in the slides). |
| **E**xecution & workflow | Trigger: a new STAFF_REVIEW row from the D2 scenario. Sense: read the row. Plan: weigh urgency, ETA, queue, constraints; pick a route. Act: record pick, reason, rejected option, and draft message; or escalate. |

**What it must not touch:** no silent substitution, no inference of allergy safety, no discounts or refunds issued, no customer-facing send, no write to the order system. Read-only on the order data, append-only on its own sheet. This matches the boundary already in the Lab 1 map: an agent can support the staff decision, it can't make the customer's choice.

**Why an agent and not a rule:** two reasonable staff could offer different resolutions to the same customer. Each added rule (a substitution table, a discount ladder) gives a longer, more brittle rulebook. See [[Decision Point]].

**Autonomy rung:** Level 3 on the *recommendation*, held at Level 1 to 2 on the *customer outcome*. Golden Rule: the simpler, the better. A capable new hire who drafts, a manager who signs.

## Sprint 2: Where Reflect sits, and the stopping rule (N, T)

**Output: where Reflect sits + the kill-switch rule → Board Memo §5.**

| A.G.E.N.T. | Our agent |
|---|---|
| **N**avigation & rules | Weighs three signals a single column can't hold: customer urgency, feasible prep ETA, queue impact, plus the customer's constraints. Logs every call: signals seen, pick, reason, rejected option, timestamp. Inputs whitelisted to the exception row; customer free text is data, never a command. |
| **T**esting & trust | **Reflect:** a daily check of each recommendation against what the shift lead actually did and what happened to the customer (accepted, pickup promise met, goodwill refund issued). Drift signal below. Adversarial testing in Lab 3, about three inputs, about three guardrails from where it breaks. |

**Where Reflect sits.** After the order closes, not after the recommendation is written. The signal is the **override-and-outcome rate on the hard cases**: how often the shift lead overrides the agent, and how often the agreed route still missed the pickup promise or needed a goodwill refund. The easy majority (a clear substitute, plenty of ETA) will look fine either way, so the check is cut by case difficulty (tight margin, dietary flag, high urgency, prior exception). This is the signal Klarna lacked: quality erosion on the nuanced cases, not volume handled. The shift lead sees it on a weekly review row; the ops manager owns the response.

**Most likely Reflect-failure.** The agent drifts to "always offer the cheapest compromise" or "always cancel and refund" because it is the safe, fast answer. That is a rule in disguise, and it would look healthy on volume and cost while repeat-exception customers quietly churn. **Guardrail that catches it:** the hard-case override rate and the repeat-exception rate are reviewed against a baseline; a rising rate flags drift before the customer metric moves.

**Stopping rule** *(thresholds proposed)*:

| Question | Rule |
|---|---|
| When it fires | Immediate escalate-to-human, no recommendation, on: missing or stale field, dietary or allergy flag, close margin between options, or an instruction embedded in customer text. Circuit breaker halts the agent after 3 consecutive overrides, or after repeated failure of a tool call. |
| Who pulls it | Shift lead pulls it per case. Ops manager can switch the agent off for the store. Integration owner can switch it off for the pipeline. |
| Where it applies | The Act step: the recommendation write and draft message. It never reaches the order system, so a stop leaves the live flow untouched and orders fall back to the current manual D3. |

**Governance by SPAR move** (the three study questions applied to us):

| Move | What we govern |
|---|---|
| Sense | Scoped read of the exception row only; stale-source check inherited from D2; no free-form crawling |
| Plan | Reason shown with every pick, with the rejected option and what would make it less reliable; uncertainty is an escalate |
| Act | Two tools; read-only on orders; append-only own sheet; progressive access (draft first, never send); sandboxed on the synthetic sandbox before anything live; every call logged |
| Reflect | Hard-case override and outcome rate, named owner, defined trip point |

## Board Memo §5 seed (one paragraph, tonight)

> Sweetgreen's D3 recovery decision is the one step on the order-to-cash map where a rule runs out. We propose a Level 3 recommender, not a decider: given an exception order routed by the D2 availability check, it weighs customer urgency, prep ETA, queue impact and customer constraints, then records a ranked recommendation and a draft message for the shift lead, using two tools only and with no write access to the order system. The customer's consent stays human. Reflect is a daily comparison of each pick against the shift lead's override and the real outcome (pickup promise kept, goodwill refund), cut by case difficulty, because the failure to fear is quiet decline on the hard cases while volume looks healthy. The stopping rule escalates on any dietary flag, missing field, close margin or embedded instruction, trips a circuit breaker after three consecutive overrides, and can be pulled by the shift lead per case and the ops manager per store. Savings are modelled exposure ($44 across six of thirty synthetic orders), not a guarantee, and we report them alongside where the agent could degrade.

## Open questions for the team

1. Builder choice and justification (Make for continuity vs a dedicated agent builder). The slides want functionality, operating cost, team skills, governance fit and continuity weighed.
2. Is the circuit-breaker threshold of 3 right, and is "3 consecutive overrides" better than a rolling override rate?
3. Do we want a second thread tag (Cash Management via goodwill refunds) or keep the value on Customer, which Module 3 expects?
4. Check wording against the board deck's S8 once the template is open.
