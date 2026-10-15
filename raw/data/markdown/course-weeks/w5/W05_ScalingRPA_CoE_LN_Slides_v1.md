---
title: W05_ScalingRPA_CoE_LN_Slides_v1
type: study-note
tags: [course-week, w5]
sources:
  - id: pdf-original
    resource: raw/data/pdf/course-weeks/w5/W05_ScalingRPA_CoE_LN_Slides_v1.pdf
---
# W05_ScalingRPA_CoE_LN_Slides_v1

| MO DULE |   2       | ·      THE   AUTO | M ATI | O N  LADDE | R   |     |     |     |
| ------- | --------- | ----------------- | ----- | ---------- | --- | --- | --- | --- |
Scaling RPA + the Center of Excellence
| Ten bots is a demo. A thousand is an operation — |     |     |     |     | and someone has to | run it. |     |     |
| ------------------------------------------------ | --- | --- | --- | --- | ------------------ | ------- | --- | --- |
Friday, October 2, 2026   ·   8:00–10:30 AM   ·   2 MTC Room 802
| IE-GY 9113B — | Systems Integration: From ERP to Agentic AI   ·   Prof. Emanuele Cimica |     |     |     |     |     |                                            |     |
| ------------- | ----------------------------------------------------------------------- | --- | --- | --- | --- | --- | ------------------------------------------ | --- |
| NYU TANDON    |                                                                         |     |     |     |     |     | IE-GY 9113B · Systems Integration · Week 5 | 1   |

CLASS OPENING 8:00
Today: rebuild the spine, work Telefónica O2, then design your CoE
The note gave you the concept. Today you apply it to your own company and design the organisation that scales it.
1 Activation 8:05 Live, timed team retrieval —not a recap. Your answers are the entry ticket to the breakout.
2 Reconnect + story 8:20 From your RPA scan to the scaling cliff; then Telefónica O2 — the programme that actually scaled.
3 The CoE, worked 8:34 What breaks at scale, the operating model that answers it, and reading a vendor case critically.
Three asks in one working block while I come round; then each team reports out —your CoE / operating model
4 Apply — team build 9:02
(Board Memo §4, slide S7).
5 Prime Lab 2 10:08 You'll build your Lab 2 first pass at home; class breaks it and adds oversight.
6 Homework + wrap 10:18 The CoE section · build your Make first pass · keep the board deck evergreen.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 2

8:03
BE FO RE W E S TART
20 bots: a triumph.
400 bots: a crisis nobody owns.
The pilot is the easy part. Today is what happens next — why programmes die on the way to scale, and the organisation that
keeps them alive. We start now, together.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 3

ACTIVATION · RETRIEVAL 8:05
Q1 — Where are we on the ladder?
make agentic AI agents (Module 3) → the agentic enterprise (Module 4)
make intelligent Intelligent automation (Module 3)
automate RPA — still Module 2. Last week you placed one bot; this week you run a hundred. ◄ you are here
integrate The integration backbone — one single source of truth (Module 1)
One programme, three threads. Last week it was one robot, three threads. This week the same threads — Customer, Operations & Supply Chain, Cash — at the
scale of a whole programme.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 4

ACTIVATION · THE QUESTION 8:07
Q2 — Your pilot worked. Why do most programmes die at scale?
The demo The operation
Two weeks, a happy sponsor. A hundred bots nobody owns.
Pick a high-volume, rules-based step, point a bot at it, and in The same surface-level fragility that made one bot cheap makes
weeks you have a working automation. The most reliable demo a thousand expensive to keep alive. Screens move, integrations
in enterprise tech — the play you learned in Week 4. drift, the plant buckles, and bots multiply with no owner.
Two-sided question. Why does a programme that works brilliantly small break as it grows — and what organisation, deliberately built, keeps it alive? That second half
is your Board Memo §4.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 5

8:09
ACTIVATION · RETRIEVAL
| Q3 — | Name the four ways a programme breaks at scale |     |     |     |     |     |
| ---- | ---------------------------------------------- | --- | --- | --- | --- | --- |
Think 30 s →   confer with your team   →   a team gets cold-called
You met all four in the note. Two are engineering problems. Two are… you tell me.
|     | 1   | 2   | 3   |     | 4   |     |
| --- | --- | --- | --- | --- | --- | --- |
Name them first — then we reveal.  And once they're up, we vote on which one kills most programmes.
| NYU TANDON |     |     |     | IE-GY 9113B · Systems Integration · Week 5 |     | 6   |
| ---------- | --- | --- | --- | ------------------------------------------ | --- | --- |

8:11
| ACTIVATION · RETRIEVAL — REVEAL |     |     |     |     |
| ------------------------------- | --- | --- | --- | --- |
The four ways a programme breaks at scale
Infrastructure
| Selector instability | Integration drift |     |     |     |
| -------------------- | ----------------- | --- | --- | --- |
Bot sprawl / shadow IT
brittleness
| A screen moves; the script  | The estate moves under the  |     |     |     |
| --------------------------- | --------------------------- | --- | --- | --- |
Bots nobody owns.
| fails. | bots. | The pilot plant can't run the  |     |     |
| ------ | ----- | ------------------------------ | --- | --- |
Easy to build, no sanctioned
| A vendor update renames a  | Dozens of systems, each  | programme. |     |     |
| -------------------------- | ------------------------ | ---------- | --- | --- |
path — teams stand up their
field — the bot stops, or runs  patched on its own schedule;  What carried ten bots
own, unmonitored.
on confidently. the surface drifts. collapses under hundreds.
Hands up — which one kills most programmes? Vote for each as we point.
Three are engineering; the fourth is organisation.  Bot sprawl has no technical cause — and it is the one this week answers.
| NYU TANDON |     |     | IE-GY 9113B · Systems Integration · Week 5 | 7   |
| ---------- | --- | --- | ------------------------------------------ | --- |

8:12
ACTIVATION · RETRIEVAL
Q4 — What does a Center of Excellence do? Name its five functions
Think 30 s →   confer with your team   →   a team gets cold-called
You named the disease — bot sprawl. Now the cure: five jobs one organisation owns.
|     | 1   | 2   | 3   | 4   | 5   |     |
| --- | --- | --- | --- | --- | --- | --- |
Cover them as a team before we reveal.  If you can name five jobs, you can design one for your company in the breakout.
| NYU TANDON |     |     |     | IE-GY 9113B · Systems Integration · Week 5 |     | 8   |
| ---------- | --- | --- | --- | ------------------------------------------ | --- | --- |

ACTIVATION · RETRIEVAL — REVEAL 8:14
A Center of Excellence — and its five functions
Governance & standards Who may build, how, and how a bot is approved before it goes live.
Intake & review A sanctioned front door for demand — the antidote to the shadow door.
Bot ownership & monitoring Every bot has an owner and a watched pulse; the audit trail catches a silent error.
Enablement & training Turns willing business people into capable, supervised builders.
Infrastructure & platform Owns the plant and scales it in step with the programme.
The CoE governs; it does not personally build everything. It makes automation a governed capability, not a pile of scripts.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 9

ACTIVATION · THE MINDSET 8:15
Q5 — Scarcity says hoard the experts. Scale says…?
Scarcity mindset Scale mindset
Hoard a few experts. Multiply the builders.
A central team builds one at a time. The queue is a lifetime of Capture the flood safely — a dam with guardrails: many
work; the ninety-ninth process never gets touched. supervised builders under the CoE's governance.
The dam, not the bottleneck. A CoE that only builds is a bottleneck with a nicer name — and a sanctioned way to build is the direct answer to shadow IT.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 10

ACTIVATION · RETRIEVAL 8:16
Q6 — “Rules-based” does not mean “no human needed.” Where does
a human stay?
Think 30 s → confer with your team → a team gets cold-called
A bot follows a wrong rule with perfect confidence. So where do you keep a person — and why there?
Decide the ‘where’ as a team before we turn the page. This is one of your three study questions — and it seeds Board Memo §5.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 11

ACTIVATION · RETRIEVAL — REVEAL 8:17
Automate the routine; route the judgement — on purpose
The trap The move
A wrong rule, run with confidence. Route the exceptions on purpose.
A bot doesn't pause, doubt, or notice the thing a person would Automate the routine; send edge cases, high-value
catch out of the corner of their eye. transactions, and irreversible actions to a human checkpoint.
Accountability is relocated, not removed. If a bot is silently wrong for weeks — who is accountable? That's the week's ethics thread, and the CoE is where it lands.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 12

ACTIVATION · ASSEMBLED 8:18
The spine, in one line
A pilot proves the logic; it does not prove the plant that runs it at ten times the volume. Scaling is an operating-model decision before it is a
technology one.
→ What breaks — selectors, integrations, infrastructure — and the organisational one, bot sprawl.
→ The answer — a Center of Excellence — governance, ownership, enablement — that makes automation a hard-to-copy capability.
→ Your job today — design that operating model for your company → Board Memo §4 (slide S7).
This week you design the organisation, not another bot. The deliverable is the operating model a board funds — the CoE / operating-model section of your memo.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 13

ACTIVATION · ENTRY TICKET 8:19
Your ticket into the breakouts
IN YOUR TEAM, WRITE ONE LINE
The single biggest scaling risk on your RPA candidate — the
stable-rules step from your §4 scan.
That line is your entry ticket to Breakout 1.
No line, no ticket. Breakout 1 starts from exactly what you write here.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 14

8:20
RECONNECT · CONTINUITY
You named where a bot belongs. Now: who runs a hundred of them?
The turn
| From Week 4 | This week |     |
| ----------- | --------- | --- |
A pilot at three bots behaves nothing
Your RPA-candidate scan (§4) named  Design the operating model that scales
like a programme at three hundred —
the stable-rules steps worth a bot. One  it and keeps it alive — the CoE section
the fragility you met last week,
| robot, three threads. | that extends §4. |     |
| --------------------- | ---------------- | --- |
multiplied.
Last week: where a bot belongs.  This week: the organisation that lets a company actually run them — still inside the Diagnose phase (Milestone 1).
| NYU TANDON | IE-GY 9113B · Systems Integration · Week 5 | 15  |
| ---------- | ------------------------------------------ | --- |

STORY · PRIMARY CASE 8:24
Telefónica O2 — the programme that actually scaled
The case in brief Telefónica O2 ran a real RPA programme inside its back office. A two-process pilot went live in about two weeks and worked — the
easy part. The case is about the climb that followed: taking it from two processes to running the whole back office, where most of the real work, and the
real risk, live.
The setting Why we study it
The question on the table
A major UK telecom. The work is ordinary, An independent, peer-reviewed field study
A working pilot proves the logic, not the
high-volume, rules-based back-office — Lacity & Willcocks (2016), open-access,
operation that must run every day. O2 made
administration — the repetitive transactions not a vendor success story. One of the few
the climb; the interesting part is how. You'll
that run an operation, and the same kind of rigorous accounts of an RPA programme
make the first call yourself in a moment.
process you flagged in your Week 4 scan. that actually scaled.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 16

8:28
STORY · YOU DECIDE
You run O2's Back Office. The pilot works at 20 bots. Do you scale?
In your team, commit to one — then we'll see what O2 did, and how lightweight RPA compared to a heavier BPMS rebuild.
| A — Scale now |     | B — Fix the plant first | C — Hand it to IT |     |
| ------------- | --- | ----------------------- | ----------------- | --- |
Push more bots onto the same setup  Re-engineer the infrastructure for load  Give it to IT to build on their queue and
and keep the momentum. The pilot  before adding bots. Slower start, fewer  standards. Safe — but no longer yours
| works — | why wait? | surprises. | to run. |     |
| ------- | --------- | ---------- | ------- | --- |
Commit before you turn the page.  One of these cost O2 ~16 weeks of rebuild. Decide which — then see.
| NYU TANDON |     |     | IE-GY 9113B · Systems Integration · Week 5 | 17  |
| ---------- | --- | --- | ------------------------------------------ | --- |

STORY · WHAT HAPPENED — THE REVEAL 8:31
The operating model was the differentiator — not the technology
Back-Office-owned The collapse (answer: B)
The programme lived in the Back Office, not IT — builders were On a ‘lead’-VM setup it worked at ~20 bots; when the count quadrupled it
reassigned process staff, so no wait on IT's queue. fell over — ~16 weeks re-engineering the plant.
Same processes, two approaches: RPA (lightweight automation over existing screens) vs a heavier, IT-led BPMS. Same capability —very different payback:
RPA ~10 months
BPMS ~3 years
“It was like driving a Ferrari with a lawn mower engine.” The gap was operating model and IT resource, not technology. (Lacity & Willcocks, 2016.)
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 18

STORY · THE RESULT 8:34
From a two-process pilot to the back office — on three threads
180
~35% of back-office transactions
160
15 core processes · 400k–500k transactions a month
140
n 120
o
itc
u Chase-up calls down >80%
d 100
o
r
p
n i
s
80 turnaround days → minutes (Customer + Cash)
to
60
B
40
~650–800% three-year ROI
20
0 hundreds of FTEs redeployed · built by 3 in-house developers
Pilot Scaled
A dull capability, run well at scale. The win came from the operating model, not a clever bot — exactly the case you'll make for your own company. (Lacity &
Willcocks, 2016.)
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 19

STORY · WHAT O2 TEACHES 8:36
Five lessons the scaled programme leaves you
1 A pilot proves logic, not the plant Working at ten bots says nothing about a hundred.
2 Operating model beats technology Same tool, different owner — 10 months vs. 3 years.
3 Own it where the work lives Back-Office ownership removed the IT-queue dependency.
4 Infrastructure is a CoE job The lead-VM collapse is what a CoE exists to prevent.
5 Scale the builders, not the queue Three builders ran 160+ bots by governing, not gatekeeping.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 20

THE CLIFF · WHY PROGRAMMES STALL 8:38
Ten bots is a demo; a thousand is an operation
120
→
s 100
r
e
v
ile
d 80
e
m
m
60
a
r
g
o
r p 40
e
h
t
e 20
u
la
V
0
0 50 100 150 200 250 300 350 400
Bots in production →
With a Center of Excellence Without a CoE (the cliff)
The cliff is not a technology limit — it is a missing capability. Past a threshold, capacity goes to re-fixing broken bots instead of building. A Center of Excellence is
what keeps the curve climbing — the difference between a demo and an operation.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 21

8:40
THE COE · WHAT IT IS
A company has no brain for automation, so it builds one
| Business | Center of Excellence | IT  |     |
| -------- | -------------------- | --- | --- |
Supplies the demand and the process  Converts scattered requests into governed,  Supplies the platform, identity, and security
| →   | →   |     |     |
| --- | --- | --- | --- |
knowledge — what is worth automating, and  owned, monitored automation. Governs; does  guardrails — the plant the programme runs on.
| how the work really runs. | not personally build everything. |     |     |
| ------------------------- | -------------------------------- | --- | --- |
The CoE sits between the business and IT.  O2 ran all five functions with three reassigned builders; Tella's review pipeline is the sanctioned front door — a governed
capability a competitor can't quickly copy, not a bigger bot factory.
| NYU TANDON |     | IE-GY 9113B · Systems Integration · Week 5 | 22  |
| ---------- | --- | ------------------------------------------ | --- |

8:43
THE FIELD · DELOITTE (2022)
Settled practice — and the hardest barriers aren't technical
|     | The barriers | Citizen-led development |     |     |
| --- | ------------ | ----------------------- | --- | --- |
74%
Process fragmentation, unclear vision, IT  Trained non-technical staff build low-complexity
readiness, resistance to change — none of  automations: a complement to the CoE, under
|     | them the technology. | its governance — | never a replacement. |     |
| --- | -------------------- | ---------------- | -------------------- | --- |
already running RPA — infrastructure, not an
experiment.
The barriers are organizational — exactly what a CoE is built to answer.  Programmes stall on fragmented processes, unclear vision, IT readiness, and resistance
to change — people and process, not the technology.
| NYU TANDON |     | IE-GY 9113B · Systems Integration · Week 5 |     | 23  |
| ---------- | --- | ------------------------------------------ | --- | --- |

THE MINDSET · SCALE IT RIGHT 8:46
Standardize AND empower — and the capability becomes hard to copy
The hard-to-copy capability
Both, not either
Where the advantage lives.
Westerman, Ch. 3.
A rival can buy the same RPA tool tomorrow. What it can't
Standardize the platform and the guardrails; empower many
quickly copy is the operating model that runs hundreds of
people to build within them. Not a trade-off — the two together
governed automations — the moat is the organisation, not the
are what let automation scale.
software.
Scale the builders under governance — the dam with guardrails. A CoE that only builds is a bottleneck with a nicer name; one that enables supervised builders is
the answer to shadow IT.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 24

THE HUMAN · IN THE LOOP 8:49
Automate the routine; route the judgement — on purpose
Unattended
Attended
Runs on its own.
Runs beside a person.
On a schedule or a queue, no human present — clearing
Triggered by them, on their machine — a hand on the wheel,
routine volume overnight. For work that needs no case-by-case
ready to take over. For work that sits near judgement.
eyes.
A bot follows a wrong rule with perfect confidence. So route edge cases, high-value transactions, and irreversible actions to a human checkpoint. You'll name and
build that oversight in Lab 2.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 25

8:52
THE ETHICS THREAD
If a bot is silently wrong for weeks — who is accountable?
| The failure |     | The CoE answer |     |     |
| ----------- | --- | -------------- | --- | --- |
The board question
A bot follows its rule confidently even  Bot ownership + monitoring + an audit
How should liability for automated
| when the rule is wrong for the case in  |     | trail: accountability is relocated to a  |     |     |
| --------------------------------------- | --- | ---------------------------------------- | --- | --- |
errors be structured — and what does
| front of it — | and no one notices for  | named owner, not removed by  |     |     |
| ------------- | ----------------------- | ---------------------------- | --- | --- |
that imply for how you design the audit?
| weeks. |     | automation. |     |     |
| ------ | --- | ----------- | --- | --- |
Automation does not remove accountability; a CoE relocates it to someone who owns it.  This is Board Memo §4 — and it grows louder in §7, the human-AI
partnership.
| NYU TANDON |     |     | IE-GY 9113B · Systems Integration · Week 5 | 26  |
| ---------- | --- | --- | ------------------------------------------ | --- |

READING THE EVIDENCE 8:55
Two telecoms, two kinds of evidence
Orange Spain ‘Robot Factory’
Telefónica O2
UiPath customer case (vendor-reported).
Peer-reviewed (Lacity & Willcocks, 2016).
~13 → ~100 people, 400+ bots, >€34M over a little over two
Independent research. It establishes what is true: the operating-
years. Marketing: it illustrates a shape — it does not verify a
model finding, the payback numbers, the scale. Load-bearing.
number.
Read a vendor case critically. Never let a vendor number carry a load-bearing claim; corroborate any figure you rely on; capture title, publisher and date so a dead
link stays traceable.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 27

9:02
| AP P LY  | ·  BY  | P RO J E CT TE | AM  |     |     |
| -------- | ------ | -------------- | --- | --- | --- |
Design your Center of Excellence
The next hour produces a real deliverable: the operating model a board would fund — Board Memo §4 (slide S7). Work all three asks
as a team while I come round to each of you; then each team reports out, and you leave with it built.
| NYU TANDON |     |     |     | IE-GY 9113B · Systems Integration · Week 5 | 28  |
| ---------- | --- | --- | --- | ------------------------------------------ | --- |

9:05
APPLY · WORK BLOCK
Build your Center of Excellence — three asks, one block
Work all three in your team — I'll come round to each as you go.
1 · What breaks at scale 2 · Your CoE / operating model 3 · Place the human + cost it
Take your entry-ticket risk and your §4 candidate. The deliverable —Board Memo §4. Take one automation in your programme.
| Floor | Floor | Floor |     |
| ----- | ----- | ----- | --- |
– Which of the four failure modes hits your candidate  – One line per the five functions —who does each at  – Which edge cases, high-value, and irreversible steps
| first? | your company? | get a human? |     |
| ------ | ------------- | ------------ | --- |
– Selector instability: name one system update that  – Who owns, builds, governs, and funds automation? – Attended or unattended —for each bot?
would break your script. – Scale it to your archetype (smallest may be one  – A simple ROI line: recurring work removed vs the
– Rank them —which breaks soonest from one bot to a  owner + a rule). CoE's cost.
hundred?
|     | Stretch                                       | Stretch                                        |     |
| --- | --------------------------------------------- | ---------------------------------------------- | --- |
|     | – Name the hard-to-copy capability it builds  | – If a bot is silently wrong for weeks —who's  |     |
Stretch
– Which are an engineering fix, and which need an  (Westerman). accountable, and how would an audit catch it?
owner? – How does your intake stop shadow IT before it starts? – What's the workforce obligation if a role changes?
– Where would a shadow, unsanctioned version appear
first?
9:05–9:47 · about 14 minutes an ask.   By 9:47 you have ranked scaling risks, five functions + ownership, and human checkpoints with a simple ROI line — your CoE /
operating-model section, Board Memo §4 (slide S7).
| NYU TANDON |     | IE-GY 9113B · Systems Integration · Week 5 | 29  |
| ---------- | --- | ------------------------------------------ | --- |

APPLY · REPORT-OUT 9:47
Each team tells its story — together they're the class's answer
What you present
The format
Your three answers as one line of reasoning: the risks that would
About 3 minutes to present, 2 minutes feedback and questions.
break it → the operating model that holds it → where the human
Four teams, roughly twenty minutes — every team is heard.
stays and what it costs.
What leaves the room Your CoE / operating-model section — five functions, the ownership model, the human checkpoints, and a simple ROI line. → Board Memo
§4 (slide S7), still in Diagnose.
You've designed the organisation that runs automation — not another bot. Next week you build one bot in Make and break it; this CoE thinking becomes the
oversight you wire in.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 30

PRIME · LAB 2 (WEEK 6) 10:08
Next: build your first pass at home — class breaks it
Build at home, before class
Refine, break, harden — in class
Following the Lab 2 note (§3), build a first-pass Make scenario
Arrive with it built (or honestly attempted). Class refines the
on your candidate: trigger → condition → action, connecting two
happy path, then breaks it on the flaws you seeded in Lab 1 —
systems; run it once and produce a real output. Budget ~1.5–2
where it breaks is where human oversight belongs.
hours.
The gate at the door: a built (or attempted) scenario + your board deck current through S5. A refine-and-present session has nothing to refine if you never
attempted the build — the deliverable is a working-workflow screenshot + a one-page post-mortem (→ §4).
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 31

PRIME · BEFORE THE LAB 10:12
Set up the connection, build the pass, and one rule
Set up first
The one rule
Make + your sandbox.
Find where it breaks.
Create a free Make account; set up the Connection to your Lab 1
A scenario that runs perfectly taught you nothing. The failure
sandbox first (import Excel to Google Sheets if needed), then
mode you capture is the lesson — this week's fragility, met at one-
connect a second system — Gmail or Slack. Half of all first-build
bot scale.
snags are the Connection.
Stuck at home is fine — empty-handed is not. If it stalls, bring the module where it broke and the exact error; the lab opens with a ~25-minute recovery window.
What you can't do is arrive with nothing to refine.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 32

PRIME · WHERE THIS POINTS 10:15
Where this points
→ §4 CoE section done → Lab 2 (Week 6) builds the bot and the one-page post-mortem.
→ The human-in-the-loop boundary → carries into agent governance (§5) and the workforce question (§7).
→ Scaling governance → the company's Stabilise → Automate → Orchestrate roadmap, Week 11.
→ Your judgement step → intelligent automation (Week 7), SPAR (Week 8), the agent build (Lab 3, Week 9).
One programme, three threads. A board funds a thread outcome — Operations & Supply Chain, Cash, Customer — not a bot.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 33

THE LIVING DELIVERABLE 10:16
Your board deck and memo are living documents — keep them
evergreen
Every week adds a slide Reviewed at every lab
By December it assembles itself
Each session's homework fills a defined Labs are interim reviews. Lab 2 checks
Keep the deck and memo current as you
part of the board deck and memo. two things at the door: your built scenario
go and practise the story each lab. The
Today's CoE section is Board Memo §4 / and your board deck current through S5.
final board presentation is then an edit,
slide S7. Add it while it's fresh — don't let Old, unfilled slides mean you spend the
not a scramble.
it queue. lab catching up, not adding.
Evergreen, not end-loaded. The team that updates every week walks into the final review ready; the team that saves it for December rebuilds under pressure.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 34

HOMEWORK · BEFORE NEXT WEEK 10:18
Before next week
1 Draft Your CoE / operating-model section → Board Memo §4 (Automation journey, slide S7).
Create your Make account and build your first-pass scenario at home (Lab 2 note §3): trigger → condition → action, run
2 Set up + build
once. Gated — class refines and breaks it.
3 Bring to the lab A built (or honestly attempted) scenario AND your board deck current through S5 — both are checked at the door.
Forum 1: your two peer replies are due Sat Oct 3 (Brightspace → Discussions). Forum 2 — the October forum — opens
4 Discussion Forum
later this month.
You leave with the organisation that runs automation. The operating model a board funds — not just a bot. The section is the argument; the build is Lab 2.
NYU TANDON IE-GY 9113B · Systems Integration · Week 5 35

10:22
| W E E K 5 |  ·  S CALI | NG  RP | A  +  COE |     |     |
| --------- | ---------- | ------ | --------- | --- | --- |
Ten bots is a demo.
A thousand is an operation.
Next · Week 6: Lab 2 —Automate the Repeatable Part
| NYU TANDON |     |     |     | IE-GY 9113B · Systems Integration · Week 5 | 36  |
| ---------- | --- | --- | --- | ------------------------------------------ | --- |
