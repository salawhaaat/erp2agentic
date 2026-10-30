---
title: Midterm Quiz Answers (Quizz 1)
type: deliverable
tags: [deliverable, quiz, midterm, sweetgreen]
description: The three Quizz 1 (Mid Term) questions with the answers submitted, written as short paragraphs.
sources:
  - id: w2
    resource: raw/data/markdown/course-weeks/w2/W02_FailureToLeverage_StudyNote_v6.md
  - id: w5
    resource: raw/data/markdown/course-weeks/w5/W05_ScalingRPA_CoE_StudyNote_v2.md
---
# Midterm Quiz Answers (Quiz 1)

IE-GY 9113B, due Oct 14, 2026, 11:59 PM. Related: [[Leverage Gap]], [[Obliterate Then Automate]], [[RPA Candidate Criteria]], [[RPA-Candidate-Scan-Sweetgreen]], [[Lab2-Automation-Sweetgreen]].

## Question 1

**Distinguish failure to leverage from implementation failure, and explain why automating a broken process makes things worse. Name the principle that fixes it and what it requires you to do first.**

An implementation failure means the system does not work, for example it crashes or never goes live. A failure to leverage means the system works, but the business gets no value because the process behind it was never fixed. Automating a broken process makes things worse, since it just runs the same bad steps faster and locks the problem in. The fix is "obliterate, then automate." It requires us to redesign the process first, where value is created or lost, and only then automate what is left.

## Question 2

**Give the three criteria that make a step a good RPA candidate, then describe one step from your own project that looks automatable but fails one criterion, and say which.**

A good RPA candidate is repetitive, rules-based, and stable. In our Sweetgreen project, D3 (choosing a recovery option for a blocked order) looks automatable because it happens often and uses structured data. However, it fails the rules-based test, since staff must judge customer urgency and wait time, and the customer must agree to the change. D2, the availability check, passes all three, so we automated that one in Lab 2.

## Question 3

**RPA works but doesn't scale. Explain one reason it stalls as it grows and what a Center of Excellence does about it; then, from your Lab 2 automation, name one failure mode and the human-oversight control it implies.**

RPA stalls because bots are brittle. When a screen changes the bot breaks, and with hundreds of bots, fixing them takes more time than building new ones. A Center of Excellence fixes this by owning the standards, tracking every bot, and handling maintenance. In Lab 2, the failure mode was bad or stale input data, because our first rule approved four problem orders. The control it implies is human review: staff review for operational problems and data review for bad inputs, plus an audit log of every decision.

## Favorite Case Study (Birmingham City Council, 2022-23)

**My favorite case from the course materials, and how it connects to the quiz concepts.**

Birmingham City Council is my favorite case, because it is the cleanest example of failure to leverage, and the record is still disputed. In April 2022 the council replaced its SAP system with Oracle Cloud Fusion for finance and HR. Instead of redesigning its processes to fit the platform, it bent Oracle to its legacy ways of working and went live in one cutover with known control weaknesses still open. The system then posted transactions incorrectly and could not produce reliable accounts, so the council lost its single source of truth. Costs grew to many times the original business case, and in September 2023 it issued a Section 114 notice.

What I like most is that the cause is contested. The council blamed equal-pay liabilities, the Sheffield Audit Reform Lab blamed Oracle, and the external auditor sat in the middle. To me that is the lesson: once you lose the single source of truth, you also lose the ability to say what went wrong. It also supports "obliterate, then automate." The software was fine, and the failure was the skipped redesign and the Big Bang rollout. Nike in 2000 is the same trap a generation earlier, which shows it is a management problem and not a technology problem.

---

# Detailed Talking Points (bullets)

Same answers as above, expanded so each one can be argued in detail. Sources: Week 2, 4, 5 study notes, the Sweetgreen RPA scan, and the Lab 2 write-up.

## Question 1: Failure to leverage vs. implementation failure

**The two failures**
- Implementation failure: the system does not work. It crashes, misses go-live, or is abandoned. Everyone can see it, and it is comparatively rare.
- Failure to leverage: the system works, but the value never arrives because the underlying process was never redesigned.
- Gartner's definition of ERP failure is "fail to fully meet original business-case goals." Gartner projects that by 2027 more than 70% of recent ERP initiatives will miss those goals, and up to a quarter will fail catastrophically. That is failure to leverage by another name, and it is the majority outcome.
- Week 2's point: most post-mortems do not blame the software. They find planning, requirements, leadership and adoption failures.

**Why automating a broken process makes it worse**
- Automation does not question a step, it only speeds it up. A bad step now runs faster and at higher volume.
- It locks the flaw in. Once code, integrations and training are built around a process, changing it costs far more than it did before.
- It hides the problem. The steps look "done," so nobody asks whether they should exist.
- Result: "a faster broken process."
- Birmingham is the extreme case. The implementation failed so badly (no reliable accounts) that the council could not even measure the value it had hoped to gain.

**The principle: obliterate, then automate (Hammer)**
- Origin: Michael Hammer's 1990 Harvard Business Review essay, "Reengineering Work: Don't Automate, Obliterate." It named the discipline of business process re-engineering (BPR), and the Week 2 note credits it as where the cure was first named.
  - The problem he saw: companies were pouring money into information technology and getting disappointing returns. The cause was that they used computers to mechanize old ways of working rather than to rethink them.
  - His prescription: do not speed up the existing process. Obliterate it, and redesign the work from a blank sheet around the outcome you actually want.
  - "Stop paving the cow paths" is the image behind it. A cow path wandered for historical reasons, and paving it makes a permanent, efficient route to nowhere sensible. Automating a process you never questioned does the same thing.
  - Why the word is violent: it is deliberate, to break the habit of treating the current process as a given. The course adds a limit: "obliterate" does not mean redesign everything. Concentrate total redesign where value is created or lost, and adopt the standard where a process already works. Otherwise you fail the opposite way, with too much change at once for the organization to absorb.
  - The two worked examples that open his article are Ford accounts payable and Mutual Benefit Life (below). The Week 2 note says every case in the course is a variation on them.
  - The deeper target: a planning paradigm, not just individual steps. Most enterprises run batch-push (plans computed overnight, humans firefighting exceptions in the morning). Automation, and later agents, only pay off once operations shift to pull-based, event-driven work, where decisions are made at the point of variance. This thread runs from the 1990 argument to the AI agents of Module 4.
  - How to use it on a quiz: it answers "what does it require you to do first?" Ask Hammer's prior question, "should this step exist in this shape at all?", before labeling anything an automation candidate.
- Ford: eliminated invoice mismatches instead of chasing them faster.
- Mutual Benefit Life: replaced a roughly 30-step, 5-department, 19-person relay with one case manager. Turnaround fell from as long as 25 days to as little as 4 hours.
- Sequence it requires: redesign first, automate second, and roll out progressively rather than Big Bang.

**What "first" means**
- Redesign the process from a blank sheet, asking whether each step should exist at all.
- Do it selectively, concentrated where value is created or lost, not reshaping the whole business to fit the platform.
- Find those spots with the Four Lenses (Week 2).
- Design adoption in from day one: the people inside the process help diagnose and reshape it.

**Sweetgreen tie-in**
- The RPA scan rejected the stock-accuracy root cause behind the freshness mismatch. A bot that keeps re-checking a stale cache faster would pave the cow path. The real fix is closing the sync gap between Olo and Crunchtime.

**Likely follow-ups**
- "Is every project that misses its business case a failure to leverage?" Not always. Mixed cases exist, and Nike is cleaner than Birmingham once you separate the working ERP from the misused planning layer.

## Question 2: RPA candidate criteria and the D3 step

**The three criteria (Week 4)**
- Repetitive: high, recurring volume, so the bot's fixed cost is spread over many transactions. Thermo Fisher's order entry (over 10 million transactions and interactions a year) is the anchor.
- Rules-based: every case is decided by explicit, complete logic, with no point where a human must exercise judgment.
- Stable: the process and the screens it runs on rarely change, because RPA drives screens and breaks when they move.
- A step must pass all three, or it is not a candidate. It goes either to redesign or to an AI/judgment path.

**D3 in the Sweetgreen project**
- D3: "Which recovery route is agreed?" Staff assess the options for a blocked order and the customer consents.
- Why it looks automatable: it is repetitive (every exception reaches it) and works on structured data (order, availability, ETA).
- Why it fails rules-based: no fixed rule says which substitution, discount or cancellation to offer, or when to escalate.
  - It depends on customer urgency, prep ETA and wait time.
  - Two reasonable staff members could offer different resolutions to the same customer. That is the definition of a judgment call.
  - The customer must also consent, which a bot cannot supply.
- Stability does not rescue it. The scan marks stability N/A because it fails on rules.
- Where it goes instead: the AI-agent target (Week 7 / Lab 3), as a recommender with a human gate, never deciding alone.

**Contrast: D2 passes all three**
- Repetitive: every order passes through it.
- Rules-based: approve when live and cached availability agree, the item is supported and the source is fresh. Otherwise hold.
- Stable: the rule and the two systems (Olo, Crunchtime cache) change rarely.
- This is the Lab 2 build. In the Lab 1 sandbox, 6 of 30 synthetic orders (20%) hit a mismatch, costing a modeled $44 and averaging 18.7 minutes late.

**Other rejected steps (good for follow-ups)**
- D1, order acceptance: the map does not state the full acceptance rule, so automating it would lock in an undocumented policy. Fix the rule first.
- Quality gate at K: the logic is rule-based, but it verifies a physical meal, not a screen, so RPA is the wrong tool.
- Stock-accuracy root cause: a redesign job, not RPA.

**Likely follow-ups**
- "Could D3 become rules-based with enough rules?" You could write rules, but the rule set is never complete, and the Week 7 note says an incomplete rule fails silently, with full confidence, on the case it did not foresee.

## Question 3: Scaling, Center of Excellence and the Lab 2 failure mode

**Why RPA stalls: brittleness**
- A bot works through the user interface, driving the same screens a person would. That is both its appeal and its weakness.
- Selector instability: the bot finds each element by a recorded "address" (this button, in this panel, with this label). When a screen changes, the address breaks and the bot fails or acts wrongly.
- Maintenance burden: with hundreds of bots across dozens of systems, each system changes independently. Teams spend more time re-fixing bots than building new ones, so realised value plateaus and then falls.
- Week 5 names four failure modes in total: selector instability, maintenance burden, infrastructure brittleness (O2's shared virtual machine was fine until load crossed a threshold), and bot sprawl / shadow IT (undocumented bots nobody owns).
- Telefonica O2 also shows the rules-without-judgment risk. Some customers ordered the same iPhone several times, and the bot shipped the duplicates because the rule covered it.

**What a Center of Excellence does**
- A small, permanent team that owns how automation is done. It governs and enables rather than building every bot.
- Five functions and the failure each prevents:
  - Governance and standards: stops bot sprawl.
  - Intake and review: stops shadow IT by giving a sanctioned front door.
  - Ownership and monitoring: a named owner, a watched pulse and an audit trail per bot, so silent errors do not run for weeks.
  - Enablement and training: avoids the builder bottleneck by training supervised business builders.
  - Infrastructure and platform: owns the plant and scales it.
- Accountability is relocated, not removed. The CoE is where it comes to rest.
- It scales down too: O2 ran 160+ robots with 3 reassigned builders. At a small firm the CoE may be one person and a written rule.

**Lab 2 failure mode: bad or stale input data**
- Setup: a Make scenario reads CheckQueue, routes each order, and writes every decision to an AutoActions audit sheet. It is inactive and only writes audit rows.
- Test set: 7 unique synthetic orders, 2 normal and 5 problem cases (unavailable stock, blocked re-entry, missing availability, stale source, unmatched item).
- What broke:
  - The original cached-availability rule approved four problem orders and silently dropped the missing-availability case.
  - Adding a Router alone changed nothing. The rules were wrong, not the routing.
  - A guarded version caught all five but lumped them into one REVIEW bucket.
  - Final three-outcomes rule: APPROVE, STAFF_REVIEW (operational problem), DATA_REVIEW (bad input). One run gave 2 approvals, 2 staff reviews and 3 data reviews.
- Why this is the key failure: nothing crashed. The bot ran confidently on bad inputs, which is the quiet kind of failure.

**Human-oversight controls it implies**
- Staff review for operational problems: the shift lead holds the order and assesses the D3 recovery.
- Data review for bad inputs: the integration owner repairs the input and re-runs D2.
- Precedence rule: staff holds win when an operational flag and a data problem coexist.
- Audit log of every decision, so errors can be reconstructed.
- Freshness limit (60 minutes, illustrative) so stale data is routed to a person rather than trusted.
- Consent and recovery (D3, CP3) stay human.

**Limits to be honest about**
- Frozen historical sandbox, not a live kitchen feed.
- Owner roles are proposed, not verified Sweetgreen assignments.
- The ROI (payback about 1.12 months, from unmeasured inputs) shows only that routing works, not that money is saved.
- Not yet built: duplicate protection, schema validation, reviewer assignment and closure, consent capture.

## Favorite case: Birmingham City Council (2022-23)

**Facts**
- April 2022: the largest local authority in Europe went live on Oracle Cloud Fusion for finance and HR, replacing a long-standing SAP system.
- The original business case was modest.
- It bent the platform to legacy ways of working instead of re-engineering the processes.
- It went live in a Big Bang cutover with known control weaknesses unresolved.

**What broke**
- Transactions posted incorrectly, and the council could not produce reliable reports or reconcile its accounts without heavy manual work.
- It lost its single source of truth, the Week 1 idea that every function must be able to read and trust one record.
- Costs ran to many times the original business case (Sheffield Audit Reform Lab).
- 5 September 2023: Section 114 notice, the local-government equivalent of being unable to balance the budget.

**The contested cause (the part that makes it my favorite)**
- Council: equal-pay liability plus an in-year budget gap. Its statement did not name Oracle.
- Sheffield Audit Reform Lab: the equal-pay figure was unaudited and used to deflect from the IT failure. "Oracle seems the more likely explanation."
- External auditor: Oracle was a contributory factor, with governance and optimism at fault rather than the technology.
- Some experts argue the council may never have been bankrupt at all. The commissioners reject that.
- Lesson: when you lose the single source of truth, you lose the ability to account for what went wrong.

**Connection to the quiz concepts**
- Q1: a clear failure to leverage, since the software was fit for purpose. The failure was the skipped redesign and the Big Bang.
- Nike 2000 is the same trap a generation earlier. A planning engine was layered on unredesigned processes and rushed live with under-trained planners. The result was about $100M in lost sales and a roughly 20% stock drop. Nike recovered by slowing down, retraining and moving planning back into SAP.
- Both are stories of a Unification ambition (one process, one truth) without the redesign and adoption work that earns it.
- Thread: Cash Management with an Operations overlay. Nike was the reverse.
- Q3 link: the same "confident on bad data" failure, with the audit trail gone.
