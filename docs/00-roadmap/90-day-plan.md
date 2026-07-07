# 00.2 — The 90-Day Plan (Learning by Doing)

> A week-by-week roadmap to go from zero reps to a competent, data-literate paid-social marketer who has **shipped real campaigns**. The organizing principle: **you learn by spending real money on real strangers, fast, and reading the results honestly.** Study is in service of the next thing you ship — never the other way around.

## Assumptions (stated so you can correct them)

These are my smart-defaults. Any of them being wrong changes the plan — flag it and I'll revise.

- **Budget:** A **$1,200 total 90-day "tuition" budget** is the sweet spot for a solo learner. Structure it as:
  - Weeks 1–4: **$20/day** live spend once you launch (~$300). Enough to exit Meta's learning phase on one ad set (needs ~50 conversions/week) *only if* your conversion event is cheap (leads, not $500 purchases — see offer note).
  - Weeks 5–8: **$30/day** (~$600) as you scale winners.
  - Weeks 9–12: **$20–40/day** flexed toward what's working (~$300–500).
  - Plus a small cushion (~$100–200) for tools/assets. **Do not spend less than ~$15/day live** — below that the algorithm can't learn and you'll draw false conclusions. If $1,200 is too much, the floor is ~$600 ($15–20/day for 6 focused weeks). If budget is *not* a constraint, don't go higher than ~$50/day as a beginner — you'll just burn cash faster on the same mistakes.
- **Offer (CONFIRMED):** **PocketTA** — AI study-kit SaaS, free tier → **$9/mo Pro**. Freemium PLG funnel: ads optimize for **free signups** (a cheap conversion event, so $20/day exits the learning phase), then free→Pro is the money metric. Full offer + positioning in [`../03-funnels/01-offer.md`](../03-funnels/01-offer.md); product choice rationale in [`product-strategy.md`](product-strategy.md). (MunchMatch is parked as a separate free organic/ASO track — no paid budget.)
- **⛔ DEPLOY GATE (Week 0):** PocketTA is **not live yet**. It must be deployed (Supabase + Vercel + Stripe, per its `DEPLOYMENT.md`) and able to take signups + payments **before any ad spend**. All Week 1–2 marketing prep (offer, landing, tracking, creative) can proceed in parallel with deployment. **Timing:** aim to be live and testing creative by early August to catch the back-to-school peak (Aug–Sep).
- **Time:** ~10–15 focused hrs/week. If you have more, compress; if less, stretch each phase but keep the *order*.

## Hard milestones (put these on a calendar)

| Milestone | Deadline |
|-----------|----------|
| 🎯 Offer defined + written up in `03-funnels/` | **End of Week 1** |
| 🎯 Landing page + lead magnet + pixel/CAPI live | **End of Week 2** |
| 🎯 **First ad live** (real spend) | **Day 21 (end of Week 3)** |
| 🎯 First read on real CAC/CPL data | **End of Week 4** |
| 🎯 **First creative A/B test concluded** (winner declared) | **Day 42 (end of Week 6)** |
| 🎯 First scaled winner OR first documented pivot | **End of Week 8** |
| 🎯 First automation system shipped in `systems/` | **End of Week 10** |
| 🎯 Profitable (or clearly-trending-profitable) funnel + full write-up | **Day 90** |

Every launched campaign gets a file in [`08-experiments/`](../08-experiments/). No exceptions.

---

## Phase 1 — Foundations & Setup (Weeks 1–2)
**Goal:** Have a complete, launchable funnel with tracking, before spending a cent on traffic.

### Week 1 — Offer + fundamentals
- **Learn:** Read [`01-foundations/growth-marketing-map.md`](../01-foundations/growth-marketing-map.md) (done). Study offer construction — Hormozi *$100M Offers* (see [shortlist](../07-resources/shortlist.md)). Watch Meta Blueprint basics.
- **Do:** Pick your practice offer. Write it up in `docs/03-funnels/01-offer.md`: the promise, price, bonuses, guarantee/risk-reversal, and who it's for. Draft a lead magnet (the free thing that earns the email).
- **Build:** Set up assets — Meta Business Manager, an ad account, a Facebook Page + Instagram account, a domain. (No spend yet.)
- **Milestone:** ✅ Offer written up.

### Week 2 — Funnel + tracking
- **Learn:** Landing page anatomy, message match, [CAPI](../05-analytics/) fundamentals.
- **Build (your wheelhouse):** Landing page with lead-capture. Install **Pixel + Conversions API** — do CAPI properly now; it's your edge and it's just software (target Event Match Quality 8.0+; Meta shipped one-click CAPI in Events Manager in April 2026 as a fallback). Wire up a 4-email welcome sequence. Set the standard events (Lead, and Purchase if selling).
- **Do:** Write the first ad *copy* and plan first creatives (don't launch yet).
- **Milestone:** ✅ Full funnel + tracking live and test-fired.

---

## Phase 2 — First Blood (Weeks 3–4)
**Goal:** Get an ad live, spend real money, and learn to read an account without fooling yourself.

### Week 3 — LAUNCH 🚀
- **Learn:** Campaign structure ([`02-meta-ads/`](../02-meta-ads/)) — in 2026 keep it *simple*: **one Advantage+ Sales / lead campaign, broad Advantage+ Audience, 3–5 creatives.** Do NOT build 20 ad sets slicing interests; that era is over.
- **Do:** **Launch your first campaign (Day 21).** Budget $20/day. Optimize for your cheap conversion event (Lead). Then **leave it alone** for 3–4 days — resisting the urge to tinker during the learning phase is itself a core skill.
- **Log:** Create `08-experiments/2026-XX-first-campaign.md` with hypothesis, setup, budget, success criteria *before* results.
- **Milestone:** ✅ First ad live.

### Week 4 — Read the data
- **Learn:** Which metrics matter (CPL/CPA, CTR, CPM, hook rate, landing CVR) and which are vanity (reach, impressions, likes). Learning phase, statistical noise, when a result is real.
- **Do:** Analyze. What's the CPL? Where's the funnel leaking — hook (low CTR)? page (low CVR)? offer (clicks but no leads)? Write the verdict in the experiment file. Make ONE change based on the biggest leak.
- **Milestone:** ✅ First honest read on CAC/CPL.

---

## Phase 3 — Creative Engine (Weeks 5–8)
**Goal:** Internalize that **creative is the lever**, and build the muscle (and later the machine) for producing and testing lots of it.

### Week 5 — Hooks & angles
- **Learn:** Hook frameworks, angle mapping (same product, many reasons-to-care), UGC vs. static vs. demo. Study winning ads (Meta Ad Library, [shortlist](../07-resources/shortlist.md)). Write it up in `docs/04-creative/`.
- **Do:** Produce **5–8 new creative concepts** (not variants — different hooks/angles). Use your phone, Canva, AI tools. Done > pretty.

### Week 6 — First A/B test 🧪
- **Learn:** How to test creative cleanly (test hooks/concepts, hold audience + offer constant; let Meta's algorithm allocate within an ad set, or use A/B test tool for clean reads).
- **Do:** Run your **first structured creative A/B test.** Declare a winner by Day 42. Log it.
- **Milestone:** ✅ First creative A/B test concluded.

### Weeks 7–8 — Iterate & find a winner
- **Do:** Kill losers, make more variations of what worked (iterate on the winning *angle*). Push the winner's budget up **10–20% every few days** (aggressive scaling breaks the learning phase). Fix the biggest remaining funnel leak.
- **Milestone:** ✅ First scaled winner, or a documented, reasoned pivot (pivoting on evidence is a *win*, not a failure).

---

## Phase 4 — Systematize & Scale (Weeks 9–12)
**Goal:** Turn manual wins into repeatable systems — your unfair advantage — and reach a profitable or clearly-trending-profitable funnel.

### Weeks 9–10 — Build your first system
- **Build:** Pick the highest-ROI automation from [`06-automation/stack-overview.md`](../06-automation/stack-overview.md) — likely the **automated reporting dashboard** or the **creative testing harness** — and ship it under `systems/`. Now your engineering compounds your marketing.
- **Milestone:** ✅ First automation system shipped.

### Weeks 11–12 — Scale, economics, retrospective
- **Learn:** Full economics — LTV:CAC, payback period, contribution margin ([`05-analytics/`](../05-analytics/)). Decide: is this funnel *actually* profitable at scale?
- **Do:** Scale the winner as far as economics allow. Write a **90-day retrospective** in `00-roadmap/`: what you learned, what worked, what you'd do differently, and the next 90-day focus.
- **Milestone:** 🎯 Profitable/clearly-trending funnel + full write-up.

---

## Rules for the whole 90 days

1. **Ship over study.** If you're studying more than ~30% of your time, you're hiding. Study the thing you're about to do, then do it.
2. **Log every campaign** in `08-experiments/` — hypothesis and success criteria *before* results. This is non-negotiable and how you build judgment.
3. **Don't tinker mid-learning-phase.** Discipline beats cleverness here.
4. **Fix the weakest link**, not the fun one. Re-read the [leverage table](../01-foundations/growth-marketing-map.md#where-the-leverage-actually-is-ranked) whenever unsure where to spend effort.
5. **Real money only.** You cannot learn paid on fake budgets. Small and real beats large and imaginary.
6. **Anything touching real spend or publishing:** I propose, you approve. Everything else, I just build.

---

**Next:** [`06-automation/stack-overview.md`](../06-automation/stack-overview.md) — the systems to build. And keep [`progress.md`](progress.md) updated every session.
