# 06.0 — Marketing Systems Stack (Ordered by ROI)

> This is where your engineering becomes an unfair advantage. Each system below turns a repetitive marketing task into code. They're ordered by **ROI for a solo builder** — impact per hour to build, weighted by how early it pays off.
>
> **Rule:** Don't build ahead of need. A system you build before you have data to feed it is procrastination dressed as productivity. Build #1 and #2 in the first 90 days; the rest when the plan calls for them.

## The ranked stack

| # | System | What it does | ROI | Build when |
|---|--------|--------------|-----|------------|
| 1 | **Automated Reporting Dashboard** | Pulls Meta (+ funnel) data daily, computes CPL/CAC/CTR/CVR/ROAS, flags anomalies. Kills spreadsheet drudgery, sharpens kill/scale decisions. | ⭐⭐⭐⭐⭐ | Weeks 9–10 (needs live data). Spec: [`01-reporting-dashboard.md`](01-reporting-dashboard.md) |
| 2 | **AI-Assisted Creative Pipeline** | Brand guide as structured data → generates hook/angle/script variations → assembles ad drafts for review. Attacks the #1 2026 bottleneck: creative *volume*. | ⭐⭐⭐⭐⭐ | Weeks 5–10 (once you know your winning angles). Spec: [`02-creative-pipeline.md`](02-creative-pipeline.md) |
| 3 | **Server-Side Tracking / CAPI Layer** | Robust Pixel + Conversions API with high Event Match Quality, dedup, offline/CRM events. Better data = cheaper CPMs. | ⭐⭐⭐⭐ | Week 2 (do a basic version early; harden later) |
| 4 | **Creative Testing Harness** | Programmatically launches structured creative tests via the Marketing API, enforces clean methodology, logs results to `08-experiments/`. | ⭐⭐⭐⭐ | Weeks 9–12+ (once testing cadence is high) |
| 5 | **Social Content Engine** | Repurposes ad creative into organic IG/TikTok/X posts, auto-publishes via scheduler API, AI-drafts replies (human-approved). **Never** automates engagement on others' content (ban + Business-Manager cascade risk). | ⭐⭐⭐ | Phase 0 (buy scheduler) now; build weeks 9–12 if organic earns it. Spec: [`03-social-content-engine.md`](03-social-content-engine.md) |
| 6 | **Ad-Library Swipe & Competitor Monitor** | Scrapes/queries the Meta Ad Library for competitors' long-running (= winning) ads; builds a searchable swipe file. | ⭐⭐⭐ | Anytime — cheap, great for creative inspiration |
| 7 | **Automated Rules & Budget Manager** | Marketing-API scripts to pause losers, scale winners within guardrails, alert on anomalies. | ⭐⭐⭐ | When spending enough that daily manual ops hurt |
| 8 | **LTV / Cohort & Economics Model** | Pipes purchase data into cohort LTV, payback period, contribution-margin models to govern scale decisions. | ⭐⭐⭐ | When you have repeat-purchase / retention data |
| 9 | **Landing Page / Funnel A-B Framework** | Reusable page framework with built-in variant testing and event tracking. | ⭐⭐ | When landing-page CVR becomes the bottleneck |

## Why these two are first

- **#1 Reporting Dashboard** — the moment you spend real money you need to *read* it correctly and daily. Doing this in spreadsheets is slow and error-prone; automating it sharpens the single most important skill (kill/scale judgment) and pays back immediately. It's also a self-contained, satisfying build.
- **#2 Creative Pipeline** — creative volume is *the* 2026 constraint (Meta removed granular targeting Jan 15, 2026; creative is now the targeting). Top brands ship 200–300 concepts/month. No solo human does that by hand — but a builder with an AI pipeline can approach it. This is your single largest structural edge.

## Full build specs

- [`01-reporting-dashboard.md`](01-reporting-dashboard.md) — Automated Reporting Dashboard
- [`02-creative-pipeline.md`](02-creative-pipeline.md) — AI-Assisted Creative Pipeline

Specs for #3–#8 will be written when their build window arrives (see the [90-day plan](../00-roadmap/90-day-plan.md)).

## Cross-cutting engineering principles

- **Never commit secrets.** Every system gets a `.env.example`; real keys stay in `.env` (gitignored). Meta tokens especially.
- **API-first.** Prefer the [Meta Marketing API](https://developers.facebook.com/docs/marketing-apis/) over scraping the UI; it's stable and permissioned.
- **Taste gates automation.** Especially for the creative pipeline: the machine drafts, *you* judge. Automating output you can't evaluate just scales slop.
- **Log to `08-experiments/`.** Systems that touch tests should write structured results back into the experiments log so the knowledge base stays the source of truth.

---

**Next:** read the two specs, then see the [90-day plan](../00-roadmap/90-day-plan.md) for when to build them.
