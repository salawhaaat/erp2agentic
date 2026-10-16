---
title: Discussion Forum 1 - Replies
type: deliverable
tags: [deliverable, discussion-forum]
description: Two substantive replies to classmates on Discussion Forum 1 (Inditex DC2 and LVMH).
---
# Discussion Forum 1 - Replies

## Reply to Siddharth Sameer (Inditex DC2)

Your split between the audit control and the manual loop around it is the right one. I want to push on two points.

First, your sandbox shows 12 of 24 tasks entering rework. That rate is seeded, so it can't tell us whether the mismatches come from bad observations or from a wrong theoretical record upstream. If the record is wrong, faster verification treats the symptom. In my Sweetgreen scan, I rejected the stock-accuracy root cause as a bot candidate for the same reason. It was a redesign job, and automating around it would pave the cow path.

Second, your RFID caveat sits awkwardly with your "management, not technology" conclusion. If reads are unreliable, part of this is a genuine technology constraint. Which finding decides it? I would say the answer depends on the share of exceptions caused by position association errors. Do you have a view on who owns that record at the control point?

---

## Reply to Vania Salsabila (LVMH)

I agree with adopting the standard at the master-data layer and leaving the Maison ERPs alone. In the Ross and Weill terms from Week 1, that is Coordination: integrate the data, not the process. I have two challenges.

First, "technology/system landscape" and "standardization and integration" are not among the Four Lenses or Three Threads. Invoices that fail mapping and need finance review are errors someone else must fix, which reads as Quality. The thread is Cash, since slow consolidation delays the group view. Naming them this way makes your funding case sharper.

Second, standards have a price. Maisons lose autonomy over supplier IDs and account definitions, so who owns the Group master data, and where is it born? If supplier IDs are fixed at creation, the finance review loop shrinks. If they are only translated at consolidation, the leak stays. Which of your exceptions are true mismatches, and which are stable rules a bot could close?
