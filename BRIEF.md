# Project brief — Centricity OD×S (One App)

Merge two existing dashboards into ONE mobile app design in Figma. Every feature from both must exist in the single app, reorganised into a clean mobile IA. iPhone frames 375×812, dark theme primary.

## Sources
1. **Centricity MF Screener** (public): https://rahultrades711.github.io/centricity-mf-dashboard/index.html — Home, Screener, Fund One-Pager, Portfolio Builder, Compare (7 funds × 6 cycles, 8 tabs), Overlap, Watchlist, Alerts/Flags, Knowledge Center, SIF, Manager Profiles, Archive (+ Stocks universe).
2. **Sentinel · OneDigital Partner** (login-gated): https://sentinel-partner.centricitywealth.tech — Acquire (CAS/PMS/AIF onboarding, risk profiling), Manage (households, quarterly reviews, drift), Product Discovery (PMS/AIF/MF research + overlap), 24×7 Support (digital advisor, Zoho), Insights Studio (dashboard, NBA, nudges, portfolio services). *(Credentials intentionally not recorded here.)*

## Brand
- Source of truth: Figma file `hekJWgSTwAaHJZqdgjhkMS` (New Empanelment/Onboarding & Txns journeys) — extract variables/styles; do not invent brand colors/fonts.
- Target Figma file: `CLPQWVuBtMRql6U9AiscN6`.
- Premium fintech, dark-first, base ~#050608, glassy cards, gradients, 16–24px radii. Negative financial values #931621; tabular figures for numbers.
- Pattern references: Mobbin (fintech/dashboard/onboarding), Swiggy (bold warm cards, motion), Skype (rounded friendly surfaces), premium credit-card apps (glass, gradients).

## Process checkpoints
1. Read figma-use / figma-generate-design skills before Figma writes.
2. Browse both dashboards, extract brand tokens → `design-system.md` + `tokens.json`.
3. Deliver sitemap/IA frame + design-system & component library page → **pause for approval**.
4. Build screens batch-by-batch on auto-layout with the component library; export screenshots per batch.

## Deliverables in this repo
- `design-system.md`, `tokens.json`, `sitemap.md`
- `reference/mf-screener/` — full-page captures of all 14 source pages
- `reference/sentinel/` — brand mark, landing capture, extracted live CSS themes (+ module captures once logged-in walkthrough is done)
- `exports/` — Figma screen exports per batch
