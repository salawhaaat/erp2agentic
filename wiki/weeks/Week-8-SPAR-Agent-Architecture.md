---
title: Week 8 - AI Agent Architecture, the SPAR Framework
type: week-summary
tags: [week-summary, week8, module3, agents, spar]
description: Catch-up summary of Week 8 (Oct 23): the SPAR loop, the three keystones, governance at every move, the Klarna case, and the A.G.E.N.T. sketch for Board Memo S5 / slide S8.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w8/W08_SPAR_StudyNote_v1.md
  - id: lecture-slides
    resource: raw/data/markdown/course-weeks/w8/W08_SPAR_LN_Slides.md
---
# Week 8: AI Agent Architecture, the SPAR Framework

Module 3, Friday Oct 23, 2026. Reading: [[W08_SPAR_StudyNote_v1|study note]], [[W08_SPAR_LN_Slides|lecture slides]]. Previous: [[Week-7-RPA-to-Intelligent-Automation]]. Next: [[Week-9-Lab-3-Governed-Agent]], Lab 3, building a governed agent.

## The one-paragraph version

Last week you named the judgment step a rule can't take. This week is the machine that takes it: an agent is a language model in a loop (see [[SPAR Framework]]), with tools to act and memory to learn from. The week's question is "what is an agent made of, and where must a human stay?" The answer: governance is a question at every move of the loop, and the move most deployments skip is Reflect.

## Key points

- **Autonomy ladder:** Module 2 was Level 1, Week 7 was Level 2, this week is the step onto **Level 3** (agentic workflow). At Level 2 the human owns the plan and the machine owns a step. At Level 3 the machine owns the plan and the human owns the goal and the guardrails.
- **SPAR is a loop, not a list:** Sense, Plan, Act, Reflect, with Reflect feeding the next Sense. Run only the first three moves and you are a script with better vocabulary.
- **Three keystones** (Bornet): Reasoning under Plan (Ch. 6), Action under Act (Ch. 5), Memory under Reflect (Ch. 7). Sense has no keystone of its own and leans on Memory (the context window). Three keystones, four moves: the asymmetry shows where the architecture is thin.
- **Bot vs agent:** a bot (L1 to L2) is deterministic, has no memory, runs a fixed script and breaks on the unexpected. An agent (L3) is non-deterministic, holds context, picks its tool, plans, self-corrects and adapts.
- **Governance at each move,** not a gate at the end:

| Move | Keystone | Governance question | Failure example |
|---|---|---|---|
| Sense | draws on Memory | What can it see, and is the input clean? | Stale field acted on with full confidence; context scrolls out of the window |
| Plan | Reasoning | How far may it decide before a human sees it? | Pharma reroute (>$1M of cargo sent via unlicensed ports); fast crossword answers wrong at the crossings |
| Act | Action | What may it touch, and who can stop it? | Great Wine Incident (~$100K of appreciating wine cleared for turnover); the kill switch lives here |
| Reflect | Memory | Did it catch its own error, or just store it? | Klarna; telecom chatbot amnesia |

- **Act governance stack:** few tools ("precision over power", practical ceiling around six), progressive access (read-only before write), sandbox, log every call, circuit breaker on repeated failure, a defined escalation path to a named human. For integration functions: sandbox against a copy of the backbone first, audit trail of every production call, hard stop on the hardest-to-undo actions (study question 3).
- **Golden Rule:** the simpler, the better. Match autonomy to the risk of the step. Treat the agent as a capable new hire.
- **Human-in-the-loop** (from [[Week-5-Scaling-RPA-and-CoE|Week 5]]) is a structural choice about where judgment stays. **Kill switch:** when it fires, who pulls it, where it applies.
- **Reflect fails first** because Sense, Plan and Act are visible and fundable while Reflect's payoff is a problem that never happened. An unreflective agent does not crash, it drifts: good on the easy majority, quietly worse on the hard minority, same confidence throughout.

## Case: Klarna's customer-service agent (2024 to 2025)

Deployed autonomously while preparing to go public, with staff cut and hiring paused. Company numbers (CX Dive, Nov 2025, Q3 2025 earnings): work of 853+ agents (up from ~700), two-thirds of inquiries, response time down 82%, repeat contacts down a quarter, ~$60M claimed cumulative savings. In May 2025 Klarna turned back toward humans (Bloomberg) and began rehiring a flexible workforce.

The record is nuanced: Klarna reported no satisfaction drop (assistant on par with humans in Q3, NPS 73), but a Forrester analyst called it an over-pivot to cost containment that shed institutional knowledge. Actual customer-service and operations cost still rose, about $42M to $50M year over year. The reading is drawn from the architecture, not a verdict Klarna accepts: Sense, Plan, Act worked, Reflect was thin, and the May reversal was a human supplying the reflection by hand.

Contrast case: a financial-services investment-inquiry agent rebuilt its memory (segmenting, attention tuning, summarising earlier turns) and cut errors about 65%. A manufacturing QC system that remembered defect patterns cut false positives about 40%.

## Design tool: A.G.E.N.T. (Bornet, Ch. 8)

SPAR is what the agent does. A.G.E.N.T. is the checklist you write down.

| Part | You decide | Maps to SPAR |
|---|---|---|
| **A**gent identity | goal, role, scope | the purpose |
| **G**ear & brain | model, platform, the few tools | Act (Action) |
| **E**xecution & workflow | triggers, inputs/outputs, steps | the loop |
| **N**avigation & rules | filtering, decision logic, logging | Plan + governance |
| **T**esting & trust | adversarial testing, feedback, guardrails | Reflect (Memory) |

Worked example (not ours): the Citi Bike dispatch agent. It recommends, not dispatches, which of two stations to service first. One tool (read the conflict rows), low-temperature Gemini. Reflect is an after-shift check of its picks against actual station fill. Likely failure: it picks the emptier-now station and ignores the forecast, "a rule in disguise". Stopping rule: escalate on missing field, close margin or embedded instruction; circuit breaker on repeated failure; ops can pull it.

## Homework and deliverable

One-paragraph SPAR sketch of the Lab 3 agent: goal (the Week 7 judgment step as an objective), the few tools, and above all where Reflect sits plus the stopping rule. It is the architecture half of Board Memo §5 (Agent Design and Governance), slide S8. Proportions matter: a long tool list and a one-line Reflect is a failed deployment on paper. Our draft is [[SPAR-Sketch-Sweetgreen]].

Before Lab 3: research free builders (n8n, Dify, Latenode, Botpress, Flowise, Make, Zapier Central; model is Gemini via NYU), choose and justify one (functionality, cost, team skills, governance fit, continuity from Make in Lab 2), set up the account, attempt a first build and expect it to break. Read the Week 9 note. Forum 2 opened Oct 21.

## Study questions

1. Define SPAR and use Klarna to explain what happens when Reflect is weak or missing.
2. What are the Three Keystones, and why does each bring a distinct governance challenge?
3. If an agent can run integration functions autonomously via Act, what governance must be in place before those tools are activated?

## Handed forward

Multi-agent systems and orchestration failures (Week 10); deepest kill-switch and accountability governance (Week 10 and Module 4).
