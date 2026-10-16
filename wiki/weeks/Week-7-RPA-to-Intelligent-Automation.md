---
title: Week 7 - From RPA to Intelligent Automation
type: week-summary
tags: [week-summary, week7, module3, intelligent-automation]
description: Catch-up summary of Week 7 (Oct 16): where rules run out, ML and intelligent automation, insight vs cost value, event-driven vs batch, the enterprise AI platform, why agents now, and JPMorgan COiN.
sources:
  - id: study-note
    resource: raw/data/markdown/course-weeks/w7/W07_RPAtoIA_StudyNote_v1.md
---
# Week 7: From RPA to Intelligent Automation

Module 3, Intelligent Automation + AI Agents, Friday Oct 16, 2026. Reading: [[W07_RPAtoIA_StudyNote_v1|study note]] (no lecture slides ingested yet). Previous: [[Week-6-Lab-2-Automate]]. Next: Week 8, the SPAR agent framework (not yet ingested).

## The one-paragraph version

In Lab 2 your bot applied its rule with full confidence to a case the rule didn't fit. That was the boundary of rules-based automation. This week names what takes the step on the other side: **intelligent automation**, a rule-based flow with a machine-learning model where the judgment used to fail. Lab 3 builds an agent for that exact step.

## Key points

- **Autonomy ladder** (Bornet et al., 2025, adapted from self-driving levels): Level 1 rule-based (Module 2), **Level 2 intelligent automation (this week)**, Level 3 agentic workflows (Weeks 8 to 10, SPAR, Lab 3), Levels 4 and 5 autonomous agents (Module 4 horizon).
- **A rule runs out two ways:** messy (unstructured) input, and the case the logic didn't foresee. A rule needs structured input and complete logic. It also fails silently and confidently.
- **Two kinds of [[Decision Point]]:**

| Type | Rule can decide? | Response |
|---|---|---|
| Stable-rules | Yes, every case mapped | RPA candidate (Level 1), see [[RPA Candidate Criteria]] |
| Judgment | No, unforeseen case or unstructured input | AI target (Level 2+), the Lab 3 agent |

  Rejection and rework are costly because they sit at judgment points automated as if they were stable. Piling more rules on a judgment step gives a longer, more brittle rulebook.
- **Machine learning** learns patterns from examples instead of following a written rule. Three families: **supervised** (reproduce a labelled expert judgment), **unsupervised** (find anomalies and groupings), **reinforcement** (learn by trying toward a goal). NLP reads human language. Pattern: NLP reads the email, a classifier decides what it is about, a rule handles it.
- **Value shifts from cost saved to insight gained.** A bot sells on labour hours. A model that reads *all* the work decides consistently at full scale and surfaces patterns nobody had hours to find. Iansiti and Lakhani's "AI factory" runs decision-making as an industrial process. That is the case a board funds as an investment, not an expense.
- **Batch-push vs event-driven.** Legacy work runs on schedules, so variance waits for the next run. Intelligent systems need a trigger at the point of variance. Add intelligence without changing the rhythm and you get a faster version of the same dysfunction.
- **Enterprise AI platform** (Tella et al.): models are "language models, not knowledge models", so they need orchestration (an execution engine that turns output into action across systems) and governance (explainability, observability, adaptability, access control). Process intelligence is one of its input methods.
- **Why agents, why now.** Language models gave a brain that could reason but couldn't act. Automation gave hands that couldn't judge, and hit the "automation plateau". An agent joins them. SPAR (sense, plan, act, reflect) is Week 8.
- **Golden rule: the simpler, the better.** Match autonomy to the step's risk. Don't use an agent where a rule would do, and don't leave the one judgment step to a rule. Agents are augmentative, like a capable new hire you wouldn't leave unsupervised. Human-in-the-loop from [[Week-5-Scaling-RPA-and-CoE|Week 5]] carries forward.
- **Thread shift:** Customer now leads the module, though this week's case lands on Operations and Cash.

## Case: JPMorgan COiN (2017)

About 12,000 commercial loan agreements a year took roughly 360,000 lawyer and loan-officer hours, with human misreads causing servicing errors. COiN learned to read contracts by ingesting data, reviewing in seconds with fewer errors. Contrast with a rule-based checker, which matches pre-specified patterns and breaks on a phrasing the template didn't foresee. The governance change when the reader is a model: who is accountable if it misreads a clause, what must be transparent so a human can check, and where a person stays (high-value agreements, unusual clauses, cases the model flags as uncertain).

## Homework and deliverable

Name the **one** step on your own process that genuinely needs AI judgment and write why rules fail there. It opens Milestone 2 (Design) and seeds Board Memo §5, Agent Design and Governance. Prep for Week 8: read the Week 8 note and Bornet et al. Ch. 1 to 3.

## Study questions

1. What can't rules-based RPA handle, and why does the boundary matter strategically?
2. How does intelligent automation change the value proposition from cost saving to insight?
3. Using COiN, contrast a rules-based document checker with an ML system, and name the governance change.
