---
title: Lab 1 Process Map — Order and Payment (Sweetgreen)
tags: [deliverable, week3, lab1, process-map, sweetgreen]
company: Sweetgreen
due: Week 3 Lab 1 (Fri Sep 18, 2026)
feeds: ["Board Memo §3 — Integration Backbone Assessment", "Storyboard S5"]
---

# Lab 1 Process Map — Order and Payment (Sweetgreen)

> The in-class BPMN build from [[W3_Lab1_Lecture-Notes|Lab 1]], move ① ("Map the real process"), ② ("Mark three diagnostic points"), and ③ ("Choose a curveball"), applied to [[Lab1-Prework-Sweetgreen|the pre-work reality brief]]'s core thesis: the handoff between digital ordering and kitchen execution. Status: map, three diagnostic points, and curveball all done. Next: generate data (move ④).

## The annotated map

![[Order-and-Payment-Process-Map]]

Full diagram source: [[diagrams/Order-and-Payment-Process-Map]].

## The three diagnostic points

| # | Point | Type | Lens tag | Routes to |
|---|---|---|---|---|
| ① | Hold incorrect meal and identify mismatch (`L`) | Worst friction — the rework loop when the finished meal doesn't match the confirmed order | Quality / Operations & Supply Chain | — |
| ② | Can the order be prepared as specified? (`I`) | Stable-rules decision point — availability/feasibility check against a known ruleset. **Post-curveball caveat:** for Infinite Kitchen stores this check now sits behind a Wonder-owned system (`IK`/`V`), so "stable rules" only holds if that vendor system's data is fresh — see below. | Operations & Supply Chain | **Lab 2 (Make)** — automate first, but two different backends (internal make-line logic vs. Wonder's API) need to be automated against, not one |
| ③ | Assess feasible options and contact customer (`S`) | Judgment decision point — no clean rule for which substitution/compromise to offer, or when to escalate vs. hold | Customer | **Lab 3 (Relevance AI)** |

## Why this map matches the capstone thesis

This directly operationalizes the throughline from [[Backbone-Context-Note-Sweetgreen]] and [[Context-and-Diagnosis-Brief-Sweetgreen]]: the backbone's weakest point is the handoff between digital ordering and kitchen execution. On this map that handoff is literally the arrow from `G` (send order to kitchen) into `H`/`I` (kitchen review and feasibility check) — and it's exactly where the process forks into the worst-friction rework loop (①) and the judgment-heavy exception path (②→③→`Q`/`S`/`T`/`R`). The rejection/rework path (`Q → S → R` and `M → K` loop) is where — per the lecture notes' anti-pattern warning — "the cost hides"; this map has one, so it reflects the real process rather than the idealized one.

This also lines up with the primary-source evidence gathered in [[research/Sweetgreen-Public-Research|the public research log]]: the CEO's own order-accuracy math (§1) and the two independently-sourced kiosk/ordering-friction incidents (§4, §6) both point at the same seam this map isolates — the point where a digitally-placed order meets kitchen execution capacity and either holds together or doesn't.

## Curveball — #2, reframed: the divestiture's parallel data

**Picked:** deck card #2, "a recently acquired unit kept its own order/customer system; the two have never been merged," reframed as its mirror image for Sweetgreen: a recently **divested** unit that now runs a system Sweetgreen no longer owns, but still depends on.

**Why this one, over #1/#3/#6:** #1 (hidden legacy system) and #3 (nightly batch) are both plausible but invented for this exercise; nothing in the confirmed backbone forces either one specifically. #2 reframed isn't invented. In December 2025, Sweetgreen sold the Infinite Kitchen technology (the Spyce platform) to Wonder for $186.4M and licensed it back (see [[research/Sweetgreen-Public-Research]] §3, and [[Backbone-Context-Note-Sweetgreen]] §2). For the ~30 Infinite Kitchen stores (growing per FY2026 guidance), the kitchen execution system this map's `Kitchen` swimlane assumed was internal is now owned and operated by a different company. That's a real, dated, sourced fact, not a hypothetical, and it exposes a real gap in the original map: it drew "Kitchen and Pickup Staff" as one uniform internal swimlane, which is no longer true for over a tenth of the fleet.

**How it changes decision point ②:** node `I` ("Can the order be prepared as specified?") was modeled as a same-company availability check. For Infinite Kitchen stores it's now a cross-company query: Sweetgreen's ordering layer has to ask a Wonder-owned system whether it has the capacity, uptime, and ingredients to fulfill the order. ② stops being purely stable-rules and starts depending on the freshness and reliability of a vendor's API, something Sweetgreen doesn't fully control under a license/supply agreement.

**New failure mode added to the map:** the original map had no path for "order confirmed to the customer, then the kitchen system that was supposed to make it turns out unable to, for reasons that have nothing to do with the food." Nodes `IK` (which kitchen system serves this store) and `V` (does the Wonder-owned system confirm capacity and availability, in sync) now sit between `G` and `H` in [[diagrams/Order-and-Payment-Process-Map|the diagram]], with `V`'s "No" edge routing to `Q` under a distinct reason: stale sync, capacity limit, or vendor system unavailable, separate from the existing "unavailable item / unsupported request" reason on `I`. Those are different root causes needing different fixes: one is a menu/inventory data problem inside Sweetgreen, the other is an integration-freshness problem between two companies.

**Revised board-level consequence:** roughly 30 of 281 restaurants, about 11% of the fleet and growing, now run kitchen execution on a system outside Sweetgreen's direct operational control. The CEO has said order accuracy is "challenging no matter how hard we try" even on the fully internal make-line (see [[research/Sweetgreen-Public-Research]] §1). The Wonder divestiture didn't close that gap, it moved part of it outside the company, adding a vendor-freshness failure mode on top of the original accuracy problem.
