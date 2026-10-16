---
title: Week 2 - Failure to Leverage
type: week-summary
tags: [week-summary, week2, module1]
description: Catch-up summary of Week 2 (Sep 11): failure to leverage vs implementation failure, obliterate then automate, the Four Lenses in full, and the Nike and Birmingham cases.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w2/W02_FailureToLeverage_StudyNote_v6.md
  - id: lecture-notes
    resource: raw/data/markdown/course-weeks/w2/W2_FailureToLeverage_Lecure Notes_v9.md
---
# Week 2: Failure to Leverage and BPR as the Remedy

Module 1, Friday Sep 11, 2026. Readings: [[W02_FailureToLeverage_StudyNote_v6|study note]], [[W2_FailureToLeverage_Lecure Notes_v9|lecture notes]]. Previous: [[Week-1-Integration-Backbone]]. Next: [[Week-3-Lab-1-Diagnose-and-Map]]. Capstone output: [[Context-and-Diagnosis-Brief-Sweetgreen]].

## The one-paragraph version

There are two kinds of failure. **Implementation failure** means the system doesn't work. **Failure to leverage** means it works and the value never arrives, because the process underneath was automated instead of redesigned. The second is the majority outcome. The cure, from Hammer (1990), is [[Obliterate Then Automate]]: redesign from a blank sheet before you build, or you "pave the cow path".

## Key points

- **Why ERP is the hardest project a company runs:** it touches everything at once and can't be rehearsed at scale. The realistic end state is a core backbone plus specialized apps, so the seams are where value leaks.
- **Delivery is an ecosystem** (integrators, internal IT, vendor, business owners). Lean too hard on the integrator or accept the platform's defaults and you give up *retained design authority*.
- **Integration on-ramps** (forms, email, file transfer, XML, APIs): the more natural they are, the higher the adoption.
- **Obliterate selectively.** Concentrate total redesign where value is made or lost, not across the whole business.
- **[[Four Lenses]] in full:**

| Lens | Detects | Usual thread |
|---|---|---|
| Frustration | the human signal from people inside the process | Customer |
| Time | waiting, queuing, rework | Operations and Supply Chain |
| Cost | money spent without producing value | Cash |
| Quality | errors that cause rework and erode trust | feeds Time and Cost |

  Run all four. They overlap on purpose, so one quality fix can pay three times. This drives the Lab 1 pre-work.
- **Rollout:** Big Bang turns every hidden problem into a simultaneous emergency. A progressive rollout buys discovery.
- **Adoption, not bolt-on change management.** The people inside the process help diagnose and redesign it from the start.

## Cases

> [!example]- Nike (2000) vs Birmingham (2022 to 23)
> | | Nike | Birmingham |
> |---|---|---|
> | What was layered on | i2 demand planning on unredesigned supply chain | Oracle Cloud Fusion on unredesigned finance and HR |
> | Rollout | Big Bang | Big Bang |
> | What broke | factory orders | the books, no single source of truth |
> | Cost | about $100M lost sales, about 20% stock drop | costs far beyond business case, Section 114 notice (Sep 5, 2023) |
> | Primary thread | Operations (Cash overlay) | Cash (Operations overlay) |
>
> Both are a Unification ambition without the re-engineering that earns it. At Birmingham the cause is disputed: the council's statement blamed equal-pay liability and a budget gap, while an audit report points at Oracle. The dispute itself is the lesson, because the failed system left the council unable to produce the numbers needed to settle it.

## Why it matters later

[[Obliterate Then Automate]] is the sequencing rule behind the Week 4 RPA filter. Midterm answer 1 uses the two-failures distinction ([[Midterm-Quiz-Answers]]).
