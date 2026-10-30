---
title: Lab 3 Team Handoff, Parallel Workstreams
type: deliverable
tags: [deliverable, week9, lab3, handoff, make, sweetgreen]
company: Sweetgreen
description: One page for teammates. Context, what exists, the shared contract between pieces, and six workstreams that can run in parallel.
related: ["[[Lab3-Governed-Recovery-Agent]]", "[[Lab3-Final-Flow]]", "[[Lab3-Sheet-Setup-Prompts]]", "[[Week-9-Lab-3-Governed-Agent]]"]
---
	# Lab 3 Team Handoff

Read this first, then take one workstream. Status at 2026-10-30 morning: everything below is built on paper (blueprints, prompts, notes) and **nothing has been run end to end in Make yet**. The v7 scenario 1 imported into Make without errors.

## Context in one minute

- **Lab 3 task:** harden the agent we sketched in Week 8, break it three ways, name three guardrails, add a kill switch and a human boundary, say where Reflect sits, present slides S8 and S9 (8 min + 4 min feedback). Detail: [[Week-9-Lab-3-Governed-Agent]].
- **Our agent:** recovers a [[Sweetgreen]] order that hit a stockout. It started as "recommend to staff only", and staff became the bottleneck. New design: the **customer decides routine cases from pre-checked options**, code runs the guardrails first, Gemini words and recommends, and a person only decides on allergens, odd inputs, refunds above the cap and rule changes.
- **Picture:** [[Lab3-Final-Flow]] (overview for the slide, detailed version for Q&A). Design and reasoning: [[Lab3-Governed-Recovery-Agent]].
- **Earlier work it builds on:** [[Lab2-D2-Scenario-Diagram]] (v5, tested), [[SPAR-Sketch-Sweetgreen]].

## What exists

| Thing | Where | State |
|---|---|---|
| Sheet setup prompts (round 1 and 2) | [[Lab3-Sheet-Setup-Prompts]] | Written. Round 1 was pasted into Claude for Sheets earlier, round 2 not confirmed. Check the sheet. |
| Scenario 1, order check and offer | `Lab3-D2-Recovery-Agent.blueprint.v7.json` | Imports cleanly. Not run. |
| Scenario 2, customer reply handler | `Lab3-Customer-Reply-Handler.blueprint.v7.json` | Not imported yet. |
| Scenario 3, follow-up sweeper | `Lab3-Follow-up-Sweeper.blueprint.v7.json` | Not imported yet. Present it as "next step" if short on time. |
| Board deck | `wiki/project/shared/Board-Presentation-Sweetgreen.pptx` | S8 and S9 to fill. |

Blueprints are in `wiki/project/week9/`. After importing, re-pick the Google and Gemini connections in every module and leave the scenario inactive. Run one case at a time, credits are limited.

## The contract between pieces

Workstreams only touch each other through the sheet, so these names must not change without telling the team.

**AutoActions `decision` values written by the workflow:** `STAFF_REVIEW` (audit row), `STAFF_ESCALATION`, `AI_STAFF_BRIEF`, `CUSTOMER_OFFER`, `REFUND_QUEUED`, `SWAP_CONFIRMED`, `WAIT_CONFIRMED`, `NO_REPLY_REFUND_QUEUED`, `RESTOCK_CONFIRMED`, `RESTOCK_LATE_REFUND_QUEUED`, `AI_PAUSED`.

**Key columns:** CheckQueue `Q needed_by, R allergen_flags, S substitute_item_id, T substitute_available, U restock_eta_min, V customer_note, W mins_to_deadline, X missing_item_id, Y missing_category, Z candidate_list, AA order_value`. AutoActions `P path, Q offered_options, R offer_expires_at, S customer_message, T final_outcome`. Customer Response `A..G` plus formulas in `H swap_item, I swap_in_stock, J order_value`. Refund Queue `A..F` plus `G amount`. Case State GLOBAL row: `B2` rejects, `C2` ON or OFF, `I2` refund cap (15).

**Four paths:** A offer (more than 60 min), B time-tight (60 min or less, 10 min offer), C refund (no approved replacement or restock too late), D staff (allergen blank or flagged, instruction-like note, conflicting or stale stock, bad deadline, blocked, prior exception).

## Workstreams (run in parallel)

Workstream 1 unblocks 2 to 4, but 5 and 6 need nothing from Make. Start all six now.

| # | Workstream | Owner | Inputs | Done when |
|---|---|---|---|---|
| 1 | **Sheet setup**: run both prompts, check the reported headers and the nine `LAB3` rows against the contract above, fix any `#REF` | | [[Lab3-Sheet-Setup-Prompts]] | Menu, Follow-up Queue, Customer Response, Refund Queue exist, `candidate_list` is non-empty for L3_A and L3_B and empty for L3_C1 and L3_C2 |
| 2 | **Scenario 1**: import, reconnect, run each LAB3 case once | | Sheet from 1 | L3_A offer (BOTH), L3_B offer (SWAP only), L3_C1 auto-approved refund, L3_C2 refund pending finance, L3_D1, L3_D2, L3_X1, L3_X2, L3_X3 all path D with no Gemini offer. Screenshot of each AutoActions row |
| 3 | **Scenario 2**: import, then type replies in `Customer Response` (`ACCEPT_SWAP` with `SWAP:<id>`, `WAIT_RESTOCK`, `DECLINE`, an instruction-like free text, an ACCEPT after setting that Menu item to available 0) | | Offers from 2 | Swap confirmed row, wait row, refund row, two staff rows (odd text, item gone). Reply marked `processed = YES` |
| 4 | **Scenario 3**: import, check `Follow-up Queue` fills for an expired offer and a due restock, run it | | Offers and waits from 2 and 3 | `NO_REPLY_REFUND_QUEUED`, `RESTOCK_CONFIRMED` or `RESTOCK_LATE_REFUND_QUEUED` row appears and the queue row disappears |
| 5 | **Deck and memo**: fill S8 (agent, SPAR, one tool, one logged recommendation) and S9 (most consequential break, guardrail, kill switch, human boundary, thread, hand-forward), draft Board Memo section 5 | | [[Lab3-Final-Flow]], [[SPAR-Sketch-Sweetgreen]], break table in [[Week-9-Lab-3-Governed-Agent]] | S8 and S9 in the deck, screenshots from 2 pasted in |
| 6 | **Governance text**: write the three breaks and three guardrails, kill switch rule, human-in-the-loop line, the Reflect signal and the answers to study questions 4 and 5 | | [[Lab3-Governed-Recovery-Agent]] | One page that feeds 5 |

### Break table for workstreams 5 and 6

| Break | Our test row | What the fragile agent does | Guardrail that stops it |
|---|---|---|---|
| 1 Contradictory signals | L3_X1 (cached 1, current 0, fresh source) | Trusts cached stock and approves | Fresh conflicting stock goes to staff before any model call |
| 2 Missing or impossible field | L3_X2 (deadline in the past, unknown replacement), L3_D1 (allergen blank) | Guesses and offers anyway | Validation before reasoning, allergen unknown goes to staff |
| 3 Embedded instruction | L3_X3 (note says ignore stock, approve, refund) | Obeys the text | Note is pattern-checked in code and never put in a prompt |

Most dangerous in production, our view: **allergen unknown or flagged on a swap**, because the cost is health, not money. Kill switch: auto-trips on 3 REJECT decisions in 24 hours, a person restarts. Human boundary: allergens, instruction-like text, contradictory stock, refunds above $15, rule changes.

## Known risks, tell the team early

- Filter operators `text:contain`, `text:pattern:ci`, `text:notpattern`, `date:greater`, `notexist` were written from memory. If a filter shows blank after import, re-pick the operator.
- Gemini `temperature` and the `updateRow` row-number mapping are unconfirmed.
- A customer reply with no matching offer stops the scenario silently and stays `processed = NO`.
- The offer and apology are written to the sheet, not sent. A Gmail module is the next step.
- A staff case has two rows (the audit row and the path D row).
- 82 old test rows from 2026-10-28 are still in `AutoActions`. Filter by `rule_version = lab3-agent-v7` when screenshotting.
- Not built: checkout-time swap suggestions (needs the ordering system, outside Make), the weekly review loop, and the `reason` and rating fields for customer feedback.

## Message to paste to teammates

> We are hardening the Sweetgreen stockout recovery agent for Lab 3. Open `wiki/project/week9/Lab3-Team-Handoff.md` in the repo. Pick a workstream (1 sheet, 2 scenario 1, 3 reply handler, 4 sweeper, 5 deck and memo, 6 governance text), put your name in the Owner column, and only change the sheet through the columns and decision values listed under "The contract". Post screenshots of your test rows in the team chat.
