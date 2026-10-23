---
title: W08_SPAR_LN_Slides
type: study-note
tags: [course-week, w8]
sources:
  - id: pdf-original
    resource: raw/data/pdf/course-weeks/w8/W08_SPAR_LN_Slides.pdf
---
# W08_SPAR_LN_Slides

```text
NYU      |   TANDON




MODULE 3           ·   INTELLIGENT AUTOMATION + AI AGENTS



AI Agent Architecture:
The SPAR Framework
You named the step a rule can't take. This week, the machine that takes it — and where
you keep your hand on it.
Friday, October 23, 2026         ·    8:00–10:30 AM         ·   2 MTC Room 802
IE-GY 9113B — Systems Integration: From ERP to Agentic AI   ·   Prof. Emanuele Cimica


NYU   TANDON
TODAY                                                                                                                                         8:00


What this morning is for
 Warm-up + recall                    8:05       Rebuild the architecture together — the loop an agent runs, and the three parts beneath it.



 The agent that scaled, then
                                     8:28       Klarna's customer-service agent: what it did, and the one move it was missing.
 stepped back

                                                Design your agent — the SPAR sketch for your own judgment step → Board Memo §5, slide
 Your team's work                    8:55       S8.



 From sketch to build                10:03      Your Lab 3 platform, and the scaffold that turns the sketch into an agent.



 Wrap + what's next                  10:20      Your deliverable, and what to set up before Lab 3.




 What you walk out with: the SPAR sketch your board deck needs next (slide S8), the architecture to build it, and your Lab 3
 platform.
BEFORE WE START



By 2025, one company's AI customer-service agent was doing the work
of:




853
two-thirds of all inquiries                        ·      ~$60M saved                  ·
                                                                                              full-time agents
                                                                                              (up from ~700 a year earlier)



                                                                                              then it stepped back toward people


    Today is about what an agent is made of, and the one part that, left thin, makes a success worth reversing.




Doerer, CX Dive (Nov 2025), reporting Klarna's Q3 2025 earnings; Levin & Nussey, Bloomberg (May 2025).
RECALL    ·   YOUR TURN                                                                                     8:08


What takes the judgment step — and what is it made of?



  You named the step a rule can't                                       You read the four moves this
  hold.                                                                 week.


  What takes it now? Call it what it is.                                Name them, in order, from memory.




 Hands up. We rebuild the loop from your answers, not from the slide.
RECALL      ·   REVEAL                                                                                                         8:11


An agent is a loop, not a list


       SENSE                               PLAN                                    ACT                       REFLECT

  Perceive: gather data,             Reason: weigh options,                 Execute: through tools          Evaluate: learn and
   hold working context                choose a course                        and APIs; monitor             adapt for next pass


     draws on Memory                    Reasoning · Ch. 6                        Action · Ch. 5               Memory · Ch. 7




                                       ↻ runs again — each pass should be better than the last




 It runs, then runs again. Sense → Plan → Act → Reflect, and back to Sense. (Bornet et al., 2025, Ch. 2.)
THE FIELD AGREES                                                                                                                                         8:14


You just learned the field's consensus


                                                                                                                       World Economic Forum
                  Bornet (2025)                                                          IBM (2024)
                                                                                                                               (2024)


                                                                           plan → reason with tools →                 “sensing, learning and acting
       Sense · Plan · Act · Reflect
                                                                                 learn & reflect                        upon their environments”


                                                                             the same loop, named “Think–Act–
       the SPAR loop — this course's spine                                                                              its working definition of an agent
                                                                                         Observe”




Bornet et al. (2025), Ch. 2; IBM Think, “What are AI agents?” (Gutowska, 2024); World Economic Forum primer (2024).




    Three independent sources, one architecture. When you sketch SPAR today, you are working from the model the whole field
    already uses.
RECALL     ·   YOUR TURN                                                                                                   8:17

Four moves, three keystones — which sits under
which?

Match each capability to the SPAR move it powers:



           Action                                       Reasoning                                         Memory


One SPAR move runs on no keystone of its own. Which — and what does it lean on?




  Sense has no keystone of its own; it draws on Memory. The other three each rest on one capability, and each raises its own
  governance question.
RECALL      ·   REVEAL                                                                                             8:20


What the loop is built from

SPAR move                 Keystone                         What it does


Sense                     — (draws on Memory)              Gathers data, detects triggers, holds working context


Plan                      Reasoning · Ch. 6                Weighs options and chooses a course of action


Act                       Action · Ch. 5                   Executes through tools and APIs; monitors


Reflect                   Memory · Ch. 7                   Evaluates outcomes; learns and adapts




   Three keystones, three governance questions. Keep them in view; they thread the next twenty minutes.
ANATOMY OF AN AGENT                                                                                                                                                          8:23


What's actually inside


                                                                             CONTROL CENTRE · orchestration



    PERCEPTS / SENSORS                                       Model                                                                                  EFFECTORS / ACTIONS
          what it senses — in                                                       Planning                  Memory           Tools                    what it does — out
                                                             (LLM)                 chooses steps             holds context      to act
                                                             the brain




                          In SPAR: Sensors = Sense                       ·    Planning = Plan            ·    Tools + Effectors = Act    ·   Memory = Reflect




Architecture adapted from WEF (2024), Fig. 3; IBM Think (2024); Bornet et al. (2025): “the AI model is the brain.”


     Put plainly: an agent is a language model placed in a loop, given tools to act with and memory to learn from.
THE QUESTION THIS MORNING                                                                           8:26




What is an agent made of —
and where must a human stay?

Keep both halves in view. We build the architecture first, then find the human's place inside it.
RECONNECT           ·   THE LADDER                                                                                           8:28


You are adding a rung, not leaving the last one

                                                                                    YOU ARE HERE
                                                                                                                    L4–5
                                                                                             L3                   Autonomous
                                                                                                                    Agents

                                                               L2                        Agentic
                                                                                        Workflows

                                   L1                      Intelligent
                                                          Automation
      L0                       Rule-Based
                               Automation
    Manual


    humans do                                             ML / NLP reads              plan · act · reflect,
                              RPA · fixed rules                                                                     goal-driven
    everything                                            what a rule can't               in bounds



        integrate                    automate                make intelligent               make agentic



 Module 2 was Level 1; Week 7 was Level 2. This week is the step onto Level 3, where the agent decides and acts inside bounds
 you set. Same backbone, one new layer.
WHAT MAKES IT AN AGENT                                                                                                                       8:31


The line between a bot and an agent
                                                                       Bot / RPA (L1–L2)                               Agent (L3)
                                                                         deterministic                              non-deterministic

Memory                                                                 none — starts fresh                         holds context, recalls


Chooses its actions                                                  no — runs a fixed script                      yes — picks the tool


Plans ahead                                                                        no                             breaks a goal into steps


Self-corrects                                                                      no                             adjusts from feedback


Handles the unexpected                                                   no — breaks on it                             yes — adapts


    Level 2 to Level 3, in a sentence: “Chatbots are a modality; agency is a technological framework.” (IBM, 2024). That difference is
    why governance changes.

IBM Think (Gutowska, 2024) — agentic vs. nonagentic; WEF (2024), Table 1 — deterministic vs. non-deterministic.
RECONNECT       ·   THE THREADS                                                                                                 8:34


Customer leads Module 3



                                                  Operations & Supply
           Customer                                                                                Cash Management
                                                         Chain

      where agents land first —                     the backbone and the flow                        the money, the controls,
      high volume, visible wins                          of physical work                                 the audit trail




 This week's case is a customer-service agent. The thread you pick for your own agent is yours; the architecture is the same.
STORY     ·   THE CASE                                                                                                   8:36


Klarna bet its service desk on an agent

2024. As it prepared to go public, the buy-now-pay-later firm deployed an autonomous customer-service agent,
paused hiring, and reduced service staff — betting the function on the agent.




        853+                       two-thirds                             −82%                             ~$60M
        agents' worth                        of all                          response                          claimed
          of work                          inquiries                           time                            savings




  Read only that, and it's a triumph. (By the company's own numbers, from CX Dive, Nov 2025, reporting the Q3 2025 earnings
  call.)
STORY   ·   YOU DECIDE                                                   8:39

It's working by the numbers. What would you
watch?



                   If you sat on Klarna's board that quarter —
            what number is NOT on the last slide, and would worry you?




 Hold your answer. The company's own next move points straight at it.
STORY     ·   WHAT HAPPENED                                                                                                      8:41


Then it stepped back toward people

May 2025. Klarna turned back toward human service: the chief executive said customers should always be able to
reach a person, and the firm began rehiring a flexible, on-demand workforce — a human-plus-agent model (Bloomberg,
May 2025).


   The record is nuanced, not “AI failed”:


   • Klarna reported no drop in satisfaction, and put the assistant on par with human agents in Q3 2025.
   • Yet its actual Q3 customer-service and operations cost rose to ~$50M, from ~$42M a year earlier. The ~$60M is a separate,
   cumulative savings the CEO claims the agent delivered, not a cut to that quarterly cost.




  The number you were missing: the actual customer-service cost still rose, ~$42M → ~$50M year over year. A claimed saving
  and a rising real cost, side by side.
STORY      ·   THE TURN                                                                                                             8:43


Sense, Plan, Act worked. Reflect was thin.

The reading is drawn from the architecture, not a verdict Klarna accepts:


                                       The agent read queries, chose responses, and acted at scale — the simple two-thirds, handled
   Sense · Plan · Act
                                       beautifully.



                                       It could not watch its own slow decline on the hard, nuanced cases, getting quietly worse
   Reflect
                                       without flagging it. That slow decline is quality erosion, and no loop caught it in time.




   The reversal                        May's turn back to people is a human supplying, by hand, the reflection the system lacked.




   Reflect detects quality erosion. Scale Act without it and reach grows faster than the ability to notice harm.
GOING DEEPER                      ·    SENSE & PLAN                                                                                                        8:45


Perceiving, then reasoning — fast is not the same as right


     SENSE — perception                                                                        PLAN — Reasoning (Ch. 6)

                                                                                               The crossword: given an interlocking puzzle, a fast model
                                                                                               answered almost instantly but got several entries wrong, right
                                                                                               where words had to cross; the checking a crossing needs got
     What the agent can see, and for how long: its inputs and its                              skipped. The pharma reroute: a logistics agent rerouted >$1M
     context window.                                                                           of temperature-sensitive drugs around a storm, a sensible-
                                                                                               looking move that sent them through ports not licensed to
                                                                                               receive such cargo, breaking transport rules before a human
                                                                                               caught it.

                                                                                               Governance: for high-stakes steps, buy reasoning time; constrain
     Governance: scope what it sees; keep inputs clean.
                                                                                               the action space.

Reasoning examples: Bornet et al. (2025), Ch. 6 (the crossword; the pharmaceutical reroute).




     A quick decision and a right one can diverge. The governance question at Plan is how much the agent may decide before a
     human sees it.
GOING DEEPER                       ·    ACT                                                                                                       8:47

Acting through tools — flawless execution, wrong
in context
Action (Ch. 5). The Great Wine Incident: an inventory agent tuned for shelf turnover used its tools perfectly to clear premium
wines that were appreciating assets — ~$100,000 in value gone before a human caught it. The WEF calls this specification
gaming: hitting the metric, not the goal — and more tools mean more ways to be confidently wrong.



The governance stack at Act:


       the few tools it needs                                                                                                     a circuit breaker
                                                                     a sandbox                                      logging
      (precision over power)                                                                                                  (stop on repeated failure)


Bornet et al. (2025), Ch. 8 (“precision over power”; circuit breakers); “specification gaming”: WEF (2024), §3.2.




     The kill switch lives at Act. Decide up front who can pull it, at what threshold, and in which domain; it belongs in the design.
GOING DEEPER         ·   REFLECT                                                                                                8:49


Memory turns a detector into something that improves


  The failure: amnesia                                                     Engineered the other way


                                                                           A financial-services agent that held account details and
  Telecom chatbots that forgot each conversation and made
                                                                           summarized earlier turns cut errors ~65%. A manufacturing
  customers repeat themselves. Satisfaction stayed low —
                                                                           QC system that remembered defect patterns cut false
  the system stored nothing it could use.
                                                                           positives ~40% over time.




                    Memory earns its place only when the agent uses what it stored to act better on the next pass.




  Klarna was missing exactly this move. Build Reflect deliberately, or a human ends up supplying it by hand.
GOING DEEPER          ·     THE GOVERNANCE QUESTION                                                                               8:51

A human who approves only the final Act has missed three
moves



        SENSE                                PLAN                                  ACT                              REFLECT




 What can it see — and is              How far may it decide              What may it touch — and              Did it catch its own error
    the input clean?                  before a human sees it?                who can stop it?                     — or just store it?




  Governance is not a gate at the end. It is a question at each move: what it sees, how far it reasons, what it may do, whether it
  caught itself.
THE FIELD AGREES                         ·    ON THE GOVERNANCE, TOO                                                                                8:52


Why a human has to stay


       Risk climbs as the leash                                           Fast enough to outrun you                  The risk is in the context
               loosens


     As an agent's autonomy rises and                                     Without a human in the loop, an           A mistake in customer service is
     human oversight falls, the chance                                   agent can take many consequential          minor; in healthcare or driving it is
        of serious harm rises with it.                                    actions before a person notices.           not. Match the autonomy to the
                                                                                                                                 stakes.




World Economic Forum primer (2024), §3.2–3.3 (autonomy vs. oversight; human-in-the-loop; context-dependent risk).


    You reached this from Klarna. The World Economic Forum reached it independently.
GOING DEEPER           ·   THE RULE                                                                                                    8:54


Match the rung to the risk — and keep it simple

The Golden Rule: the simpler the design that meets the need, the better. Build a capable new hire, not a genius with no
supervision. Klarna chose Level 3 on customer service precisely because adaptability earns its keep and an error there is
lower-cost and visible.




   Human-in-the-loop                                                         Kill switch

   a person kept in the decision path                                        a defined stop: when it fires, who pulls it, where it applies




   The rung is only half the decision. What you build around it to keep it in bounds is the other half, and the §5 sketch you're about
   to write.
YOUR TEAM'S WORK           ·   8:55–10:00


Design your agent: the SPAR sketch
Two short sprints produce one real deliverable: the goal, the few tools, and where Reflect must sit
→ Board Memo §5, slide S8.




NYU   TANDON
YOUR TEAM'S WORK           ·   THE QUESTIONS                                                                           8:55


The questions behind the sketch

           Define SPAR (Sense, Plan, Act, Reflect) — and use Klarna to explain what happens when Reflect is weak or
  1        missing.




  2        What are the Three Keystones of agentic AI, and why does each introduce a distinct governance challenge?




           When the Act keystone runs autonomous integration functions, what governance steps belong in place before you
  3        turn it on?




 These are the syllabus study questions. Your sketch is the first pass at answering all three with your own process.
TWO TOOLS, ONE SKETCH                                                                                                     8:56


SPAR is what the agent does; A.G.E.N.T. is how you design it

You know SPAR, the four moves an agent runs. A.G.E.N.T. (Bornet, Ch. 8) is the design checklist: the five things you decide to
build one. They line up. Use SPAR to think through the behaviour, and the A.G.E.N.T. headings to organize what you write down.


       A.G.E.N.T. part                     What you decide                                          Maps to SPAR


 A     Agent identity                      goal, role, scope                                        the purpose


 G     Gear & brain                        the model, platform + the few tools                      Act · Action


 E     Execution & workflow                triggers, inputs/outputs, steps                          the loop


 N     Navigation & rules                  filtering, decision logic, logging                       Plan + governance


 T     Testing & trust                     adversarial testing, feedback, guardrails                Reflect · Memory




   In the sprints: SPAR tells you the moves; the A.G.E.N.T. headings organize what you decide for each.
WORKED EXAMPLE                            ·    A SHARED CASE, NOT YOURS                                                                                                 8:57


A filled-in Sprint 1: the Citi Bike dispatch agent
One truck, two competing stations — which to service first? The same A.G.E.N.T.                                        SPAR table you just saw, now worked. Map the
pattern to your own step; don't copy the case.


            A.G.E.N.T. part · SPAR                                The Citi Bike agent — worked (define half)



            Agent identity                                        Recommend — not dispatch — which of two competing stations to service first, to lose the fewest rider-trips
  A         · the purpose                                         over ~20 min. Role: ops dispatcher. Decide only between the two given.



            Gear & brain                                          Model: Gemini, low temperature — the same case decides the same way twice. One tool: read the conflict
  G         · Act                                                 rows. Few tools on purpose.



            Execution & workflow                                  Sense: read one conflict row (two stations + signals). Plan: weigh present emptiness vs. ~20-min forecast
  E         · the loop                                            vs. wasted-trip cost → choice, one-line reason, rejected option. Act: record the pick, or escalate to a person.



     Build A, G, E and you have a working loop. The govern half — N and T, where Reflect and the stopping rule live — is Sprint 2.


Course-built worked case (synthetic data). The full build appears in the Week 9 / Lab 3 study note.
SPRINT 1      ·   BY TEAM      ·   8:58–9:25



Define your agent
Take the judgment step you named in Lab 2 / Week 7. Build the first three moves, using the A.G.E.N.T. headings you
just saw.


    START HERE      Name the agent (goal, role, scope). Then write its Sense (what it reads), Plan (what it decides), and Act
    (what tools it uses).



    GO FURTHER     Add the one or two tools it actually needs, no more, and what it must not touch. Note a platform you'd
    build on, and why.




OUTPUT: a one-paragraph sketch: goal, what it senses, what it decides, what it acts on.




   Close-out at 9:25: every team has an agent defined through Act; the Reflect half comes next.
SPRINT 2      ·   BY TEAM      ·   9:25–9:50



Where must Reflect sit — and the stopping rule?
Now the governance half: the feedback the agent needs, and the human's place in the loop.


    START HERE     Say where Reflect lives: what signal tells the agent (or you) it is drifting on the hard cases. Then set the
    stopping rule: when it fires, who pulls it, where it applies.



    GO FURTHER     Name the agent's most likely Reflect-failure, the way it would quietly get worse, and the one guardrail
    that would catch it.




OUTPUT: the sketch completed: where Reflect sits + the kill-switch rule → Board Memo §5.




   Close-out at 9:50: each team can say where a human stays, and what stops the agent.
CLOSE-OUT       ·   REPORT-OUT          ·   9:50–10:03                                                          9:50


Each team, in four lines



         goal                                 tools                           where Reflect sits   the stopping rule




  What leaves the room: your SPAR sketch, which becomes Board Memo §5, slide S8. It is the target your Lab 3 agent
  will take, and the step you'll defend to the board in December.




 Finish it tonight if it isn't done. Walk into Lab 3 with the sketch ready.
CLOSE-OUT        ·   THE GOVERN HALF, REVEALED                                                                                                     10:00


Now the Citi Bike answer: N and T
You named where Reflect sits and the stopping rule for your own agent. Here is the worked case for the same two parts — compare
it to yours; don't copy it.

       A.G.E.N.T. part · SPAR             The Citi Bike agent — worked (govern half)



       Navigation & rules                 How it weighs the signals — forecast vs. present emptiness vs. trip cost, the trade a single column can't hold.
 N     · Plan + governance                Log every call: signals seen, choice, reason, rejected option.




                                          Reflect: an after-shift check of its picks against what actually happened to station fill — the drift signal Klarna
       Testing & trust                    lacked. Most likely failure: it picks the emptier-now station and ignores the forecast — a rule in disguise.
 T     · Reflect · Memory                 Guardrail: weigh the forecast; validate inputs; data is never a command. Stopping rule: escalate on missing
                                          field / close margin / embedded instruction; a circuit breaker halts on repeated failure, and ops can pull it.




   A sketch, not a finished agent. When you build and test it, what you wrote here will change — the breaks are where the
   guardrails come from. That is Lab 3.
WHAT'S NEXT    ·   FROM SKETCH TO BUILD   ·   10:03


Next week you build the agent
you just sketched



NYU   TANDON
WHERE TO START                         ·    FREE NO-CODE BUILDERS                                                                                   10:05


Gemini is guaranteed; the builder is your call
Platform                            Free model                                                       Code?       Strength

n8n                                 Community edition (self-hosted)                                     No       Workflow automation, EU-based

Dify                                Self-hosted, fully free                                             No       RAG & document agents

Latenode                            1,000 credits / month                                               No       Fast production deployment

Botpress                            Free starter plan                                                   No       Conversational agents

Flowise                             Open source (self-hosted)                                           No       LangChain without code

Make.com                            Free tier available                                                 No       Extend existing automations

Zapier Central                      Free tier available                                                 No       Largest app ecosystem

                  These builders aren't tied to one model: pair with Gemini (your model via NYU) or another you have. A paid account is fine too.
Table adapted from chatarmin.com/en/blog/free-ai-agents — free tiers and credits change; verify current terms.



     Need help choosing or building? Shravani Dorlikar, Course Assistant for Prof. Mazzone, is available for targeted help —
     ssd9840@nyu.edu.
RESEARCH AND CHOOSE YOUR BUILDER                                                                                                10:08


Choose your builder, and justify it

Pick from those options or another you know, and be ready to say why.

WEIGH


     functionality              operating cost                  skills on                  governance                   continuity
   (what it must do)               / credits                    the team                       fit                   (Make from Lab 2)




  Free to choose: any builder that fits your case, including a paid account you already have.
  An enterprise platform or a self-hosted custom build need faculty approval.




  You're not graded on which you pick. Doing the research and justifying the fit is the work, and the Gemini floor means a thin-
  credit option never costs you marks.
BUILDING ONE WELL                              ·    BORNET, CH. 8                                                                                                              10:11


Four rules that keep an agent from running away


     One tool, one agent                                                                                            A circuit breaker

     “Precision over power”: give it the few tools it needs, clearly                                                Stop execution on repeated failure; Bornet calls it the agent's
     defined and limited, rather than every tool it could have.                                                     immune system.




     Trusted inputs                                                                                                 A human in the loop

     Whitelist the sources it may read, so it can't act on anything it                                              Keep a person in the decision path. Building an agent is
     finds.                                                                                                         ongoing, not a one-time task.




Bornet et al. (2025), Ch. 8 (“precision over power”; circuit breakers; human-in-the-loop; build as an ongoing process).


     That is the “Testing & trust” step, the T in A.G.E.N.T. Lab 3 is where you build it in.
WHAT'S NEXT         ·   LAB 3 (PREVIEW)                                                                                    10:14


What Lab 3 produces
A preview, not today's work — the five A.G.E.N.T. parts you sketched become next week's build:



    A working agent that takes the single judgment step from Lab 2 / Week 7.




    Adversarially tested to failure — about three adversarial inputs, with about three guardrails derived from where it breaks.




    A human-in-the-loop seed: the point where a person stays in the decision path.




   It feeds Board Memo §5 and storyboard S8–S9. The sketch you wrote today is its starting line.
WHAT'S NEXT                    ·    WEEK 10 (PREVIEW)                                                                                   10:18


Where governance goes from here


     Many agents                                                                    More power, more risk

     Agents that collaborate, compete or negotiate — in a
                                                                                    And new failure modes: orchestration failures, infinite
     network, or under a supervisor agent (WEF). Multi-agent
                                                                                    loops, and shared blind spots when agents lean on the
     systems reach what one agent can't: scale and
                                                                                    same model (IBM).
     resilience.



Multi-agent architectures: WEF (2024), §2.5; multi-agent risks: IBM Think (2024).




     Handed forward, not taught today. This week you designed one governed agent; Week 10 is the system around it.
WRAP     ·   BEFORE NEXT WEEK                                                                                                         10:20


Before Lab 3

 Research               free tiers and credits across the platforms shown, and any others you know



 Choose                 pick a builder, justify it (functionality, operating cost), and set up its account; model is Gemini via NYU



 Build                  a first attempt at your agent — expect it to break; the breaks are the lesson



 Finish                 your SPAR / A.G.E.N.T. sketch → Board Memo §5, slide S8



 Read                   the Week 9 (Lab 3) note     ·    Forum 2 opens Oct 21




 Walk in with a first build you can break open. Lab 3 is where you harden it.
WEEK 8         ·   AI AGEN T ARC HI TEC TU RE


You've designed the agent.
Next week you build it.
Next · Week 9: Lab 3 — Building a Governed Agent




NYU   TANDON

```
