# 05.2 — PocketTA Tracking Spec: Pixel + Conversions API

> Build this **during/right after deploy, before any ad spend**. In 2026, CAPI is required infrastructure — browser-only tracking misses 20–35% of conversions; server-side pushes match to 95%+, which means Meta optimizes on real data and your CPMs drop. This is pure software, i.e., your moat. It fits PocketTA's exact stack (Next.js on Vercel + Supabase + Stripe).

## Event schema (the funnel, instrumented)

| Event | Standard name | Fires | Source | Purpose |
|---|---|---|---|---|
| Landing view | `PageView` / `ViewContent` | landing load | Pixel + CAPI | Funnel top, retargeting pool |
| **Free signup** | `CompleteRegistration` | Supabase auth signup success | Pixel + CAPI | **The ad-optimization event** (cheap → exits learning phase at $20/day) |
| First kit generated | `Activation` (custom) | first successful generate | **CAPI only** (server, in the generate route) | The activation moment; best predictor of Pro conversion; later, optimize campaigns on this |
| Pro subscription | `Subscribe` (or `Purchase`, value=9, currency=USD) | **Stripe webhook** `checkout.session.completed` | **CAPI only** (server) | The money event; feeds value optimization later |

**Principles:** browser-visible events fire from **both** Pixel and CAPI with a shared `event_id` (dedup); server-truth events (activation, subscription) fire **CAPI-only** from the backend where they actually happen. The Stripe webhook is already "the only writer of a user's plan" in PocketTA's architecture — it's also the only honest source of `Subscribe`.

## Identity plumbing (this is what makes EMQ high)

**Capture at first touch, persist to the user record:**
- `fbclid` (URL param on ad clicks) → store on the Supabase profile at signup. Convert to `fbc` format: `fb.1.<timestamp>.<fbclid>`.
- `_fbp` cookie (Meta's browser ID) → read client-side, send with signup.
- On every CAPI event send (SHA-256 hashed where required): **email, fbp, fbc, client IP, user agent, external_id (= Supabase user id)**.

**Event Match Quality targets** (Events Manager → your pixel → EMQ): **8.0+ overall; Subscribe/Purchase 8.8–9.3.** Below 7 = you're leaving cheap conversions on the table; fix the parameters above first.

## Implementation plan (Next.js + Vercel + Supabase + Stripe)

1. **Meta side (~20 min):** Events Manager → create dataset/pixel → generate a CAPI access token. Add `META_PIXEL_ID`, `META_CAPI_ACCESS_TOKEN` to Vercel env (server-only, never `NEXT_PUBLIC_`).
2. **Pixel client-side:** base snippet via Next `<Script>` in the marketing layout; fire `PageView` on route change, `CompleteRegistration` on signup success — each with a generated `event_id` (uuid) stashed so the server can reuse it.
3. **CAPI server module** (`lib/meta-capi.ts`): one function `sendServerEvent({event_name, event_id, user_data, custom_data})` posting to `graph.facebook.com/v23.0/<pixel_id>/events` (check current API version). Hash email/phone with SHA-256; pass IP + UA from the request. Fire-and-forget with error logging — tracking must never block the product.
4. **Wire the four events:** signup handler (browser + server, shared `event_id`) · generate route (`Activation`, server-only) · Stripe webhook (`Subscribe`, server-only, with hashed email + stored fbc/fbp from the profile).
5. **Test with Meta's Test Events tool** (Events Manager) before launch: verify all four arrive, dedup works (browser+server `CompleteRegistration` shows as ONE), and EMQ per event.
6. **Fallback if time-crunched:** Meta's one-click CAPI (Events Manager, since Apr 2026) gets you a baseline in minutes — but the custom `Activation`/`Subscribe` server events above are the real value; do them properly within the first weeks.

## Supporting analytics (beyond Meta)
- **Own-DB funnel truth:** you already have Supabase — a simple `events` table (user_id, event, ts, meta jsonb) written at the same four moments gives you *unsampled* funnel truth independent of Meta's reporting, and feeds the [reporting dashboard](../06-automation/01-reporting-dashboard.md). 30 minutes of work, do it.
- **Microsoft Clarity** (free) on the landing page for session recordings, first weeks only.
- **UTM discipline:** every ad URL gets `utm_source/medium/campaign/content` (content = creative concept ID) so your own DB can attribute signups per creative — this is how you judge creative winners *without* trusting Meta's attribution alone.

## Definition of done
- [ ] All 4 events visible in Test Events, dedup confirmed, EMQ ≥ 8.0
- [ ] `fbclid`/`fbp` persisted on profiles; Stripe webhook sends `Subscribe` with match keys
- [ ] Own-DB events table logging the same moments
- [ ] No tokens in client bundles or git ([.gitignore](../../.gitignore) covers `.env`)

---
**Related:** [analytics overview](README.md) · [landing page plan](../03-funnels/02-landing-page.md) · [offer economics](../03-funnels/01-offer.md#economics--fill-these-in-with-real-data-this-decides-everything) · [reporting dashboard spec](../06-automation/01-reporting-dashboard.md)
