# Product Requirements Document — Centricity Unified Partner App

**Product:** Centricity Wealth · Unified Partner Mobile App (working name)
**Platform:** iOS-first mobile app (375 × 812), dark theme
**Author:** Product / Design
**Status:** Draft v1.0 — reverse-engineered PRD covering the delivered Figma design
**Design source of truth:** Figma file `CLPQWVuBtMRql6U9AiscN6` · repo `github.com/utkarshv187/od-x-s`
**Last updated:** July 2026

---

## 1. Document purpose

This PRD documents, in a single place, the product that was designed by merging two existing Centricity web dashboards into one mobile app. It captures the problem, goals, users, information architecture, feature requirements, user flows, screen inventory, design system, and a competitive analysis of comparable products in the Indian wealth-tech market. It is written to be usable by product, design, and engineering for build planning, and as a reference for future iterations (light theme, prototype, dev handoff).

---

## 2. Executive summary

Centricity operates two separate web surfaces for its wealth-management partners:

1. **Centricity MF Screener** (an institutional mutual-fund research dashboard under "Invictus Private Wealth / Centricity WealthTech Products Team") — a deep research and portfolio-construction tool built around a proprietary 22-parameter fund score.
2. **Sentinel · OneDigital Partner** (an AI-native partner workspace) — a client lifecycle platform spanning acquisition, management, product discovery, support, and an AI insights studio.

Partners today move between two logins, two design languages, and two mental models. The unified app collapses both into **one dark-themed mobile app** organised around four tabs — **Home, Discover, Portfolio, More** — so an advisor can run the entire wealth journey (acquire a client → build a portfolio → research products → monitor drift → act on AI nudges → get support) from a single surface.

The design is complete: a frozen design system (26 components, 55 variables, 16 text styles, 5 elevation styles) and 20 polished screens with device chrome, all version-controlled in GitHub.

---

## 3. Background & problem statement

### 3.1 The two source products

**Source 1 — MF Screener (research & construction).** Institutional dashboard for HNI / UHNI / Family-Office advisors, refreshed fortnightly, reconciled against an in-house 22-parameter scoring engine. Modules observed: Home (cycle summary, Top-10 Centricity Rank, manager switches, universe composition, cycle deltas), Screener (filters, saved views, sortable table), Fund One-Pager (returns, risk, rolling windows, holdings, manager history), Portfolio Builder (allocation-first model portfolios, export to PPT), Compare (up to 7 funds × 6 cycles, 8 metric tabs), Overlap, Watchlist, Alerts/Flags (manager movement, AUM breaches, style drift), Knowledge Center, SIF research, Manager Profiles, Archive, Stocks universe.

**Source 2 — Sentinel Partner (client lifecycle & AI).** AI-native partner workspace with five modules: **Acquire** (CAS/PMS/AIF onboarding, risk profiling), **Manage** (households, quarterly reviews, drift), **Product Discovery** (PMS/AIF/MF research and overlap), **24×7 Support** (digital advisor, Zoho handoff), **Insights Studio** (dashboard, Next-Best-Action, nudges, portfolio services). Two additional routes were found in the logged-in walkthrough: a real Insights Studio dashboard and a "Copilot" chat hub.

### 3.2 The problem

- **Fragmentation.** Research lives in one product; client lifecycle and AI live in another. Advisors context-switch constantly.
- **No mobile surface.** Both sources are desktop-first web dashboards (viewport 1680 / 1440). Advisors in the field have no coherent mobile tool.
- **Two design languages.** MF Screener is ivory + champagne-gold + serif ("Invictus Private Wealth"); Sentinel is dark + copper + AI-gradient. Inconsistent brand experience.
- **Duplicated concepts.** Overlap, compare, portfolio, and research exist in both, implemented differently.

### 3.3 The opportunity

A single, premium, mobile-first app that unifies research depth with lifecycle workflow and AI assistance — positioned for HNI/UHNI/Family-Office advisors who need institutional data on the move.

---

## 4. Product vision & goals

**Vision:** *One desk for the entire wealth journey* — the advisor's single mobile home for acquiring clients, constructing and monitoring portfolios, researching every product class, and acting on AI intelligence.

### 4.1 Goals

| # | Goal | Rationale |
|---|------|-----------|
| G1 | Unify both dashboards into one coherent mobile IA | Remove context-switching and dual logins |
| G2 | Preserve research depth (22-parameter score, rolling consistency, overlap) | This is Centricity's differentiator |
| G3 | Surface AI intelligence (NBA, nudges, Copilot) at the point of decision | Sentinel's "AI native" promise |
| G4 | Deliver a premium, low-cognitive-load dark UI | Match the standard of best-in-class fintech apps |
| G5 | Cover the full client lifecycle: acquire → build → monitor → serve | Turn a research tool into a workflow product |

### 4.2 Non-goals (this phase)

- Light theme (deferred; a variable-mode flip is scoped for later).
- Live back-end integration and real data wiring (design phase only).
- Android-specific layouts (iOS-first; Android follows).
- Client-facing app (this is a *partner/advisor* app).

---

## 5. Target users & personas

**Primary persona — The Wealth Partner / MFD-RIA.** An advisor or distributor serving HNI/UHNI/family-office clients across MF, PMS, AIF, and SIF. Needs institutional research, fast portfolio construction, drift monitoring, and a professional client-facing output (proposal PPT). Mobile-first for meetings and travel.

**Secondary persona — The Product/Research desk user.** Uses screener, compare, overlap, manager profiles, and the archive to shortlist funds and defend recommendations.

**Tertiary persona — The Relationship Manager.** Focuses on households, quarterly reviews, alerts, and the Copilot/support handoff.

Key jobs-to-be-done: *"Onboard a new client fast"; "Show which funds are best this cycle and why"; "Build a model portfolio I can send as a proposal"; "Tell me which clients are drifting and what to do"; "Answer a client question with data, now."*

---

## 6. Information architecture

The two sources' ~21 feature areas were mapped into a **4-tab bottom navigation** (reduced from an initial 5-tab proposal after merging Insights into Home):

| Tab | Icon (Phosphor) | Contains |
|-----|-----------------|----------|
| **Home** | house | Book overview, Acquire CTA, KPIs, Next-Best-Actions + nudges, Top-10 preview, cycle deltas, Insights Studio entry |
| **Discover** | compass | Natural-language search, MF/PMS/AIF/SIF/Stocks, Screener, Compare, Overlap, Managers, SIF/Stocks/Knowledge Center |
| **Portfolio** | briefcase | Households by AUM, drift/attention alerts, Portfolio Builder flow, allocation/result, household detail, watchlist |
| **More** | dots-three | Support/Copilot, Knowledge Center, Archive, Profile, settings |

Design decisions taken during the process:
- **Acquire** promoted to a primary action on **Home** (onboarding is the advisor's first job).
- **Insights Studio** removed as a standalone tab; NBA + nudges surfaced on Home, deeper Studio screens still reachable.
- Center **"Ask Sentinel" FAB** (copper sparkle) overlaps the tab bar for always-available AI Copilot.

A full source→destination audit and a 21-screen production list are maintained in `sitemap.md` in the repo.

---

## 7. Feature requirements by module

Each feature below is stated as a requirement. Priority: **P0** = core to launch, **P1** = important, **P2** = enhancement.

### 7.1 Home (P0)
- Greeting header with advisor avatar + notification bell (badged), cycle chip.
- **Total Book AUM** hero (e.g. ₹1,152.8 Cr) with a period delta pill and cycle facts as a quiet caption.
- **Quick actions** row: Onboard (Acquire), Screen, Build, Compare.
- **Next-Best-Actions** ("For you today"): one AI NBA card + deep-link rows (e.g. "Convert latest CAS → proposal", "10 drafts pending").
- **Top-10 Centricity Rank** preview (top 3–5) with "See all → Screener".
- **Since last cycle** delta pills (gainers / losers / manager changes).
- **Insights Studio** entry row with pending count.

### 7.2 Discover (P0)
- Natural-language **search** as the hero (search is the tab's primary job) + segmented control: MF / PMS / AIF / SIF / Stocks.
- **Research tools**: Screener, Compare, Overlap, Managers.
- **Top rated this cycle**: one full Fund Card + calm list rows.
- **Research desk**: SIF, Stocks universe, Knowledge Center.

### 7.3 Screener (P0)
- Search + **filters** (asset class, category, AMC chips) with a "22 scoring parameters · Edit weights" entry (weight sliders).
- **Results table**: frozen first (fund) column, horizontal scroll, mono column headers, sortable by score/AUM/1Y/3Y/Sharpe/MaxDD.
- Export actions (PDF/CSV).
- Saved views persist per user (from source behaviour).

### 7.4 Fund One-Pager (P0)
- **Score-first hero**: Centricity Score (22 parameters), giant numeral, rank movement, peer-group caption.
- Key-fact metric tiles: AUM, TER, Sharpe, Max Drawdown.
- **Returns** row (with alpha footnote), **Rolling consistency** rows with "beat category" tags.
- **Top holdings** with movement tags (Added/Held/Trimmed).
- Manager row with AMC score; action stack (primary CTA + Compare/Watch).

### 7.5 Compare (P1)
- Removable fund chips + "Add" (up to 7), metric-tab chips (8 tabs).
- Frozen-parameter comparison table with a benchmark column; auto-generated change summary; PDF/PPT export.

### 7.6 Overlap (P1)
- Fund chips + N×N **overlap matrix** with intensity coding, an actionable caption (e.g. "share 41% — consider dropping one"), top common holdings with combined weights, PNG/PPT export.

### 7.7 Portfolio tab (P0)
- Header: households + total AUM advised.
- Quick actions: Build, Review, Import CAS, Watchlist.
- **Needs attention**: critical drift alert card.
- **Households by AUM** rows with status tags (Critical Drift / Review Due / In Sync).
- Watchlist preview.

### 7.8 Portfolio Builder — flow (P0)
- **Setup**: step rail (Corpus → Allocation → Filters → Risk → Review), corpus input, allocation sliders, risk chips, "Build portfolio" CTA.
- **Result**: allocation **donut** (persona presets), recommended funds with weight + ₹, "Export proposal · PPT" + "Adjust inputs".

### 7.9 Household detail (P1)
- Hero AUM with a **drift** pill, time chips, **Allocation vs Target** bars (drift semantics: % of target, tick at 100%, DRIFT/WATCH badges), top holdings, "Run quarterly review" CTA.

### 7.10 Watchlist (P1)
- Watch rows with since-added returns and rank-move / manager-change tags; manager-change warning alert cards.

### 7.11 Acquire — 5-step flow (P0)
Client details → Risk Persona → Goals → Advisory & Portfolio (AI-suggested model + donut) → Review (summary + proposal status: Draft/Sent/Approved; "Send proposal" / "Save as draft").

### 7.12 Insights Studio (P1)
- Book metrics KPI grid (Total AUM, active clients, brokerage MTD, pending alerts).
- Next-Best-Actions, Product Mix donut (real book mix), Cash Flow tiles, recent transactions with type tags, Portfolio Services with status rows.

### 7.13 Alerts & Flags (P1)
- Filter chips (All / Manager / AUM / Drift); severity-tiered sections: **Critical**, **Warning** (manager change, AUM breach, style drift), **Watched** (auto-resolving), severity-coded cards.

### 7.14 Support / Digital Advisor (P1)
- **Ask Sentinel** Copilot chat (area chips: Clients/Funds/Revenue/Reports), AI-gradient bot bubbles, copper user bubbles, input + send FAB, **Zoho handoff** row with open-ticket tag.

### 7.15 Knowledge Center (P2)
- Search + topic chips; sections (Score & Rank, Risk & Ratios, Guides) as tappable term rows with one-line definitions.

### 7.16 Archive (P2)
- Cycle chips; current-cycle deltas; past-cycle rows (each with gainers/losers/mgr-changes + scored-fund count); Cycle PDF / Data CSV downloads.

### 7.17 Profile (P2)
- Identity block; Workspace (saved views, export history, default cycle); Preferences (theme, biometric, notifications); Account (partner ID, sign out).

### 7.18 Splash / Login (P0)
- Brand block, "One desk for the entire wealth journey", email/password inputs, "Sign in", "Unlock with Face ID".

---

## 8. Key user flows

1. **Acquire a client → proposal.** Home → Onboard → 5-step Acquire wizard → AI-suggested model portfolio → Review → Send proposal (status pill Draft→Sent).
2. **Research a fund → recommend.** Discover → Screener (filter + weight) → Fund One-Pager (score-first) → Watch/Compare → add to a build.
3. **Build a model portfolio.** Portfolio → Build → set corpus/allocation/risk → Result donut + funds → Export PPT proposal.
4. **Monitor & act on drift.** Portfolio → Needs attention / Household detail (allocation vs target) → Run quarterly review; or Home NBA → deep link.
5. **Answer a client question.** Any screen → FAB "Ask Sentinel" → Copilot chat → escalate via Zoho handoff.
6. **Cycle review.** Home cycle deltas → Archive → compare cycles → download cycle PDF.

---

## 9. Screen inventory (delivered)

20 active screens (40 frames: viewport + full-scroll) with iOS device chrome:
Splash/Login · Home · Discover · Screener · Portfolio · Portfolio Builder (setup) · Portfolio Builder (result) · Household detail · Watchlist · Fund One-Pager · Compare · Overlap · Insights Studio · Alerts & Flags · Acquire (5 steps) · Support/Copilot · Knowledge Center · Archive · Profile.
*(Light Home variant deferred.)*

---

## 10. Design system & UX requirements

**Theme:** Dark-first. Deep near-black canvas (`#050608`) with an elevated surface scale, glassy cards, and gradients — a premium fintech/credit-card-app aesthetic. Light theme deferred (single variable-mode flip).

**Brand tokens (reconciled against the brand Figma file):**
- Accent: **copper `#B69377`** (brand "Brown 400 / Primary"); Sentinel gold `#B89E55` retained as a web-only alias.
- **AI gradient** reserved for intelligence moments (NBA, Copilot, advisory).
- Negatives in `#931621` with an `#E4536B` legibility companion for small text on dark.
- Type: **Figtree** (UI) + **Tabular / JetBrains Mono** (numerals, tabular figures).
- **Line-height rule:** font-size × 1.5, rounded down to even. **Icon size** = paired line height.

**Component library (26 components):** Button (metal/secondary/ghost), filter chips, delta pills, badges, metric tile, KPI stat card, Fund card (score ring), NBA card (AI border), Alert card (severity bar), List row, frozen-column Table row, Top app bar, glass Tab bar, segmented control, Search bar, Slider (0–100% in 10% steps), Drift Bar (% of target), Donut (persona presets), Input, Quick Action, Back Button, Avatar (40/44/56), FAB, Tag Pill. Icons from swappable Phosphor stroked (inactive) / filled (active) sets.

**Elevation (5 effect styles):** Card, Raised, Overlay, Glass (blur), Hero glow (copper bloom).

**UX principles applied:** one accent per section; 44px section rhythm; quiet mono section headers; low cognitive load via generous negative space; 44px minimum touch targets; WCAG-passing text contrast (section text moved to `text/tertiary`).

**Known constraint:** meters (Slider/Drift/Donut) are variant-based (Figma instance children can't be resized), so values snap to defined steps rather than arbitrary data — acceptable for design; a data-accurate prototype would need more variants or a different technique.

---

## 11. Competitive analysis

The unified app sits at the intersection of three tool categories that exist as *separate* products in the Indian market. No single competitor combines institutional MF research + PMS/AIF discovery + client lifecycle + AI Copilot in one mobile advisor app — which is the app's core positioning.

### 11.1 Category A — MFD / IFA distributor platforms (client lifecycle + transactions)

| Product | What it does | Model | Gap vs Centricity app |
|---------|--------------|-------|-----------------------|
| **AssetPlus** | MFD platform, 22,000+ MFDs; analytics, SIP top-up, multi-AMC reconciled brokerage; partner app | Free, operates under ND ARN | Transaction/ops-first; lacks a 22-parameter research engine, PMS/AIF discovery, deep overlap |
| **NJ Wealth** | India's largest MF distributor; 100% digital, national ND | ND (retains 10–30 bps trail) | Closed ecosystem; not research-led; not AI-native |
| **Prudent (Fundzbazar)** | Large ND platform + back-office | ND | Similar to NJ; ops-centric |
| **Wealth Elite (REDVision)** | White-label SaaS for mid/large practices | Subscription, own ARN | Back-office strength, weaker on institutional research + AI |
| **IFANow / IFA-Planet** | Lightweight, affordable advisor SaaS (4,700+ advisors) | Subscription | Budget positioning; not HNI/UHNI-grade research |

### 11.2 Category B — PMS / AIF research & discovery

| Product | What it does | Gap vs Centricity app |
|---------|--------------|-----------------------|
| **PMS Bazaar** | India's #1 PMS/AIF platform; 500+ PMS, 200+ AIF, 60+ GIFT funds; comparisons, analytics, events; 100,000+ subscribers | PMS/AIF only — no MF screener, no client lifecycle, no portfolio drift/household monitoring |
| **PMS AIF World** | PMS/AIF advisory & comparison content | Advisory/content-led; not a partner workflow tool |

*(Market context: PMS + AIF assets ≈ ₹23.4 lakh cr as of Sep 2025, ~31% 10-yr CAGR — a fast-growing discovery category the app taps via its MF/PMS/AIF/SIF segmented Discover.)*

### 11.3 Category C — MF research / screeners

| Product | What it does | Gap vs Centricity app |
|---------|--------------|-----------------------|
| **Value Research Online** | Long-standing MF research, ratings, screener | Retail/DIY-oriented; no advisor workflow, no proprietary partner score, no lifecycle |
| **Morningstar India** | Independent ratings, screener, compare, star ratings | Data/ratings utility; not a partner app; no AI Copilot |
| **RankMF (SAMCO)** | Independent MF research + ranking | Ranking + retail transactions; not HNI advisor lifecycle |
| **PrimeInvestor** | Subscription MF screener + research/recommendations | Research-led for investors; not a partner build/monitor tool |

### 11.4 Adjacent — premium B2C wealth apps (UX benchmarks)

Groww, Kuvera, INDmoney, ET Money, Dezerv — best-in-class mobile UX and the visual bar the app's dark, card-led design targets. They are *client-facing*, not advisor tools, so they are design references rather than direct competitors.

### 11.5 Positioning summary

**Where Centricity wins:** the only offering that fuses (1) proprietary 22-parameter institutional MF research, (2) PMS/AIF/SIF discovery + overlap, (3) full client lifecycle (acquire → build → monitor households/drift), and (4) an AI-native layer (NBA, nudges, Copilot) — in a single premium **mobile** advisor app aimed at HNI/UHNI/Family-Office partners.

**Where competitors are ahead today:** transaction execution and reconciled brokerage (AssetPlus, NJ, Prudent), breadth of PMS/AIF coverage (PMS Bazaar), and depth of independent MF ratings history (Value Research, Morningstar). These indicate priorities for later phases (execution, coverage depth, ratings credibility).

---

## 12. Non-functional requirements

- **Platform:** iOS-first, 375 × 812 baseline; responsive to common iPhone sizes; Android as a fast-follow.
- **Performance:** research tables and cycle data should load progressively; tables use horizontal scroll with a frozen key column.
- **Accessibility:** WCAG AA text contrast on dark surfaces; 44px minimum touch targets; tabular numerals for scannable financial data.
- **Security/Privacy:** biometric unlock (Face ID); partner authentication; no client credentials stored in design/spec files; role-appropriate data.
- **Data cadence:** fund universe refreshed fortnightly (cycles); archive retains prior cycles.
- **Export:** partner-ready PPT/PDF/CSV for proposals, comparisons, overlap, and cycle reports.

---

## 13. Success metrics

- **Adoption:** % of partners active weekly on mobile; logins consolidated from two products to one.
- **Acquisition:** proposals created per partner; Draft→Sent→Approved conversion.
- **Engagement:** NBA/nudge action rate; Copilot sessions per active partner.
- **Research usage:** screener runs, fund one-pager views, compares, overlaps per partner.
- **Portfolio health:** households in "In Sync" vs "Drift"; quarterly reviews completed on time.
- **Efficiency:** time-to-onboard a client; time-to-build a proposal.

---

## 14. Release plan / roadmap

**Phase 0 — Design (complete).** Unified IA, dark design system, 20 screens, GitHub backup.

**Phase 1 — Prototype & handoff.** Interactive prototype (tab nav + transitions), Dev-Mode specs, redlines.

**Phase 2 — Build P0.** Splash/Login, Home, Discover, Screener, Fund One-Pager, Portfolio + Builder flow, Acquire flow — wired to real data.

**Phase 3 — Build P1.** Compare, Overlap, Household detail, Watchlist, Insights Studio, Alerts, Support/Copilot.

**Phase 4 — Enhancements.** Knowledge Center, Archive, Profile depth, light theme, Android, transaction/execution and reconciled brokerage (to close the gap vs distributor platforms), deeper PMS/AIF coverage.

---

## 15. Risks & open questions

- **Meter data fidelity** — variant-based meters vs arbitrary values; decide before a data-wired prototype.
- **Execution scope** — do partners need to *transact* in-app (vs AssetPlus/NJ), or is this research + lifecycle only?
- **PMS/AIF coverage depth** — how much of PMS Bazaar-grade coverage is in scope?
- **Brand unification** — final call on copper vs gold as the single accent across both legacy audiences.
- **Data sources & refresh** — live integration for AUM, CAS import, brokerage, and cycle data.
- **Role-based views** — partner vs research-desk vs RM permissions.
- **Light theme** — timing and scope.

---

## 16. Appendix — glossary

- **Centricity 22-parameter score** — proprietary percentile-rank score of a fund within its asset-class peer group (100% = best).
- **Cycle** — fortnightly refresh of the fund universe and rankings; "since last cycle" deltas track changes.
- **NBA (Next-Best-Action)** — AI-recommended action surfaced on Home / Insights.
- **Drift** — deviation of a household's allocation from its target; DRIFT/WATCH thresholds trigger review.
- **Overlap** — shared-holdings analysis between funds (portfolio de-duplication).
- **CAS** — Consolidated Account Statement (imported during Acquire/onboarding).
- **SIF** — Specialised Investment Fund research area.
- **Copilot / Ask Sentinel** — AI assistant (FAB) for querying clients/funds/revenue/reports, with Zoho human handoff.

---

*Sources for the competitive analysis are listed with the delivery of this document. This PRD reverse-documents a completed design; feature behaviours are inferred from the two source dashboards and the delivered Figma screens, and should be validated against product intent before build.*
