# Centricity OD×S — Design System Spec (v0.1)

One mobile app merging the **Centricity MF Screener** and **Sentinel · OneDigital Partner** dashboards.
Frame: **375×812 iPhone** · **Dark-first** (light = semantic remap of Home only for v1).

---

## 1. Token sources & provenance

| Source | Status | What it contributed |
|---|---|---|
| Sentinel live CSS (`sentinel-partner.centricitywealth.tech`) | ✅ extracted | Surface scale (#050608 → #252B36), text ramp, module accents, priority/tier/chart palettes, radii, shadows, motion |
| Local `~/Desktop/centricity-design-system` (claude.fig, 296 vars) | ✅ read | Champagne-metal CTA gradient, glass/grain treatment, Figtree + Tabular fonts, obsidian layering philosophy, component inventory |
| Brand Figma `hekJWgSTwAaHJZqdgjhkMS` (Empanelment/Onboarding) | ⛔ **no access** — MCP account `utkarshv187@gmail.com` not shared | To reconcile once shared: logos/marks, any variables that disagree with the above |
| Brief overrides | ✅ applied | Negative financials `#931621`, base ~`#050608`, radii 16–24, tabular figures |

**Canonical values live in [tokens.json](tokens.json).** This doc explains the decisions.

## 2. Color system

- **Surfaces (6 steps):** canvas `#050608` → raised `#0D1017` → card `#14181F` → sheet `#1A1F28` → hover `#1F242E` → pressed `#252B36`. Depth = lighter surface + soft shadow, never hard borders. Glass surfaces (`rgba(13,16,23,0.72)`, blur 20, 1px inner top highlight) for tab bar, floating pills, segmented controls.
- **Brand accent — champagne gold** `#B89E55` (Sentinel's entry gold; kissing cousin of claude.fig copper `#B69377`). Primary CTA is the **brushed-metal gradient** with an **ink label** (never white). **One metal CTA and at most one gold rim-glow per screen.**
- **AI gradient** `#4A6CFF → #8B5CF6` is reserved for AI moments: NBA cards, nudges, digital advisor. It is the "Sentinel intelligence" signature.
- **Module tints** (from Sentinel) for wayfinding chips/icons only, at 14–18% alpha: Acquire indigo, Manage green, Discover purple, Serve amber, Insights cyan.
- **Data semantics:** positive `#10B981`, negative **`#931621`** (brief-mandated) — used for badge fills, delta pills, large numerals; small negative text on dark cards uses the legibility companion `#E4536B` (same hue family, AA-passing). Warning `#D97706`, info `#4A6CFF`. 7-color categorical chart palette in tokens.
- **Zero decorative color** beyond the above. Purple/cyan/etc. appear only in their semantic roles.

## 3. Typography

| Role | Family | Notes |
|---|---|---|
| UI, headings, body | **Figtree** | Brand font (Google Font — available in Figma natively) |
| All numerals / currency | **Tabular** | Brand custom font (installed from DS repo `fonts/`); tabular-aligned, ₹ Indian grouping (₹23,179 Cr). Figma fallback: Figtree + tabular figures |
| UPPERCASE micro data-labels | **JetBrains Mono** | `3Y CAGR`, `AUM ₹ CR`, `SCORE` — 10px, +1.2 tracking |

Scale (px/lh): display 34/40 · h1 28/34 · h2 22/28 · h3 18/24 · bodyLg 16/24 · body 14/20 · caption 12/16 · micro 10/14 · numLg 24/30 · num 14/20 · numSm 12/16.

## 4. Space, radius, elevation, motion

- **4pt grid**: 4/8/12/16/20/24/32/40/48 · 16px side gutters · 12px between cards.
- **Radii**: chips pill · controls 10–14 · cards 16–20 · sheets 24 (top corners) — per brief's 16–24 band.
- **Elevation**: card / raised / overlay shadow ramp (tokens) + glass blur 20. Gold glow `rgba(184,158,85,0.18)` for the single focal element.
- **Motion**: 120/220/400ms, standard easing `cubic-bezier(0.4,0,0.2,1)`, spring only for sheet presentation. Mobile states: pressed (scale 0.97), disabled, loading, error — no hover.

## 5. Component library (to build as Figma components)

**Navigation:** Top app bar (title + cycle chip + search + avatar) · Bottom tab bar (5 tabs, glass) · Segmented control · Filter pills row · Back header with contextual actions.

**Content:** Fund card (rank, name, category, AUM, score, sparkline) · Metric tile (micro-label + Tabular numeral + delta pill) · Portfolio/household card · NBA card (AI gradient border) · Nudge card · Manager-switch row · List row (leading icon / title / meta / trailing value) · **Mobile table row with frozen first column** (fund name sticky, metrics scroll horizontally) · Comparison column card · Overlap matrix cell · Delta pill (▲/▼) · Badges & flags (T0–T3 tier, P1–P5 priority, manager-change, AUM-breach, style-drift) · Score ring/donut.

**Charts:** sparkline · rolling-return line · donut allocation · growth-of-₹1L line · overlap heat matrix · drift bar.

**Inputs:** Search bar · Filter bottom sheet (checkbox groups + range sliders) · Sort control · Weight-editor slider row · Amount input (₹, Indian grouping) · Risk-profile selector · Stepper.

**Feedback:** Bottom sheets/modals · Toast · Empty state · Loading skeleton (all cards get one) · Alert banner · Progress stepper (onboarding).

Component tiering follows base → semantic → component; components consume semantic tokens only — no raw hex.

## 6. Open items (blocked on access)

1. **Brand Figma file** — share `hekJWgSTwAaHJZqdgjhkMS` (and target `CLPQWVuBtMRql6U9AiscN6`) with **utkarshv187@gmail.com** as editor, then variables/logos get reconciled and the DS page gets built in the target file.
2. **Sentinel authenticated modules** — needs a manual login (rule: I never type credentials). The in-app browser is parked on the login page; log in there and I'll walk all five modules and capture `reference/sentinel/` screenshots.
3. **Tabular font in Figma** — install the OTFs from the DS repo so the Figma desktop app can use them; otherwise fallback applies.
