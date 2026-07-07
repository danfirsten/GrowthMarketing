# Growth OS

This repo is my **Growth OS** — a combined knowledge base and build environment for going from "strong engineer who can't market" to **elite growth marketer**.

I'm a 22-year-old CS new grad. I can build almost anything. My bottleneck is marketing. This repo attacks that head-on: it captures what I learn as structured, cross-linked docs, and it houses the automation systems I build to turn my engineering skills into an unfair marketing advantage.

## How this repo is organized

```
docs/        # all knowledge — reads like a book, worked through in order
systems/     # all code/automations we build
```

### `docs/`

| Folder | What lives here |
|--------|-----------------|
| [`00-roadmap/`](docs/00-roadmap/) | The 90-day plan, skills gap analysis, and a running progress log |
| [`01-foundations/`](docs/01-foundations/) | Mental models: how growth works, the Meta auction, funnel theory |
| [`02-meta-ads/`](docs/02-meta-ads/) | Campaign structure, targeting, budgets, Meta playbooks |
| [`03-funnels/`](docs/03-funnels/) | Landing pages, offers, lead magnets, email sequences |
| [`04-creative/`](docs/04-creative/) | Hooks, angles, ad formats, creative testing frameworks |
| [`05-analytics/`](docs/05-analytics/) | Tracking, attribution, CAC/LTV, dashboards |
| [`06-automation/`](docs/06-automation/) | Buildable specs for marketing systems (each spec = one file) |
| [`07-resources/`](docs/07-resources/) | Curated high-signal resources + an "overrated/avoid" list |
| [`08-experiments/`](docs/08-experiments/) | One file per real campaign/test: hypothesis → spend → results → verdict |

Start at [`docs/README.md`](docs/README.md) — it's the master index.

### `systems/`

Real engineering projects. Each automation gets its own folder with a README, clean structure, `.env.example`, and **no secrets committed**. See [`systems/README.md`](systems/README.md).

## Operating principles

1. **Ship, don't consume.** The point is real campaigns with real (small) budgets, logged in `08-experiments/` — not tutorial hell.
2. **Creative is the lever.** In 2026, Meta's targeting is mostly automated. What you say and show is where the game is won.
3. **Systematize everything.** If a task repeats, it becomes a spec in `06-automation/` and then code in `systems/`.
4. **Economics decide.** CAC vs. LTV is the scoreboard. Everything else is input.

## For future sessions

Read [`CLAUDE.md`](CLAUDE.md) (the governing prompt for this repo), then [`docs/00-roadmap/progress.md`](docs/00-roadmap/progress.md) to see where we left off.
