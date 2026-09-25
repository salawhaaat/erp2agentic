---
type: deliverable
tags: [deliverable, week2, context-and-diagnosis-brief, sweetgreen]
company: Sweetgreen
due: Week 3 (before Lab 1)
feeds: ["Board Memo §2", "Storyboard S4"]
---
# Context-and-Diagnosis Brief — Sweetgreen

> One page. Assembles the three Week 2 breakouts (friction list → selective-redesign call → adoption + leverage case) over the [[Backbone-Context-Note-Sweetgreen|Week 1 backbone-context note]]. Board Memo §2 · Storyboard S4.

## The strategic problem

Sweetgreen sells a fast, customized, consistent meal, and **61.8% of FY2025 revenue arrives digitally — climbing to 66.3% by Q2 2026** — but that demand lands on two different kitchen formats (traditional make-line and Infinite Kitchen) and multiple ordering channels (app, web, kiosk, Olo-routed third-party) that don't obviously share one live truth about menu availability, order status, and kitchen capacity. The backbone works well enough to take the order; it does not obviously guarantee the order survives contact with the kitchen unchanged.

**Update (Sep 2026):** two real-world developments sharpen this diagnosis since it was first drafted:

1. **The Infinite Kitchen handoff now crosses a company boundary.** In December 2025, Sweetgreen sold the Infinite Kitchen technology to **Wonder**, keeping only a license-back; Wonder now owns and operates that kitchen system at ~30 stores and sells units back to Sweetgreen. The channel→kitchen integration this brief calls for is no longer purely internal — for those stores it is an inter-company data-sharing problem, which raises both the stakes and the difficulty of the fix.
2. **Cash pressure has intensified, and a category-wide trust shock shows the Customer thread is fragile.** FY2025 net loss widened to $(134.1)M (from $(90.4)M), and same-store sales fell further through Q2 2026, partly attributed to a multistate cyclospora outbreak (traced by the FDA to a Taylor Farms iceberg-lettuce supply chain, which Sweetgreen does not use). Sweetgreen wasn't at fault, but still lost ~25% of market cap in days and had to shift its menu toward warm bowls/wraps — evidence that **consumer trust in "what's actually in my order" is a systemic vulnerability for the category**, and reinforces why order-accuracy/availability visibility (this brief's core leverage case) is board-fundable, not a nice-to-have.

## Breakout 1 — Four-Lenses friction list (Order-to-Cash)

**Process traced:** Customer places order → Payment authorized → Order enters restaurant system → Kitchen receives order → Meal prepared → Order verified and packed → Pickup or delivery → Transaction completed.

| Lens | Suspected value leak | Why it matters | Thread |
|---|---|---|---|
| **Frustration** | Unavailable ingredients or substitutions aren't communicated consistently across channels | Customer gets something different from what they ordered; employee has to explain or fix it | Customer |
| **Time** | App, web, in-store, and third-party orders compete for the same kitchen capacity at peak | Orders queue, employees are pressured, customers/drivers wait longer than promised | Operations |
| **Cost** | Incorrect, delayed, or canceled orders trigger remakes, refunds, extra packaging and labor | The restaurant spends resources twice without creating additional customer value | Operations + Cash |
| **Quality** | Menu availability and customization details don't reliably stay consistent from ordering channel through kitchen execution to handoff | The finished meal may not match the promised digital order | Customer + Operations |

**The overlap (circled leak):** order accuracy and availability information **at the handoff between digital ordering and kitchen execution** — it rings all four lenses and all three threads (Customer, Operations, Cash) at once. This is corroborated by Sweetgreen's own recruitment materials, which name order accuracy, menu availability, third-party platform performance, item availability, and "86'ing" (marking an item unavailable) workflows as active coordination problems between digital product and restaurant operations — and by the now-confirmed backbone, where that handoff runs through at least four separate vendor systems (**Olo** ordering → **PAR Brink** POS/order intake → **Crunchtime** inventory/ops → **Wonder**-owned Infinite Kitchen hardware for ~30 stores), each a potential point where the "single live truth" this brief calls for can silently drift.

## Breakout 2 — Selective redesign call

**Obliterate vs. adopt-standard:** Sweetgreen should **not** assume it needs a wholesale new automated kitchen — it already operates Infinite Kitchen locations and has reported throughput and accuracy gains there (and continues expanding it, now via a long-term supply arrangement with Wonder). The platform standard to adopt is the existing vendor stack (Olo, PAR Brink, Crunchtime, Wonder); the part to redesign is the **integration layer** between order intake and kitchen execution — including, now, the API/data-sharing contract with an external vendor (Wonder) rather than a purely internal system.

**Redesign candidates, in order of value at stake:**

1. **Order accuracy at preparation** — the biggest overlap leak. A customized item is prepared incorrectly, an ingredient is missed, or the wrong order reaches the customer. This is where Sweetgreen's core value proposition (fast, customized, consistent) is actually delivered or lost.
2. **Peak-period kitchen congestion** — digital, delivery, and walk-in demand compete for the same fixed kitchen capacity; queues form faster than the line can absorb, and this caps how much revenue the store can economically capture during its most valuable hours.
3. **Cross-company data sharing with Wonder** — new since the Dec 2025 divestiture. For Infinite Kitchen stores, real-time menu/capacity/status visibility now depends on a contractual integration with a separate company, not just internal engineering priority. This is a governance and vendor-management redesign as much as a technical one.

**One-sentence leverage gap:** *"Our backbone fails to leverage at the channel→kitchen handoff — now partly a cross-company handoff with Wonder — Sweetgreen generates digital demand faster and with more customization variance than its kitchens can reliably and visibly absorb, costing order accuracy, throughput, and customer trust."*

## Breakout 3 — Adoption note + leverage case

- **Who co-designs it:** frontline crew and shift managers who currently absorb both the lunch-rush stress and the burden of remaking incorrect orders — they must help define how the redesigned handoff actually works on the line.
- **Standardization tax:** a tighter, more event-driven make-line reduces workers' physical autonomy over portioning and pacing. Soften it by explicitly redefining roles — shifting time freed from repetitive assembly toward prep quality and front-of-house hospitality, not simply speeding up the same job.
- **Rollout phasing:** progressive, not Big Bang. Pilot the tighter channel↔kitchen integration in a small number of new builds or high-volume urban retrofits first, prove the lift in accuracy and throughput against the current baseline, then scale.
- **The one-line leverage case (board-fundable):** *"Fund a phased integration of real-time menu, capacity, and order-status visibility between ordering channels and kitchen execution — traditional and Infinite Kitchen alike — to cut order-accuracy failures and peak-hour wait times, and structurally raise throughput without expanding the kitchen footprint."* Not "install new kitchen software" — redesign how the channel and the kitchen see each other.

## First-pass functional vs. technical requirements

| | Functional (what the business needs) | Technical (what the system must do) |
|---|---|---|
| 1 | Every channel must show the same real-time item/ingredient availability | Shared, live availability state read by all ordering channels (Olo, app, web, kiosk) and both kitchen formats |
| 2 | Promised completion time must reflect actual kitchen load | Real-time capacity signal feeding channel-facing time estimates, sourced from PAR Brink/Crunchtime and, for Infinite Kitchen stores, Wonder's system |
| 3 | An order's status must be traceable end-to-end, including exceptions | One order record that both the traditional-line stack and Wonder's Infinite Kitchen system write to/read from — requiring a defined API contract, not just internal integration |

---
**Carries forward into:** [[Lab1-Prework-Sweetgreen]] (Lab 1 pre-work, due before Week 3) and Board Memo §2 / Storyboard S4.

> [!info]- Sourcing for the Sep 2026 update
> - FY2025 10-K (filed 2026-02-27): [sg-20251228.htm](https://www.sec.gov/Archives/edgar/data/1477815/000162828026012520/sg-20251228.htm)
> - Q2 2026 earnings release (8-K ex99.1, filed 2026-08-06): [q226sweetgreenearningsrele.htm](https://www.sec.gov/Archives/edgar/data/1477815/000162828026054324/q226sweetgreenearningsrele.htm)
> - Systems Engineer II, New Restaurant Openings job posting (careers.sweetgreen.com, via freehire.me) — confirms PAR Brink, Olo, Salesforce, Crunchtime-adjacent inventory/loyalty stack
> - CNBC, "Sweetgreen isn't linked to cyclospora, but the outbreak is still hurting business" (2026-08-13): [cnbc.com](https://www.cnbc.com/2026/08/13/cyclospora-outbreak-sweetgreen-ceo.html)
> - Bloomberg, "Sweetgreen Expands Menu With Warm Bowls, Wraps as Salad Sales Decline" (2026-08-12): [bloomberg.com](https://www.bloomberg.com/news/articles/2026-08-12/sweetgreen-seeks-to-shake-salad-image-as-diners-turn-from-greens)
> - Restaurant Technology News on the Wonder divestiture: [restauranttechnologynews.com](https://restauranttechnologynews.com/2025/11/sweetgreen-sells-restaurant-robotics-arm-to-wonder-while-continuing-infinite-kitchen-expansion/)
