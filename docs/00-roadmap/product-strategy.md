# 00.4 — Product Strategy: FlowZone vs. MunchMatch

> Two real products, two *completely different* growth motions. This doc decides where the paid budget goes and why. Written 2026-07-07, Session 2.

## TL;DR

- **FlowZone → primary paid-marketing vehicle.** Put the $1,200 and the [90-day plan](90-day-plan.md) behind it. It has real monetization ($9/mo), a clean conversion event, a targetable audience (students), and a **time-sensitive back-to-school window** (Aug–Sep). This is where you learn paid social.
- **MunchMatch → organic / content / ASO play. Zero paid budget** until it has a monetization model. It's a virality-driven consumer app, not a paid-acquisition business. You'll still learn a second, valuable growth motion — for free.
- **Don't split the $1,200.** Focus beats dilution for a learner. One product, done well, teaches more than two done shallowly.

## The filter: does paid acquisition even make sense?

Paid ads work only when this chain holds:

```
monetization model → you can estimate LTV → spend CAC < LTV → scale
```

Break the chain anywhere and paid spend is just setting money on fire. Scoring both:

| Criterion | FlowZone | MunchMatch |
|---|---|---|
| Has a revenue model | ✅ $9/mo Stripe subscription | ❌ none in the repo |
| Can compute LTV | ✅ yes (churn × $9) | ❌ no → **paid ads recoup $0** |
| Clean, cheap conversion event | ✅ free signup (email) → Pro upgrade | ⚠️ app install (high friction) |
| Attribution sanity | ✅ web pixel + CAPI, full control | ❌ iOS/SKAdNetwork — noisy, delayed, will mislead a beginner |
| Natural growth motion | **Paid social + product-led** | **Virality + ASO + network effects** |
| Audience targetable on Meta | ✅ students, exam-preppers, lifelong learners | ⚠️ "hungry people in groups" — everyone, i.e. no one |
| Timing edge right now | 🔥 back-to-school in ~6–8 weeks | neutral |

**Verdict:** FlowZone passes the filter cleanly. MunchMatch fails the monetization gate — which means paid is premature, *not* that the product is bad.

---

## FlowZone — the paid-social play

**What it is:** Paste a YouTube lecture or transcript → AI generates structured notes (with diagrams), flashcards with spaced repetition, quizzes, AI-graded short-answers, a printable study guide, and a glossary. Web app + Chrome extension. Free (10 kits/mo) / **Pro $9/mo** (300 kits/mo + AI diagrams).

**Why it's a great first paid-marketing product:**
- Clear, painful, universal job-to-be-done: "I have a lecture/exam and need to actually learn it, fast."
- **Demo-able creative** — a 15-second screen recording of *paste link → full study kit in 60 seconds* is a killer hook. Creative (the [2026 lever](../01-foundations/growth-marketing-map.md#where-the-leverage-actually-is-ranked)) writes itself.
- Free tier = a cheap top-of-funnel conversion event (signup) so you exit Meta's learning phase on a small budget, then upsell to Pro. Classic **product-led + paid** funnel.
- **Seasonality is a gift, not a curse** — align the launch with back-to-school and exam seasons.

**Audience angles to test (creative = targeting in 2026):**
- College students (general "study smarter") · exam crammers (finals/midterms) · standardized-test preppers (MCAT/LSAT/bar — higher willingness to pay) · people who watch educational YouTube · online-course learners (Coursera/Udemy) · language/self-learners.
- Let the *creative* find these audiences (broad Advantage+ Audience). Don't slice interests — that lever is dead as of Jan 15, 2026.

**Funnel archetype:** direct-to-signup PLG. `ad → landing page → free signup → activate (first study kit) → Pro upgrade`. Optimize ads for signups first; watch signup→activation→Pro as the real economics.

**Free/organic multipliers to run alongside paid:**
- **Chrome Web Store** listing + SEO (the extension is a discovery channel in itself).
- Short-form content (study-hack Reels/TikToks) — same demo footage as the ads.
- Student communities: Reddit (r/GetStudying, r/college, r/premed), Discord study servers, campus reps.
- Student-influencer affiliates ("studytok").

**Economics to nail early** (see [05-analytics](../05-analytics/)): at $9/mo, LTV hinges on **churn**. If average retention is ~4 months, LTV ≈ $36 gross (minus AI/infra cost per user — you know these). That sets your **max CAC** (target < ~1/3 of LTV → aim for blended CAC under ~$10–12 for a Pro customer, or a *free-signup* cost low enough that your signup→Pro rate makes the math work). **Instrument free→Pro conversion from day one** — it's the number the whole model rides on.

**Biggest risk:** low free→Pro conversion (people use the free tier forever) or high churn (students subscribe for finals, then cancel). Watch both like a hawk; they decide whether paid can scale.

---

## MunchMatch — the organic / content / ASO play

**What it is:** Tinder-style swiping to pick where to eat — solo, couples, or groups swipe the same deck of nearby restaurants; a match when everyone likes the same spot. Mobile (Expo/React Native), Google Places. **No monetization model yet.**

**Why NOT paid (yet):**
- **No revenue → no LTV → paid acquisition is structurally impossible to do profitably.** You'd pay for free installs and recoup nothing.
- Mobile **app-install ads + iOS attribution (SKAdNetwork)** are noisy, delayed, and privacy-limited — a terrible environment to *learn* paid marketing in. You'd be debugging attribution instead of learning creative and offers.
- Consumer-social/utility apps grow on **network effects and virality**, not bought installs. Paid installs of a free social app is a classic money-pit.

**The right motion — and it's genuinely strong here:**
1. **Short-form content is the whole game.** "Couple can't decide where to eat → opens MunchMatch → swipes → *it's a match* 🍅" is inherently relatable and shareable. Film real people using it. This concept is *built* for TikTok/Reels. Volume of content = your growth.
2. **App Store Optimization (ASO)** — title, keywords, screenshots, preview video. Free, compounding, decisive for app discovery. This is a core skill worth learning.
3. **Seeded virality** — the product needs ≥2 people to shine (couple/group mode). Design and push invite loops; seed friend groups and campuses directly.
4. **Product Hunt / Reddit / communities** launch.

**Monetization (CONFIRMED): affiliate / reservation kickbacks** — earn a referral fee when a matched group books/orders (OpenTable, Resy, DoorDash/Uber Eats, etc.). Implications:
- **Revenue is per-match, not per-user** → LTV = (matches per user over lifetime) × (booking rate) × (avg. commission). This is likely **small per user** (a few dollars at most) and depends on a booking actually happening. That's a **thin margin for paid acquisition** — reinforces organic-first.
- **The metric to instrument:** match → booking-click → confirmed-booking conversion, and average commission per booking. Until you know these, you can't estimate LTV, and paid stays off.
- **Partnerships are the unlock:** you need the affiliate relationships live (OpenTable/Resy affiliate programs, delivery referral programs) — that's the gating first build, not ads.

Once you can estimate revenue-per-user from real match/booking data, *then* revisit whether paid installs could ever clear that (bar is high; content/ASO likely stays primary indefinitely).

*Other models considered and set aside for now:* freemium premium features (cleaner LTV, revisit if affiliate revenue is too thin), restaurant-side featured listings (marketplace — needs scale first), in-app ads (weak until large).

**What you learn from it (for free):** ASO, organic short-form content, virality/invite-loop design, and community launches — a whole second growth toolkit that complements the paid skills FlowZone teaches.

---

## The decision

- **FlowZone** is the subject of the [90-day plan](90-day-plan.md) and the [experiments log](../08-experiments/). The $1,200 goes here. Offer written up next in [`03-funnels/01-offer.md`](../03-funnels/README.md).
- **MunchMatch** gets an organic-growth track (its own docs when we start it), no paid budget, and a **monetization decision** as the gating first step.
- **Focus:** run FlowZone paid as the main learning loop; layer MunchMatch organic content in as a lighter parallel track. Don't dilute the paid budget across both.

## Open questions

1. **Are both deployed/live yet?** FlowZone needs to be live (Supabase + Vercel + Stripe) before we can send it traffic. MunchMatch needs to be in the App/Play stores for organic to matter.
2. **MunchMatch monetization** — which model (freemium / affiliate / other)? Gates any future paid consideration.
3. **Confirm the focus:** all-in on FlowZone for the paid track (recommended), or do you want to split attention?

---
**Related:** [90-day plan](90-day-plan.md) · [foundations map](../01-foundations/growth-marketing-map.md) · [progress log](progress.md)
