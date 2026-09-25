---
title: Sweetgreen Public Research — Raw Source Log
type: research-log
tags: [research, sweetgreen, sources]
company: Sweetgreen
status: living note
feeds: ["Backbone-Context-Note-Sweetgreen", "Context-and-Diagnosis-Brief-Sweetgreen"]
---

# Sweetgreen Public Research — Raw Source Log

> Raw, source-tagged research gathered from public sources (SEC filings, press, an executive interview). This is a **research log**, not a deliverable — extend [[Backbone-Context-Note-Sweetgreen]] and [[Context-and-Diagnosis-Brief-Sweetgreen]] from here rather than duplicating this content into them wholesale. Add new sources to the bottom as they're found; keep entries dated.

## How to use this note

Each section below is one source. Every claim is tagged with where it came from so it can be cited or re-verified. The **Synthesis** section at the end pulls out what's new/useful for the capstone's core thesis (digital-channel ↔ kitchen-execution handoff).

---

## 1 · CEO interview: "Inside sweetgreen's Infinite Kitchen with CEO Jonathan Neman" (RestaurantSpaces, Jan 2024)

> [!info]- Source metadata
> - **URL:** https://www.youtube.com/watch?v=PPm53P6-xdk
> - **Channel:** influence group / RestaurantSpaces
> - **Upload date:** 2024-01-25 · **Duration:** 34:34
> - **Extraction method:** `yt-dlp` auto-captions, de-duplicated locally (no external tool install needed — `yt-dlp` was already present at `~/.local/bin/yt-dlp`)

> [!example]- Full cleaned transcript excerpt — origin story, automation rationale, Spice acquisition, personalization, format expansion
> **Origin & mission**
> - Founded by Jonathan Neman, Nicolas Jammet, Nathaniel Ru — Georgetown students, first restaurant Aug 2007 in a converted 500 sq ft burger shack in DC, budget overran from a planned $50–100K to ~$300K.
> - Mission since day one: "build healthier communities by connecting people to real food." First core value: **win-win-win** (customer / community / company).
> - By the time of this interview: 220 restaurants, ~20 cities, all company-owned, ~$2–3M average unit volume (AUV).
>
> **Automation rationale (why Infinite Kitchen exists)**
> - Three kitchen workflow stages: (1) hot/cold prep — skilled, valued work; (2) assembly — not value-add, source of most operational problems; (3) hospitality/service — the valued human-facing work. Automation targets stage 2 specifically.
> - **Digital already dominates ordering**: "60% of our business happens digitally... people aren't even looking at a guest, they're making orders off a screen."
> - **Order accuracy math (direct quote, close paraphrase):** average bowl has 12 ingredients; 10 bowls = 120 items; getting 1 in 12 wrong across a batch yields a ~10% customer-facing error rate — accuracy is "challenging no matter how hard we try" on the manual make-line.
> - Labor cost trajectory cited as existential: CA minimum wage ~$20, compounding ~3.5%/yr → ~$29/hr in 10 years; plus unionization risk. Automation framed as the main lever to bring cost down "over time."
> - Sweetgreen tried building automation in-house first and **failed multiple times** — "if everything was almonds and sunflower seeds, automation would be really easy... it's all about the edge cases" (dressing viscosity, temperature, plating).
>
> **Spice Kitchen acquisition → Infinite Kitchen**
> - Sweetgreen met Spice's founders ~7–8 years before the interview (met at the Harvard Square restaurant opening); shared investor (chef Daniel Boulud). Acquired the Spice team and technology ~2 years before the interview (i.e., ~2022).
> - First pilot location: **Naperville, IL, opened May 2023** ("aille" in the auto-caption = Naperville). Second unit: Huntington Beach, CA, "in less than two months" from interview date (~early 2024).
> - **Performance claims (Naperville pilot, first month):** 500 bowls/hour throughput, near-perfect accuracy, brighter/less-oxidized food, lower turnover, and a reported **26% four-wall margin** in the store's first month of operation.
> - **Design principle:** did not retrofit automation onto the existing workflow — built the whole restaurant format around it, same philosophy Sweetgreen used when first digitizing stores. Redesigned the front-of-house too: introduced kiosk ordering, concierge ordering, moved prep to the front.
> - **Resilience/modularity:** system is modular by lane and by module — a single lane can fail without stopping the whole line; only a full power outage stops it. Stores have a manual **"finishing station"** for a few ingredients that don't work in the machine (avocado, fish) as backup.
> - **Rollout economics:** greenfield is cheaper than retrofitting existing stores; retrofits will follow store renovation cycles. Sweetgreen intends to eventually **license/monetize the technology to other operators** ("democratizing automation").
> - **Moat framing:** patents exist, but Neman explicitly says technology is not the durable moat — brand, food quality, and experience are; technology advantages "dissipate" over time (cites COVID-era digital ordering as a precedent — Sweetgreen's early digital lead evaporated within about a week once the whole industry went online).
>
> **AI / personalization**
> - Two in-house proprietary ML-driven kitchen tools already in use at the time: a "hot prep" tool and a "cold prep" tool that guide kitchen staff on what to make and when, to minimize waste/maximize freshness.
> - Vision for **personalized menus** ("the Spotify of food") — using taste/nutrition/lifestyle profile data to generate a daily personalized menu per customer, plus a "personal chef" style constraint-based ordering mode (e.g., "50g protein, low sugar, spicy").
> - Loyalty/CRM personalization increasingly outsourced to third-party platforms rather than built in-house.
>
> **Store format expansion**
> - Sweet Lane (digital-only drive-thru pickup) launched ~2023 — described as the best-performing new channel, limited by real-estate availability.
> - Digital-only pickup store format (no ordering line, app-only) tested in dense urban/CBD environments.
> - Footprint mix shifted from >75% urban pre-COVID to ~50/50 urban/suburban, with continued suburban/Midwest push (80% of the US population is more suburban).
> - Sourcing philosophy: mix of national and regional suppliers; deliberately accepts regional taste variation (e.g., different kale/goat cheese by region) rather than forcing McDonald's-style national consistency.

---

## 2 · SEC 10-K — Fiscal Year 2025 (period ended 2025-12-28)

> [!info]- Source metadata
> - **URL:** https://www.sec.gov/Archives/edgar/data/1477815/000162828026012520/sg-20251228.htm
> - **Filing type:** Form 10-K (Annual Report), FY ended December 28, 2025
> - **Note:** this is the same 10-K already cited in [[Backbone-Context-Note-Sweetgreen]] §2/§5 — re-confirmed here, plus a few additional facts pulled out.

- **Corporate structure:** Delaware corp., incorporated Oct 2009; HQ 3102 36th St, Los Angeles, CA 90018; NYSE: SG; 106.9M Class A + 11.9M Class B shares outstanding (as of Feb 23, 2026); market cap ~$1.4B (mid-2025).
- **Footprint:** 281 restaurants, 24 states + DC; 6,486 total employees (248 corporate / 6,238 restaurant-level). Net new openings: 35 (2025), 25 (2024); ~15 planned for 2026.
- **Infinite Kitchen at FY-end:** deployed in 30 restaurants. **Sold to Wonder Group in December 2025**, retaining a perpetual, irrevocable, royalty-free license to keep deploying it in Sweetgreen-branded stores; deal includes milestone-based contingent consideration extending past FY-end.
- **Financials:** FY2025 net loss $(134.1)M vs. FY2024 $(90.4)M — losses widening, expected to continue.
- **Strategy:** "Sweet Growth Transformation Plan" — operational excellence, menu innovation, personalized engagement, brand relevance, disciplined capital allocation.
- **Risk disclosures:** consumer spending pressure (inflation, rates), labor cost inflation, tariff exposure, competitive intensity, post-pandemic WFH reducing urban lunch traffic, brand/reputation risk from automation rollout and food-safety incidents amplified on social media.

---

## 3 · Sweetgreen → Wonder Infinite Kitchen deal (Spyce sale), Nov 2025

> [!info]- Source metadata
> - **URLs:**
>   - https://foodondemand.com/11182025/wonder-buys-sweetgreens-infinite-kitchen-tech-whats-next/ (fetched successfully)
>   - https://www.qsrmagazine.com/story/sweetgreen-to-sell-infinite-kitchen-business-to-wonder-for-186-million/ (blocked — HTTP 403; title/headline only, via search snippet)
>   - https://www.restaurantbusinessonline.com/technology/sweetgreen-completes-sale-spyce-robotics-business-wonder
>   - https://www.restaurantbusinessonline.com/technology/sweetgreen-sell-spyce-technology-company-wonder-1864m

- **Deal:** Wonder acquired **Spyce** (the robotics/software platform underlying Infinite Kitchen) from Sweetgreen for **$186.4M** — $100M cash + $86M Wonder stock (per search-result summary; corroborates the 10-K's "contingent consideration" language).
- **What Sweetgreen keeps:** continues operating existing and future Infinite Kitchens under a **supply and license agreement** with Wonder — i.e., Sweetgreen is now a *customer* of its own former in-house technology.
- **What Wonder gets:** Spyce's automation IP/platform and **38 Spyce engineers/co-founders** join Wonder.
- **Wonder's plan:** open an Infinite-Kitchen-powered Wonder location in Manhattan (2026); target installing the tech in half of new Wonder kitchens by 2027; long-term aspiration of 100+ restaurant concepts run from compact automated kitchens; wants to extend automation beyond bowls to fryers, ovens, woks, beverages.
- **Strategic framing (Wonder's words):** the system has "proven ability to deliver significantly faster throughput and enhanced food quality, order accuracy, and portion consistency" while reducing team member turnover.
- **This is the single most important new fact for the capstone thesis:** the channel→kitchen handoff for Infinite-Kitchen stores now crosses a **corporate boundary** (Sweetgreen's ordering/POS stack talking to a Wonder-owned and Wonder-operated kitchen system), not just a systems boundary inside one company. Already flagged in [[Backbone-Context-Note-Sweetgreen]] §4, but this source adds the deal mechanics (price, engineer transfer, licensing structure) that make the boundary concrete.

---

## 4 · Operational turnaround reporting — Q1 2026 same-store sales decline & hospitality-vs-digital balance

> [!info]- Source metadata
> - **URL:** https://www.restaurantdive.com/news/sweetgreens-turnaround-hospitality-human-digital/823364/

- **Same-store sales fell 12.8% YoY in Q1 2026; traffic fell 11.2%** — this is new, and more severe than anything previously logged in the vault's deliverables (which cite FY2025/Q2 2026 digital-mix growth but not this magnitude of traffic decline). **Needs reconciling** with the Q2 2026 earnings figures already cited in the Backbone note — check whether Q2 showed recovery or continued decline.
- **Kiosk confusion at Infinite Kitchen stores:** early layouts put the ordering kiosk "front and center," which confused first-time customers about whether to order at the kiosk or with a person at the counter; Sweetgreen repositioned kiosks "off to the side" and added more front-of-house staff and signage to fix this — a direct, sourced example of the digital-channel/kitchen-execution handoff **failing at the customer-facing edge**, not just the backend.
- **~60% of transactions are off-premise/pickup** (consistent with the CEO interview's "60% digital" figure, though this specific number is about pickup, not digital ordering share — worth not conflating the two in the deliverables).
- Co-founder Nicolas Jammet quote: "There's so many different versions of the Sweetgreen experience" — supports the "stratification of formats" point from the CEO interview (urban vs. suburban, Infinite Kitchen vs. traditional, kiosk vs. counter).
- Service standard: greet every customer within 5 seconds of entering; specialized training at high-new-customer / automated locations.

---

## 5 · dotconor.com — Sweetgreen digital strategy case study (undated, appears to cover c. 2016–2021)

> [!info]- Source metadata
> - **URL:** https://www.dotconor.com/sweetgreen

- Digital-first product history: responsive web app + native iOS app (launched Jan 2016); salad builder, dietary filters, real-time pricing/calorie calc, SSO, Apple HealthKit integration.
- Custom internal CMS for "Head Coaches" (store staff) to manage ingredient sourcing/availability, plus real-time analytics dashboards for throughput, wait times, menu affinity, customer modifications — **an internal tool predating the Infinite Kitchen / Crunchtime-era stack**; useful historical context for how far back Sweetgreen's build-vs-buy tech philosophy goes.
- **68% of total sales were digital as of September 2021**, vs. Chipotle's 42.8% in the same quarter — Sweetgreen was a clear digital-adoption leader well before Infinite Kitchen existed.
- 1,000+ "Outpost" pickup locations (corporate offices, hospitals) — a fulfillment channel not otherwise covered in the vault's deliverables; worth checking whether Outposts still exist in the current footprint (not confirmed in FY2025 10-K search above).

---

## 6 · CNBC — "Inside Sweetgreen's first automated location" (2023-06-24)

> [!info]- Source metadata
> - **URL:** https://www.cnbc.com/2023/06/24/inside-sweetgreens-first-automated-location-plans-to-take-tech-nationwide.html
> - **Fetched via:** `defuddle` CLI (WebFetch returned HTTP 403 on this domain)
> - **Reporting date:** ~3 weeks after the Naperville, IL location opened (early May 2023)

> [!example]- Key facts — pilot mechanics, acquisition economics, labor math, early customer friction
> **Timeline & guidance**
> - Naperville, IL was the **first** Infinite Kitchen location, open since early May 2023.
> - CEO Neman, at the William Blair Growth Stock Conference (June 2023): *"In five years, we do expect eventually all Sweetgreen stores to be automated."*
> - A second location was planned for later in 2023 as a **retrofit** of an existing store (not disclosed at the time — this predates the Huntington Beach opening mentioned in the CEO interview, §1 above).
>
> **Spice acquisition economics**
> - Sweetgreen acquired Spyce in **August 2021**, just months before Sweetgreen's own November 2021 IPO, for **roughly $50M** (final valuation contingent on the startup's tech performance per regulatory filings) — a materially different, more precise figure than the qualitative "acquired the team and technology" framing in the CEO interview.
> - Spyce was founded in 2015 by four MIT graduates; ran two Boston-area restaurants pre-acquisition.
> - Post-acquisition, Sweetgreen trialed menu items in a former Spyce restaurant before closing it, then spent ~18 months adapting the tech: e.g., solving dispensing problems for goat cheese (clumps) and cherry tomatoes (squishes), consistent portioning for light (arugula) vs. heavy (sunflower seeds) ingredients, adding bowl rotation on the conveyor for even fill, and adding end-of-line mixing.
>
> **Naperville store design & throughput**
> - Ordering: five tablets in-store plus the app; mobile orders no longer require the traditional 10–15 minute wait.
> - Assembly: dispensers add dressing first, then greens/grains, then toppings, with the bowl rotating between stations; bowls skip stations for unneeded ingredients.
> - **Manual finishing step still required** for herbs, avocado, and fish — the same gap the CEO interview (§1) later confirms was still true in 2024.
> - **Throughput: up to 600 bowls/hour** if no bowl needs manual mixing — higher than the 500 bowls/hour figure cited in the 2024 CEO interview, suggesting either a later, more conservative operating figure or a difference between theoretical max and typical throughput. **Worth flagging this discrepancy (600 vs. 500 bowls/hr) explicitly if citing throughput numbers in the deliverables.**
> - Conveyor holds up to 20 bowls; mezzanine level above the line for staff to restock dispensers; digital screens flag low ingredients or malfunctions. **No backup make-line existed at Naperville** if the system failed — a materially different resilience picture than the "modular by lane" framing Neman gives in the 2024 interview, which describes graceful single-lane degradation but doesn't address a full-system failure with no manual fallback.
>
> **Labor economics**
> - T.D. Cowen estimate (2022): **~30% of Sweetgreen's costs are labor**, split roughly evenly between food prep and order assembly — assembly is exactly the stage Infinite Kitchen targets, which is the direct cost-rationale link back to the CEO's "assembly is the non-value-add stage" argument in §1.
> - Infinite Kitchen locations run on **roughly half the staff** of a traditional location (VP of Ops Strategy Tim Noonan). Peak periods (~90 min/day) no longer require extra scheduled staff — "the machine absorbs the peak."
> - Anticipated secondary benefits: faster/simpler new-hire training (no need to memorize prep recipes), potentially lower turnover from a calmer work environment.
>
> **Early customer friction — a second sourced example (in addition to the kiosk-placement issue in §4)**
> - Customers mistook the ordering tablets for "the automation" and the ingredient dispensers for a display fridge — i.e., **the automation itself was invisible to customers**, while the *ordering* UX was what they actually noticed.
> - **Longer lines reported at the tablet-ordering step**, not the kitchen: traditional Sweetgreen lets customers finalize their order while walking the assembly line (fast, incremental decisions); Naperville's app-like tablet UI forces undecided customers to stall at the point of order, creating a bottleneck. One Yelp reviewer describes walking away rather than wait in a line that stretched out the door.
> - Chicago-area industry analyst (Technomic VP Rich Shank) quote: **"The verdict is out on whether the user interface of any sort of kiosk can solve that problem"** — and separately notes machines can't yet handle real-time customization requests ("extra light on the dressing") the way a human line worker can. **This is a second, earlier, independently-sourced example of the same order-accuracy/handoff friction pattern** documented in §4's kiosk-repositioning story — useful as corroboration, not just a one-off anecdote.

---

## 7 · PIX11 / Yahoo — "Sweetgreen opens first automated kitchen in New York City" (Penn Plaza, Manhattan)

> [!info]- Source metadata
> - **Original URL (blocked, HTTP 403 on both WebFetch and defuddle):** https://pix11.com/news/local-news/quicker-and-easier-sweetgreen-opens-first-automated-kitchen-in-new-york-city/
> - **Mirror actually fetched (via `defuddle`):** https://www.yahoo.com/tech/quicker-easier-sweetgreen-opens-first-002655997.html — identical PIX11-bylined text, redistributed by Nexstar Media
> - **Location:** Sweetgreen at 7 Penn Plaza, Midtown Manhattan
> - **Opening:** first of the (then-)41 NYC Sweetgreen locations to get Infinite Kitchen; retrofit completed **July 15** after a **seven-week** remodel (year not stated in the article text itself, but consistent with the broader 2024 NYC retrofit wave — cross-check before citing a specific year)

- **Throughput claim here is lower and more specific than other sources: 400–500 bowls/hour, described as "50% more than a regular restaurant."** This is a third distinct throughput figure (alongside 500/hr from the 2024 CEO interview and 600/hr max from the 2023 CNBC piece) — treat these as a range (400–600 bowls/hr depending on store, mix, and whether it's a stated max or typical rate) rather than a single fixed number in the deliverables.
- VP Tim Noonan: staff get **notifications to restock ingredients and track orders** — i.e., the human role shifts from assembly execution to a monitoring/replenishment loop, consistent with the CNBC piece's description of staff watching screens for low-ingredient alerts.
- **Employment framing (contested claim):** Sweetgreen states no jobs were lost in the retrofit and that it's growing overall headcount even as per-store staffing drops — Chief People Officer Adrienne Gemperle is quoted making this claim directly. **This is a company claim, not independently verified in the article** — worth flagging as PR framing rather than fact if cited in the deliverables' risk/labor discussion.
- Andrew Rigie (Executive Director, NYC Hospitality Alliance) provides an external, non-Sweetgreen voice: acknowledges the job-loss concern directly, but is measured ("I think we're far off from The Jetsons") — a useful third-party quote for the deliverables if a labor-relations/community stakeholder perspective is needed for the Four Lenses analysis.
- Customer reactions were mixed-to-positive on speed, with one customer flagging portion consistency and malfunction risk as an open concern ("Hopefully the portion size stays consistent, and there are no malfunctions") — a lay-customer echo of the same accuracy/reliability concerns raised more analytically in §1 and §6.

---

## 8 · Not relevant — ruled out

- **https://www.columbia.edu/~cs2035/courses/ieor4405.S16/p26.pdf** — checked; this is an unrelated IEOR 4405 (Production Scheduling) course PDF with no Sweetgreen content. Included here only so it isn't re-checked by mistake later.

---

## Synthesis — what's new and actionable for the capstone

1. **The Wonder deal is more consequential than previously documented.** The Backbone note already flagged the company-boundary risk qualitatively; this research adds the deal mechanics (§3) that make it concrete and citable: $186.4M price, Sweetgreen now buys back its own former tech under a license/supply agreement, 38 engineers left with the IP. This strengthens Move 6 / the leverage-gap argument — the backbone's weakest handoff is now literally outside the company's own walls for ~30 (soon more) locations.
2. **Q1 2026 same-store sales/traffic decline (§4) is a new, more alarming data point** than what's in [[Backbone-Context-Note-Sweetgreen]] §1 — reconcile against the Q2 2026 figures already cited there (digital mix climbing) to see if this is a channel-mix story (more digital, fewer total transactions) or a broader demand problem. Worth a follow-up SEC/earnings check.
3. **The kiosk-confusion finding (§4) is a concrete, sourced example of the order-accuracy/handoff friction the thesis argues about** — not hypothetical. Good candidate for a specific anecdote in the Context-and-Diagnosis Brief's "friction list."
4. **CEO's own words (§1) directly confirm the thesis's central claim**: he describes assembly (not prep, not service) as the low-value, error-prone middle step, and gives the 10%-error-rate math himself. This is now a primary-source quote available for the deliverables, not just an inference from filings.
5. **Open thread:** Outpost pickup locations (§5) — confirm whether these still exist in the current footprint; not mentioned in the FY2025 10-K excerpt pulled so far.
6. **The ordering-side bottleneck is now corroborated by two independent, dated sources a year apart** (§6, Naperville 2023; §4, fleet-wide 2026), not just one anecdote — customers stall at tablet/kiosk ordering because Sweetgreen's traditional line lets people finalize choices incrementally while automated formats force an up-front decision. This is a *second, distinct* friction point from the "assembly/accuracy" one the CEO emphasizes in §1 — the deliverables should probably treat "ordering UX" and "assembly accuracy" as two separate friction nodes rather than folding them into one.
7. **Resilience claim in §1 is contradicted by §6:** Neman's 2024 description of graceful, lane-level failure ("only power can really shut it down") doesn't match CNBC's 2023 reporting that Naperville had **no backup make-line** for a full-system failure. Either the backup capability was added later (between 2023 and 2024) or the two accounts are simply inconsistent — worth a direct citation caveat rather than treating Neman's claim as unqualified fact.
8. **Throughput figures vary by source (400–500/hr NYC retrofit, 500/hr Naperville per CEO interview, up to 600/hr max per CNBC) and by whether manual mixing is needed** — cite as a range, not a single number, when used in the deliverables.
9. **Spice acquisition price is now precisely sourced: ~$50M in Aug 2021** (CNBC/regulatory filings), vs. Sweetgreen's ~$186.4M sale of the same asset back in 2025 — a striking multiple that's worth a line in the Context-and-Diagnosis Brief's financial framing of the Wonder divestiture.
10. **Labor economics are now quantified**: ~30% of costs are labor (T.D. Cowen, 2022 estimate, split roughly evenly between prep and assembly), Infinite Kitchen stores run on ~half the staff. Useful for a cost/benefit line in the diagnosis brief's redesign-candidate section.

## Next research candidates (not yet pulled)

- Wonder's Manhattan Infinite-Kitchen opening (2026) once it happens — would show the tech operating fully outside Sweetgreen for the first time.
- Q1 2026 10-Q or earnings release, to get the primary-source version of the 12.8% same-store sales decline (currently only sourced via Restaurant Dive's paraphrase).
- Whether Outpost program is still active in FY2025/2026 filings.
