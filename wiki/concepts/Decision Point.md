---
title: Decision Point
type: concept
tags: [concept]
---

# Decision Point

A moment where the flow is routed — approve or reject, one path or another — as distinct from a [[Control Point]], where data is born rather than chosen between. A named BPMN gateway. The costly case is usually rejection, which sends work back for manual rework before it re-enters the flow.

Decision points split into two kinds, and the split is the spine of Module 2:

- **Stable-rules decision point.** Every case is decided by explicit, complete logic — see [[RPA Candidate Criteria]]. This is the [[W04_RPA_StudyNote|Week 4]] RPA target.
- **Judgment decision point.** No fixed rule; two reasonable people could decide differently. This is the Week 7 / Lab 3 AI-agent target.

**Introduced:** [[W01_IntegrationBackbone_StudyNote_PB14|Week 1]].

**Used in:**
- [[W01_IntegrationBackbone_StudyNote_PB14|Week 1 study note]] — original definition, "Where the Path Forks: Decision Points."
- [[W04_RPA_StudyNote|Week 4 study note]] — the entire RPA-candidate filter is built on separating stable-rules from judgment decision points ("Three Tests for a Good Candidate").
- [[Lab1-Process-Map-Sweetgreen|Lab 1 process map (Sweetgreen)]] — D1 (order accepted, `E`), D2 (feasibility/freshness check, `I`, stable-rules), D3 (recovery decision, `R`, judgment).
- [[RPA-Candidate-Scan-Sweetgreen|RPA-candidate scan]] — confirms D2 as the Lab 2 (RPA) target and D3 as the Lab 3 (AI-agent) target, and works through why D1 and the quality gate at `K` don't qualify yet.

**Why it matters for the capstone:** the three diagnostic points marked in Lab 1 are almost always a mix of control points and decision points, and which kind a step is determines which course tool (RPA, AI agent, or redesign) applies to it.
