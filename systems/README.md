# systems/

Real, buildable automation projects — where engineering becomes the marketing edge. Each system is a proper engineering project.

## Conventions
- One folder per system: `systems/<project-name>/`.
- Each has its own `README.md`, clean structure (`src/`, `tests/`), and `.env.example`.
- **Never commit secrets.** Real keys live in `.env` (gitignored). Meta tokens and `ANTHROPIC_API_KEY` especially.
- Systems that run tests write structured results back to [`docs/08-experiments/`](../docs/08-experiments/) so the knowledge base stays the source of truth.

## Planned systems (ordered by ROI)
Specs live in [`docs/06-automation/`](../docs/06-automation/stack-overview.md). Build order per the [90-day plan](../docs/00-roadmap/90-day-plan.md):

1. **reporting-dashboard** — daily Meta metrics, derived KPIs, anomaly flags → [spec](../docs/06-automation/01-reporting-dashboard.md) *(Weeks 9–10)*
2. **creative-pipeline** — AI-assisted creative concept generation → [spec](../docs/06-automation/02-creative-pipeline.md) *(Weeks 5–10)*
3. Tracking/CAPI layer, testing harness, ad-library monitor, budget rules, LTV model — specced when their build window arrives.

*Nothing built yet — this repo is freshly scaffolded. First system ships around Week 10.*
