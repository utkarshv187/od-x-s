# Sentinel · OneDigital Partner — module walkthrough (captured 2026-07-17, logged-in session)

App shell: left icon rail — Copilot (new chat), Insights Studio (dashboard), Acquire (person+), Manage (briefcase), Discover (search), Serve (chat bubble). Breadcrumb top bar "Workspace › <module>". Every module has a floating **"✦ Ask Sentinel"** pill (AI entry). Fonts: Inter UI + JetBrains Mono for all numerals/labels/status pills. Surfaces `#050608/#0D1017/#14181F`, indigo-violet gradient for active/AI elements.

## Copilot — /app/chat ("Hello, kk")
Hero AI greeting + prompt box ("Ask Sentinel anything…", attachment clip) + 8 area chips: Insights, Acquire, Manage, Discover, Serve, Clients, Revenue, Reports.

## Insights Studio — /app/dashboard
- Time-range segmented control: 1M · 3M · 6M · 1Y · YTD · ALL
- 4 KPI stat cards with sparklines + delta vs prev: TOTAL AUM ₹1152.80 Cr (+3.2%), ACTIVE CLIENTS 13 (+1.8%), BROKERAGE MTD ₹60.0L (+8.4%), PENDING ALERTS 8 (−12.5%, red sparkline)
- **URGENT ALERTS · 12** — cards with severity left-border (red critical / amber alert): "<client> drift X%" (equity over/underweight by N pp) and "<family> review due" (Nd since last review), chevron to act
- **NEXT BEST ACTIONS · 3** — action cards with deep links: "Review Anjali Sen drift → Open management", "Convert latest CAS into a proposal (parsed holdings + pitch points ready) → Open acquisition", "Follow up draft proposals (10 in Draft) → Review proposals"
- PRODUCT MIX across book — donut by asset class: Equity 49.6% ₹571.39 Cr · Debt 30.7% ₹354.33 Cr · Alternatives 19.7% ₹227.08 Cr
- TOP 10 CLIENTS by AUM — table: avatar initials, client/group, AUM, last review (Nd ago), NBA chip (Critical drift / Review drift / In sync), Open
- CASH FLOW last 12 months — stacked bars: new investments vs trail commissions (₹0–16 Cr axis)
- RECENT TRANSACTIONS last 20 — type filter All/Buy/Sell/SIP/Dividend; rows: client, fund/product, type, amount, date

## Acquire — /app/acquire
- **LIVE PROPOSALS** — cards: client name, PROP-ID · risk (Aggressive/Moderate/Conservative) · status pill (Draft amber / Sent blue / Approved green), ₹ target in green mono
- **Client Acquisition** — "Select investor type": Existing Investor | New Investor → Continue (indigo)
- New-investor journey: 5-step rail — 1 Client details (PAN, full name, DOB, mobile, email, client group [multi-PAN grouping], AUM target; "KYC reconciliation happens after submit") · 2 Risk Persona · 3 Investment goals · 4 Advisory & Portfolio (advisory chat) · 5 Review → proposal
- Existing-investor path: CAS-based (see NBA "Convert latest CAS into a proposal")

## Manage — /app/manage
- Client group switcher + status dot; tabs: **Overview · Upsell · Rebalance · Review · Client portfolio**
- Actions: "Run quarterly review" (primary indigo-violet gradient), "Generate upsell proposal", "Open client portfolio ↗"
- KPI cards (mono, color-coded): AUM ₹1.00Cr (indigo) · DRIFT 0.0% (green) · STATUS In Sync · LAST REVIEW 2026-05-27
- ALLOCATION donut (Equity 60 / Debt 30 / Alt 10) · AUM TREND last 4 quarters (bars)
- DRIFT CONTRIBUTORS table: asset class, actual %, target %, delta pp, severity (Low/…)
- NEXT BEST ACTIONS: "Propose rebalance" / "No actions queued — in sync"
- Rebalance tab: drift-derived fund shortlist (offline view in demo)

## Discover — /app/discover (Product Discovery)
- "Screener across 1179 products (MF · PMS · AIF) · Centricity Research Desk"
- Scope segmented: All / MF / PMS / AIF; NL search ("Search funds, AMCs, or try: large cap low drawdown")
- Filter groups (accordions): ASSET CLASS (Equity/Hybrid/Debt/Others) · CATEGORY & AMC (multi-select) · RETURNS (1Y/3Y/5Y/Rolling 3Y/YTD ranges) · RISK RATIOS (Sharpe/Sortino/StdDev/MaxDD/Beta) · FUND PROFILE (AUM/Expense/Turnover/Tenure/Stocks) · **SCORE & VERDICT (Buy / Hold / Review / Avoid)** · Reset All · **Weights** editor
- Results: "50 results · 10 in compare · Compare · Columns"; table rows: rank #, fund + AMC, category pill (indigo tint), score 0–1 with green bar, 1Y/3Y/5Y %, AUM (K Cr), expense %; checkbox select; sortable headers
- Pagination "Page 1"

## Serve — /app/serve (24×7 Support)
- "RESOLUTION WORKSPACE — Help & Support"; chat thread with SUPPORT bot bubble ("Ask anything — about your clients, day-to-day tasks, or a message you need to send"), suggested queries list (left panel at desktop width), input + Send, status line "Support desk ready" (Zoho handoff behind the scenes)

## Mobile design implications
- Sentinel's NBA/alert/severity system + KPI sparkline cards → Home & Insights Studio screens
- Verdict chips (Buy/Hold/Review/Avoid) → merge into fund cards alongside Centricity 22-param score
- Proposal status pills (Draft/Sent/Approved) → Acquire flow cards
- Copilot area chips + "Ask Sentinel" floating pill → global AI entry on mobile (Support tab + FAB on Home)
- All numerals mono/tabular → matches Tabular font direction; status/label mono treatment → JetBrains Mono micro-labels
