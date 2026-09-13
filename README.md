# LLY Tracker

Real-time dashboard and diligence workspace for Eli Lilly & Company (NYSE: LLY). It combines server-side Alpaca market/news data, transparent technical signals, peer performance, and a sourced fundamental lens. It is decision support, not investment advice.

## Run locally

1. Copy `.env.example` to `.env` and add an Alpaca market-data key and secret.
2. Run `npm start`.
3. Open `http://localhost:3000`.

The browser never receives the Alpaca credentials. The Node server reads them from environment variables and only exposes the dashboard payload at `/api/dashboard`. Do not commit `.env`.

## What the dashboard calculates

- **Trend state:** latest LLY price versus the 20- and 50-trading-day simple moving averages.
- **Relative context:** one-day movement for obesity/pharma peers (NVO, MRK, ABBV, PFE), a payer proxy (UNH), and healthcare sector ETF XLV.
- **Correlation:** Pearson correlation of LLY and XLV daily returns when overlapping observations are available. Correlation is descriptive, not predictive.
- **News:** recent Alpaca news for LLY and related healthcare names. Headlines are context, deliberately not translated into buy/sell recommendations.

## Fundamental starting point

Lilly reported FY2025 revenue of $65.179 billion, up 45% year-over-year. Mounjaro generated $22.965 billion and Zepbound $13.542 billion—together about 56% of reported 2025 revenue. The company said Q2 2026 revenue was $23.0 billion, up 48%, and raised 2026 revenue guidance to $85–87 billion. These are operating facts, not a valuation conclusion.

Key upside variables include durable obesity/diabetes demand, production capacity, international expansion, and pipeline/regulatory progress. Key downside variables include realized-price pressure, reimbursement and policy changes, supply execution, safety/regulatory outcomes, acquisition integration, and intense obesity-market competition. Review the separate `balance-sheet-analysis` branch for a forward-looking solvency framework and scenario table.

## Sources

1. Eli Lilly, [2025 Form 10-K](https://investor.lilly.com/static-files/70c644f5-d894-471a-a4c5-6464848ca393), filed February 2026 — FY2025 revenue and product sales.
2. Eli Lilly, [Q2 2026 financial results](https://investor.lilly.com/news-releases/news-release-details/lilly-reports-second-quarter-2026-financial-results-raises-full), August 5, 2026 — Q2 performance, updated guidance, pipeline and investment commitments.
3. Alpaca Market Data — live IEX snapshots, bars, and news supplied at runtime via the connected account. Feed timestamps and coverage vary; validate before acting.

## Limitations

The IEX feed may not represent consolidated market volume or the national best bid/offer. Technical indicators are simple and intentionally inspectable; they do not account for valuation, events, market microstructure, taxes, or an investor’s objectives. This repository does not place orders.
