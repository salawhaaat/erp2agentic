---
title: Lab 1 Process Map — Order and Payment (Sweetgreen)
type: deliverable
tags: [deliverable, week3, lab1, process-map, sweetgreen]
company: Sweetgreen
due: Week 3 Lab 1 (Fri Sep 18, 2026)
feeds: ["Board Memo §3 — Integration Backbone Assessment", "Storyboard S5"]
sources:
  - id: final-annotated-map
    resource: raw/data/pdf/sweetgreen-lab1-evidence/Sweetgreen-Lab1-Final-Annotated-Map.pdf
    title: Team's final annotated process map (graded, 24 Sep 2026)
  - id: lab1-sandbox
    resource: raw/data/datasets/Sweetgreen-Lab1-Sandbox.xlsx
    title: Gemini-generated Lab 1 sandbox
---

# Lab 1 Process Map — Order and Payment (Sweetgreen)

> The in-class BPMN build from [[W3_Lab1_Lecture-Notes|Lab 1]], all four moves: map the real process, mark three diagnostic points, choose a curveball, and generate data last. Applied to [[Lab1-Prework-Sweetgreen|the pre-work reality brief]]'s core thesis: the handoff between digital ordering and kitchen execution. Status: all four moves done, data sandbox built in [[Sweetgreen-Lab1-Sandbox.xlsx]], sharpened post-checkpoint with a more specific control-point register (trigger, owner, fields, downstream use for CP1–CP6). Ready for present & share, and feeding [[RPA-Candidate-Scan-Sweetgreen|the Week 4 RPA-candidate scan]].

## The annotated map

![[Order-and-Payment-Process-Map]]

Full diagram source: [[Order-and-Payment-Process-Map]].

## Swimlane view

![[Order-and-Payment-Process-Map#Swimlane view (primary)]]

## The three diagnostic points

| # | Point | Type | Lens tag | Routes to |
|---|---|---|---|---|
| ① | Hold incorrect meal and identify mismatch (`L`) | Worst friction — the rework loop when the finished meal doesn't match the confirmed order | Quality / Operations & Supply Chain | — |
| ② | Can the order be prepared as specified? (`I`) | Stable-rules decision point — availability/feasibility check against a known ruleset. **Post-curveball caveat:** the input to this check now comes from two sources, a live system and a nightly legacy cache, and they don't always agree (`STALE`) — see below. | Operations & Supply Chain | **Lab 2 (Make)** — automate first, but a freshness gate on the availability input needs to be part of the automation, not just the yes/no rule |
| ③ | Assess feasible options and contact customer (`S`) | Judgment decision point — no clean rule for which substitution/compromise to offer, or when to escalate vs. hold | Customer | **Lab 3 (Relevance AI)** |

## Why this map matches the capstone thesis

This directly operationalizes the throughline from [[Backbone-Context-Note-Sweetgreen]] and [[Context-and-Diagnosis-Brief-Sweetgreen]]: the backbone's weakest point is the handoff between digital ordering and kitchen execution. On this map that handoff is literally the arrow from `G` (send order to kitchen) into `H`/`I` (kitchen review and feasibility check) — and it's exactly where the process forks into the worst-friction rework loop (①) and the judgment-heavy exception path (②→③→`Q`/`S`/`T`/`R`). The rejection/rework path (`Q → S → R` and `M → K` loop) is where — per the lecture notes' anti-pattern warning — "the cost hides"; this map has one, so it reflects the real process rather than the idealized one.

This also lines up with the primary-source evidence gathered in [[Sweetgreen-Public-Research|the public research log]]: the CEO's own order-accuracy math (§1) and the two independently-sourced kiosk/ordering-friction incidents (§4, §6) both point at the same seam this map isolates — the point where a digitally-placed order meets kitchen execution capacity and either holds together or doesn't.

## Control points

Specified per the checkpoint feedback below: each control point now names its trigger, proposed owner, the fields it captures, and how it's used downstream, not just what it records.

| ID | Control point | Trigger | Proposed owner | Fields | Downstream use |
|---|---|---|---|---|---|
| CP1 | Confirmed order (`F`) | Order accepted at D1 | Ordering/payment system | Order ID, accepted items/customizations, promise time | Binds the fulfillment reference used by every later control point and by D2's feasibility check |
| CP2 | Fulfillment issue recorded (`Q`) | Item unavailable, unsupported request, or uncorrectable meal | Kitchen system / exception queue | Blocked item, reason, exception ID | Opens the case D3 works from; feeds the friction-chain count |
| CP3 | Agreed order changes (`X`) | Customer agrees to a feasible change (`R`) | Ordering system, staff-entered | New specification, customer consent, timestamp | Versions the order before kitchen re-entry at `H` |
| CP4 | Order completion (`W`) | Order handed over (`P`) | POS / pickup system | Order ID, collection time | Closes the order; source for on-time vs. late reporting |
| CP5 | Cancellation and payment status (`Y`) | Customer cancels (`R`) | Ordering/payment system | Cancellation reason, capture status (captured vs. authorized only) | Routes into CP6's refund-vs-void branch |
| CP6 | Payment resolution (`Y4`) | Refund or void completes | Payment processor | Refund/void outcome, amount, transaction reference | Links back to CP5's cancellation record; feeds the $20 goodwill-refund line in the consequence below |

## Checkpoint feedback: what changed, and what didn't

The guest lecturer suggested introducing a control point for quality at the checkpoint (Sep 18), and the team discussed whether it would help narrow the three diagnostic points down. **Decision, finalized Sep 24: not taken as a new control point.** `K` ("does the meal match the confirmed order?") and `Y1` ("payment already captured?") stay as routing gateways — necessary decisions the map already needed, but not new authoritative facts in the CP1–CP6 sense. The checkpoint feedback actually acted on was different and more specific: **make the existing six control points more specific** — each one now names a trigger, a proposed owner, its fields, and its downstream use, which is the table above. That's a stronger response to "where does data get born and who owns it" than adding a seventh control point would have been.

This does confirm one thing about the diagnostic points: the lab requires three diagnostic markers, but only two of them need to sit on decision points. ① (`L`, hold and identify mismatch) is the worst-friction marker and sits downstream of the `K` gateway, not on a decision point itself — that's fine and doesn't need CP status to count. ②/D2 (`I`, feasibility check) and ③/D3 (`R`, recovery decision) are the two that carry the diagnostic weight, and neither changed: D2 is still the stable-rules candidate (its rule is explicit and complete once the freshness gate is folded in), D3 is still the judgment candidate (no rule decides which recovery to offer). See [[RPA-Candidate-Scan-Sweetgreen]] for the full three-test walkthrough that reaches this conclusion.

## Routing decisions

| ID | Decision | Type | Notes |
|---|---|---|---|
| D1 | Order accepted? (`E`) | Gate | Routes to confirmed order or notify-customer/end. Payment approval and order-acceptance criteria need to be explicit. |
| D2 | Can the order be prepared as specified? (`I`, our ②) | Stable rules → Lab 2 | Checks ingredient availability and supported customizations. The freshness of the availability input has to be checked too, not just the rule (see curveball below). |
| D3 | Which recovery route is agreed? (`R`, our ③) | Judgment → Lab 3 | Staff assess feasible options and the customer consents; routes to agreed change, cancellation, or hold/escalation. Staff judgment happens in `S`, just before this branch. |

## Curveball — #3: nightly batch, not real time

**Picked:** deck card #3, "a key data source only updates overnight, so decisions are made on yesterday's numbers." Availability data feeding decision ② now comes from two places: a live system, and a nightly legacy cache that only refreshes once a day. They don't always agree.

**Why this one fits the map:** the confirmed backbone ([[Backbone-Context-Note-Sweetgreen]] §2) is a stitched stack, Olo for ordering, PAR Brink for POS, Crunchtime for inventory, not one system with one source of truth for menu availability. Nothing in that confirmed stack guarantees those systems agree in real time; a nightly-batch lag between a live feed and a cached snapshot is an ordinary failure mode for exactly this kind of multi-vendor stitching, not a contrived scenario. It also lands on the single decision point the lab asks us to stress: ②, tagged "stable rules" and slated for Lab 2 automation. Before the curveball, ② was a clean yes/no rule, easy to automate, nothing left to design. After it, the rule still holds, but it now has a precondition (which source do you trust, and when) that a naive automation would get wrong by construction. That's a genuinely harder, more useful Lab 2 target than a decision point with no such tension, which is the bar the lecture notes set for a curveball that "genuinely challenges" the process rather than one that's just plausible-sounding.

**Why not the others:** card #6 (compliance hold) would add a new sign-off gate, but nothing in the confirmed backbone points at a specific new regulation, so it would have been invented for the exercise rather than grounded in it. Card #1 (hidden legacy system) is close in spirit but vaguer, it doesn't specify which data disagrees or how a decision point should resolve the disagreement, where #3 forces a concrete answer: pick a freshness gate, or don't, at ②. An earlier draft of this note instead picked card #2 (acquisition's/divestiture's parallel data), reframed around the real Sweetgreen-Wonder Infinite Kitchen divestiture. That reasoning is still sound as a description of company-boundary risk and stays useful background (see [[Sweetgreen-Public-Research]] §3), but it targets a different failure (who owns the kitchen system) than the one this map's own decision ② actually tests (which data source is correct). #3 is the tighter fit for this specific map, and it's also what the data sandbox already models, which is corroborating evidence, not the reason on its own.

**How it changes decision point ②:** node `I` assumed one clean availability check. The map now has `STALE`, a check right before `I`, asking whether the live system and last night's cached snapshot agree. When they don't, the order gets held (`Q`) for a reason distinct from "unavailable item": a stale-source mismatch that needs a freshness gate, not a menu fix.

**What the data sandbox shows:** [[Sweetgreen-Lab1-Sandbox.xlsx]] seeds 24 menu configurations where the live system shows unavailable but the nightly cache still shows available, a mismatch on 10 of them. Against 30 synthetic orders, 6 hit the mismatch and enter exception recovery, a 20% rework rate. Trace order `O001` end to end: menu `M001` → line `L001` → kitchen run `K001` → exception `E001` → payment `P001`.

## Friction chain and board-level consequence

**Chain:** availability/specification mismatch (Quality / Operations) → hold and manual customer contact (Frustration / Customer + Operations) → agreed changes, correction, and kitchen re-entry (Time / Operations) → later readiness (Customer) → extra labor capacity and refunds (Cost / Cash).

**The number:** 6 of 30 synthetic orders enter exception recovery (20%). They consume 60 extra staff minutes and $20 in goodwill refunds. At an assumed $24/hour loaded labor rate, that's $24 + $20 = **$44** in modeled exposure, or $7.33 per affected order. Combined lateness across those six orders is 112 order-minutes, averaging 18.7 minutes late each.

**A correction, made in the open:** an earlier pass through this sandbox added $28 of discarded partial-prep food waste on top, for a $72 headline. That was wrong for this map: since ② checks availability *before* the kitchen starts preparing, the six seeded stockout cases shouldn't also carry food-waste cost, that would double-count a failure this map's own control flow is designed to prevent. The final sandbox ([[Sweetgreen-Lab1-Sandbox.xlsx]], regenerated Sep 25) carries only the corrected $44 in its `Summary` tab; the $72 figure no longer appears anywhere in the file. A separate, uncosted branch — the meal-quality remake path (① in the friction chain) — is a suspected friction distinct from the availability failure this sandbox quantifies; its cost hasn't been seeded or measured, and shouldn't be conflated with the $44.

**Caveats, stated plainly:** this is a synthetic, illustrative sample, not measured Sweetgreen performance. The causal chain (mismatch → hold → cost) is a working hypothesis the sandbox demonstrates, not something proven against real restaurant data. No company-wide extrapolation is justified from 30 orders at one modeled store. Labor capacity is not necessarily incremental payroll — the $24 figure prices staff time, it isn't a claim that Sweetgreen would actually cut a shift.

## What the board could fund

Validate the sources and exception reasons against real restaurant data, then pilot a freshness gate on the availability check at D2 (Lab 2: stable-rules automation) and consistent exception tracking. Next, test an assistant that recommends recovery options at D3 for manager review and customer consent (Lab 3). At D3 specifically: weigh customer urgency, feasible prep ETA, queue impact, and customer constraints/consent; never infer allergy safety or make a silent substitution. An agent can support that staff decision, it can't make the customer's choice.

Potential benefit: fewer missed pickup promises and less avoidable recovery work. $44 is modeled exposure, not a guaranteed saving.

## Where this lands: slide S5 and next week

Per [[W3_Lab1_Lecture-Notes]], what gets presented today is slide S5 (Backbone diagnosis) of the board deck, and the evidence for Board Memo §3. This note is that evidence: the annotated map above, the one-line consequence ("$44 in modeled exposure across 6 of 30 synthetic orders, 18.7 minutes late on average"), and the friction chain feed straight into `IE-GY_9113B_Board_Presentation_Template` slide S5. It's Milestone 1 (Diagnose).

**Week 4 — RPA.** The Lab 2 target is confirmed: **D2, "can the order be prepared as specified"**, specifically the freshness gate on its availability input (live vs. nightly cache) exposed by this week's curveball. That's the stable-rules step to automate first, and the full three-test walkthrough for it (plus what was rejected and why) is now written up in [[RPA-Candidate-Scan-Sweetgreen]], feeding slide S6 and Memo §4.

**Submitted (final, Sep 24):**

| Deliverable | Status | File |
|---|---|---|
| Sandbox (Gemini-generated) | Done, regenerated | [[Sweetgreen-Lab1-Sandbox.xlsx]] — clean $44 modeled burden, no lingering $72 figure |
| Annotated map (★◆ + rejection path + 3 points + chain), specific control-point register | Done | [[Order-and-Payment-Process-Map]] — the [[Order-and-Payment-Swimlane\|swimlane image]] (primary) plus a Mermaid full-BPMN fallback. The team's graded PDF export (24 Sep 2026) was read and its content folded in here; the PDF itself is kept at `raw/data/pdf/sweetgreen-lab1-evidence/`, with a Markdown transcription at `raw/data/markdown/sweetgreen-lab1-evidence/`, see [[ROBOT]] |
| One-page diagnosis (chain, consequence, prize) | Done | This note, §"Friction chain and board-level consequence" above — carries everything the graded "Section 3: Process diagnosis" page had |
| Board deck, slide S5 filled in | Done | `wiki/project/shared/Board-Presentation-Sweetgreen.pptx` — the annotated map and one-line consequence dropped into the official `IE-GY_9113B_Board_Presentation_Template.pptx`'s S5 (Backbone diagnosis) slide; every other slide stays a placeholder for later weeks |
| Standalone Lab 1 presentation (map, curveball, data, consequence) | Done | `wiki/project/week3/Lab1-Presentation-Sweetgreen.pptx` — a self-contained 5-slide deck for the in-class 6-minute share-out, separate from the semester-long board deck above |
