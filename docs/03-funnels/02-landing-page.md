# 03.2 — PocketTA Landing Page: Conversion Plan

> The page's one job: turn an ad click into a **free signup**. Every point of conversion rate here directly divides your CAC ([why](../01-foundations/growth-marketing-map.md#where-the-leverage-actually-is-ranked)). The app already has a Next.js site — this is the spec to optimize/adjust it *before* traffic arrives, not a rebuild.

## First principles

1. **One page, one goal.** Free signup. No competing CTAs above the fold (no "learn more," no docs links up top).
2. **Message match** — the #1 CRO principle for paid traffic. The visitor clicked an ad promising something specific ("2-hour lecture → study kit in 60 seconds"). The page's first screen must repeat that promise in nearly the same words + visual. Mismatch = instant bounce = wasted spend. When we run multiple ad angles, each angle ideally gets a matched hero variant (query-param driven — trivial in Next.js).
3. **Show, don't claim.** The product demo IS the argument. A 15–30s autoplay screen-capture (paste link → kit appears) above the fold beats any copy.
4. **Speed + mobile-first.** ~All Meta traffic is mobile. LCP under ~2s; test the page on a real phone over cellular. Vercel + Next helps; heavy hero video must be compressed/poster-framed.

## Page anatomy (top to bottom)

| Section | Contents | Notes |
|---|---|---|
| **Hero** | H1 = the one-liner: *"Turn any lecture into a complete study kit in 60 seconds."* Subhead = the kit contents in one line. **Primary CTA: "Make your first study kit — free"** + demo video/GIF | CTA copy sells the *action's value*, not "Sign up." No credit card required — say so under the button. |
| **How it works** | 3 steps: Paste → Generate → Study. Visual per step | Kill any perceived effort ("no prompting, no setup") |
| **The kit (value stack)** | Notes + AI diagrams · flashcards + spaced repetition · quizzes · AI-graded short answers · printable guide · glossary · Chrome extension | Show real artifacts, not icons. This is the differentiation vs. flashcard-only rivals — make "the WHOLE kit" land |
| **Proof** | Testimonials w/ names+photos, usage numbers when real, "SM-2 — the same algorithm as Anki" | ⚠️ No fabricated testimonials, ever. Pre-launch: use credibility markers (algorithm, demo honesty) until real quotes exist. Collect them from week 1. |
| **Objection FAQ** | "Is it accurate?" / "What sources work?" / "Is free really free?" / "vs ChatGPT?" | Each FAQ = a real objection from ad comments (mine them weekly) |
| **Pricing** | Free vs Pro table, anchored on free | Goal is signup; Pro sells itself in-product |
| **Final CTA** | Repeat hero CTA | People who scroll to the bottom are warm — catch them |

## Copy rules
- Second person, present tense, concrete ("your 2-hour bio lecture," not "educational content").
- Outcome > feature: "remember it next week" > "SM-2 spaced repetition" (put the algorithm in the proof section, not the headline).
- **Compliance:** no grade promises/guarantees (Meta ad-policy + honesty). "Study faster" ✅, "Get an A" ❌.

## Measurement (wire before launch — see [tracking spec](../05-analytics/02-pixel-and-capi.md))
- Events: `PageView` → `ViewContent` → `CompleteRegistration` (signup = the ad-optimization event) → `Activation` (first kit generated, custom event) → `Subscribe` (Stripe).
- **Landing CVR** (signups ÷ landing views) is the metric this page lives or dies by. Benchmarks for cold paid traffic to a free-signup SaaS: **10%+ good, 15%+ great, <5% = something's broken** (usually message match or load speed).
- Session recordings (e.g., free Microsoft Clarity) for the first weeks — watching 20 real sessions teaches more than any framework.

## Test queue (once traffic flows, one variable at a time, biggest lever first)
1. Hero headline/promise (match to winning ad angle)
2. Demo video vs. static hero
3. CTA copy ("Make your first study kit free" vs. "Try it on your last lecture")
4. Signup friction (email+password vs. Google OAuth one-tap — likely a big win with students)

---
**Related:** [offer](01-offer.md) · [tracking spec](../05-analytics/02-pixel-and-capi.md) · [brand brief](../04-creative/02-brand-design-brief.md) (visual tokens) · [90-day plan Week 2](../00-roadmap/90-day-plan.md)
