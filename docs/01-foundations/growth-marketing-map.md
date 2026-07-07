# 01.1 — The Growth Marketing Map

> The mental model everything else hangs off of. Read this first. If you internalize one doc in the repo, make it this one.

## The one-sentence model

**Growth marketing is the engineering of a system that turns money into more money through customers — profitably and repeatably.**

You put $1 of ad spend in one end. If a *predictable* amount more than $1 comes out the other end over the customer's lifetime, you have a business, and your only job is to pour in more money and widen the pipe. If less comes out, no amount of hustle saves you. Everything in this repo is about (a) finding that profitable machine and (b) making the pipe wider and cheaper.

This is why growth marketing suits an engineer: **it's a system with inputs, transformations, outputs, and feedback loops.** You already think this way.

## The five stages (the funnel, as a pipeline)

```
   COLD TRAFFIC          you pay to interrupt strangers
        │  ▼ (Meta auction decides who sees you, and what it costs)
   ATTENTION / CLICK     the creative earns the click
        │  ▼ (hook → angle → offer)
   LANDING / CONVERSION  the page + offer earn the action (lead or sale)
        │  ▼ (message match, friction, proof)
   ACTIVATION / PURCHASE the first real value exchange
        │  ▼ (onboarding, email, upsell)
   RETENTION / LTV       repeat value → the number that makes ads affordable
        │  ▼
   ECONOMICS            LTV > CAC, and the ratio + payback period decide everything
```

Each stage has a **conversion rate**. The whole machine's output is the *product* of those rates. This is the single most important consequence:

**Growth is multiplicative, not additive.** If 1,000 people see your ad, 2% click, 10% of clickers convert, and 30% ever buy again, your outcomes are chained multiplications. Doubling *any* weak stage roughly doubles the whole system's output — but a 0 anywhere zeroes the whole thing. Your job is to find the **weakest link** and fix that, not to optimize what's already good. Engineers over-optimize the fun part (usually the code/tracking); marketers who win obsess over the highest-leverage weak stage (usually the offer and the creative).

## Where the leverage actually is (ranked)

This ordering is contrarian to how beginners spend their time. Learn it now and you'll save months and thousands of dollars.

| Rank | Lever | Why it dominates | How much beginners over/under-invest |
|------|-------|------------------|--------------------------------------|
| 1 | **Offer** | The single biggest multiplier. A great offer to the wrong list beats a great ad for a mediocre offer. "$100 off + free returns + results in 14 days or refund" changes conversion more than any headline tweak. | Massively **under**-invested |
| 2 | **Creative (hook + angle)** | In 2026, targeting is automated by Meta — *creative is now the targeting.* The algorithm shows your ad to whoever responds to it. The first 3 seconds decide everything. | Under-invested (in *volume* and *variety*) |
| 3 | **Funnel / landing page** | Message match and friction. A 1%→2% landing conversion literally halves your CAC. | Under-invested |
| 4 | **Economics understanding** | You can't scale what you can't measure. LTV:CAC and payback period decide how aggressive you can be. | Under-invested (ignored until too late) |
| 5 | **Targeting / audiences** | Mostly abdicated to Meta's AI now (see [02-meta-ads](../02-meta-ads/)). Meta removed granular interest targeting on Jan 15, 2026. | Massively **over**-invested by beginners |
| 6 | **Bid/budget micro-tweaks, dayparting, "hacks"** | Rounding error until you're spending a lot. | Wildly over-invested |

**The beginner's fatal mistake:** spending 80% of their energy on #5 and #6 (fiddling with audiences and settings) because it feels like "doing marketing," while ignoring #1 and #2 where the money actually is.

## How the Meta auction actually works (first principles)

You are not "buying ad slots." You are entering an **auction, billions of times a day**, for individual impressions in front of individual people. For each impression Meta ranks competing advertisers by **Total Value**, roughly:

```
Total Value ≈ (Your Bid) × (Estimated Action Rate) + (User Value / Ad Quality)
```

- **Bid** — what you're willing to pay (usually Meta sets this for you via the budget you give it).
- **Estimated Action Rate** — Meta's *prediction* that this specific person will do the thing you optimized for (buy, submit lead). This is where you win or lose. **Better creative + better landing page → higher predicted action rate → you win more auctions at a lower price.**
- **Ad Quality / User Value** — signals like engagement bait, clickbait, poor post-click experience *penalize* you.

**The profound implication:** You don't primarily lower costs by bidding smarter. You lower costs by making an ad+offer+page combo that *Meta predicts people will act on*, because Meta wants to show relevant ads (relevant ads = users stay on the platform = Meta earns more long-term). **Relevance is the discount.** This is why creative and offer sit at the top of the leverage table — they directly move the term that decides the auction.

CPM (cost per 1,000 impressions) is the "rent." CTR and conversion rate are how much value you extract per unit of rent. Your effective cost per result = `CPM ÷ (CTR × conversion rate) × 1000`-ish. Improve the multipliers, not the rent.

## Why funnels exist (first principles)

Cold strangers don't buy $2,000 things from a 15-second video. Trust and intent are built in **steps**, and each step should ask for only slightly more commitment than the last (the "commitment ladder"):

`see ad → click → get value for free (lead magnet) → give email → get nurtured → small purchase → bigger purchase → repeat`

Two archetypes you'll use:

- **Lead-gen / nurture funnel** (higher-priced, considered purchases, B2B, services): capture email with a lead magnet, nurture with email until ready. Ads optimize for **leads**; email does the selling.
- **Direct-response / e-commerce funnel** (lower-priced impulse-friendly products): ad → product/landing page → buy now → post-purchase upsell. Ads optimize for **purchases**.

A funnel exists to **spread the ask across trust-building steps** so you can profitably acquire customers who'd never buy on impression one. As an engineer: it's rate-limiting + state management for human trust.

## The economics that govern the whole thing

Memorize these four. They are the vocabulary of every scale decision. (Full treatment in [05-analytics](../05-analytics/).)

- **CAC** — Customer Acquisition Cost = total spend ÷ new customers. What one customer costs to buy.
- **LTV** — Lifetime Value = total gross profit one customer generates over their life. (Use *gross profit*, not revenue — margins matter.)
- **LTV:CAC ratio** — the health gauge. **>3:1** is healthy; **~1:1** you're buying dollars for dollars (dead); **>5:1** you're probably *under*-spending and leaving growth on the table.
- **Payback period** — how many days/months until a customer repays their CAC. This governs *cash flow* and therefore how fast you can scale. A great LTV:CAC with a 12-month payback can still bankrupt you if you're funding ads out of pocket.

**The whole game in one line:** find a repeatable way to acquire customers for meaningfully less than they're worth, prove it with small spend, then scale it before the market or the algorithm changes.

## Where Meta / Instagram ads fit

Meta (Facebook + Instagram + Messenger + Audience Network) is the default first channel for a solo builder because:
- **Intent-agnostic, interest-driven demand generation** — unlike Google (which captures *existing* demand from people searching), Meta *creates* demand by interrupting people. You can launch a product nobody is searching for yet.
- **Best-in-class self-serve auction + AI optimization** — you can start at $20/day and the algorithm does the heavy lifting on delivery.
- **Creative-led** — plays directly to the highest-leverage skill you can build.
- **Fast feedback loops** — you learn in days, not quarters. Perfect for an experiment-driven builder.

Google/Search comes later when you have demand to capture. TikTok when you have creative volume. Start with Meta.

## What matters most for a *solo technical builder* (your edge)

1. **You can build the measurement layer others pay agencies for.** CAPI/server-side tracking, dashboards, automated reporting — these are just software. Most marketers can't build them; you can. This is a real moat (see [06-automation](../06-automation/)).
2. **You can win on creative *volume* via automation.** The 2026 game is shipping many creative *concepts*, fast. AI-assisted creative pipelines are an engineering problem. Top brands ship 200–300 net-new concepts/month; you can build a system to approach that solo.
3. **Your bottleneck is taste and message, not tooling.** So: spend your *learning* time on offer + creative + copy (the things you can't yet do), and your *building* time on the systems that multiply them. Don't hide in the tooling because it's comfortable.
4. **Small budget is fine — but not zero.** You cannot learn paid marketing without spending real money on real strangers. Budget "tuition" (see the [90-day plan](../00-roadmap/90-day-plan.md)).

## The loop you'll run forever

```
HYPOTHESIS → build creative + offer + page → spend small → measure (CAC/CVR)
     ▲                                                            │
     └──────────── KILL losers, SCALE winners, learn ◄───────────┘
```

Everything in `08-experiments/` is one turn of this loop. That's the job. Get fast at the loop.

---

**Next:** [`00-roadmap/skills-gap-analysis.md`](../00-roadmap/skills-gap-analysis.md) — the specific skills you must build, ranked by leverage.
