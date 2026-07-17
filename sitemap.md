# Centricity OD×S — Information Architecture (v0.1, for approval)

Single mobile app, 5-tab bottom bar. Every feature of both dashboards mapped below — nothing dropped.

```
                                   ┌─────────────────────┐
                                   │  Splash → Login      │
                                   │  (biometric re-entry)│
                                   └──────────┬──────────┘
      ┌────────────┬────────────────┬─────────┴──────┬────────────────┐
      ▼            ▼                ▼                ▼                ▼
   🏠 HOME      🔍 DISCOVER      💼 PORTFOLIO      ✨ INSIGHTS       ⋯ MORE
```

## Tab 1 — Home (command center)
Merged Screener-home + Sentinel dashboard.
- Greeting + cycle chip (15 Jun 2026 ▾ — 6 cycles) + search + alerts bell (badge)
- Cycle summary stat row: fund universe 2,014 · 45 SEBI categories · update date
- **Next-Best-Action carousel** (Sentinel NBA — AI gradient cards)
- Quick Actions grid (Screener / One-Pagers / Build / Compare / Onboard client / Review due)
- **Top 10 — Centricity Rank** (asset-class picker → mobile table, frozen fund column, 22-param score)
- Manager switches · top 6 (→ full list in Insights/Flags)
- Universe composition (asset-class donut + active/passive split)
- "What changed since last cycle" delta cards (new entrants / dropped / gainers / losers / manager changes → Archive)
- *Light-theme variant of this screen also delivered (per brief)*

## Tab 2 — Discover (all research)
Merged MF Screener + Sentinel Product Discovery.
- Segmented scope: **Mutual Funds · PMS · AIF · SIF · Stocks**
- **Screener** — search, filter pills, saved views, filter bottom sheet (asset class/type/category/AMC/AUM/returns/risk ratios), edit-weights sheet (22 params, live re-rank), sortable mobile table (frozen first column), export PDF/PPT
- **Fund One-Pager** (fund detail): header + score ring, returns (YTD/1/3/5Y, calendar), risk & ratios, rolling windows (3Y/5Y·10Y), holdings & sectors, market-cap mix, manager history, costs/TER/exit load, actions: ⭐ watchlist · + compare · share · download
- **Compare** — up to 7 funds × 6 cycles, 8 metric tabs (Overview/Returns/Risk/Portfolio/Manager & AMC/Costs & Structure/…), growth-of-₹1L chart, auto change summaries, export
- **Overlap analysis** — fund multi-select → pairwise overlap heat matrix + common-holdings drill-in, export
- **Stocks universe** — company/industry/mkt-cap/P/E/1Y/held-by-funds; stock → funds holding it
- **SIF research** — specialized investment funds table
- **Manager Profiles** — manager list → profile (funds run, tenure, track record, overseas mandates)

## Tab 3 — Portfolio (client work)
Merged Portfolio Builder + Sentinel Manage.
- **Households** (Manage) — household list → household detail: holdings, allocation, drift meter, quarterly-review status & scheduler
- **Portfolio Builder** — 10-step config as mobile stepper (corpus, force-include, mode Rank-based/Centricity-Select, asset allocation, liquidity sleeve, m-cap mix, filters, risk profile, horizon, fund count) → **Result**: model portfolio, allocation donut, fund list with weights, export PPT/PDF
- **Portfolio Review** — upload/import CAS → gap analysis vs model
- **Watchlist** — swipe rows, delta since added, alerts toggle per fund
- **Portfolio drift** — drift bars per household, rebalance suggestions

## Tab 4 — Insights (intelligence & monitooring)
Merged Insights Studio + Flags/Alerts + Archive.
- **Insights dashboard** — KPI tiles (AUM, active clients, reviews due, NBA acceptance)
- **NBA queue** — full next-best-action list, accept/dismiss, priority P1–P5
- **Nudges** — client nudge feed + templates
- **Alerts & Flags** — manager movement, AUM breaches, style drift; filterable, per-fund flag history (MF "Flags" page + planned alerts panel)
- **Archive / cycle history** — 6 cycles, cycle-over-cycle deltas, reclassifications
- **Portfolio services** — service requests status

## Tab 5 — More (acquire, support, knowledge, profile)
- **Acquire — client onboarding** (Sentinel): 3-step mobile flow — 1) client & CAS/PMS/AIF selection, 2) document/CAS import, 3) risk profiling → summary
- **24×7 Support** — digital advisor chat (AI gradient), Zoho ticket handoff, FAQ
- **Knowledge Center** — glossary (Score & Rank, Returns, Risk & Ratios, Portfolio & Holdings, Debt metrics, Costs & Taxes) as searchable accordion
- **Profile & settings** — partner identity, theme (dark/light), biometric lock, saved views, export history, sign out

## Feature-mapping audit (source → destination)

| Source feature | Destination |
|---|---|
| MF Home (cycle summary, quick actions, top 10, switches, composition, deltas) | Home |
| Screener + filters + saved views + weights | Discover → MF |
| Fund One-Pager | Discover → fund detail |
| Portfolio Builder + result/export | Portfolio → Builder |
| Compare (7×6, 8 tabs) | Discover → Compare |
| Overlap | Discover → Overlap |
| Watchlist | Portfolio → Watchlist |
| Alerts/Flags (manager/AUM/drift) | Insights → Alerts & Flags |
| Knowledge Center | More |
| SIF research | Discover → SIF |
| Manager Profiles | Discover → Managers |
| Archive | Insights → Archive |
| Stocks universe (extra page found) | Discover → Stocks |
| Sentinel Acquire (CAS/PMS/AIF, risk profiling) | More → Acquire (entry also on Home quick actions) |
| Sentinel Manage (households, reviews, drift) | Portfolio → Households |
| Sentinel Product Discovery (PMS/AIF/MF + overlap) | Discover (scope segments) |
| Sentinel 24×7 Support (advisor, Zoho) | More → Support |
| Sentinel Insights Studio (dash, NBA, nudges, services) | Insights (NBA also surfaces on Home) |

## Screen list for production (after approval)

1. Splash / Login (+ biometric) · 2. Home dark · 3. Home light · 4. Discover hub/Screener · 5. Filter sheet · 6. Edit-weights sheet · 7. Fund One-Pager · 8. Compare · 9. Overlap · 10. Portfolio Builder (stepper) · 11. Builder result · 12. Households list · 13. Household detail (drift) · 14. Watchlist · 15. Insights dashboard (NBA + nudges) · 16. Alerts & Flags · 17. Acquire step 1–3 · 18. Support / digital advisor · 19. Knowledge Center · 20. Profile/More · 21. Archive.
