# 05 — Analytics

Tracking, attribution, and the economics that decide **kill vs. scale**: CAC, LTV, payback period. Your [strongest technical moat](../00-roadmap/skills-gap-analysis.md#4-analytics-tracking--attribution) — most of this is just software.

## The economics vocabulary (memorize)
- **CAC** — Customer Acquisition Cost = spend ÷ new customers.
- **LTV** — Lifetime Value = total *gross profit* per customer over their life (use profit, not revenue).
- **LTV:CAC** — health gauge. >3:1 healthy · ~1:1 dead · >5:1 you're under-spending.
- **Payback period** — days/months to recoup CAC. Governs cash flow → how fast you can scale.
- **CPL / CPA** — cost per lead / per acquisition (your daily operating metric).
- **Hook rate, CTR, landing CVR** — the funnel-stage rates that tell you *where* it leaks.

## The 2026 tracking reality
- **CAPI (Conversions API) is required infrastructure**, not optional. Browser-only tracking misses 20–35% of conversions; CAPI pushes match to 95%+ → cheaper CPMs and better optimization.
- **Target Event Match Quality (EMQ) 8.0+** (Purchase 8.8–9.3). Send email, phone, fbp, fbc, IP, user-agent, external_id.
- **Run Pixel + CAPI together with event deduplication** (shared event IDs).
- Meta discontinued the **Offline Conversions API in May 2025** — offline/CRM events now flow through standard CAPI (store the `fbclid` with each lead to attribute later conversions).
- Don't rabbit-hole on perfect attribution — get to "good" and move on.

## Docs to write here
- `01-metrics-that-matter.md` — the metrics vs. vanity metrics, with definitions + formulas
- `02-pixel-and-capi.md` — setup, EMQ, dedup (feeds the [tracking system](../06-automation/stack-overview.md))
- `03-attribution.md` — windows, blended vs. platform-reported, sane defaults
- `04-cac-ltv-economics.md` — the models that govern scaling

*Basic pixel/CAPI happens in [90-day plan](../00-roadmap/90-day-plan.md) Week 2; economics deepens in Weeks 11–12. This README is the placeholder.*
