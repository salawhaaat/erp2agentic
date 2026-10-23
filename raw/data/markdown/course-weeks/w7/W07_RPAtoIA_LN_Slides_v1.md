---
title: W07_RPAtoIA_LN_Slides_v1
type: study-note
tags: [course-week, w7]
sources:
  - id: pdf-original
    resource: raw/data/pdf/course-weeks/w7/W07_RPAtoIA_LN_Slides_v1.pdf
---
# W07_RPAtoIA_LN_Slides_v1

```text
NYU | TANDON




MODULE 3           ·   INTELLIGENT AUTOMATION + AI AGENTS



From RPA to Intelligent Automation

Last week your bot broke at the judgment step. This week you meet what takes it.


Friday, October 16, 2026      ·   8:00–10:30 AM      ·      2 MTC Room 802
IE-GY 9113B — Systems Integration: From ERP to Agentic AI    ·   Prof. Emanuele Cimica




N Y U T AN D O N
TODAY                                                                                                                              8:00


What this morning is for

                                                          Rebuild the spine together — where we are on the ladder, and the step a rule
    Warm-up + recall                          8:05
                                                          can't take.



    The bank that learned to read             8:25        JPMorgan COiN — a machine takes a judgment step 360,000 hours wide.




    Your team's work                          8:55        Name the AI-judgment step in your own process → Board Memo §5, slide S8.



                                                          A step back with our partners across the whole course — integrate to agentic,
    Industry panel (mid-semester)             9:45
                                                          and the board panel ahead.



    Wrap + what's next                        10:20       Your deliverable, and the SPAR loop you meet next week.

     What you walk out with: the exact piece your board deck needs next (slide S8), plus a practitioner's read on the whole
     journey you're building toward.
N Y U T AN D O N                                       IE-GY 9113B · Systems Integration · Week 7                                         2
BEFORE WE START



A bank was spending this much, every year, reading its own contracts:




360,000                                                                           lawyer- & loan-officer
                                                                                  hours a year




12,000 contracts a year · every one read and interpreted by hand · then: seconds, by machine




    Today is about the step a rule can't take, and who is accountable when a machine takes it.



Son, Bloomberg (2017); open access via ABA Journal (2017).
RECALL · YOUR TURN                                                                                             8:05


Where are we on the ladder — and what does this week
add?

        Last week you ran a bot. Which rung were you on, and which one are we climbing to now?




                                                                                          make
           integrate                    automate                                                     make agentic
                                                                                       intelligent




     Quick one — I ask, you answer. No huddle; hands up and we move straight on.
N Y U T AN D O N                                   IE-GY 9113B · Systems Integration · Week 7                         4
RECALL · REVEAL                                                                                                             8:08


The step up to intelligent automation




     You are not leaving RPA behind. You add the rung above it, for the steps a rule can't hold. Same backbone, same bots, one
     new layer.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                   5
RECALL · YOUR TURN                                                                                                           8:10


Two kinds of decision point — which gets a bot, which gets
a brain?
          You have been sorting these since Lab 1, on your process map and in what you chose to
                   automate. Recall the logic, then point to where you already met both.


   The logic                                                                        In your own work

   What makes a decision point stable-rules                                         Where on your map, or in a breakout, did you
   versus judgment? One line for each.                                              tag each kind — and how did it shape what you
                                                                                    automated?




     Talk it out in your team — 60 seconds. Then we reveal and sharpen it together.
N Y U T AN D O N                                     IE-GY 9113B · Systems Integration · Week 7                                     6
RECALL · REVEAL                                                                                                    8:13


Every decision point splits two ways




     You have been doing this since Lab 1: tagging points on your map and choosing automations around them. The costly
     pattern is a judgment point treated as a stable one, where the rule fires with full confidence and is wrong.
N Y U T AN D O N                                  IE-GY 9113B · Systems Integration · Week 7                              7
RECALL · YOUR TURN                                                                                                               8:15


A rule can't read a contract. What can — and in how many
ways?
     Name the kind of system that reads prose, images, and clauses, and its three sub-types, one
                                           example each.


   The problem                                                                      Your recall

   A rule needs a value in a field. A contract is                                   What reads it? And what are the three ways
   prose — meaning with no field to point at.                                       such a system learns?




     Talk it out in your team — 60 seconds. Then we reveal and sharpen it together.
N Y U T AN D O N                                     IE-GY 9113B · Systems Integration · Week 7                                         8
RECALL · REVEAL                                                                                                                8:18


A rule can't read a contract — three ways a machine can

What reads it: machine learning (ML). For text like a contract, that is natural-language processing (NLP); its most
capable form today is a large language model (LLM). ML learns in three ways:


   Supervised                                   Unsupervised                                       Reinforcement

   Learns from an expert's labels               Finds the odd one out — the                        Learns by trying toward a goal
   — reads a contract the way a                 transaction or record that                         — keeps what improves its
   lawyer marked up thousands                   doesn't fit the pattern. Anomaly                   position, discards what doesn't.
   before it.                                   detection.




     Intelligent automation bolts a model onto a rule-based flow: the model takes the judgment step; the rule keeps the
     structured remainder.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                      9
RECALL · YOUR TURN                                                                                                            8:20


RPA sells on cost. What does intelligent automation sell?


                   A bot is a cheaper clerk. What does a machine that reads all of the work add?


   Rule-based bot → ?                                                               Intelligent automation → ?

   What is the business case — in a word?                                           What is the bigger prize, once a machine reads
                                                                                    everything, not a sample?




     Talk it out in your team — 60 seconds. Then we reveal and sharpen it together.
N Y U T AN D O N                                     IE-GY 9113B · Systems Integration · Week 7                                      10
RECALL · REVEAL                                                                                                                      8:23


The value shifts: from cost saved to insight gained

   Rule-based bot → cost                                                               Intelligent automation → insight

   Does what people already do, faster and cheaper.                                    Does what people cannot: reads every contract and
   The business case is labour-hours removed.                                          message, at a scale and speed no team could
                                                                                       reach. The prize is the pattern that only shows up
                                                                                       when you read all of it, not a sample.




     The board case is not a cheaper back office. It is a company that sees and decides at a scale it could not reach before.
     Iansiti and Lakhani call it the AI factory.
N Y U T AN D O N                                       IE-GY 9113B · Systems Integration · Week 7                                           11
RECONNECT · YOUR TURN                                                                                                             8:24


Last week you built a bot and broke it. What broke — and
what did breaking it prove?

          Cast your mind back to Lab 2. The bot ran fine, then hit the rows you seeded, and failed.


   What broke                                                                       What it proved

   Where in the process did the bot fail — and                                      What did that failure say about the limit of rules
   what kind of step was it?                                                        — and what has to take that step instead?




     Talk it out in your team — 60 seconds. Then we reveal and sharpen it together.
N Y U T AN D O N                                     IE-GY 9113B · Systems Integration · Week 7                                          12
RECONNECT · THE CLIMB SO FAR                                                                                                 8:27


You integrated it, automated it, broke it — now make it
intelligent
   Module 1 — integrate                         Module 2 — automate                               Module 3 — make
                                                                                                  intelligent
   The integration backbone: one                RPA on the repeatable, rules-                     A machine takes the step the
   connected set of systems, one                based work. In Lab 2 you built a                  rule couldn't — and soon
   source of truth. Everything runs             working bot — and broke it at                     pursues a goal on its own.
   on it.                                       the judgment step.




     You build above what you have, not instead of it. Module 3 moves the Customer thread to the front, though today's case
     lands first in the back office.
N Y U T AN D O N                                     IE-GY 9113B · Systems Integration · Week 7                                     13
RECONNECT · THE THREE THREADS                                                                                                   8:30


One programme, three threads — Customer leads now

   Customer                                      Operations & Supply Chain                         Cash Management

   Serving the person as one                     Planning, inventory,                              How fast and reliably the
   promise. Module 3 leads here                  synchronisation. It led Module 2                  backbone turns activity into
   — agents land first at service,               — and today's bank case                           cash. A faster, surer decision
   fulfilment, dispute resolution.               proves the mechanism here                         speeds the cash it governs.
                                                 first.




     Tag your judgment step to the thread it moves. A board funds a thread outcome, not a capability or a bot.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                       14
RECONNECT · THE RHYTHM                                                                                                8:33


Stop pushing work in batches; react to events




     Add a smart model to a batch-world job and you get a faster version of the same dysfunction. The gain lands only when
     the system acts at the moment the exception occurs.
N Y U T AN D O N                                    IE-GY 9113B · Systems Integration · Week 7                               15
STORY · THE CASE                                                                                                                               8:36


A judgment step at industrial scale

JPMorgan COiN — Contract Intelligence: a machine-learning system that reads commercial loan agreements.

   The work                                                                                  The cost of doing it by hand

   Every commercial loan agreement must be read                                              ≈ 360,000 lawyer- and loan-officer-hours a year
   and interpreted — its terms, obligations,                                                 across ~12,000 contracts — and misreadings
   exceptions. Reading a clause is judgment, and no                                          became loan-servicing errors downstream.
   two contracts are quite alike.




Son, Bloomberg (2017); open access via ABA Journal (2017).




     Unstructured input, a rulebook that can't cover every contract, a costly error when it's wrong. That is a judgment
     decision point, not clerk work.
N Y U T AN D O N                                             IE-GY 9113B · Systems Integration · Week 7                                               16
STORY · YOU DECIDE                                                                                                         8:40


You run the bank's contract review. How do you automate
it?
   A — Rules-based checker                     B — A system that learns                          C — Keep it human
                                               to read
   Match keywords against a fixed              Train on thousands of                             It's judgment — don't automate
   template. Fast to build, easy to            contracts; generalise to                          it. Pay the 360,000 hours.
   explain.                                    agreements it has never seen.




     A show of hands, no huddle — A, B, or C? One of these breaks the moment a contract is phrased in a way the template
     didn't foresee. Then we see what the bank did.
N Y U T AN D O N                                    IE-GY 9113B · Systems Integration · Week 7                                    17
STORY · WHAT HAPPENED                                                                                                                  8:43


It didn't check the contracts — it learned to read them

   How COiN works                                                                    What changed

   Built on machine learning, not a keyword template.                                Minutes per contract → seconds.
   It “learns by ingesting data to identify patterns and
   relationships,” generalising to agreements it hadn't
   seen.                                                                             And because it read consistently, the servicing
                                                                                     errors from human misreading went down.




Son, Bloomberg (2017).




     That is the difference between automating a clerk and automating a reader. The two differ in kind, not degree. (The
     answer is B.)
N Y U T AN D O N                                     IE-GY 9113B · Systems Integration · Week 7                                               18
STORY · THE TURN THAT MATTERS                                                                                               8:47


When a machine takes the judgment step, the question
changes
The question moves from “does it work?” to three governance questions:


   Who is accountable?                         What is transparent?                              Where does a human stay?

   If the model misreads a clause              Can a non-technical person see                    On the high-value, the unusual,
   — the model, the team that                  how it reached its reading —                      the case the model flags
   trained it, the officer who relied          and check it? (Explainability.)                   uncertain. (Human-in-the-loop.)
   on it?




     Where the machine acts and where the human stays is the heart of the design. It is what your Board Memo has to get
     right.
N Y U T AN D O N                                    IE-GY 9113B · Systems Integration · Week 7                                     19
THE ENTERPRISE AI PLATFORM                                                                                                        8:51


A model is a capability; a platform makes it usable

                          ENTERPRISE-GRADE GOVERNANCE                 ·     security · access control · ethics & bias


                      Inputs                                                                       Must-have characteristics

           Human-driven (plain-language                                                                    Explainability
                      ask)
                                               EXECUTION ENGINE
                                                                                                      Utility-like (plug & run)
         Auto-discovery (process mining)             orchestration
                                                                                                           Observability
                                               turns a reading into action
                                                  across your systems
            Business-reactive (exception
                     patterns)                                                                     Adaptability (feedback loop)




     The model reads; the platform turns the reading into action, and keeps a human able to see and stop it. (Tella, Brinker
     and Pezzini, 2023.)
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                         20
YOUR TEAM'S WORK        ·   8:55–9:25


Name the step that needs AI judgment


Two short team sprints produce a real deliverable: the one step in your process a rule can't hold,
the value it carries, and where a human stays. → Board Memo §5, slide S8 of your board deck.




N Y U T AN D O N
YOUR TEAM'S WORK · THE ASK                                                                                                       8:55


Three questions frame the work — these are your study
questions

      1            What can rules-based RPA not handle — and why does that boundary matter strategically?




      2            How does intelligent automation shift the value from cost-saving to insight generation?



                   Using COiN: a rules-based checker vs. a genuine ML system — and what changes in
      3            governance?




     Work them in your team; I come round to each. By 9:25 you leave with the setup for slide S8: the step, its value, and its
     human boundary.
N Y U T AN D O N                                       IE-GY 9113B · Systems Integration · Week 7                                       22
SPRINT 1 · BY TEAM · 8:55 –9:10


Find the one step where the rule runs out

On your Lab 1 / Lab 2 process map, hunt the judgment decision point — the step a rule can't hold.


   START HERE Mark each decision point stable-rules or judgment. Pick the single clearest judgment step.



   GO FURTHER Say why the rule fails there — unstructured input, or a case it can't foresee? Which ML family would read it?




OUTPUT: one judgment step, named, + one line on why rules fail there.



     Close-out: each team names its step in a sentence. This is your Board Memo §5 starting line, and the target your Lab 3
     agent will take.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                              23
SPRINT 2 · BY TEAM · 9:10 –9:25


Make the case: the value, and where a human stays

For the step you just named: price its value by thread, and draw its human boundary.


   The value — by thread                                                              The human — the boundary

   START HERE One line of value; name the thread it                                   START HERE One case you'd route to a person —
   moves — Customer, Operations, or Cash.                                             ambiguous, high-value, irreversible.


   GO FURTHER The insight a model-at-scale unlocks —                                  GO FURTHER Who's accountable if it's wrong, and what
   why it's an investment, not an expense.                                            must the platform make visible?




OUTPUT: a value line (by thread) + a one-line human boundary. → Board Memo §5.



     Close-out: two teams share. A board funds a thread outcome, and trusts a design that says where the human stays.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                             24
CLOSE-OUT · REPORT-OUT                                                                                                     9:25


Each team — two minutes on your reasoning

                                               Walk us through your chain:


 the step → why rules fail → the value, by thread → where the human stays




                    What leaves the room: your agent-design setup — Board Memo §5, slide S8 of
                                               the final board deck.




     Two minutes per team, no slides. Just talk us through the chain. Then we look at where this is all heading, and our
     partners step in.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                  25
WHAT'S NEXT · WHY AGENTS, WHY NOW                                                                                      9:33


Agents are here because thinking and acting finally met




     No single new invention made this happen. The thinking stream and the acting stream matured at the same moment, and
     could finally be joined (Bornet et al., 2025).
N Y U T AN D O N                                    IE-GY 9113B · Systems Integration · Week 7                                26
WHAT'S NEXT · THE ARCHITECTURE (PREVIEW)                                                                                          9:38


SPAR — the four capabilities you meet next week


   Sense                              Plan                                           Act                    Reflect

   take in the situation              work out the steps                             do them in real        check its own work
                                                                                     systems




     Named today; taught next week; built in Lab 3. Read for the four parts, and for where Reflect has to sit if an agent is to
     catch its own mistakes.
N Y U T AN D O N                                        IE-GY 9113B · Systems Integration · Week 7                                       27
INDUSTRY PANEL · YOUR TURN                                                                                                        9:43


Our guests are practitioners. What would you ask them?

Halfway through the course: integrate, automate, make intelligent, make agentic. Jot one question
                             from anything that's puzzled you so far.


   From the work                                                                     From the career

   Something the ERP, automation, or AI material                                     How this actually plays out in their organisation
   raised that you'd want a practitioner's read on.                                  — and what they look for in people who build it.




     Bring one question. The sharpest come from what you've actually wrestled with, and from the capstone you're building.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                                         28
INDUSTRY PANEL · MID-SEMESTER           ·   9:45–10:20



Halfway in — the people who do this for
real
A step back across the whole arc: integrate, automate, make intelligent, make agentic. The
partners who guest-lecture through the term, and who sit on the board panel your team presents to
in December.




N Y U T AN D O N
INDUSTRY PANEL · WHO'S HERE                                                                                          9:46


Meet Our Industry Panel




     These partners guest-lecture through the term and sit on your December board panel. Today they step back and take
     the whole journey with you, from the backbone to the agentic enterprise.
N Y U T AN D O N                                   IE-GY 9113B · Systems Integration · Week 7                               30
INDUSTRY PANEL · THE QUESTIONS                                                                                                9:52


The questions on the table


      1            Integration first: years into digital investment, where do backbone and data problems still bite?




      2            Automate, intelligent, agentic — where is the real value today, and where is the hype?




      3            Customer, operations, or cash: which thread is AI actually moving the needle on for you?



                   When a machine takes a decision a person used to make — how do you govern it, and what do you
      4            want from the engineers who build it?

     Listen for where their line sits across the whole journey. It is the same judgment you'll defend to the board in December.
     Bring your own question too.
N Y U T AN D O N                                        IE-GY 9113B · Systems Integration · Week 7                                   31
WRAP · BEFORE NEXT WEEK                                                                                             10:20


Before next week


                                    The AI-judgment step + rationale → Board Memo §5 (Agent Design, slide S8). One
    Draft
                                    step, named, with why rules fail there.




    Read                            The Week 8 study note




    Keep evergreen                  Your board deck current through S8 (setup). Add it while it's fresh.




     You leave with the step an agent will take. Named and defended today; architected next week; built in Lab 3.
N Y U T AN D O N                                      IE-GY 9113B · Systems Integration · Week 7                            32
WEEK 7             ·   RPA → INTELLIGENT AUTOMATION


You named the step a machine should take.

Next · Week 8: SPAR — Inside the Mind of an AI Agent




N Y U T AN D O N

```
