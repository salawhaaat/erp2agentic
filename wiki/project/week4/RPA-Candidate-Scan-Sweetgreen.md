---
title: RPA-Candidate Scan (Sweetgreen)
type: deliverable
tags: [deliverable, week4, rpa, sweetgreen]
company: Sweetgreen
due: Week 4 (Fri Sep 25, 2026)
feeds: ["Board Memo §4 — Automation Journey", "Storyboard S6"]
---
# RPA-Candidate Scan (Sweetgreen)

> Runs the [[RPA Candidate Criteria|three-test filter]] from [[W04_RPA_StudyNote|Week 4's study note]] (repetitive, rules-based, stable) across the sharpened [[Lab1-Process-Map-Sweetgreen|Lab 1 process map]] — see [[RPA vs Traditional Automation vs AI]] for the three-way comparison this filter picks between. This is diagnostic work, not a build: it names which step becomes the Lab 2 automation and which stays a Lab 3 (AI agent) target, and rejects the rest with reasons. Milestone 1 (Diagnose), Board Memo §4. Covers all three in-class breakouts from [[W04_RPA_LN_Slides_v1|the Week 4 lecture slides]]: the map tagged end to end, the filtered scan itself, and one candidate costed and governed.

## Swimlane view

![[Order-and-Payment-Process-Map#Swimlane view (primary)]]

Full detail: [[Order-and-Payment-Process-Map]]. Control points, decision points, and the friction chain are unpacked in [[Lab1-Process-Map-Sweetgreen]].

## Breakout 1 — the map, tagged end to end

Every step of the swimlane view above, tagged traditional / RPA / AI / redesign, per [[W04_RPA_LN_Slides_v1|the Week 4 in-class breakout instructions]].

| Step | Tag | Why |
|---|---|---|
| O1.1–O1.2 Select items, submit order | — (customer action) | Not a candidate for any of the three; it's the customer's own input, nothing to automate on Sweetgreen's side |
| O1.3 Process payment | Traditional | Payment capture already runs through Olo/PAR Brink's native integration — the plumbing, not a bot |
| O1.4 Order accepted? (D1) | Not yet taggable | Acceptance criteria beyond payment aren't fully specified on the map — a mapping gap, not a routing call |
| ★ CP1 Confirm order | Traditional | Record-creation inside the ordering system, not a screen-driven step |
| K2.1 Review spec & availability | Traditional (native) / RPA (freshness check) | Reviewing the spec is system-native; the live-vs-cache comparison it feeds is the RPA candidate below |
| **K2.2 Feasible? live vs. cached (D2)** | **RPA** | **Repetitive, rules-based, stable — see the filter table below** |
| K2.3 Prepare meal | — (physical kitchen work) | Not a screen or system step; outside RPA's reach entirely |
| K2.4 Quality check: matches order? | Rules-based, but not RPA | Passes the logic test but fails the RPA pattern — see "What was rejected" below |
| K2.5 Pack & hand over | — (physical kitchen work) | Same as prep: not a candidate for any of the three |
| C4.1 Collect order | — (customer action) | Not Sweetgreen's step to automate |
| ★ CP4 Record completion | Traditional | Native system write on collection |
| X3.1 Hold order, record issue | Traditional (record) / feeds AI below | The record-creation is native; the judgment about what happens next is the AI candidate |
| **X3.2 Assess feasible options (D3)** | **AI** | **No fixed rule — see the filter table below** |
| X3.3 Customer's choice / escalate | AI-adjacent (human + assistant) | Downstream of the D3 judgment call, not independently automatable |
| ★ CP3/CP5/CP6 Record change/cancel/resolve | Traditional | Native system writes once a human or the AI assistant has decided |

**Circled candidates: K2.2 (RPA) and X3.2 (AI)** — same two diagnostic points Lab 1 already marked, confirmed here by walking the whole map rather than just the three flagged steps.

## The filter, walked step by step

| Step | Repetitive? | Rules-based? | Stable? | Verdict |
|---|---|---|---|---|
| D1 — Order accepted? (`E`) | Yes, every order | Partial — payment approval is a clean rule, but "order acceptance" criteria beyond payment are not fully specified on this map | Yes | Not yet a candidate: needs the acceptance rule made explicit before automating; a redesign-adjacent gap, not a build target this cycle |
| **D2 — Can the order be prepared as specified? (`I`, incl. `STALE` gate)** | **Yes — every order passes through it** | **Yes, once you fold in the freshness gate: approve when live and cached availability agree and the item/customization is supported, else hold** | **Yes — the rule and the two source systems (Olo, Crunchtime cache) don't change often** | **RPA candidate — Lab 2 target** |
| Quality gate (`K`, does meal match order — a routing decision, deliberately not elevated to a control point at the Sep 24 checkpoint) | Yes | Yes on paper — compare prepared items to the confirmed spec — but the input is a physical, visually/manually verified meal, not structured system data a bot can read off a screen | Screens are stable, but the object being checked isn't a screen at all | Not an RPA candidate this cycle: the comparison logic is rule-based, but nothing here is "reading a screen" in the RPA sense. Revisit if kitchen-side computer vision or a scale/scanner check ever exists, but that is a different tool, not this week's scope |
| **D3 — Which recovery route is agreed? (`R`, staff assess options and customer consents)** | **Yes — every exception reaches it** | **No — no fixed rule decides which substitution, discount, or cancellation to offer, or when to escalate; it depends on customer urgency, prep ETA, and consent** | N/A — fails on rules, so stability doesn't rescue it | **Not RPA. Judgment step — AI-agent target, Week 7 / Lab 3** |
| Stock-accuracy root cause (upstream of `STALE`) | N/A | N/A | N/A | **Not RPA — redesign job.** A bot pointed at the symptom (mismatched availability) without fixing why two systems disagree would pave the cow path; see [[W04_RPA_StudyNote]]'s task-mindset warning |

## The candidate: D2, the feasibility-and-freshness check

**Why it passes all three tests.** Every order runs through it (repetitive). The rule is complete: approve if the live system and the cached snapshot agree on availability and the requested customization is supported, otherwise hold (rules-based). The rule and the two systems behind it, Olo for ordering and the Crunchtime inventory cache, don't change week to week (stable). This is the same conclusion [[Lab1-Process-Map-Sweetgreen]] reached before the curveball was absorbed; the curveball sharpened it rather than overturning it, because the freshness gate is itself a clean rule ("do the two sources agree, yes or no"), not a source of judgment.

**Thread ([[Three Threads|see the three threads]]):** Operations and Supply Chain, primarily — it is an inventory/feasibility check. It also touches Cash (fewer wrongly-accepted orders that later get rejected mid-prep, fewer refunds) and Customer (fewer holds the customer has to be contacted about).

**Rough prize.** From the [[Lab1-Process-Map-Sweetgreen|Lab 1 sandbox]]: 10 of 24 seeded menu configurations show a live-vs-cache mismatch, and 6 of 30 synthetic orders hit it and enter exception recovery (20%), costing a modeled $44 across those six orders (60 staff-minutes plus $20 in goodwill refunds) and averaging 18.7 minutes late. A bot that checks freshness automatically before committing to `I` doesn't eliminate every mismatch (the underlying data lag is a plumbing problem, not something RPA fixes, per [[W04_RPA_StudyNote]]'s Bailey Hydraulics lesson), but it removes the manual copy-and-compare step and flags the disagreement consistently, which is the labor cost this scan is arguing for.

**Attended or unattended, and where the human stays.** Unattended: the check itself needs no human in the loop when the two sources agree. The human stays exactly where the current map already routes them: at `Q`/`S` once the freshness gate fails, i.e., the exception, not the routine case. That is deliberate, not a gap: automating the yes/no gate and still routing every "no" to a person is the human-oversight design [[W04_RPA_StudyNote]] asks for on a rules-based bot.

## What was rejected, and why

- **D1, order acceptance beyond payment.** Repetitive and probably stable, but the map doesn't yet state the full acceptance rule (what, besides payment, can block an order). Automating an underspecified rule risks locking in an implicit, undocumented policy. Fix the rule first; this is a mapping gap, not an automation call yet.
- **The quality gate at `K`.** Passes the rules test on paper, but fails the RPA pattern itself: RPA drives *screens*, and this check verifies a physical meal against a spec, which is not a screen-based comparison a bot can perform without additional tooling (vision, scale, scanner) that isn't part of this course's default stack. Kept as a routing decision, not elevated to a control point (the checkpoint feedback was to specify the existing six control points, not add a seventh) — see [[Lab1-Process-Map-Sweetgreen]]'s "Checkpoint feedback" section.
- **D3, the recovery decision.** Fails the rules-based test outright: two reasonable staff members could offer different resolutions to the same customer, which is the definition of a judgment call. This is the Lab 3 / Week 7 AI-agent target, not RPA, per the boundary [[W04_RPA_StudyNote]] draws between rules and judgment.
- **The stock-accuracy root cause behind the freshness mismatch.** Automating around it (e.g., a bot that just keeps re-checking a stale cache faster) would be [[Obliterate Then Automate|paving the cow path]] — the fix is closing the sync gap between Olo and Crunchtime, an integration/redesign question from Week 2's sequence, not an RPA question.

## What the board could fund

Pilot an automated freshness-and-feasibility gate at D2: a bot (or, per Lab 2, a Make scenario) that checks live availability against the cached snapshot before an order is accepted for kitchen prep, and routes disagreements straight to exception handling with the mismatch reason attached, instead of a person or the kitchen discovering it after the fact. Estimated exposure removed: up to $44 / 6 orders in the 30-order sample (proportionally, roughly 1.5% of order volume), pending validation against real order volume and real mismatch rates. This is the Lab 2 build target.

Separately, flag D3 (recovery decision) as the Lab 3 AI-agent target: an assistant that recommends a recovery option for manager review, never deciding unilaterally, per the human-in-the-loop boundary in [[Lab1-Process-Map-Sweetgreen]]'s board-funding section.

## Breakout 3 — cost it, and govern it

One candidate (D2, the feasibility-and-freshness gate) taken through to a board number and a human safeguard, per [[W04_RPA_LN_Slides_v1|the Week 4 breakout instructions]].

**The number, order-of-magnitude.** In the 30-order sandbox sample, 6 orders (20%) hit the live-vs-cache mismatch and consume 60 minutes of manual reconciliation between them — 10 minutes per affected order. If a single store runs on the order of 300 digital orders a day (an assumed, not sourced, per-store volume — validate against Sweetgreen's real per-store digital mix before using this in the actual board memo), the same 20% mismatch rate implies roughly 60 affected orders a day, or about 10 staff-hours a day of manual freshness-checking and exception handling across a store. That is the labor-removed side of the payback; the build side is the one-time Make scenario plus its ongoing licence, which this scan doesn't have a number for yet (Lab 2 produces that). **This is a shape, not a commitment** — the sandbox is synthetic and one modeled store; a real payback period needs real per-store order volume and real mismatch rates, not this scan's placeholder assumption.

**Attended or unattended.** Unattended: the freshness gate itself needs no human when the two sources agree — that's the routine path, and it's most of the volume. The human stays exactly where the map already routes them, at the exception queue once the gate disagrees — not case-by-case on the happy path, but every time on the path that actually needs judgment.

**The human-oversight and workforce note.** The checkpoint this bot needs is already named: every freshness disagreement routes to a person, never auto-resolved, because guessing which source is right when they disagree is exactly the kind of silent-wrong-answer risk [[W04_RPA_StudyNote]] warns a rules-based bot creates with perfect confidence. On the workforce side: this candidate removes a manual copy-and-compare check, not a role — nothing in the sandbox implies a position eliminated, and the freed minutes are exception-queue minutes returned to staff who are already doing exception handling, not hours cut from a schedule. That's a narrower claim than "redeployment to higher-value work," and it's the honest one this scan can currently support; a fuller answer (what the firm owes anyone whose role does change as automation scales past this one candidate) is Board Memo §7's job, not this scan's.

## Where this lands: slide S6 and Board Memo §4

This scan is the evidence for Board Memo §4 (Automation Journey) and fills the Automation-opportunity slide (S6) of the board deck, still inside Milestone 1 (Diagnose) — naming where automation belongs, not yet proposing how to run it enterprise-wide. The next concrete step is Lab 2 (Week 6): build the D2 freshness-and-feasibility gate in Make, then break it and state the human oversight, per [[W04_RPA_StudyNote]]. Lab 2 itself needs a Make account (setup happens before Week 6, not this week) and is not attempted in this note.
