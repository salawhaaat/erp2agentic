---
title: Discussion Forum 1 - Post
type: deliverable
tags: [deliverable, discussion-forum, sweetgreen]
description: Discussion Forum 1 post on the Sweetgreen availability-check leak, with the obliterate-and-redesign call.
---
# Discussion Forum 1 - Post

**The leak**

The step that leaks most is the availability check before the kitchen starts cooking (D2, "can the order be prepared as specified?"). It reads from two sources: a live system and a nightly legacy cache. They don't always agree. In my sandbox, 6 of 30 orders hit that mismatch. They cost 60 extra staff minutes and $20 in refunds, about $44 in modeled exposure, and ran 18.7 minutes late on average.

**Lens and thread**

The Frustration lens surfaces it. A customer pays for a bowl the kitchen can't make, then waits for staff to call. It rings the Operations and Supply Chain thread, with Customer close behind.

**My call: obliterate and redesign**

I would not adopt the platform standard here. The yes/no rule is fine. The input feeding it is the problem. So I would drop the nightly cache as a decision source and rebuild the check around one live availability state. A freshness gate would hold any order when the sources disagree. Leaving the step alone means automating a rule that is wrong by construction, because it would faithfully act on yesterday's numbers.

**The central claim**

My diagnosis mostly bears it out. Sweetgreen runs Olo for ordering, PAR Brink for POS and Crunchtime for inventory. Nothing in that stack forces a nightly batch. Syncing tools like these is ordinary integration work. A stale cache survives when nobody owns menu availability across channels. That is a management gap wearing a technology costume.

I should be honest about the limits. The nightly batch was a curveball I chose, and the data is synthetic, so I haven't proven that Sweetgreen's real systems lag. Some legacy sources may truly lack a live feed. If so, the constraint is genuine. It still argues for a freshness gate, not for accepting the lag.
