---
title: W05_ScalingRPA_CoE_StudyNote_v2
type: study-note
tags: [course-week, w5]
sources:
  - id: pdf-original
    resource: raw/data/pdf/course-weeks/w5/W05_ScalingRPA_CoE_StudyNote_v2.pdf
---
# W05_ScalingRPA_CoE_StudyNote_v2

New York University — Tandon School of Engineering
Department of Technology Management and Innovation
IE-GY 9113B — Systems Integration: From ERP to Agentic AI

Study Note — Week 5: Scaling RPA and the Center of Excellence
Module 2: The Automation Ladder   |   Friday, October 2, 2026

Readings for this week

Primary case

Supporting

Go deeper
(optional)

Robotic Process Automation at Telefónica O2 — Mary Lacity and Leslie
Willcocks, MIS Quarterly Executive, 2016; the peer-reviewed account of a
pioneering programme that scaled RPA through a small in-house team and a
Back-Office-owned operating model. Read the open-access working paper (LSE
Outsourcing Unit 15/02):
https://eprints.lse.ac.uk/64516/1/OUWRPS_15_02_published.pdf

Orange Spain, ‘Robot Factory’ — a UiPath customer case study. This is vendor
marketing, not independent research: treat every figure in it as a claim the
vendor is making, not a verified fact. We read it only to see the shape of a
second telecom’s Center-of-Excellence growth arc, and to practise reading a
vendor case against an independent one:
https://www.uipath.com/resources/automation-case-studies/orange-spain-
telecom-rpa

Deloitte, Automation with intelligence (2022). The 7th Global Intelligent
Automation survey (479 executives, 35 countries). Read it for the barriers that
stop programmes scaling and for what a Center of Excellence is for. Open
access:
https://www.deloitte.com/us/en/insights/topics/talent/intelligent-automation-2022-
survey-results.html
Tella, Brinker and Pezzini, The New Automation Mindset, Ch. 4–5 (the scale
mindset and orchestration); Westerman, Bonnet and McAfee, Leading Digital,
Ch. 3 (exploiting the power of core operations). Reference, not required reading
— the note teaches the ideas directly and points you to the source at the exact
place it uses each one.

Before next
session

Lab 2 is in Week 6 and it runs on Make (free tier). Create your Make account
this week so the build time next week is spent building, not signing up.

You Named the Stall Last Week — This Week You Build the Thing That
Prevents It

This course moves through four stages — integrate, automate, make intelligent, make agentic —
and  everything  you  build  sits  on  the  first.  You  are  still  on  the  second  stage,  still  climbing  the
automation ladder inside Module 2, and still, in project terms,  in the Diagnose phase you have
been in since Week 1: you are working out what your company should do about automation before
you build the enterprise version of it. But the question has changed shape. Week 4 taught you to

1

pick a single good candidate — the repetitive, rules-based, stable step that deserves a bot — and
it  left  you  holding  a  warning  it  promised  to  come  back  to.  A  bot  works  the  screens,  not  the
plumbing, so it breaks the moment a screen it depends on moves; and Week 4 said, in as many
words, remember that failure mode, because it returns in Week 5 as the reason RPA programmes
stall at scale. This is Week 5. Here is where that failure mode grows from a footnote about one
bot into the central problem of running hundreds.

Week 4 also handed you a second thread. When it zoomed out to the market, Deloitte’s 2022
survey  reported  that  the  hardest  barriers  to  scaling  automation  were  process  fragmentation,  a
lack of clear vision, a lack of IT readiness, and resistance to change (Deloitte, 2022) — and you
were asked to notice that not one of them is the technology. Week 4 named the organisational
answer to those barriers and then deliberately withheld it: the Center of Excellence, the thing that
governs the jump from a pilot to an enterprise programme. It even pointed the last of Week 4’s
study  questions  straight  at  it  —  what  is  the  single  biggest  governance  risk  of  deploying  RPA
without a Center of Excellence? This week delivers the answer you were told to expect. By the
end of it you should be able to explain why programmes die between ten bots and a thousand,
design  the  operating  model  and  governance  that  keep  them  alive,  and  say  precisely  where  a
human still belongs even in a system built to run without one.

Keep the three threads in your ear, because this module leads with one of them and this week is
no exception. The Customer thread is taking an order and serving the person as one coherent
promise; the Operations and Supply Chain thread is planning, inventory, and synchronization, so
a company can deliver what it promised; and the Cash Management thread is how fast and how
reliably the backbone turns activity into cash — the thread that matters because cash flow is the
most  common  way  businesses  fail.  Scaling  RPA  lives  first  on  Operations  and  Supply  Chain,
because that is where the repetitive, rules-based work is generated and where a large programme
finds most of its bots. But watch it land on the other two exactly as Week 4 did: when Telefónica
O2 drove a routine service request from days down to minutes, that compressed cash conversion
(Cash) and removed the customer’s need to phone and chase (Customer) in the same motion.
One programme, three threads.

And  keep  the four  archetypes  in view,  because a Center  of  Excellence  looks  different  at  each
scale:  a  consumer-packaged-goods  manufacturer  running  sales-and-operations  planning  on
SAP; a mid-market manufacturer running order-to-cash on NetSuite; a Series-B startup running
order-to-cash across Stripe, Shopify, and QuickBooks; and a fifty-person services firm living in
HubSpot and Notion. The primary case this week, Telefónica O2, is a very large enterprise, and
its programme has a shape a Fortune-500 board would recognise. Part of your work is to translate
that shape down to your own company’s scale — because the governing idea holds at every size,
even when the fifty-person firm’s ‘Center of Excellence’ is one person and a written rule.

This week answers the question Week 4 left open.  Week 4 chose one good bot and
flagged two things for later: the brittleness that breaks a bot when a screen moves, and the
Center of Excellence that Deloitte’s non-technical barriers point to. Week 5 develops both.
You are still on the automate rung and still in the Diagnose phase — now designing how

2

automation is run across a company, not building a single bot. Operations and Supply Chain
leads; Cash and Customer follow.

The Week’s Question: Your Pilot Worked — So Why Do Most
Programmes Die on the Way to Scale, and Who Keeps Them Alive?

Here  is  the  question  the  whole  session  turns  on.  The  RPA  pilot  is  one  of  the  most  reliably
successful demonstrations in enterprise technology: pick a high-volume, rules-based step, point
a bot at it, and within weeks you have a working automation and a happy sponsor. Week 4 taught
you to run exactly that play. The trouble is what happens next. The pilot that dazzled at three bots
behaves nothing like a programme at three hundred. The same surface-level fragility that made
one bot cheap to build makes a thousand bots expensive to keep running; the same easy path
that let one team stand up a bot in a fortnight lets forty teams stand up four hundred bots that
nobody owns; and the infrastructure that carried the pilot quietly buckles when the load multiplies.
So the question is two-sided, just as Week 4’s was. Why does a programme that works brilliantly
small break as it grows — and what organisation, deliberately built, keeps it working as it scales?
Answering that is the entire skill of the week, and it is exactly what your Board Memo §4 will ask
you to design for your own company: not another list of bots, but the operating model that would
let a company run them.

Ten Bots Is a Demo; a Thousand Bots Is an Operation

Start with why programmes stall, because the failure is not random and it is not about the tool
being bad. It follows directly from what a bot is. Recall the definition from Week 4: a software robot
operates  a  company’s  existing  applications  through  their  user  interface  —  driving  the  same
screens a person would, reading fields, clicking buttons, copying a value out of one screen and
typing it into another by a fixed script. That surface-level approach is the source of both RPA’s
appeal and its fragility. At the scale of one bot, the fragility is a manageable maintenance chore.
At the scale of hundreds, it compounds into the thing that kills programmes. Four failure modes
do most of the killing, and you should be able to name them the way you name the three candidate
tests.

3

Figure 1. The value a pilot promises keeps rising with bot count; the value a programme without a Center of Excellence
actually realises plateaus and then falls, as maintenance and fragility overtake new work.

The first and most concrete is selector instability, and it is worth slowing down on because it is
one of this week’s study questions and because it makes the abstract word ‘brittle’ into something
mechanical you can picture. A bot does not see a screen the way you do. To click the right button
or read the right field, it needs an address for that element — a selector, a description of where
the element sits in the structure of the page or window: this button, in this panel, with this label,
at this position. When the bot is built, those selectors are recorded against the screen exactly as
it looks that day. Now the vendor of that application ships a routine update. A field is renamed, a
button moves into a new menu, a pop-up is added to confirm an action, a column is inserted into
a table. To a human, none of this is disruptive — you glance at the new layout and carry on. To
the bot, the selector it was given no longer points at anything, or points at the wrong thing, and
the script fails. That is selector instability: the bot’s dependence on the screen looking exactly as
it did when it was built, and its inability to improvise when the screen changes underneath it. An
‘unexpected system update’ is not exotic; it is a Tuesday. The customer never approved it, nobody
told the automation team, and one morning a bot that ran flawlessly for a year is silently doing
nothing — or worse.

‘Or  worse’  is  the  half  that  matters  most,  and  Telefónica  O2’s  own  programme  supplies  the
archetype. A bot follows its rule with perfect confidence even when the rule has become wrong
for the case in front of it — it does not pause, does not doubt, does not notice the thing a person
would have caught out of the corner of their eye. When Apple opened pre-orders for a new iPhone,
some of O2’s customers, in their enthusiasm, ordered the same phone several times. A human
clerk would have recognised that a single customer really wanted a single phone. The bot did not:
it followed its instructions and shipped the duplicates (Lacity and Willcocks, 2016). The lesson O2
drew is exactly the scaling lesson — that automating a step which ‘obviously’ had sufficient rules
still forced them to add explicit common-sense checks that a person had supplied for free. Multiply
that  across  hundreds  of  bots  and  thousands  of  edge  cases  and  you  see  the  shape  of  the

4

maintenance burden: every bot is a promise that the world will keep looking the way it did the day
the bot was born, and the world does not keep that promise.

The second failure mode is integration drift, which is selector instability spread across time and
across a whole estate. A single bot bridges two systems at the surface. A programme bridges
dozens  of  systems  with  hundreds  of  bots,  and  every  one  of  those  systems  is  independently
evolving — patched, upgraded, reconfigured, occasionally replaced — on its own schedule, by
teams who have never heard of your bots. The surface each bot rides on is slowly drifting out
from under it. What was a stable seam becomes a moving one, and the cost of keeping the estate
running rises not with the number of bots but with the number of connections between bots and
changing systems, which grows far faster. This is the mechanism behind the plateau in Figure 1:
past  a  certain  size,  a  programme  without  a  governing  function  spends  more  and  more  of  its
capacity re-fixing bots that broke and less and less building bots that add value, until maintenance
overtakes  new  work  and  the  realised  value  bends  downward  even  as  the  bot  count  keeps
climbing.

The third failure mode is infrastructure brittleness, and O2 lived it in a way that is almost too neat.
The company chose to run its bots on virtual machines, with a ‘lead’ machine orchestrating the
others.  That  arrangement  worked  cleanly  at  around  twenty  robots.  When  the  robot  count
quadrupled, it collapsed; the head of the programme described the mismatch memorably —
“It was like driving a Ferrari with a lawn mower engine.” The point is not the specific technology;
it is that the platform which comfortably carries a pilot is not the platform that carries a programme,
and the two look identical right up until the load crosses a threshold and the smaller one fails. O2
needed roughly sixteen weeks to re-engineer the infrastructure — moving servers and databases
closer together to cut latency — before the scaled programme ran properly (Lacity and Willcocks,
2016). A pilot proves the automation logic; it does not prove the plant that will run it at ten times
the volume.

The fourth failure mode is the one that has no technical cause at all, and it is the bridge to the rest
of the week: bot sprawl, the uncontrolled proliferation of automations that nobody owns. When
building a bot is easy and there is no sanctioned path for doing it well, teams build their own —
quietly,  off  to  the  side,  to  solve  a  problem  they  could  not  get  onto  anyone’s  roadmap.  The
automation literature has a name for this, and Tella, Brinker and Pezzini describe it plainly in the
reading: shadow IT, which in its worse forms becomes rogue IT, where business data is moved
and transformed in unsanctioned ways that no one is watching (Tella, Brinker and Pezzini, 2023).
Each  shadow  bot  is  individually  reasonable  and  collectively  a  liability  —  undocumented,
unmonitored, duplicated across teams, and quietly accreting the technical debt that lands on IT’s
backlog when one of them fails. This is precisely why Deloitte’s most-cited barrier to scaling is
process  fragmentation  (Deloitte,  2022):  a  scatter  of  local,  unconnected  automations  is  not  a
programme,  it  is fragmentation  with bots  on top.  Note  where this  points.  The first  three failure
modes ask for engineering discipline. The fourth asks for an organisation — someone whose job
is to make sure automation is built well, owned, and watched. That someone is the subject of the
rest of this note.

5

Why programmes
stall

Selector instability

Integration drift

What goes wrong at scale

Anchored exemplar

A routine system update moves or renames a
screen element; the bot’s address for it no longer
resolves and the script fails — silently or loudly

O2: a bot shipped duplicate iPhones
because it followed its rule without
the common sense a person
supplies

Dozens of systems evolve on their own
schedules; the surfaces hundreds of bots ride on
drift, and maintenance grows faster than the bot
count

O2’s estate of 15 core processes
across many systems — each
change a chance to break a brittle
seam

Infrastructure
brittleness

The platform that carries a pilot buckles when
load multiplies; the failure is invisible until a
threshold is crossed

Bot sprawl (shadow
automation)

With no sanctioned path, teams build their own
unowned, unmonitored bots — fragmentation with
bots on top

O2’s lead virtual machine — fine at
~20 robots, imploded when the
count quadrupled; ~16 weeks to re-
engineer

Shadow IT hardening into rogue IT
(Tella et al., 2023); Deloitte’s No. 1
barrier is process fragmentation
(2022)

A pilot proves the logic; it does not prove the programme.  Bots stall at scale for four
reasons: selector instability (a screen changes and the script breaks), integration drift (many
systems evolving under many bots), infrastructure brittleness (the pilot’s platform buckles
under load), and bot sprawl (unowned shadow automations). The first three demand
engineering discipline; the fourth demands an organisation. That organisation is the Center of
Excellence.

A Company Has No Brain for Automation, So It Builds One

A  single  successful  bot  creates  a  demand  it  cannot  satisfy.  Once  one  team  has  proved  that
automation works, every other team wants theirs, and the company faces a choice it usually does
not recognise as a choice. It can let each team fend for itself — the road to bot sprawl — or it can
build a standing function whose job is to make automation a governed capability rather than a
scatter of one-off scripts. That function is the Center of Excellence, or CoE: a small, permanent
team that owns how automation is done across the company. It is not a bigger bot factory. It is
the  organisational  answer  to  the  four  failure  modes  of  the  previous  section,  and  it  is  the  thing
Week 4 promised and Deloitte’s non-technical barriers point straight at.

Be precise about what a CoE actually does, because ‘Center of Excellence’ is the kind of phrase
that can mean everything and therefore nothing. Five functions do the real work, and you should
be able to design each one for your own company.

6

Figure 2. The Center of Excellence sits between the business (which supplies demand and process knowledge) and IT
(which supplies the platform, identity, and security guardrails). It converts scattered requests into governed, owned,
monitored automation.

The first function is governance and standards — the rules for who may build an automation, how
it must be built, and how it is approved before it goes anywhere near production. This is the direct
antidote to bot sprawl: a bot that has passed a review is not a shadow bot. Tella, Brinker and
Pezzini describe a company that made this the very first thing its new automation team built —
an automation review pipeline through which every automation the business created had to pass
before it went live (Tella et al., 2023). The pipeline is not bureaucracy for its own sake; it is the
mechanism that lets a company say yes to far more builders without saying yes to chaos. The
second function is intake and the review pipeline itself — the sanctioned front door through which
demand arrives, is triaged, and is either built centrally, handed back to a trained business builder
under supervision, or declined. A visible front door is what makes the shadow door unnecessary.

The third function is bot ownership and monitoring, and it is the one students most often forget,
even though it is where the ethics of this week live. Every bot in production has a named owner
and a watched pulse: someone is accountable for it, and something is checking, continuously,
that it is doing what it should. Consider the week’s ethics question in its sharpest form: if a bot
produces incorrect outputs silently for weeks, who is accountable, and how should the liability for
automated errors be structured? A programme with no ownership function has no answer — the
bot has no owner, its outputs are not watched, and the silent error runs until a customer complains
or an auditor finds it. A CoE’s ownership-and-monitoring function is exactly the answer: it assigns
the accountable human, it defines what ‘healthy’ looks like for each bot, and it designs the audit
trail  so that  a wrong output  is  caught  in days,  not  discovered  in months.  Automation  does not
remove accountability; it relocates it, and the CoE is where it comes to rest. The fourth function
is  enablement  and  training  —  turning  willing  people  in  the  business  into  capable,  supervised
builders — and the fifth is infrastructure and platform — owning the plant that runs the bots and,
crucially,  scaling  it  in  pace  with  the  programme  so  that  O2’s  lead-machine  collapse  does  not
happen  to  you.  Keep  those  five  in  view:  governance,  intake,  ownership  and  monitoring,

7

enablement, infrastructure. A CoE that neglects any one of them stalls in the way that function
protects against.

Now walk O2’s operating model against that template, because it is the anchor for the whole idea
and because its most instructive choice is one most companies get wrong. O2 ran its entire scaled
programme — fifteen core processes, more than a hundred and sixty robots — with a team of
just three in-house developers (Lacity and Willcocks, 2016). More striking is where those people
came from and who owned the work: the programme lived in the Back Office, not in IT. Its builders
were  process-improvement  staff reassigned to automation,  which meant the  head of the  Back
Office could move people from improving a process to automating one with, in effect, no change
to the budget and no dependency on IT’s development queue. That single organisational fact is
what made O2’s business case beat the alternative. When the company compared RPA against
its existing business-process-management system on the same two processes, the technologies
performed comparably; the financial gap came almost entirely from resourcing. The management
system  needed  scarce  IT  developers  and  formal  project  teams  and  would  have  taken  around
three  years  to  pay  back;  RPA,  run  by  reassigned  business  people,  paid  back  in  roughly  ten
months (Lacity and Willcocks, 2016). The lesson is not that one tool is better than another. It is
that  a  scaled  automation  programme  is  an  operating-model  decision  before  it  is  a  technology
decision — who owns it, who builds it, and against whose budget it runs.

Deloitte’s survey puts the same idea in the language of the wider field and adds a distinction you
will  need.  A  classic  Center  of  Excellence,  in  Deloitte’s  account,  focuses  on  the  high-value
automations and the end-to-end process redesign that the whole company cares about, and it
exists to drive the governance protocols under which more local automation can safely happen
(Deloitte, 2022). That is the crucial word: the CoE governs; it does not personally build everything.
It sits, as Figure 2 shows, between the business that supplies demand and knowledge and the IT
function that supplies the platform, identity, and security guardrails, converting scattered requests
into  governed,  owned,  monitored  automation.  Deloitte  also  names  the  thing  a  CoE  is  often
confused with — citizen-led development, where trained non-technical employees build their own
low-complexity  automations  —  and  is  careful  to  say  it  is  not  a  replacement  for  a  CoE  but  a
complement  that  only  works  under  a  CoE’s  governance  (Deloitte,  2022).  Hold  that  distinction
lightly  for  now;  the  machinery  that  makes  safe  citizen  development  possible  is  a  later  week’s
subject, and we preview it below rather than teach it here.

The CoE’s five functions  What it does

Anchored exemplar

Governance & standards  Sets who may build, how, and how a bot is

approved before production — the direct
antidote to sprawl

Tella et al. (2023): every
automation passes an ‘automation
review pipeline’ before it goes live

Intake & review pipeline

A sanctioned front door for demand — triage,
then build centrally, hand to a supervised
builder, or decline

A visible front door makes the
shadow door unnecessary (Tella et
al., 2023)

Bot ownership &
monitoring

Every bot has a named owner and a watched
pulse; the audit trail catches a silent error in
days

The answer to the week’s ethics
question — accountability is
relocated, not removed

Enablement & training

Turns willing business people into capable,
supervised builders

O2 ran the whole programme with
3 reassigned Back-Office builders
(2016)

8

The CoE’s five functions  What it does

Anchored exemplar

Infrastructure & platform  Owns the plant and scales it in pace with the

programme

O2’s lead-VM collapse is what this
function exists to prevent (2016)

The CoE’s job is to make automation a governed capability, not a pile of scripts.  Its five
functions — governance and standards, intake and review, bot ownership and monitoring,
enablement, and infrastructure — each answer one way a programme stalls. O2 ran 160+
bots with three reassigned Back-Office builders and beat its alternative on operating model,
not technology: who owns automation, who builds it, and against whose budget it runs.
Accountability is relocated to the CoE, not removed by automation.

Scarcity Says Hoard the Experts; Scale Says Multiply Them

There is a mindset underneath the operating model, and if you miss it you will build a CoE that is
just a bottleneck with a nicer name. Tella, Brinker and Pezzini frame it as a contrast between a
scarcity mindset and a scale mindset, and the arithmetic they use to motivate it is worth carrying
because a board will feel it immediately. Imagine a mid-size company with a couple of hundred
applications and a thousand employees, each touching a handful of processes a day. The number
of automatable processes runs into the thousands, most of them small and unnamed, living only
in the heads of the people who do them. Now suppose a central team builds automations one at
a  time.  Even  at  a  brisk  pace,  the  queue  is  a  lifetime  of  work;  the  authors  put  the  timeline  to
automate everything through a single specialist team at over eighty years (Tella et al., 2023). The
point of the number is not its precision. It is that you cannot scale an automation programme by
adding  specialists,  because  there  will  never  be  enough  of  them,  and  treating  scarce  technical
people as the  only  ones  allowed  to build  is  a  scarcity  mindset that  guarantees the  ninety-nine
percent of processes never gets touched.

The scale mindset is the opposite move: instead of hoarding a scarce resource, you multiply who
can use it, safely, under guardrails. Tella and his co-authors reach for an image that captures the
fear and the answer at once. Picture a river held back by a dam. Remove the dam and you get a
flood; leave it in place and the water never flows. The move is neither — it is to remove the dam
and install guardrails that channel the current, so innovation flows fast but within banks (Tella et
al., 2023). Applied to a company: you do not lock automation inside a tiny team (the dam), and
you do not throw the tools open to everyone with no oversight (the flood). You build the guardrails
— which is precisely what the CoE’s governance, intake, and review functions are — and then
you let far more people build within them. Read against Figure 2, this reframes what the CoE is
for.  It  is  not  the  company’s  automation  factory;  it  is  the  company’s  automation  steward.  The
authors put the shift crisply: central IT stops being an automation factory that the business queues
up  behind  and  becomes  a  service  provider  that  enables  the  business  to  build.  That  is  not  a
demotion of IT — it raises IT’s standing, because stewarding the whole company’s automation is
a larger job than personally writing every bot.

This  is  also,  directly,  the  answer  to  the  second  study  question’s  harder  half:  how  does  a  CoE
prevent shadow IT? Not by policing it. Shadow IT is what people do when the sanctioned path is
closed or too slow — it is a symptom of scarcity, of a central team that is a dam. The CoE drains

9

the  shadow  by  opening a  better-lit  path than the  shadow  one:  a review pipeline  that  says yes
quickly, training that makes people competent, and support that makes the sanctioned way the
easy  way.  Tella’s  account  of  the  company  that  built  its  CoE  this  way  is  instructive  precisely
because the team resisted the urge to open a request queue and start taking build orders. It ran
a class instead, licensed the graduates to build, and put every build through the review pipeline
— and within months a large majority of the company’s automations were being built by people
who  were  not  deep  technical  specialists,  with  the  relationship  between  IT  and  the  business
repaired rather than strained (Tella et al., 2023). The CoE prevented shadow IT by making itself
unnecessary to route around.

Two things here are previews, not this week’s lesson, and you should hand them forward cleanly
rather than reach for them now. The technology that makes safe, large-scale citizen development
actually work — the platform and controls beneath democratisation — is a later subject; in Tella’s
own structure it is the architectural underpinning that follows the scale-mindset chapter, and in
this course its fuller treatment comes with the agent-design and governance work later in the term.
And the deeper questions of what to do when the tools become generative — when someone can
describe an automation in words and have it built — belong to Modules 3 and 4. For Week 5, hold
the mindset and the guardrails; the machinery underneath comes later.

A CoE that hoards is a bottleneck; a CoE that stewards is a multiplier.  The scarcity
mindset treats scarce specialists as the only ones allowed to build, so the ninety-nine percent
of processes never gets automated. The scale mindset removes the dam and installs
guardrails — the CoE’s governance and review — so far more people build safely. That is
also how a CoE prevents shadow IT: not by policing it, but by opening a better-lit path than
the shadow one. The platform beneath large-scale citizen building is previewed for Week 8,
not taught here.

Automate Alongside the Workforce, Not Instead of It

A  scaled  automation  programme  is  a  decision  about  people  as  much  as  about  bots,  and  this
section makes explicit a question Week 4 planted and promised would grow louder: even for a
rules-based system, where should a human stay in the loop on purpose? The comfortable reading
of ‘rules-based’ is ‘no human needed’, and it is a trap. Two bodies of thinking sharpen the answer
— one about how automation and people fit together in an operation, one about how automation
and people fit together across the whole design.

Westerman, Bonnet and McAfee, in the operations chapter of Leading Digital, give you the frame
for the design question. They argue that managers have long treated a set of operational choices
as painful either/or trade-offs, and that digital technology, used well, breaks the trade-off into a
both/and.  The  one  that  matters  most  here  is  standardizing  versus  empowering.  The  old
assumption  was  that  standardising  work  —  and then automating  it  —  necessarily  deskills  and
disempowers the people who did it. Westerman and his co-authors show companies for whom it
did the opposite: automating the routine freed people into the judgement-heavy work only people
can  do.  Their  cleanest  example  is  a  paint  company  that  moved  routine  order-taking  from  field
salespeople into a standardised, centralised system — and, in doing so, turned those salespeople

10

from order-takers into relationship managers, doing more valuable work than the routine had ever
allowed (Westerman, Bonnet and McAfee, 2014). The point for your programme is that ‘automate
alongside the workforce, not instead of it’ is not a slogan you bolt on at the end; it is a design
choice you make when you decide which part of a role the bot takes and what the person is freed
to do instead.

The same authors add a second idea that reframes what a CoE is really building. They observe
that operational advantage is peculiarly hard for competitors to copy, because it lives not in any
single tool but in the way processes, skills, and information are tuned to work together as one
machine — the workings are hidden even when the results are visible (Westerman, Bonnet and
McAfee, 2014). Read that against the CoE. A pile of bots is easy to copy; anyone can license the
same  tool.  A  Center  of  Excellence  —  the  people,  the  standards,  the  review  pipeline,  the
accumulated judgement about which processes reward automation and which do not — is exactly
the tuned, hidden capability that is hard to copy. When you argue for a CoE to your board, this is
the argument that lands: you are not asking to buy bots, which any competitor can also buy; you
are asking to build a capability they cannot simply purchase.

Tella and his co-authors give you the operational side of the human question, in a taxonomy that
will also serve you as you preview the rest of the course. They distinguish three approaches to
automating work. Task-based automation takes a single discrete step and automates it in isolation
— the Week 4 move, useful and limited. Straight-through processing runs a whole flow end to
end with no human touch at all, which is right for high-volume, time-critical work like payments
but  wrong for  most  processes,  because  most  processes  still  need  a  person  somewhere  —  to
handle  an  exception,  exercise  judgement,  or  provide  the  human  contact  a  customer  actually
wants. Their third approach, orchestration, coordinates people, software, and data across an end-
to-end process, deliberately keeping people in the parts where their strengths matter most and
letting the machinery carry the rest (Tella et al., 2023). One clarification you must carry, because
the same word is about to mean three different things in this course: Tella’s ‘orchestration’ is an
automation-tooling idea — how you weave tasks, systems, and people into one flow. It is not the
same as the company roadmap phase you will meet in Week 11, and the deep machinery Tella
builds it on — event-driven architecture and an enterprise automation platform — is Module 3 and
4 territory that this note previews and does not teach. For Week 5, take from the taxonomy only
its  human  lesson: even at  the  pinnacle of  automation, the mature design  keeps people where
judgement lives.

11

Figure 3. Task-based automation, straight-through processing, and orchestration differ in how much runs without a person
— but in all three the mature design deliberately routes certain cases to a human.

Now answer the study question directly: when should a human be intentionally integrated into an
automated workflow, even for a rules-based system? Route a case to a person whenever the cost
of the bot being confidently wrong exceeds the cost of a human touch. Concretely, that means
the ambiguous edge cases where the rule does not really fit — O2’s multiple-iPhone order is the
archetype, a case that looked rule-covered and was not; the high-value or irreversible actions,
where a  single wrong  output  does  damage  that  cannot  be  undone  by re-running the  bot;  and,
above  all,  anything  a  silently-wrong  bot  could  quietly  ruin  over  weeks  before  anyone  notices,
which loops straight back to the ethics question and the CoE’s monitoring function. ‘Rules-based’
tells you the routine can be automated; it does not tell you the whole step should run unattended.
Choosing where the human stays is part of designing the automation, not an afterthought to it —
and in a scaled programme it is a standing governance decision the CoE owns, not a one-off call
a builder makes and forgets.

O2 lets you see the workforce side of this at scale, and honestly. Its programme did not eliminate
a department; the company estimated the people it freed in the hundreds, and — tellingly — as
service requests were handled faster and more accurately, the volume of customer ‘chase up’
calls fell by more than eighty percent, which in turn reduced the load on the front office as well as
the  back  (Lacity  and  Willcocks,  2016).  Some  of  those  freed  people  were  redeployed  as  the
business grew. That is the genuine version of ‘automate alongside the workforce’ — and Week 4
taught  you  to  be  sceptical  of  the  phrase,  because  ‘redeployment  to  higher-value  work’  is
sometimes a real commitment and sometimes a convenient narrative a firm tells to avoid a harder
conversation. Hold the question open rather than closing it with a slogan; Week 13 returns to the
human side of automation in full, and your Board Memo §7 will have to answer it for your own
company rather than wave at it. For this week, plant the flag: a scaled programme is designed
around people from the start, or it is designed to fail them.

12

‘Rules-based’ does not mean ‘no human needed’.  Automating the routine can empower
people into judgement work rather than deskill them (Westerman et al., 2014), and a CoE is
the hard-to-copy capability, not the bots. Keep a human in the loop wherever a confidently-
wrong bot costs more than a human touch: ambiguous edge cases, high-value or irreversible
actions, and anything a silent error could ruin. The workforce obligation is real — hold it open;
Week 13 answers it in full.

Two Telecoms, Two Kinds of Evidence

You have read O2 in pieces throughout this note; now assemble it as one story, because its arc
is the arc of the week. Then set beside it a second telecom that looks superficially similar and is
a completely different kind of evidence — and learning to tell those two kinds apart is itself a board
skill.

The anchor — Telefónica O2 (Lacity and Willcocks, 2016)

The  problem.  O2  is  a large  UK  mobile  operator whose back  office,  like most, faced relentless
pressure to do more work for less money. Through the 2000s it pursued the standard cost levers
—  offshoring,  then  process  elimination  and  simplification  —  and  reached  the  point  where
offshoring had little left to give and the mandate became blunt: cut headcount, response time, and
failure-driven customer calls each by half. Automation surfaced as the next lever.

What happened. O2 ran a deliberately small proof of concept — two high-volume, low-complexity
processes, automated in about two weeks — to answer three questions its board would ask of
any new tool: will it integrate with our systems without breaking them, will it deliver quality, and
will it pay back (Lacity and Willcocks, 2016)? It did, so emphatically that the bots’ volume tripped
the  company’s  own  fraud  alarms  and  the  programme’s  sponsor  was  briefly  suspected  of  an
intrusion.  Then  O2  did  the  disciplined  thing  and  tested  RPA  against  its  incumbent  business-
process-management  system  on  comparable processes;  the two automated  the  work  similarly
well, but RPA won decisively on the business case — roughly ten months to pay back against
about three years — and, as we saw, the reason was the operating model, not the technology:
RPA was run by reassigned Back-Office people with no draw on IT’s scarce developers. From
there  the  programme  scaled  in  waves  —  twenty  robots,  then  seventy-five,  then  more  than  a
hundred and sixty — run throughout by a team of three in-house developers, automating fifteen
core processes and reaching about thirty-five percent of all back-office transactions, at four to five
hundred  thousand  transactions  a  month,  a  twelve-month  payback,  and  a  three-year  return  on
investment the case puts at between six hundred and fifty and eight hundred percent (Lacity and
Willcocks,  2016).  The  scaling  was  not  frictionless  —  recall  the  lead-machine  collapse  and the
sixteen weeks of infrastructure re-engineering — which is exactly why the case is a scaling lesson
and not a fairy tale.

The lesson. The value landed on the three threads this course always watches. On Operations
and Supply Chain, the repetitive rules-based work was carried by bots at a fraction of the cost.
On  Cash,  turnaround  times  fell  from  days  to  minutes,  compressing  cash  conversion.  On
Customer,  the  eighty-percent  drop  in  chase-up  calls  meant  the  service was  fast  and  accurate
enough that customers no longer needed to phone. And the five lessons O2 itself drew read like

13

a  charter  for  a  Center  of  Excellence:  sequence  process  elimination  and  improvement  before
automation; give robots more explicit instructions than humans because they lack common sense;
grow the infrastructure in pace with the programme; choose the sourcing model deliberately; and
bring IT in early rather than pioneering behind its back (Lacity and Willcocks, 2016). That last one
is the governance moral of the fraud-alarm story: the pilot succeeded, but it nearly cost its sponsor
his job precisely because there was no sanctioned path — which is the case, in miniature, for
building one.

The illustration — Orange Spain’s ‘Robot Factory’ (UiPath vendor case study)

Now  set  beside  O2  a  second  telecom,  and  change  how  you  read.  The  Orange  Spain  case
describes  a  Center  of  Excellence  —  a  ‘Robot  Factory’  —  that  the  vendor  reports  grew  from
thirteen people and zero bots into a team of around a hundred deploying more than four hundred
bots across the company, saving, it says, over thirty-four million euros in a little over two years,
while training employees across the company to build automations. Read as a growth arc, this
illustrates two things this week teaches: the same pilot-to-enterprise trajectory O2 lived, and the
human dimension — hundreds of employees trained as builders is the scale mindset made visible,
automation built alongside the workforce rather than dropped on it.

But read it as evidence and everything changes, and this is the deliberate lesson of pairing the
two  cases.  Orange  Spain  is  a  UiPath  customer  story:  it  is  marketing,  produced  by the  vendor
whose product it praises, to sell that product. Every figure in it — the four hundred bots, the thirty-
four  million  euros,  the  hundred-strong  team  —  is  a  claim  the  vendor  is  making,  not  a  number
independently verified by researchers, and you should treat it that way. That does not make the
figures  false;  it  makes  them  uncorroborated,  which  is  a  different  thing  your  board  must
understand. The discipline is threefold: never let a vendor number carry a load-bearing claim in
your argument; corroborate any figure you actually need from an independent source before you
rely  on  it;  and  capture  the  source’s  title,  publisher,  and  date  so  that  even  if  the  link  dies,  the
provenance stays traceable. O2 and Orange Spain teach the same scaling lesson, but they are
not the same kind of evidence — one is peer-reviewed research, one is a sales asset — and a
board-ready analyst is the person who can hold both, use each for what it is good for, and never
confuse the two. That is why the two telecoms travel together in this note.

Use the anchor to establish, the vendor case to illustrate — and never confuse the two.
Telefónica O2 is peer-reviewed research: its figures — pilot to 160+ bots, three builders,
~35% of transactions, days-to-minutes, 650–800% ROI — can carry your argument. Orange
Spain’s ‘Robot Factory’ is vendor marketing: its figures are claims, useful only to illustrate the
growth arc and the certified-builder workforce, never to carry a load-bearing point.
Corroborate what you rely on; capture provenance so a dead link stays traceable.

Where This Points: The Threads, the Labs, and the Capstone

Pull the week together on the three axes this course always uses. On the threads, scaling and
governance sit first on Operations and Supply Chain — the programme finds most of its bots in
operational, rules-based work — but you have watched the payoff land on Cash (O2’s days-to-
minutes turnaround) and on Customer (the collapse in chase-up calls). When you design your

14

company’s operating model, tag the value by thread, because a board funds a thread outcome,
not an org chart.

On the  labs,  this  week  is  the  concept  that  Lab 2  makes  physical. In Week  6 you  will  take  the
stable-rules decision point you found in Lab 1 — your RPA candidate — and build it in Make, and
then you will deliberately break it. That break is not a mishap; it is this week’s selector-instability
lesson delivered at one-bot scale, so the brittleness you read about here stops being abstract.
And the one-page post-mortem Lab 2 asks for — what broke, what human oversight you would
build in — is the CoE’s bot-ownership-and-monitoring function practised on a single bot before
you argue for it across a company. Keep the lab spine straight, unchanged since Week 4: the
stable-rules decision point is your RPA candidate and your Lab 2 target; the judgment decision
point is not for RPA — it branches off to become your AI-agent target — you pin it down in Week
7 and build it in Lab 3 (Week 9).

On  the  capstone,  your  deliverable  is  the  operating-model  half  of  Board  Memo  §4  (Automation
Journey): a draft Center-of-Excellence and operating-model section for your company. Week 4
gave §4 its first half — the RPA-candidate scan, which fills the Automation-opportunity slide. This
week gives §4 its second half — how automation would be owned, governed, and run at scale —
which fills the Automation-journey slide, S7. Both are still Diagnose-phase work: you are not yet
proposing the intelligent, agentic future; you are showing the board that you know how a company
would actually run automation, not just where a bot could go. Lab 2’s working automation and
post-mortem complete §4’s evidence.

Two directions are deliberately left for later, and you should hand them forward rather than reach
for them. The move from rules to genuine machine judgement — intelligent automation — is Week
7;  the  agent’s  SPAR  architecture  is  Week  8;  and  you  build  the  agent  in  Lab  3,  Week  9.  The
platform  and controls  beneath  safe large-scale citizen  building  come  later  in  the term,  not this
week. The deeper redesign toward event-driven operations, and the strategic roadmap a board
commits to, are Modules 3 and 4 — and note again that this course uses ‘orchestrate’ in more
than one sense: Tella’s tooling sense is not the roadmap phase you will build in Week 11, and
this note deliberately avoids the roadmap’s language so the two never blur. This week teaches
only the second rung fully: how a programme scales, who governs it, and where the human stays.

This week designs how automation is run; the next steps make it intelligent and, later,
strategic.  Tag your operating model’s value by thread — boards fund outcomes, not org
charts. Lab 2 builds your Lab 1 stable-rules candidate in Make and breaks it, making selector
instability and the ownership discipline concrete; the judgment point is handed to AI (Week 7,
Lab 3). Your deliverable is the CoE / operating-model half of Board Memo §4 — the
Automation-journey slide, S7 — still Diagnose-phase work.

Writing Your CoE and Operating-Model Section

Turn all of this into the deliverable, because an operating model is only useful if it is written in a
form  a  board  could  actually  staff.  Do  not  draw  an  aspirational  org  chart.  Design  the  smallest
governing  arrangement  that  would  let  your  company  run  automation  past  the  pilot  —  sized

15

honestly to your archetype — and write it as a short section a board could act on. Six questions
structure it, and they map one-to-one onto the CoE’s five functions plus the human question.

First,  who  owns  automation?  Name  the  home  —  and  remember  O2’s  lesson  that  the  most
consequential choice is whether it lives with the business or with IT, and against whose budget it
runs.  Second,  what  is  the  sanctioned  path  —  how  does  a  new  automation  request  arrive,  get
reviewed, and get approved before it goes live? This is your answer to bot sprawl and shadow IT.
Third, who owns each bot in production, and how is its health watched — so that a silent error is
caught in days, not discovered by a customer? This is where you answer the week’s accountability
question  explicitly.  Fourth,  how  do  you  enable  more  builders  safely  —  do  you  train  business
people,  and  if  so  under  what  guardrails?  Fifth,  how  does  the  infrastructure  scale  so  your
programme does not hit O2’s lead-machine wall? And sixth, running through all of them: where
do you deliberately keep a human in the loop, and what does the company owe the people whose
routine work the programme automates?

Scale the answer to your archetype rather than copying O2’s. For the fifty-person services firm
on HubSpot and Notion, the ‘Center of Excellence’ may be one named owner, a one-page rule
for what may be automated and who signs off, and a shared list of every automation with an owner
beside  it  —  that  is  a  governing  model,  small  but  real.  For  the  mid-market  manufacturer  on
NetSuite,  it  may be  a  two-person  function  that  reviews  and  owns  bots  and  trains  a  handful  of
business builders. For the CPG enterprise on SAP, it may look much like O2’s. Keep it honest
and short: a board is more convinced by a small operating model it believes you could staff on
Monday than by a grand one it knows you cannot. That written section, with Lab 2’s working bot
and post-mortem beside it, is your Board Memo §4  — and it is worth more than a longer plan
precisely because it shows you know how automation is run, not just where it could go.

Design the smallest governing model your company could actually staff.  Answer six
questions: who owns automation (and against whose budget), what the sanctioned build path
is, who owns and monitors each bot, how you enable more builders safely, how infrastructure
scales, and where the human stays. Size it to your archetype — one named owner and a
written rule is a real model for a fifty-person firm. A small model a board believes beats a
grand one it doesn’t. This is Board Memo §4.

Study Questions

Bring  reasoned  answers;  they  are  designed  to  be argued  with the  cases  and frameworks,  not
recited.

1.  What is ‘selector instability’, and how does an unexpected system update break an RPA
script? Explain the mechanism in your own words, then use the O2 iPhone example — or a step
from your own Lab 1 map — to show why ‘the bot kept running and did the wrong thing’ can be
worse than ‘the bot stopped’.

2.  What is the primary managerial function of an Automation Center of Excellence, and how
does it prevent shadow IT? Answer both halves: what a CoE governs (not just builds), and why
opening a sanctioned path drains the shadow better than policing it does. Ground your answer
in O2’s Back-Office-owned model and Tella’s scale mindset.

16

3.  When should a human be intentionally integrated into an automated workflow, even for a
rules-based system? Give the general rule — route to a person when a confidently-wrong bot
costs more than a human touch — and three concrete triggers. Connect your answer to the
week’s ethics question about a bot that is silently wrong for weeks, and note what you expect
Week 13 to add.

Running Glossary

New this week, plus the carried terms this note builds on.

Center of Excellence (CoE).  A small, permanent function that owns how automation is done
across a company — setting standards, running the intake and review pipeline, owning and
monitoring bots, enabling builders, and owning the platform. It governs automation as a
capability rather than building every bot itself.

Operating model (for automation).  The organisational design of a programme: who owns
automation, who builds it, against whose budget it runs, and how it is governed. O2’s case
shows this is a bigger determinant of success than the choice of tool.

Bot ownership.  The discipline of giving every production bot a named accountable owner and
a monitored health signal, with an audit trail that catches a wrong output in days. Where
accountability comes to rest once a task is automated.

Selector instability.  A bot addresses screen elements by selectors recorded when it was built;
a routine system update that moves, renames, or re-wraps an element breaks those selectors,
so the script fails or silently does the wrong thing. The mechanical form of RPA’s brittleness.

Integration drift.  The gradual failure that accumulates as the many systems a programme’s
bots ride on evolve independently over time, so stable seams become moving ones and
maintenance grows faster than the bot count.

Bot sprawl (shadow automation).  The uncontrolled proliferation of unowned, unmonitored
automations built off to the side when there is no sanctioned path — fragmentation with bots on
top. The organisational failure a CoE exists to prevent.

Scale mindset (vs scarcity mindset).  Treating the ability to build automation as something to
multiply under guardrails rather than a scarce resource to hoard inside a specialist team.
‘Remove the dam, install guardrails’ (Tella et al., 2023).

Shadow IT / rogue IT.  Technology or automation adopted by the business without IT’s
sanction; in its worse form (rogue IT), business data moved or transformed in unsanctioned,
unwatched ways. A symptom of a closed or slow sanctioned path.

Guardrails.  The standards, intake review, and controls a CoE puts around building so that
many people can automate safely — the mechanism that lets a company embrace scale without
embracing chaos.

Straight-through processing (STP).  Running a whole flow end to end with no human touch;
right for high-volume, time-critical work, wrong for most processes, which still need a person for
exceptions and judgement (Tella et al., 2023).

Orchestration (automation-tooling sense).  Coordinating people, software, and data across
an end-to-end process, keeping people where their strengths matter (Tella et al., 2023). Distinct

17

from the Week-11 roadmap phase of the same name and from Westerman’s operational
‘orchestrating’ — do not conflate the three.

Human-in-the-loop.  A deliberate design choice to route certain cases to a person even in a
rules-based system — ambiguous edge cases, high-value or irreversible actions, and anything
a silently-wrong bot could ruin. A standing governance decision the CoE owns.

RPA candidate criteria.  The three tests a step must pass to be worth a bot: repetitive, rules-
based, and stable. (Introduced Week 4; the stable-rules decision point that passes them is the
Lab 2 target.)

Leverage gap.  The distance between a backbone that works technically and a backbone that
delivers business value. Closing it, layer by layer, is the work of the course. (Introduced Week
1.)

make the master edit. No master bump from this chat.

18
