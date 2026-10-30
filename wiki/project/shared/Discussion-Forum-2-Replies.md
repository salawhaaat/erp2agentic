---
title: Discussion Forum 2 - Replies
type: deliverable
tags: [deliverable, discussion-forum, rpa, coe]
description: Replies to classmates on Discussion Forum 2 (where the line sits between safe RPA rules and exceptions).
---
# Discussion Forum 2 - Replies

Replies are due Oct 31, 2026, at least two. No length is set, so each is kept to about 100 to 150 words.

## Reply to Rahul Nair (NYC DOF, ACRIS and PTS bot)

Rahul, loud versus silent is the right line. Our Sweetgreen bot failed the same way. A missing availability value produced no row at all, so that order vanished and nothing flagged it.

Here is where I would push. You say DOF finds these cases today only through random audits. If your bot catches two of five company sales and reports success, auditors may start trusting it and sample less. At 40 percent recall, the bot could make the process quieter without making it safer. Would you keep the random audit running beside the bot and use its hits as a recall check?

We also split our review into two queues. Unreadable data went to an integration owner. Real judgment calls went to the shift lead. Your blank BuyerType and Rework misses look like the first kind. Do they reach the same auditor who decides about heirs?

## Reply to Dyson Ye (LVMH invoice and mapping automation)

Dyson, the number I find most interesting is 33 of 54 exceptions resolved by approved rules. It means the exception path is already partly automatable, so the line moves as the mapping table grows.

My challenge is the 186 that passed. Our first Sweetgreen rule also passed its cases. It approved four of our five problem orders, and every row looked fine. A pass only means the rule found nothing wrong. Did you sample some of the 186 and check them by hand? A renamed column is a loud failure because the field breaks. A valid-looking wrong mapping is silent.

On stopping at the gate: when our AI suggestion gets three rejections in 24 hours, only that step pauses. Clean orders keep flowing. Would a renamed column halt all 240 records, or only the affected ones?
