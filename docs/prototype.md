# OD×S — Interactive Prototype (dark, v2)

**Play it:** https://www.figma.com/proto/CLPQWVuBtMRql6U9AiscN6/?page-id=10%3A3&node-id=53-1620&starting-point-node-id=53%3A1620&scaling=scale-down-width
Starting frame: **Splash · Login**. All interactions live on the 375×812 viewport frames on page `03 · Screens`; visuals untouched.

**v2 — Screener & Portfolio clusters now lead to real UI everywhere** (no dead controls). Five new surfaces added (interactions-only, built from library instances): Screener Filter sheet, Screener Edit-Weights sheet, Builder Proposal-Ready sheet, Household Quarterly-Review sheet, and a full Import-CAS screen.

## Named flows
| Flow | Entry frame |
|---|---|
| Onboarding | Splash · Login |
| Research | Discover |
| Build | Portfolio |
| Monitor | Insights Studio |
| Copilot | Support · Advisor |

## Global behavior
- **Scroll:** every screen scrolls vertically; status bar, glass tab bar, FAB, and home indicator are pinned (fixed children).
- **Tabs:** Home / Discover / Portfolio / More(→Profile) on every tab screen — Smart Animate 250ms so the persistent bar carries continuity; active tab = filled icon, inactive = stroked (pre-set per screen).
- **FAB ✦ (Ask Sentinel):** on all 5 main screens → Support/Copilot, Move-in from bottom 300ms (sheet-style); its Back returns.
- **Back buttons (19):** Navigate back.
- **Screen pushes:** Move-in left, 300ms, ease-out — consistent everywhere. Auth + proposal-send use a 250ms dissolve.

## Link map (67 hotspots)
- **Splash:** Sign in / Face ID → Home.
- **Home:** Onboard→Acquire 1 · Screen→Screener · Build→Builder setup · Compare→Compare · bell→Alerts & Flags · NBA card→Household · top-fund rows→One-Pager · "See all"→Screener · "View all"→Insights Studio · Studio row→Insights Studio · archive caption→Archive.
- **Discover:** tools→Screener/Compare/Overlap · Fund Card + fund rows→One-Pager · Knowledge Center row→KC · "Open full Screener"→Screener. (Managers/SIF/Stocks have no screens — intentionally unwired.)
- **Screener:** all 5 result rows→One-Pager · filter chips + search bar→**Filter sheet** (bottom sheet) · "Edit weights"→**Edit-Weights sheet** (bottom sheet).
- **Filter sheet:** asset/category/AMC chips, returns+risk sliders, Buy/Hold/Review/Avoid verdict badges; "Show 1,157 funds" / "Reset all" / scrim tap → back to Screener.
- **Edit-Weights sheet:** 6 group-weight sliders (22 params); "Apply weights" / "Reset defaults" / scrim → back.
- **One-Pager:** primary CTA & Compare→Compare · Watch→Watchlist.
- **Compare:** "＋ Add" chip→back. **Overlap:** back only.
- **Portfolio:** Build→Setup · Review→Household · Import CAS→**Import-CAS screen** · Watchlist→Watchlist · alert card + household rows→Household · watchlist rows→Watchlist · "All 13 households"→Household.
- **Import CAS:** dropzone + parsed-preview rows; "Build proposal from CAS"→Builder setup · "Add to a household"→Household · dropzone→Builder setup.
- **Builder:** "Build portfolio" + Review chip→Result · Result "Adjust inputs"→back · Result **"Export proposal · PPT"→Proposal-Ready sheet**.
- **Proposal-Ready sheet:** success confirm + generated PPT/PDF rows; "Share with client" / "Back to result" / scrim → back.
- **Household:** back · **"Run quarterly review"→Quarterly-Review sheet** · "Propose rebalance"→Builder result.
- **Quarterly-Review sheet:** 4-item review checklist (Done/Pending); "Complete review" / "Reschedule" / scrim → back.
- **Acquire 1–5:** Continue→next step · step chips jump to any step · backs→previous · Step 5 "Send proposal" & "Save as draft"→Home (dissolve).
- **Insights Studio:** NBA→Household · CAS row→Acquire 1 · drafts row→Acquire 5.
- **Profile (More tab):** Sign out→Splash · Export history→Archive. KC/Support/Archive are reachable via Discover row, FAB, and Home caption respectively (no dedicated "More menu" screen exists in the design).

## New v2 frames (exports in /exports)
`26-screener-filters-dark.png` · `27-screener-weights-dark.png` · `28-builder-proposal-dark.png` · `29-household-review-dark.png` · `30-import-cas-dark.png`

## Known notes
- Sheets are separate frames (scrim + rounded sheet) opened with Move-in-from-bottom and dismissed via footer buttons or scrim tap — the plugin API can't create true Figma overlays, so these use full-frame navigation that reads identically in the player.
- Prototype *device* (iPhone bezel) isn't settable via the plugin API — pick "iPhone 13 mini/similar" once in Figma's prototype settings panel if you want the bezel.
- A user-made duplicate frame named "0" sits at x≈−2750 on the Screens page (not created by the design pipeline); its auto-flow label was removed. Delete it if it's not yours.
