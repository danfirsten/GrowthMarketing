# 04.2 — Brand Design Brief (Instructions for a Claude Session)

> **This file is a self-contained work order.** It's written so a *fresh Claude session — any account, zero prior context* — can execute it end-to-end and produce the complete brand identity for the product currently called FlowZone (rename pending, see [01-brand-naming.md](01-brand-naming.md)). If you are that future Claude session: read this whole file, then follow **Process** at the bottom. If the repo is available to you, skim the *Related* links; if not, this file alone is sufficient.

---

## 1. Context you need (everything essential, inlined)

**The product:** A web app + Chrome extension for students. Paste a YouTube lecture or transcript → AI generates a **complete study kit** in ~60 seconds: structured notes (with AI-drawn diagrams), flashcards with spaced repetition (SM-2 — same algorithm as Anki), quizzes, AI-graded short-answer questions, a printable study guide, and a glossary. **Free tier:** 10 kits/month. **Pro ($9/mo):** 300 kits/mo, AI diagrams, longer sources.

**The name: PocketTA** — "your TA, in your pocket" (chosen 2026-07-07, replacing "FlowZone"; see [01-brand-naming.md](01-brand-naming.md)). **Confirm with the user that the verification checklist (domain/USPTO/app stores) passed before producing deliverables.** If it failed, the fallback is **StudySesh**. The companion/TA framing is core to the brand regardless: PocketTA is a *companion, not a tool* — warm, college-native, competent. Lean into TA-culture verbal territory (office hours, review sessions, "your TA has notes ready").

**One-liner / positioning:** *Turn any lecture into a complete study kit in 60 seconds.*
- **vs. manual notes:** 100× faster, plus flashcards/quizzes you'd never make by hand.
- **vs. ChatGPT:** a study *system*, not a wall of text — one paste, full kit, built-in review scheduling, zero prompting.
- **vs. Quizlet/Knowt:** generated from *your* lecture, not someone else's decks — and it's the whole kit, not just flashcards.
- **vs. other AI study tools (Mindgrasp, NoteGPT, Turbo, StudyFetch):** completeness (the full kit incl. AI diagrams + graded short answers + printable guide) and the one-paste YouTube flow via the extension.

**Audience (primary → secondary):**
1. College students (17–24) — "study smarter, not longer"; back-to-school and finals seasonality.
2. Standardized-test preppers (MCAT/LSAT/bar/nursing/CPA) — higher stakes, higher willingness to pay.
3. Online-course / lifelong learners.

**Where the brand must perform (design for these contexts, hardest first):**
1. **Meta ads (Reels/Stories/feed)** — thumb-stopping at 375px wide, sub-3-second recognition. This is the #1 context; the business runs on paid social where *creative is the targeting*.
2. **Landing page** — instant credibility + message-match with ads.
3. **The app UI** — clean study environment; Chrome extension button on YouTube.
4. **App-store / Chrome-store listings, social profiles.**

**Personality target:** smart-but-not-corporate, energetic-but-credible. Think "the friend who's annoyingly well-organized for finals" — NOT enterprise SaaS, NOT childish edu-clipart, NOT dark-academia. Students smell try-hard instantly; err toward confident simplicity with one memorable twist.

## 2. Deliverables (produce ALL of these, as files in the repo)

Create a `docs/04-creative/brand/` folder containing:

### A. `brand-guide.md` — the human-readable brand book
1. **Brand strategy** — mission (1 line), promise, 3 messaging pillars (speed / completeness / actually-learn-it), elevator pitch, boilerplate paragraph.
2. **Verbal identity** — voice & tone (with a "sounds like / never sounds like" table + 5 rewritten example lines), tagline + 3 alternates (candidates to consider: "Your TA, in your pocket" · "You skipped the lecture. Your TA didn't." — note: the founder likes the skipped-class direction; keep it as *campaign* language, not the master tagline, since the master tagline must also serve serious test-preppers), naming conventions for features (what do we call a "study kit", "review session", etc. — consistency matters in UI and ads), copy do's/don'ts (e.g., never promise grades/outcomes — ad-policy risk; say "study faster", not "get an A guaranteed").
3. **Visual identity** —
   - **Logo direction:** wordmark-first (solo dev, no budget for custom marks) + a simple geometric icon usable as favicon/app icon/extension icon at 16px. Describe construction; provide SVG if capable.
   - **Color palette:** primary, secondary, 2 accents, neutrals — **with exact hex values**, usage ratios, and WCAG AA contrast pairs checked. Must pop on both white (landing) and dark (Reels) backgrounds.
   - **Typography:** display + body from **Google Fonts** (free, web-safe, licensing-clean), with weights/sizes scale.
   - **Iconography & illustration style:** one consistent style; kit/box/checklist motifs are on-strategy ("the whole kit").
   - **Imagery direction:** real-student UGC-style over stock; screen-recordings of the product are the hero asset.
4. **Ad-creative system** — templates/specs for the 3 core Meta formats: (a) 9:16 screen-demo Reel with hook text overlay, (b) 1:1 static "value stack" card, (c) 9:16 UGC-testimonial frame. Define: safe zones, text-overlay style, logo placement, CTA button style, subtitle style. **This is the most important deliverable — the brand exists to make ads faster to produce.**
5. **Landing-page design tokens** — hero layout, button styles, section rhythm, social-proof modules (consistent with the app's existing Next.js/Tailwind stack).

### B. `brand.yaml` — the machine-readable brand guide
Structured data mirroring the guide: name, one-liner, pillars, voice rules (as directives an LLM can follow), banned claims/compliance rules, palette hexes, font names, personas, proof points. **Purpose:** this file feeds an AI creative pipeline (see the automation spec in `docs/06-automation/02-creative-pipeline.md` if repo access) that generates ad concepts programmatically. Write every rule so an LLM can *execute* it ("use second person, present tense; max 12-word hooks; never mention grades or guarantees") rather than vague vibes ("be friendly").

### C. `assets/` — whatever you can produce directly
SVG wordmark/icon if capable; otherwise precise specs a human (or a design tool session) can execute. CSS custom-properties file with the tokens.

## 3. Constraints & guardrails

- **Zero budget assumptions:** Google Fonts only, no paid stock, no custom lettering requiring a designer.
- **Meta ad policy compliance baked in:** no before/after grade claims, no "guaranteed results," nothing implying personal attributes ("struggling student?" → not allowed as *targeted* phrasing). Encode these in `brand.yaml`.
- **Accessibility:** AA contrast minimum on all text/background pairs you specify.
- **Don't over-design:** this is a solo-dev brand that must be *executable fast*. Every element you add is production cost on every future ad. Bias to fewer, stronger elements.
- **The existing app** is Next.js + Tailwind — tokens should drop into that stack.

## 4. Process (follow in order)

1. **Confirm the name** with the user (see [01-brand-naming.md](01-brand-naming.md) if available). Do not produce deliverables under "FlowZone."
2. **Ask the user at most 3-5 questions** that genuinely change the output (e.g., any colors/styles they love or hate; formal vs. playful lean; any existing assets). Otherwise make opinionated choices and state them.
3. **Draft brand strategy + verbal identity first** → get a quick user thumbs-up (cheap to revise now, expensive after visuals).
4. **Produce visual identity + ad system + tokens.** Show, don't just describe — render sample ad frames/mockups if the environment allows (HTML/SVG mockups are fine).
5. **Write `brand.yaml` last** (it encodes the decisions).
6. **Update the repo index** (`docs/README.md`) and progress log (`docs/00-roadmap/progress.md`) if working in the Growth OS repo.

## 5. Definition of done

- [ ] All three deliverables exist as files (guide, yaml, assets/specs)
- [ ] A stranger could produce an on-brand Meta ad in 30 minutes using only the ad-creative system section
- [ ] An LLM could produce on-brand, compliant ad copy using only `brand.yaml`
- [ ] Every color pair passes AA; every font is Google Fonts; no banned-claim examples anywhere
- [ ] User has explicitly approved the name, strategy, and palette

---
**Related (if repo access):** [naming](01-brand-naming.md) · [offer & positioning](../03-funnels/01-offer.md) · [product strategy](../00-roadmap/product-strategy.md) · [creative pipeline spec](../06-automation/02-creative-pipeline.md) · [90-day plan](../00-roadmap/90-day-plan.md)
