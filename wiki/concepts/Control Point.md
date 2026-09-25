---
title: Control Point
type: concept
tags: [concept]
---

# Control Point

A moment in a process where the business commits and a new authoritative fact is created — a PO issued, a serial number generated, credit approved, an invoice posted. Where governance and, later, automation attach. Distinct from a [[Decision Point]], where a routing choice is made rather than a fact born.

**Introduced:** [[W01_IntegrationBackbone_StudyNote_PB14|Week 1]].

**Used in:**
- [[W01_IntegrationBackbone_StudyNote_PB14|Week 1 study note]] — original definition, "Where Data Is Born: Control Points."
- [[W04_RPA_StudyNote|Week 4 study note]] — glossary carries the definition forward unchanged.
- [[Lab1-Process-Map-Sweetgreen|Lab 1 process map (Sweetgreen)]] — CP1–CP6 marked on the order-and-payment map (`F`, `Q`, `X`, `W`, `Y`, `Y4`). A guest lecturer suggested adding a seventh control point for quality at `K`; the team considered it and, at the Sep 24 checkpoint, chose instead to make the existing six more specific (trigger, owner, fields, downstream use) and keep `K` (quality) and `Y1` (payment captured) as routing gateways, not control points. See that note's "Checkpoint feedback" section for the full reasoning.
- [[RPA-Candidate-Scan-Sweetgreen|RPA-candidate scan]] — the quality gate at `K` was scanned as a possible RPA candidate precisely because it stayed a decision rather than becoming a control point; it was rejected because its input (a physical meal) isn't screen-readable data.

**Why it matters for the capstone:** every control point is a candidate place to attach governance or automation later. A process with no control points has no reliable record of what happened, which is exactly the symptom Week 1 calls "the human as the integration."
