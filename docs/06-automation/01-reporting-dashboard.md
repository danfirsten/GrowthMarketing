# 06.1 — Build Spec: Automated Reporting Dashboard

> **System #1** in the [stack](stack-overview.md). Pulls your Meta Ads (and funnel) data on a schedule, computes the metrics that actually drive decisions, flags anomalies, and presents it so you can make **kill/scale** calls in minutes, not hours.

## Problem it solves
Reading a Meta account by hand in Ads Manager is slow, noisy, and biases you toward vanity metrics. You need a single view of **cost-per-result, funnel conversion rates, and trend** — computed consistently, refreshed daily, with the derived metrics (blended CAC, hook rate, landing CVR) that Ads Manager doesn't give you directly. This is the tool that turns "staring at dashboards" into "making decisions."

## Inputs
- **Meta Marketing API** — Insights endpoint: spend, impressions, reach, clicks, CTR, CPM, results (leads/purchases), cost-per-result, by campaign/adset/ad, by day. (Requires a Meta app, a system user token with `ads_read`, and your ad account ID.)
- **Funnel data** — landing page sessions + conversions (from your own DB/analytics, or the Pixel/CAPI events) to compute landing-page CVR that Meta can't see fully.
- **(Optional) Revenue/CRM data** — for CAC, ROAS, and LTV once you have purchases.
- **Config** — your target CPL/CAC thresholds, date ranges, which accounts/campaigns to include.

## Outputs
- A **daily dashboard** (web page or notebook) showing per-campaign and blended: spend, CPL/CPA, CTR, CPM, **hook rate** (3-sec video views ÷ impressions), **landing CVR**, results, and day-over-day / 7-day trend.
- **Anomaly flags:** CPL up >X% vs. 7-day avg, spend with zero results, CTR collapse (creative fatigue), learning-phase status.
- **A daily digest** (email/Slack) with the 3 things needing attention.
- **A machine-readable snapshot** (JSON/CSV) written to `systems/reporting-dashboard/data/` for history and for feeding other systems.

## Architecture
```
┌─────────────┐   ┌──────────────┐   ┌───────────────┐   ┌──────────────┐
│ Meta         │──▶│ Ingest        │──▶│ Transform      │──▶│ Present       │
│ Marketing    │   │ (API pulls,   │   │ (compute       │   │ (dashboard +  │
│ API + funnel │   │  cache raw)   │   │  derived KPIs, │   │  digest +     │
│ data         │   │               │   │  anomaly rules)│   │  JSON export) │
└─────────────┘   └──────────────┘   └───────────────┘   └──────────────┘
        ▲                                                          │
        └──────────────── scheduler (cron / GitHub Action) ───────┘
```
- **Ingest** — thin API client; cache raw responses (respect rate limits; use async/batch for date ranges).
- **Transform** — pure functions computing derived KPIs + anomaly detection. *Unit-test these* — correctness of your metrics is the whole point.
- **Present** — start dead simple: a static HTML report or a Streamlit app. Digest via email (Resend/SMTP) or Slack webhook.
- **Schedule** — cron or a GitHub Action running daily each morning.

## Tools / APIs
- **Language:** Python (best ecosystem: `facebook_business` SDK, pandas) or TypeScript/Node if you prefer. Python recommended for the data work.
- **Meta:** [Marketing API](https://developers.facebook.com/docs/marketing-api/insights/) — Insights endpoint; `facebook_business` SDK.
- **Dashboard:** Streamlit or a static HTML generator (start static — don't over-build).
- **Digest:** Slack incoming webhook or Resend/SMTP.
- **Storage:** flat files (CSV/JSON/SQLite) — no database needed at this scale.
- **Secrets:** `.env` (gitignored) + `.env.example`. Never commit the Meta token.

## Step-by-step build plan
1. **Scaffold** `systems/reporting-dashboard/` — README, `.env.example` (`META_ACCESS_TOKEN`, `META_AD_ACCOUNT_ID`, `META_APP_ID`, `SLACK_WEBHOOK_URL`), `pyproject.toml`/`requirements.txt`, `src/`, `tests/`, `data/` (gitignored).
2. **Auth spike** — create the Meta app + system user token; pull *one* day of account-level insights; print it. De-risk auth first (it's the fiddly part).
3. **Ingest module** — fetch insights by campaign/adset/ad for a date range; cache raw JSON to `data/`.
4. **Transform module (TDD)** — pure functions: derived KPIs (blended CAC, hook rate, landing CVR, trends) + anomaly rules. Write tests with fixture data *first*.
5. **Present v1** — render a single static HTML report (or Streamlit). Just get the numbers on screen correctly.
6. **Digest** — post the top-3-attention summary to Slack/email.
7. **Schedule** — daily cron/GitHub Action; write dated snapshots to `data/` for history.
8. **Iterate** — add funnel CVR (from your own events), then revenue/ROAS once you have purchases.

## Success criteria
- One command (or scheduled run) produces an accurate daily view you *trust* enough to make kill/scale decisions from — replacing manual Ads-Manager reading. Metrics match Meta's UI to within rounding.

## Scope discipline (YAGNI)
- **v1 does NOT need:** a database, auth/login, multi-user, fancy charts, or real-time. A correct static daily report + a Slack digest is the whole win. Add complexity only when a real need appears.

---

**Related:** [`stack-overview.md`](stack-overview.md) · [`../05-analytics/`](../05-analytics/) (metric definitions) · [90-day plan Weeks 9–10](../00-roadmap/90-day-plan.md#weeks-910--build-your-first-system)
