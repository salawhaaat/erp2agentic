---
tags: [deliverable, week2, context-and-diagnosis-brief, sweetgreen]
company: Sweetgreen
due: Week 3 (before Lab 1)
feeds: ["Board Memo §2", "Storyboard S4"]
---

# Context-and-Diagnosis Brief — Sweetgreen

> One page. Assembles the three Week 2 breakouts (friction list → selective-redesign call → adoption + leverage case) over the [[Backbone-Context-Note-Sweetgreen|Week 1 backbone-context note]]. Board Memo §2 · Storyboard S4.

## The strategic problem

Sweetgreen sells a fast, customized, consistent meal, and **61.8% of FY2025 revenue arrives digitally** — but that demand lands on two different kitchen formats (traditional make-line and Infinite Kitchen) and multiple ordering channels that don't obviously share one live truth about menu availability, order status, and kitchen capacity. The backbone works well enough to take the order; it does not obviously guarantee the order survives contact with the kitchen unchanged.

## Breakout 1 — Four-Lenses friction list (Order-to-Cash)

**Process traced:** Customer places order → Payment authorized → Order enters restaurant system → Kitchen receives order → Meal prepared → Order verified and packed → Pickup or delivery → Transaction completed.

| Lens | Suspected value leak | Why it matters | Thread |
|---|---|---|---|
| **Frustration** | Unavailable ingredients or substitutions aren't communicated consistently across channels | Customer gets something different from what they ordered; employee has to explain or fix it | Customer |
| **Time** | App, web, in-store, and third-party orders compete for the same kitchen capacity at peak | Orders queue, employees are pressured, customers/drivers wait longer than promised | Operations |
| **Cost** | Incorrect, delayed, or canceled orders trigger remakes, refunds, extra packaging and labor | The restaurant spends resources twice without creating additional customer value | Operations + Cash |
| **Quality** | Menu availability and customization details don't reliably stay consistent from ordering channel through kitchen execution to handoff | The finished meal may not match the promised digital order | Customer + Operations |

**The overlap (circled leak):** order accuracy and availability information **at the handoff between digital ordering and kitchen execution** — it rings all four lenses and all three threads (Customer, Operations, Cash) at once. This is corroborated by Sweetgreen's own recruitment materials, which name order accuracy, menu availability, third-party platform performance, item availability, and "86'ing" (marking an item unavailable) workflows as active coordination problems between digital product and restaurant operations.

## Breakout 2 — Selective redesign call

**Obliterate vs. adopt-standard:** Sweetgreen should **not** assume it needs a wholesale new automated kitchen — it already operates Infinite Kitchen locations and has reported throughput and accuracy gains there. The platform standard to adopt is the existing kitchen technology; the part to redesign is the **integration layer** between order intake and kitchen execution.

**Redesign candidates, in order of value at stake:**

1. **Order accuracy at preparation** — the biggest overlap leak. A customized item is prepared incorrectly, an ingredient is missed, or the wrong order reaches the customer. This is where Sweetgreen's core value proposition (fast, customized, consistent) is actually delivered or lost.
2. **Peak-period kitchen congestion** — digital, delivery, and walk-in demand compete for the same fixed kitchen capacity; queues form faster than the line can absorb, and this caps how much revenue the store can economically capture during its most valuable hours.

**One-sentence leverage gap:** *"Our backbone fails to leverage at the channel→kitchen handoff: Sweetgreen generates digital demand faster and with more customization variance than its kitchens can reliably and visibly absorb, costing order accuracy, throughput, and customer trust."*

## Breakout 3 — Adoption note + leverage case

- **Who co-designs it:** frontline crew and shift managers who currently absorb both the lunch-rush stress and the burden of remaking incorrect orders — they must help define how the redesigned handoff actually works on the line.
- **Standardization tax:** a tighter, more event-driven make-line reduces workers' physical autonomy over portioning and pacing. Soften it by explicitly redefining roles — shifting time freed from repetitive assembly toward prep quality and front-of-house hospitality, not simply speeding up the same job.
- **Rollout phasing:** progressive, not Big Bang. Pilot the tighter channel↔kitchen integration in a small number of new builds or high-volume urban retrofits first, prove the lift in accuracy and throughput against the current baseline, then scale.
- **The one-line leverage case (board-fundable):** *"Fund a phased integration of real-time menu, capacity, and order-status visibility between ordering channels and kitchen execution — traditional and Infinite Kitchen alike — to cut order-accuracy failures and peak-hour wait times, and structurally raise throughput without expanding the kitchen footprint."* Not "install new kitchen software" — redesign how the channel and the kitchen see each other.

## First-pass functional vs. technical requirements

| | Functional (what the business needs) | Technical (what the system must do) |
|---|---|---|
| 1 | Every channel must show the same real-time item/ingredient availability | Shared, live availability state read by all ordering channels and both kitchen formats |
| 2 | Promised completion time must reflect actual kitchen load | Real-time capacity signal feeding channel-facing time estimates |
| 3 | An order's status must be traceable end-to-end, including exceptions | One order record that both traditional and Infinite Kitchen systems write to/read from |

---
**Carries forward into:** [[Lab1-Prework-Sweetgreen]] (Lab 1 pre-work, due before Week 3) and Board Memo §2 / Storyboard S4.
