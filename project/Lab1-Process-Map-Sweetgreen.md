---
title: Lab 1 Process Map — Order and Payment (Sweetgreen)
tags: [deliverable, week3, lab1, process-map, sweetgreen]
company: Sweetgreen
due: Week 3 Lab 1 (Fri Sep 18, 2026)
feeds: ["Board Memo §3 — Integration Backbone Assessment", "Storyboard S5"]
---

# Lab 1 Process Map — Order and Payment (Sweetgreen)

> The in-class BPMN build from [[W3_Lab1_Lecture-Notes|Lab 1]], all four moves: map the real process, mark three diagnostic points, choose a curveball, and generate data last. Applied to [[Lab1-Prework-Sweetgreen|the pre-work reality brief]]'s core thesis: the handoff between digital ordering and kitchen execution. Status: all four moves done, data sandbox built in [[Sweetgreen-Lab1-Sandbox.xlsx]]. Ready for present & share.

## The annotated map

![[Order-and-Payment-Process-Map]]

Full diagram source: [[diagrams/Order-and-Payment-Process-Map]].

## The three diagnostic points

| # | Point | Type | Lens tag | Routes to |
|---|---|---|---|---|
| ① | Hold incorrect meal and identify mismatch (`L`) | Worst friction — the rework loop when the finished meal doesn't match the confirmed order | Quality / Operations & Supply Chain | — |
| ② | Can the order be prepared as specified? (`I`) | Stable-rules decision point — availability/feasibility check against a known ruleset. **Post-curveball caveat:** the input to this check now comes from two sources, a live system and a nightly legacy cache, and they don't always agree (`STALE`) — see below. | Operations & Supply Chain | **Lab 2 (Make)** — automate first, but a freshness gate on the availability input needs to be part of the automation, not just the yes/no rule |
| ③ | Assess feasible options and contact customer (`S`) | Judgment decision point — no clean rule for which substitution/compromise to offer, or when to escalate vs. hold | Customer | **Lab 3 (Relevance AI)** |

## Why this map matches the capstone thesis

This directly operationalizes the throughline from [[Backbone-Context-Note-Sweetgreen]] and [[Context-and-Diagnosis-Brief-Sweetgreen]]: the backbone's weakest point is the handoff between digital ordering and kitchen execution. On this map that handoff is literally the arrow from `G` (send order to kitchen) into `H`/`I` (kitchen review and feasibility check) — and it's exactly where the process forks into the worst-friction rework loop (①) and the judgment-heavy exception path (②→③→`Q`/`S`/`T`/`R`). The rejection/rework path (`Q → S → R` and `M → K` loop) is where — per the lecture notes' anti-pattern warning — "the cost hides"; this map has one, so it reflects the real process rather than the idealized one.

This also lines up with the primary-source evidence gathered in [[research/Sweetgreen-Public-Research|the public research log]]: the CEO's own order-accuracy math (§1) and the two independently-sourced kiosk/ordering-friction incidents (§4, §6) both point at the same seam this map isolates — the point where a digitally-placed order meets kitchen execution capacity and either holds together or doesn't.

## Control points

| ID | Control point | What it records |
|---|---|---|
| CP1 | Confirmed order (`F`) | Order ID, accepted items/customizations, and promise time become the fulfillment reference. |
| CP2 | Fulfillment issue recorded (`Q`) | An exception record, created when an unavailable item, unsupported request, or uncorrectable meal blocks the order. |
| CP3 | Agreed order changes (`X`) | The new specification and customer consent, before kitchen re-entry. |
| CP4 | Order completion (`W`) | Successful collection/completion, against the order ID. |
| CP5 | Cancellation and payment status (`Y`) | Cancellation, and whether payment was captured or only authorized. |
| CP6 | Payment resolution (`Y4`) | The refund or authorization-void outcome, amount, and transaction reference. |

## Routing decisions

| ID | Decision | Type | Notes |
|---|---|---|---|
| D1 | Order accepted? (`E`) | Gate | Routes to confirmed order or notify-customer/end. Payment approval and order-acceptance criteria need to be explicit. |
| D2 | Can the order be prepared as specified? (`I`, our ②) | Stable rules → Lab 2 | Checks ingredient availability and supported customizations. The freshness of the availability input has to be checked too, not just the rule (see curveball below). |
| D3 | Which recovery route is agreed? (`R`, our ③) | Judgment → Lab 3 | Staff assess feasible options and the customer consents; routes to agreed change, cancellation, or hold/escalation. Staff judgment happens in `S`, just before this branch. |

## Curveball — #3: nightly batch, not real time

**Picked:** deck card #3, "a key data source only updates overnight, so decisions are made on yesterday's numbers." Availability data feeding decision ② now comes from two places: a live system, and a nightly legacy cache that only refreshes once a day. They don't always agree.

**Why this one:** an earlier draft of this note picked card #2 (acquisition's/divestiture's parallel data), reframed around the real Sweetgreen-Wonder Infinite Kitchen divestiture. That reasoning is still sound as a description of company-boundary risk and stays useful background (see [[research/Sweetgreen-Public-Research]] §3), but it's **not** the curveball this map and its data sandbox actually model. Building the synthetic sandbox surfaced #3 as the sharper, more tractable fit: a stale nightly cache disagreeing with a live source is a concrete, testable failure that shows up directly in decision ②'s inputs, rather than requiring a change to who owns the kitchen system.

**How it changes decision point ②:** node `I` assumed one clean availability check. The map now has `STALE`, a check right before `I`, asking whether the live system and last night's cached snapshot agree. When they don't, the order gets held (`Q`) for a reason distinct from "unavailable item": a stale-source mismatch that needs a freshness gate, not a menu fix.

**What the data sandbox shows:** [[Sweetgreen-Lab1-Sandbox.xlsx]] seeds 24 menu configurations where the live system shows unavailable (`CurrentAvailable = 0`) but the nightly cache still shows available (`CachedAvailable = 1`), a mismatch on 10 of them. Against 30 synthetic orders, 6 hit the mismatch and enter exception recovery, a 20% rework rate.

## Friction chain and board-level consequence

**Chain:** availability/specification mismatch (Quality / Operations) → hold and manual customer contact (Frustration / Customer + Operations) → agreed changes, correction, and kitchen re-entry (Time / Operations) → later readiness (Customer) → extra labor capacity and refunds (Cost / Cash).

**The number:** 6 of 30 synthetic orders enter exception recovery (20%). They consume 60 extra staff minutes and $20 in goodwill refunds. At an assumed $24/hour loaded labor rate, that's $24 + $20 = **$44** in modeled exposure, or $7.33 per affected order. Combined lateness across those six orders is 112 order-minutes, averaging 18.7 minutes late each.

**A correction, made in the open:** an earlier pass through this sandbox added $28 of discarded partial-prep food waste on top, for a $72 headline. That's wrong for this map: since ② checks availability *before* the kitchen starts preparing, the six seeded stockout cases shouldn't also carry food-waste cost, that would double-count a failure this map's own control flow is designed to prevent. $44 is the map-consistent number. The raw $72 figure is still visible in the sandbox's `Summary` tab (it predates this correction); `Calculations` and this note carry the corrected $44.

**Caveats, stated plainly:** this is a synthetic, illustrative sample, not measured Sweetgreen performance. The causal chain (mismatch → hold → cost) is a working hypothesis the sandbox demonstrates, not something proven against real restaurant data. No company-wide extrapolation is justified from 30 orders at one modeled store.

## What the board could fund

Validate the sources and exception reasons against real restaurant data, then pilot a freshness gate on the availability check at D2 (Lab 2: stable-rules automation) and consistent exception tracking. Next, test an assistant that recommends recovery options at D3 for manager review and customer consent (Lab 3). At D3 specifically: weigh customer urgency, feasible prep ETA, queue impact, and customer constraints/consent; never infer allergy safety or make a silent substitution. An agent can support that staff decision, it can't make the customer's choice.

Potential benefit: fewer missed pickup promises and less avoidable recovery work. $44 is modeled exposure, not a guaranteed saving.

## Where this lands: slide S5 and next week

Per [[W3_Lab1_Lecture-Notes]], what gets presented today is slide S5 (Backbone diagnosis) of the board deck, and the evidence for Board Memo §3. This note is that evidence: the annotated map above, the one-line consequence ("$44 in modeled exposure across 6 of 30 synthetic orders, 18.7 minutes late on average"), and the friction chain feed straight into `IE-GY_9113B_Board_Presentation_Template` slide S5. It's Milestone 1 (Diagnose).

**Next week — RPA.** Bring the Lab 2 target: **D2, "can the order be prepared as specified"**, specifically the freshness gate on its availability input (live vs. nightly cache) exposed by this week's curveball. That's the stable-rules step to automate first, feeding slide S6 and Memo §4.

**Submit by Monday (Google Workspace folder):**

| Deliverable | Status | File |
|---|---|---|
| Sandbox (Airtable/Sheets) | Done | [[Sweetgreen-Lab1-Sandbox.xlsx]] |
| Annotated map (★◆ + rejection path + 3 points + chain) | Done | [[diagrams/Order-and-Payment-Process-Map]], plus the presentation-ready annotated image at `project/diagrams/assets/Order-and-Payment-Process-Map-Annotated.png` |
| One-page diagnosis (chain, consequence, prize) | Done | This note, §"Friction chain and board-level consequence" above |
| Board deck, slide S5 filled in | Done | `project/Board-Presentation-Sweetgreen.pptx` — the annotated map and one-line consequence dropped into the official `IE-GY_9113B_Board_Presentation_Template.pptx`'s S5 (Backbone diagnosis) slide; every other slide stays a placeholder for later weeks |
