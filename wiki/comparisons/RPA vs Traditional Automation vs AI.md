---
title: RPA vs Traditional Automation vs AI
type: comparison
tags: [comparison]
---
# RPA vs Traditional Automation vs AI

The three ways to take a human out of a process step, distinguished by where each one acts and what kind of input it can handle. Introduced in [[W04_RPA_StudyNote|Week 4]] as the axis the whole automation module is organized around.

| Approach | Where it acts | What it handles | Anchored exemplar |
|---|---|---|---|
| Traditional / back-end automation | In the plumbing — APIs, database, native integration | Structured data through proper system interfaces; robust, but needs engineering to change | [[Bailey Hydraulics]]' native NetSuite Order-to-Cash flow |
| RPA | At the surface — the same screens a person uses | Repetitive, rule-based steps with no judgement; fast to build, brittle when a screen changes | [[Thermo Fisher Scientific]]'s order-entry bot moving order data across systems |
| AI | On judgement — unstructured, ambiguous input | Cases with no fixed rule: reading intent, classifying, resolving ambiguity | The exception routed out of Thermo Fisher's flow (previewed in Week 4; taught in Week 7) |

**The one-line version:** traditional automation is robust but expensive to build or change; RPA is cheap and fast but brittle, because it drives screens instead of the plumbing underneath; AI is for the steps that have no fixed rule at all. See [[RPA Candidate Criteria]] for the three-test filter that decides whether a step is an RPA candidate, an AI candidate, or neither.

**Applied to this capstone:** [[RPA-Candidate-Scan-Sweetgreen]] places Sweetgreen's D2 (feasibility/freshness check) in the RPA column and D3 (recovery decision) in the AI column, and explicitly rejects the quality gate at `K` from the RPA column because its input (a physical meal) isn't screen-readable data — none of the three approaches fit it yet.
