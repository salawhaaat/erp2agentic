---
title: SPAR Framework
type: concept
tags: [concept, agents, week8]
description: Bornet's Sense, Plan, Act, Reflect loop for AI agents, the three keystones beneath it, and the governance question at each move.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w8/W08_SPAR_StudyNote_v1.md
---
# SPAR Framework

Bornet et al. (2025, Ch. 2): an AI agent runs **Sense, Plan, Act, Reflect** as a continuous loop, not a checklist. Reflect feeds the next Sense. Defined in Week 8 ([[Week-8-SPAR-Agent-Architecture]]); previewed in [[Week-7-RPA-to-Intelligent-Automation]].

| Move | What it does | Keystone | Governance question |
|---|---|---|---|
| Sense | Gathers data, detects triggers, holds working context | none (leans on Memory, the context window) | What can it see, and is the input clean? |
| Plan | Weighs options, chooses a course | Reasoning (Ch. 6) | How far may it decide before a human sees it? |
| Act | Executes through tools and APIs, monitors | Action (Ch. 5) | What may it touch, and who can stop it? |
| Reflect | Evaluates outcome against intent, adapts | Memory (Ch. 7) | Did it catch its own error, or just store it? |

- **Reflect fails first.** It is invisible until missing, so it gets cut. An agent without it drifts quietly on the hard cases and gets wronger faster at scale. Klarna is the course example.
- **Storage is not reflection.** A log records what happened. The feedback loop compares it to what was intended.
- **A.G.E.N.T.** (Agent identity, Gear & brain, Execution & workflow, Navigation & rules, Testing & trust) is the design checklist that organises what you write down for a SPAR sketch.
- Related: [[Decision Point]] (the judgment kind is the agent's target), [[Three Threads]] (Customer leads Module 3).
