# 00.3 — Progress Log

> Updated every session. Newest entry on top. Any future session: read this first to see where we left off, then continue from the current phase in the [90-day plan](90-day-plan.md).

## Current status

- **Phase:** Phase 1, Week 1 — Foundations & Setup (product chosen; awaiting deploy status + focus confirmation).
- **Live spend:** $0. No campaigns live yet.
- **Confirmed (Session 1):** Budget **~$1,200 / 90 days** ($20–40/day live). **Starting from zero** (no site/list/following).
- **Products (Session 2):** Two real repos — **FlowZone** (AI study-kit SaaS, $9/mo, web + Chrome ext) and **MunchMatch** (Tinder-for-restaurants mobile app, no monetization yet).
- **Decision:** **FlowZone = paid-marketing vehicle** (has $9/mo revenue, clean signup event, students targetable, back-to-school window Aug–Sep). **MunchMatch = organic/content/ASO only, no paid budget** until monetized. See [`product-strategy.md`](product-strategy.md).
- **Confirmed (Session 2):** **All-in on FlowZone** for paid. **Neither product is live** → deploying FlowZone is the Week 0 gate before any ads. MunchMatch monetization = **affiliate/reservation kickbacks** (thin per-match margin → stays organic-only).
- **Session 3 (2026-07-07, same day):** ⚠️ **Rename decided: "FlowZone" must change** — trademarked sprayer brand (fzspray.com) owns the SERP; naming doc with candidates + verification checklist at [`04-creative/01-brand-naming.md`](../04-creative/01-brand-naming.md). Wrote the **brand design brief** ([`04-creative/02-brand-design-brief.md`](../04-creative/02-brand-design-brief.md)) — self-contained work order executable by a fresh Claude session on any account. Wrote [`03-funnels/02-landing-page.md`](../03-funnels/02-landing-page.md) and [`05-analytics/02-pixel-and-capi.md`](../05-analytics/02-pixel-and-capi.md). Competitive intel added to offer doc (crowded field: Mindgrasp, NoteGPT, Turbo, StudyFetch, Laxu $4.99, Knowt free → wedge = completeness + one-paste flow).
- **Critical path now:** (1) **USER: pick the new name** (gates brand, domain, ad accounts — checklist in naming doc) · (2) **USER: deploy the app** (Supabase+Vercel+Stripe) · (3) execute brand brief (any Claude session) · (4) implement tracking spec during deploy · (5) creative concepts → launch. Target: live + testing creative by early August (back-to-school peak Aug–Sep).
- **Note for future sessions:** user may continue on a **different Claude account** — every work order must stay self-contained in files (the brand brief is the template for this).

## Open questions

1. **New product name** — user verifying candidates (domain/USPTO/SERP checks in the [naming doc](../04-creative/01-brand-naming.md)).
2. Once live: real free→Pro rate, churn, cost-per-free-user for the economics table in [`03-funnels/01-offer.md`](../03-funnels/01-offer.md).

## Session log

### 2026-07-07 — Session 1: Repo scaffolded
- Built the full `docs/` + `systems/` structure, root `README.md`, and `CLAUDE.md` (governing prompt).
- Wrote foundations: [`growth-marketing-map.md`](../01-foundations/growth-marketing-map.md).
- Wrote roadmap: [`skills-gap-analysis.md`](skills-gap-analysis.md), [`90-day-plan.md`](90-day-plan.md), this log.
- Wrote automation: [`stack-overview.md`](../06-automation/stack-overview.md) + specs for the [reporting dashboard](../06-automation/01-reporting-dashboard.md) and [creative pipeline](../06-automation/02-creative-pipeline.md).
- Wrote [`resources/shortlist.md`](../07-resources/shortlist.md) (verified via web search).
- **Key 2026 facts established:** Meta removed granular interest targeting Jan 15, 2026 → creative is now the targeting lever; Advantage+ Sales dominant; CAPI is required infrastructure (target EMQ 8.0+; one-click CAPI in Events Manager since April 2026).
- **What's next:** user answers open questions → build the offer.

<!-- Template for future entries:
### YYYY-MM-DD — Session N: <title>
- What I learned:
- What I built/shipped:
- Experiments run (link to 08-experiments/):
- Decisions made:
- What's next:
-->
