# Experiment: Launch Campaign #1 — PocketTA cold-traffic signups

- **Status:** planned (gated on: name checklist ✅ → deploy ✅ → tracking ✅ → creatives produced)
- **Dates:** target start early August 2026 (back-to-school runway) → 10–14 days
- **Owner:** me

## Hypothesis
Cold Meta traffic (broad Advantage+ Audience, US, 18–34) shown 5 distinct creative concepts will produce **free signups at ≤ $5 each**, with at least one concept clearly out-pulling the rest — giving us (a) proof the offer resonates, (b) a winning angle to iterate on, and (c) first real funnel data (landing CVR, signup→activation).

## Setup
- **Offer:** free signup, 10 kits/mo, no card ([offer doc](../03-funnels/01-offer.md))
- **Funnel:** ad → landing ([plan](../03-funnels/02-landing-page.md)) → signup → first kit (activation)
- **Campaign:** 1 campaign, 1 ad set (no audience slicing), broad Advantage+ Audience, US, 18–34, all placements (Advantage+)
- **Creatives:** C1–C5 ([launch concepts](../04-creative/03-launch-concepts.md)), each tagged `utm_content`
- **Conversion event optimized for:** `CompleteRegistration`
- **Tracking gate (must be ✅ before spend):** Pixel + CAPI live, dedup verified, EMQ ≥ 8.0 ([spec](../05-analytics/02-pixel-and-capi.md))

## Budget
- **Daily:** $20/day
- **Total planned:** $200–280 (10–14 days)
- **Kill-switch:** pause any single ad > $30 spend with 0 signups; kill campaign if blended cost/signup > $12 after $150 (that's "offer or page broken," not "creative needs tweaking")

## Success criteria (set BEFORE launch — do not move)
- **Win:** blended cost per signup ≤ $5 AND ≥ 40 signups AND a top concept with ≥ 2× the signups of the median concept
- **Acceptable/iterate:** $5–8/signup with a clear creative winner, or cheap signups but landing CVR < 5% (→ fix page, not ads)
- **Kill:** > $12/signup after $150 with landing CVR ≥ 8% (traffic converts on page but won't sign up = offer problem)
- **Learning even if it fails:** which angle got the best hook rate + CTR; where the funnel leaks (hook / click / page / signup)
- ⚠️ **Not the goal yet:** Pro conversions. At this spend we won't get significant Pro data — we're buying signal on angle + funnel, and building the signup base whose free→Pro rate we measure in weeks 5–8.

## Results
| Metric | Value |
|--------|-------|
| Spend | |
| Impressions | |
| Hook rate (per concept) | |
| CTR (per concept) | |
| CPM | |
| Landing CVR | |
| Signups (per concept) | |
| Cost/signup (blended + per concept) | |
| Signup → activation (first kit) rate | |

## Verdict
_(fill after)_

## Follow-up
_(fill after — next experiment, winning angle, changes)_
