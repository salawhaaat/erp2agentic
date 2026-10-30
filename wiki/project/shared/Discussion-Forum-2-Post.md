---
title: Discussion Forum 2 - Post
type: deliverable
tags: [deliverable, discussion-forum, rpa, coe, sweetgreen]
description: Discussion Forum 2 post on where the line sits between safe RPA rules and exceptions, argued from the Sweetgreen Lab 2 build and break.
sources:
  - id: lab2
    resource: wiki/project/week6/Lab2-Automation-Sweetgreen.md
  - id: coe
    resource: wiki/concepts/Center of Excellence.md
---
# Discussion Forum 2 - Post

Prompt: Module 2 claims RPA is the fastest, lowest-risk way to capture value from a working backbone, and also that it is brittle without a Center of Excellence. Argue where the line sits, using Lab 2. Post due Oct 28, 2026, 300 to 350 words. Two replies to classmates due Oct 31.

Copy everything under the line below into the forum box. It is 346 words, plain text, no formatting needed.

---

The line sits where a rule needs a fact it cannot check.

In Lab 2 I automated D2, Sweetgreen's availability check, in Make. A rule can safely decide the clean case: the item is in stock, the order is new, the source is under 60 minutes old, and every line matched. Our two happy orders went straight through. That is a good RPA candidate. The input is stable and the answer is yes or no.

Then we broke it. My first rule approved an order whenever the cached availability said 1. It approved four of our five problem cases. In two of them the current feed said the bowl was out. In another the source was 670 minutes old. The fifth case had a missing value and produced no row at all, so that order just disappeared. Nothing crashed. The bot kept writing confident rows. That silent confidence is the brittleness Module 2 warned about. Adding a Router changed nothing, because the rules were wrong, not the routing.

The failure taught me that exceptions come in two kinds, and each needs a different person. Stale or missing data goes to the integration owner, who repairs the input. A real stockout goes to the shift lead, who judges the recovery at D3 and gets the customer's consent at CP3. So the final rule has three outcomes: approve, staff review, data review. When we later added an AI suggestion on top, the same idea held. It recommends, a person decides, and three rejected suggestions in 24 hours switch it off.

A Center of Excellence is what lets this scale. It would own and version the rules, and require a break test before release, with problem cases and not only happy ones. It would name an owner for each review queue, set a freshness limit, and stop duplicate rows. Our data is synthetic, so I cannot say how often this happens in a real store. I can say a rule is only as safe as the exceptions someone tested.

Where would you draw the line in your own case?
