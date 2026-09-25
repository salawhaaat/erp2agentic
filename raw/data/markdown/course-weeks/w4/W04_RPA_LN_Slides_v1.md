---
title: RPA — The Tactical Integration Layer (Lecture Slides)
type: study-note
tags: [study-note, week4, rpa, sweetgreen, lecture-slides]
---
# Module 2 · RPA — The Tactical Integration Layer

*IE-GY 9113B — Systems Integration: From ERP to Agentic AI · Prof. Emanuele Cimica*
*Friday, September 25, 2026 · 8:00–10:30 AM · 2 MTC Room 802*

> In-class lecture/breakout deck, companion to [[W04_RPA_StudyNote|the Week 4 study note]] — the note is the reading, this is the room's run of show. Same structure as [[W3_Lab1_Lecture-Notes]]: activation questions, a worked story, a worked case, then three team breakouts producing the actual deliverable.

## How today runs — 8:00

| # | Block | Time | What happens |
|---|---|---|---|
| 1 | Activation | 8:05 | Rebuild the week's spine from memory — the floor everyone joins from |
| 2 | Reconnect + story | 8:19 | Back to obliterate-then-automate and your Lab 1 decision point; then Thermo Fisher |
| 3 | Two cases, worked | 8:35 | Automate the rule, route the exception — Thermo Fisher and Bailey, then the scan on Citi Bike |
| 4 | Apply — 3 breakouts | 9:03 | By team, finish your Lab 1 map and build the §4 piece: your RPA-candidate scan |
| 5 | Prime Week 5 | 10:13 | Scaling RPA and the Center of Excellence — why bots stall past a handful |
| 6 | Homework + wrap | 10:22 | The RPA-candidate scan · read the Week 5 note |

## Activation — 8:05–8:17

Six retrieval questions rebuilding the week's spine from memory, before any new material.

**Q1 — Where are we on the ladder?** integrate (Module 1, the backbone) → **automate — RPA, this week (Module 2, you are here)** → make intelligent (Module 3) → make agentic (Module 4).

**Q2 — What is a "bot," really?** *Works the screens, not the plumbing* — RPA drives a company's existing applications through the user interface: clicking, reading fields, copying between screens by a fixed script. A robot that does the human's cross-system carrying. *Fast, and brittle* — speed traded for robustness: it bridges un-integrated systems in days, not months, but it breaks the moment a screen it depends on changes. A tactical patch over a missing integration, not a fix.

> [!tip] Surface, not structure.
> RPA automates the symptom of a missing foundation — a person moving data between systems. Powerful and quick; inherently fragile.

**Q3 — Three ways to take a human out of the loop.** Traditional (in the plumbing — APIs, database, native integration; robust, needs engineering; Bailey's NetSuite O2C) · RPA (at the surface — the same screens a person uses; rules-based, fast to build, brittle when a screen moves; Thermo Fisher's order-entry bot) · AI (on judgement — unstructured, ambiguous input, no fixed rule; reads intent, classifies, resolves; the exception, previewed, taught Week 7). Rule vs. judgement is the line drawn by hand in Lab 1 — it organizes the whole module.

**Q4 — What makes a good RPA candidate?** Repetitive (high, recurring volume — a bot's fixed cost pays back) · Rules-based (complete, explicit logic — no point needing judgement) · Stable (screens rarely change — a moving screen breaks the bot's brittle script). All three, or it isn't a candidate. The step that passes all three is the Lab 1 stable-rules decision point — and the Lab 2 (Make) target.

**Q5 — When should a bot NOT be built?** *The task mindset* bolts a bot onto a tedious step — a few hours come back, while the tangled process it lives in stays tangled. *The process mindset* asks what the whole flow is for, redesigns first, automates the stable residue that survives (obliterate, then automate — Week 2's Ford). Automate a broken process and you pave the cow path.

**Q6 — Where is all this repetitive work made?** MRP + S&OP, the batch-push planning layer (MRP explodes a plan into component orders, Orlicky 1975; S&OP reconciles demand with supply, Ling & Goddard 1988) — plans compute overnight, cascade, and humans clear the exceptions at dawn. RPA automates the firefighting, not the fire; the deeper cure (event-driven operations) is later work, Modules 3–4.

> [!tip] The spine, in one line.
> A working backbone throws off repetitive, rules-based exception work. Sort it: automate the stable-rules step → RPA candidate → Lab 2 (Make). Needs judgement → AI-agent target → Lab 3 (Week 9). Changes constantly / broken → redesign first (obliterate, then automate, Week 2). This week you sort the work — you are not building yet; you're producing the RPA-candidate scan that becomes Board Memo §4.

## Reconnect — 8:19: you already found this week's target

- **From Week 2:** obliterate, then automate. Ford eliminated the invoice-mismatch work — it didn't automate the chasing of mismatches faster.
- **From Lab 1:** you marked three diagnostic points on your process — two of them decision points: one with stable rules, one that needs judgement.
- **This week:** the stable-rules decision point *is* your RPA candidate. Today you formalize it and justify it — the scan for §4.

## Story · Primary case — 8:23–8:31: Thermo Fisher

The company: one of the world's largest suppliers of scientific instruments, years of mergers, a sprawl of disparate ERPs and CRMs, 10M+ transactions and interactions a year. The pain: a rep answering "where is my order?" navigated nine systems and nine screens; a routine call ran past ten minutes — a person carrying data between systems that couldn't talk. Through the lenses: Frustration (staff and customers) and Time (ten minutes for a one-line answer) — Operations first, with an immediate Customer face.

**Project Northstar** — automate the rule, route the exception: RPA + machine learning + OCR ingest incoming orders (including faxed and emailed ones) and move the data across systems of record automatically; no months-long ERP consolidation. The repetitive, rules-based order entry is automated; the ambiguous order exception routes out to a case-management portal, to where judgement lives. Processes were mapped to the click level with a delivery partner before a line was automated — process-first, bot-last, which is why Lab 1 came before this week.

**The result, on two threads:** −27% average call hold times after full deployment (Customer gain) · faster order processing accelerated cash flow (Cash gain). The win came from a bot doing something dull, reliably, at volume — not from cleverness.

## Case · The pattern — 8:35–8:44: one move, reusable on any process

"Automate the rule, route the exception" is the whole craft of the week. Run every step of a mapped process through three tests and it sorts into three destinations:

| Result | Routes to | Why |
|---|---|---|
| Passes all three (repetitive + rules-based + stable) | RPA | Your Lab 2 (Make) build |
| Needs judgement | AI | Two reasonable people route it differently — Lab 3 (Week 9) |
| Broken / unstable | Redesign | Automating it just paves the cow path — fix it first |

**The three-way split, on one order-to-cash step (order entry):** Traditional — order → inventory reservation → ledger entry, underneath the interface (what Bailey has: native integration, no screen involved). RPA — a bot logs into the order tool, reads the fields, types them into the separate finance system: same outcome, riding the surface, brittle to a screen change. AI — the order that arrives as a free-text email, or the dispute that fits no rule: something must interpret, not transcribe.

### Running example: Citi Bike (your Lab 1 worked example)

The same annotated process map from [[W3_Lab1_Lecture-Notes]], carried forward: ★ control point (Task created — data born) · ◆ decision points (Empty/Full?, stable-rules; Which truck/reroute?, judgement) · red dashed rejection/rework path (reject → reroute → re-serve late) · ⚡ value leaks (Four Lenses) · a missing link (the demand forecast the system records but never consumes).

**◆ Empty/Full? → RPA.** Repetitive · rules-based · stable. Automate the trigger → Lab 2 (Make). Brittle where it rides the nightly status feed — build the human checkpoint, then break it on the stale feed. Thread: Operations (empty docks → Customer; fleet hours → Cash).

**◆ Which truck / reroute? → AI.** Two stations compete — no clean rule for which shortfall to serve first when trucks are scarce. Judgement → Lab 3 (Week 9). Not this week's target.

> [!tip] RPA automates the firefighting, not the fire.
> The bot speeds the reactive trigger; the prize — the demand forecast the system already records but never consumes — is a redesign for later. Synthetic: ≈1 in 7 of 57 rebalancing tasks hit rework, re-served 40–70 min late. This is the shape of your §4 scan → slide S6.

## Case · Working-backbone baseline — 8:41: Bailey Hydraulics

Before: a mid-market hydraulic-components manufacturer on a customized legacy ERP, storefront bolted on separately — orders moved by hand between web and back end, financial close at 20 days. After: one NetSuite platform gave order-to-cash a single source of truth; placement and fulfilment became continuous. Close fell from 20 days to 3. The lesson: that gain came from native integration — the plumbing — not a bot. When systems become one, whole "carry data between screens" tasks simply vanish. **Ask what integration already owns before you point a bot at a seam** — given a working backbone, what would RPA still change? Often less than you'd think, at the manual edges only.

## Case · Cost structure — 8:44–8:53

**Marginal cost collapses toward ≈0 per transaction after build** — variable labour becomes a fixed cost. Worked estimate: 3 minutes × 500 times a day ≈ 25 hours a day, three to four people. A bot takes out the rules-based bulk (exceptions still go to a human); the board case is recurring labour removed vs. one-time build + licence, as a payback period. This is why "repetitive" is the first test — a bot on low volume is a fixed cost with nothing to spread it over.

**The same sentence describes a person.** "Marginal cost collapses toward zero" means hours a human used to spend are no longer needed for that task. Sometimes real: freed from moving data, a specialist works the judgement-heavy cases a bot can't touch — genuinely better work. Sometimes a story: "redeployment to higher-value work" can be the phrase a firm uses to avoid a harder conversation. **Ethics thread, held open:** when RPA removes the routine part of a role, what does the firm owe the person? Board Memo §7. Most firms Deloitte surveyed hadn't even calculated the workforce impact.

**Attended vs. unattended — "rules-based" ≠ "no human needed."** Attended: runs beside a person, triggered by them, a hand on the wheel — for work near judgement. Unattended: runs on its own, on a schedule or a queue — for high-volume work needing no case-by-case eyes. A bot follows a wrong rule with perfect confidence — route edge cases, high-value transactions, and irreversible actions to a human checkpoint. Name that oversight in Lab 2; Week 5 governs it.

**The market — Deloitte (2022), settled practice, not a bet.** 74% already implementing RPA — infrastructure, not an experiment. Payback lengthened 16 → 22 months as firms invest more to get more (one exec's >70% cost cut came only after radically re-engineering the process). Top scaling barriers: process fragmentation, unclear vision, IT readiness, resistance — none of them the technology (Week 5's Center of Excellence). ~44% of mature adopters already moving from task bots toward end-to-end automation, another ~48% planning to.

## Apply — 9:03: the three breakouts

By project team. Output across all three: the RPA-candidate scan, §4 of Board Memo, slide S6 (Automation opportunity), still inside Milestone 1 (Diagnose).

### Breakout 1 — Finish your map, then sort the work (9:03–9:26, 20 min + 3 debrief)

Pull up the Lab 1 map. Confirm it carries the stable-rules ◆ point and the judgement ◆ point — finish any gap. Walk it end to end; tag each step traditional / RPA / AI. Circle the one or two steps a bot could plausibly run.

*Stretch:* name what native integration already handles, so a bot isn't pointed at a seam a real integration should own. Flag any step that only looks rules-based until inspected (as Citi Bike's Empty/Full trigger is, until the stale feed).

**Output:** a finished map + a tagged process — each step marked traditional / RPA / AI.

### Breakout 2 — Run the three tests (9:26–9:52, 20 min + 6 present)

Run the candidate filter across the process and produce the scan itself — the piece that becomes Board Memo §4. For each RPA-tagged step, test: repetitive? rules-based? stable? Keep the two or three that pass all three. For each, record: the step, why it passes, and the thread it moves.

*Stretch:* name the prize per candidate (the board-level consequence — days of cash, fewer rejects). Write the honest rejections: one "redesign first," one "needs judgement."

**Output:** the RPA-candidate scan: 2–3 candidates + threads + prize, and what was rejected.

### Breakout 3 — Cost it, and govern it (9:52–10:08, 16 min + 5 assemble)

Take one candidate from the scan and make the board case — the number, and the human safeguard. Estimate volume × time saved for one candidate. Sketch the simple payback: labour removed vs. build + licence. Say whether the bot is attended or unattended.

*Stretch:* name where a human stays in the loop — which edge cases or irreversible actions get a checkpoint. State the workforce obligation the firm takes on if the role changes.

**Output:** a one-candidate ROI sketch + the human-oversight and workforce note.

## Prime — 10:13: Week 5, why bots stall past a handful

The problem: scaling RPA — the brittleness met today, multiplied. Screens move, selectors break, integrations drift; most programmes stall at a handful of bots. The answer: the Center of Excellence — the governance and operating model that lets automation scale past the pilot: standards, ownership, a human-in-the-loop by design. **The hardest barriers are organizational, not technical.**

**Study question to bring:** What is the single biggest governance risk of deploying RPA without a Center of Excellence? Answer from what you know now, then note what you expect Week 5 to add. Think about the bot that follows a wrong rule, at scale, with no one watching.

## Homework — 10:20: Discussion Forum 1 launches today

Module 1 · Brightspace → Discussions · 10% of grade. Post by Wed Sep 30; two peer replies by Sat Oct 3. A 300–350-word post — graded on depth of analysis, not length or agreement: challenge an assumption with evidence, add a case or data point, or offer a reasoned alternative. Not "I agree" or a summary.

**The prompt.** *The leak:* building on your Lab 1 diagnosis (not a new case), name the single leak where your process most fails to leverage. Say which of the Four Lenses surfaces it and which thread it rings. Then make the call: obliterate and redesign, or adopt the platform standard and leave it alone? Justify the choice. *The claim:* take a position on the module's central claim — that a failure to leverage is usually a management problem wearing a technology costume. Does your diagnosis bear that out, or did you hit a genuine technology constraint? Argue from what you found.

> [!example]- Discussion Forum 1 grading rubric
> | Criterion (weight) | Unacceptable — 0% | Minimal — 70% | Competent — 85% | Effective — 90% | Mastery — 100% |
> |---|---|---|---|---|---|
> | Original Post: Analytical Argument (50%) | Summary or generic opinion; no argument, no counterargument, not actionable | Argument attempted but stays close to summary; thin reasoning, no limitation acknowledged | Clear analytical argument beyond summary, reads as usable, counterargument treated lightly | Well-reasoned argument acknowledging a real counterargument/limitation, gives an executive something to act on | Crisp argument advancing a defensible position, engages the strongest objection, executive-ready |
> | Original Post: Grounding in Cases & Frameworks (20%) | No specific reference to a course case or framework | Vague/incidental reference that doesn't shape the argument | At least one specific, correct reference that supports the point | References chosen well and integrated into the reasoning | Evidence is precise and connective, shows command of the module |
> | Substantive Peer Engagement, two responses (30%) | Responses missing, or only agree/restate/generic | One substantive response, or two that only partly clear the bar | Two responses that each add something — a case, a data point, or a reasoned alternative | Two responses that challenge an assumption with evidence or offer a reasoned alternative that advances the thread | Two responses that reshape the discussion, introducing evidence or a reframing the original author must reckon with |

## Wrap — 10:23: before next week

1. **Homework:** finish the RPA-candidate scan → Board Memo §4 (Automation opportunity, slide S6).
2. **Read:** the Week 5 note — Scaling RPA + the Center of Excellence — before the next session.
3. **Set up:** Make account, before Lab 2 (Week 6). AWS or custom path: notify and onboard now.
4. **Discussion Forum 1:** post by Wed Sep 30, two replies by Sat Oct 3 — Brightspace → Discussions (10%).

> [!tip] The scan is the argument; the build is Lab 2.
> §4 done today → §5 (Agent Design) is Module 3; §7 (Human-AI Partnership) carries the workforce question. Your stable-rules candidate → Lab 2 (Make, Week 6): build it, then break it. Your judgement step → intelligent automation (Week 7) and the agent build (Lab 3, Week 9). One robot, three threads — thread-tag every candidate, because a board funds a thread outcome, not a bot.
