---
title: RPA-Candidate Scan (Sweetgreen)
type: deliverable
tags: [deliverable, week4, rpa, sweetgreen]
company: Sweetgreen
due: Week 4 (Fri Sep 25, 2026)
feeds: ["Board Memo §4 — Automation Journey", "Storyboard S6"]
---

# RPA-Candidate Scan (Sweetgreen)

> Runs the [[RPA Candidate Criteria|three-test filter]] from [[W04_RPA_StudyNote|Week 4's study note]] (repetitive, rules-based, stable) across the sharpened [[Lab1-Process-Map-Sweetgreen|Lab 1 process map]] — see [[RPA vs Traditional Automation vs AI]] for the three-way comparison this filter picks between. This is diagnostic work, not a build: it names which step becomes the Lab 2 automation and which stays a Lab 3 (AI agent) target, and rejects the rest with reasons. Milestone 1 (Diagnose), Board Memo §4.

## Swimlane view

![[Order-and-Payment-Process-Map#Swimlane view (primary)]]

Full detail: [[Order-and-Payment-Process-Map]]. Control points, decision points, and the friction chain are unpacked in [[Lab1-Process-Map-Sweetgreen]].

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

## Where this lands: slide S6 and Board Memo §4

This scan is the evidence for Board Memo §4 (Automation Journey) and fills the Automation-opportunity slide (S6) of the board deck, still inside Milestone 1 (Diagnose) — naming where automation belongs, not yet proposing how to run it enterprise-wide. The next concrete step is Lab 2 (Week 6): build the D2 freshness-and-feasibility gate in Make, then break it and state the human oversight, per [[W04_RPA_StudyNote]]. Lab 2 itself needs a Make account (setup happens before Week 6, not this week) and is not attempted in this note.
