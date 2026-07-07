# 06.3 — Build Spec: Social Content Engine (organic IG / TikTok / X)

> Automates the **compliant 90%** of running PocketTA's organic social: creation, repurposing, scheduling/publishing, reply-drafting, and analytics — with you as the 10% human gate. Explicitly does **NOT** automate engagement on other people's content (see Compliance — this is the part that gets accounts and ad Business Managers banned).

## Problem it solves
Organic social is a free reach multiplier for the same creative we're already producing for ads — but running 3 platforms by hand is a daily time sink. The repetitive parts (adapting one video into platform-native posts, captioning, scheduling, drafting comment replies, pulling stats) are automatable; the parts platforms punish (fake engagement) and the parts that build trust (genuine interaction) are not.

## Compliance boundary (non-negotiable, verified July 2026)
- **May 2026:** Meta purged 10M+ IG accounts for bots/fake engagement/coordinated inauthentic behavior. TikTok and X enforce equivalents.
- **Banned & detected:** auto-follow/unfollow, auto-comment on others' posts, cold DMs, browser-automation bots, engagement pods.
- **⚠️ Cascade risk:** the IG account links to the Meta Business Manager that runs our PAID ads. An organic-side flag can take down the paid channel. Never risk paid for botted organic.
- **Compliant:** official-API publishing; AI-*drafted* human-approved replies to comments on OUR posts; **user-initiated** DM flows within rate limits (e.g., "comment TA → DM the link" — one of the best-converting organic mechanics right now); analytics reads.

## Inputs
- Ad/creative assets from the [creative pipeline](02-creative-pipeline.md) (C1–C6 footage first) + `brand.yaml` (voice, banned claims)
- Content calendar config (cadence per platform, posting windows)
- Comments/DM triggers on own posts (via official APIs/webhooks)

## Outputs
- **Platform-native post variants** from each source asset (hook text, caption, hashtags per platform norms) → **approval queue** (approve/edit/reject, same human-gate pattern as the creative pipeline)
- **Scheduled publishes** across IG/TikTok/X
- **Drafted replies** to comments on our posts → one-tap approve
- **Comment-to-DM flows** (Phase 2, Meta official API, user-initiated only)
- **Weekly organic digest** (views, follows, profile→site clicks, best post) feeding the [reporting dashboard](01-reporting-dashboard.md)

## Architecture
```
creative assets ─▶ Adapt (Claude: per-platform     ─▶ Approval ─▶ Publish (scheduler API      ─▶ Analytics
+ brand.yaml       captions/hooks/hashtags, JSON)     queue        or direct platform APIs)       digest
                                                        ▲                    │
you (10%): approve queue · approve drafted replies ─────┘        comment webhooks ─▶ Claude drafts reply ─▶ you tap ✓
```

## Tools / APIs — buy vs. build
| Layer | Decision | Why |
|---|---|---|
| Scheduling/publishing | **BUY or self-host** — Buffer/Metricool (~$0–25/mo) or **Postiz** (open-source, self-hosted, has API) | Solved problem; building a scheduler = re-implementing a $15/mo product. Push content in via *their* API |
| Content adaptation | **BUILD** — Claude API module shared with the creative pipeline | This is the differentiating layer; nobody's tool knows our brand + angle library |
| Reply drafting | **BUILD** (small) — webhook → Claude draft → approval UI | Cheap to build, big daily time save |
| Comment-to-DM | **BUY** — ManyChat-style tool on Meta's official API (Phase 2) | Compliance-critical; let a vendor own rate limits |
| Analytics | **BUILD** (thin) — platform insights APIs → dashboard | Reuses dashboard plumbing |

## Build plan
1. **Phase 0 (now, no code):** sign up for a scheduler; hand-post repurposed C1–C6 cuts to seed the accounts. Learn what organic traction looks like before automating it.
2. **Phase 1 (weeks 9–12, if organic shows signal):** `systems/social-content-engine/` — adaptation module (asset+brand → platform variants, JSON), approval queue (reuse creative-pipeline review UI), publish via scheduler API, weekly digest.
3. **Phase 2 (post-90-day):** comment webhooks + reply drafting; comment-to-DM flows; X auto-posting of text variants.

## Success criteria
- One source video → approved, scheduled posts on 3 platforms in < 10 min of human time; comment replies handled in < 10 min/day; zero policy strikes.

## Scope discipline
- **Do not build before the first ad campaign is live.** Organic is the side quest; paid is the 90-day learning loop. Phase 0 (buy scheduler, repost ad creative) captures most of the value for ~zero effort — build only when organic data earns it.

---
**Related:** [stack overview](stack-overview.md) · [creative pipeline](02-creative-pipeline.md) · [launch concepts (source assets)](../04-creative/03-launch-concepts.md) · [product strategy: MunchMatch organic track](../00-roadmap/product-strategy.md) (this engine later serves MunchMatch too)
