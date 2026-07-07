# 06.2 — Build Spec: AI-Assisted Creative Pipeline

> **System #2** in the [stack](stack-overview.md). Turns your brand + winning angles into a *high-volume stream of ad creative drafts* for you to curate. Attacks the single biggest 2026 bottleneck: **creative volume and variety.**

## Problem it solves
As of Jan 15, 2026, Meta removed granular interest targeting — **creative is now the targeting.** The algorithm finds buyers based on who responds to your ads, so whoever ships the most good, varied creative wins. Top DTC brands ship **200–300 net-new concepts/month**. A solo human can't hand-produce that. But a builder with an AI-assisted pipeline — brand-as-data in, structured ad drafts out, human taste as the gate — can approach it. **This is your largest structural edge.**

## Design principle: the machine drafts, you judge
Do **not** automate end-to-end publishing. The pipeline generates *drafts*; your taste is the quality gate. Automating output you can't evaluate just scales slop and burns money. Volume × taste — not volume alone.

## Inputs
- **Brand guide as structured data** (`brand.yaml`/`brand.json`): voice/tone, value props, target personas, forbidden claims/compliance rules, proof points/testimonials, product facts, visual guidelines.
- **Winning-angle library**: angles/hooks that have tested well (fed back from [`08-experiments/`](../08-experiments/) — closes the loop).
- **Swipe file / references** (optional): competitor and inspiration ads (from the Ad-Library monitor, system #6).
- **A generation brief**: "produce N concepts for persona X around angle Y in format Z."

## Outputs
- **Structured ad concepts** — each with: hook (first 3 sec), angle, primary text, headline, format (UGC/static/demo), script or shot list (for video), and a suggested visual direction.
- **Assembled drafts** where possible — static images via templated design (e.g., programmatic Figma/Canva or an image model), or video scripts + storyboards ready to shoot/edit.
- **A review queue** — concepts presented for you to approve/reject/edit; approved ones export to a batch ready to upload to Meta (manually at first).
- **Feedback loop** — approved/winning concepts write back to the winning-angle library, so the system compounds.

## Architecture
```
┌──────────────┐   ┌───────────────┐   ┌────────────────┐   ┌──────────────┐
│ brand.yaml    │──▶│ Prompt         │──▶│ Generate        │──▶│ Assemble      │
│ + angles      │   │ assembly       │   │ (Claude API:    │   │ (templated    │
│ + swipe file  │   │ (context pack) │   │  hooks, copy,   │   │  image/video  │
│               │   │                │   │  scripts)       │   │  drafts)      │
└──────────────┘   └───────────────┘   └────────────────┘   └──────┬───────┘
        ▲                                                            ▼
        │                                                    ┌──────────────┐
        └──────── winning angles (from 08-experiments) ◄─────│ Human review  │
                                                             │ queue (gate)  │
                                                             └──────────────┘
```

## Tools / APIs
- **Text/concept generation:** **Claude API** (`claude-opus-4-8` for high-quality concepting; `claude-sonnet-5` for cheaper bulk variation). Use structured outputs (tool use / JSON schema) so concepts come back machine-readable. *(When building, load the `claude-api` skill for current model IDs, pricing, and structured-output patterns.)*
- **Static image assembly:** templated design via the Figma API or Canva API, or an image-generation model for backgrounds/variations. Start with templates (brand-consistent, cheap) over full generation.
- **Video:** scripts + shot lists first (you shoot/edit); add AI video tools later if quality justifies.
- **Review UI:** simplest thing that works — a local web app or even a generated HTML review page with approve/reject.
- **Storage:** concepts as structured files (JSON/YAML) in `systems/creative-pipeline/concepts/`; brand + angles version-controlled.
- **Secrets:** `.env` for `ANTHROPIC_API_KEY`, design-tool tokens. Never commit.

## Step-by-step build plan
1. **Scaffold** `systems/creative-pipeline/` — README, `.env.example`, `brand.yaml` template, `src/`, `concepts/`, `tests/`.
2. **Codify the brand** — fill `brand.yaml` with voice, value props, personas, proof, and hard compliance rules (what you may/may not claim).
3. **Concept generator (v1, text-only)** — Claude API call that takes brand + angle + persona + format and returns N structured concepts (hook, primary text, headline, script). Enforce a JSON schema. *This alone is already useful.*
4. **Review queue** — render concepts to an approve/reject page; store decisions.
5. **Feedback loop** — approved/winning concepts append to the angle library; feed test results from `08-experiments/` back in so generation improves.
6. **Static assembly** — templated image generation (Figma/Canva API) for approved static concepts.
7. **Batch export** — package approved creatives + copy for manual upload to Meta.
8. **(Later) Video + volume scaling + optional Marketing-API upload** once the manual loop is proven.

## Success criteria
- You can go from "I need 10 fresh concepts for persona X / angle Y" to **10 reviewable, on-brand, compliance-safe drafts in minutes**, and your *approved* output rate per week clearly beats what you could produce by hand — without quality dropping (measured by test win rate in `08-experiments/`).

## Scope discipline (YAGNI)
- **v1 is text concepts + a review page.** That already solves most of the volume problem. Image/video assembly and API publishing come only after the manual loop proves the concepts convert.
- **Compliance is not optional:** bake Meta's advertising policy constraints into `brand.yaml` and the prompt so generated claims don't get you banned.

---

**Related:** [`stack-overview.md`](stack-overview.md) · [`../04-creative/`](../04-creative/) (hooks/angles theory) · [90-day plan Weeks 5–10](../00-roadmap/90-day-plan.md#phase-3--creative-engine-weeks-58) · load the `claude-api` skill before building the generator.
