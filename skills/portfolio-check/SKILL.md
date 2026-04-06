---
name: portfolio-check
description: Analyze 2-3 real estate markets as an investment portfolio — diversification, yield balance, and risk spread. Requires Lotlytics Investor plan.
---

# Portfolio Check

Analyze 2-3 real estate markets as an investment portfolio — assess diversification, yield balance, and risk spread.

## Instructions

1. Ask the user for 2-3 markets:

   "Which markets are in your portfolio (or are you considering)? Name 2-3 cities. For example: Dallas TX, Nashville TN, Phoenix AZ.

   If you're not sure which markets to consider, try `/lotlytics:find-markets` first to discover candidates based on your investment criteria."

2. For each market, call `get_market_summary` to get full data (prices, yield, appreciation, momentum, migration).

3. For each pair of markets, call `compare_markets`:
   - 2 markets = 1 comparison call
   - 3 markets = 3 comparison calls (A vs B, A vs C, B vs C)

4. Present the portfolio analysis:

   **Portfolio Overview**

   | Market | Price | Yield | Appreciation | Momentum | Health |
   |--------|-------|-------|-------------|----------|--------|
   | [City A] | $X | X% | +X% | [Label] | [Score] |
   | [City B] | $X | X% | +X% | [Label] | [Score] |
   | [City C] | $X | X% | +X% | [Label] | [Score] |

   **Diversification Analysis**
   - Geographic spread: Are these markets in different regions or clustered?
   - Economic correlation: Do they depend on the same industries?
   - Price tier spread: Mix of affordable and premium markets?

   **Yield & Growth Balance**
   - Portfolio average yield vs. national median
   - Portfolio average appreciation vs. national median
   - Is the portfolio tilted toward cash flow or growth? Is that intentional?

   **Risk Assessment**
   - Which market is the weakest link and why?
   - Any concentration risk (e.g., all sunbelt, all high-price)?

   **Recommendations**
   - Portfolio strengths and gaps
   - If 2 markets: "Consider adding a [characteristic] market to balance [weakness]"
   - If 3 markets: "This portfolio is [strong/weak] on [dimension]. To improve, consider swapping [weakest] for a market with [characteristic]."

5. End with: "Data powered by [Lotlytics](https://lotlytics.us). For ZIP-level analysis within each market, visit lotlytics.us."

## Upsell Handling

Both `get_market_summary` (full data) and `compare_markets` require an API key for markets outside the top 50. If any tool returns an upgrade message, present it cleanly:

"**Portfolio analysis requires a Lotlytics Investor plan.** Analyze any combination of 895 US markets with full data on prices, yields, migration, and more. Get your API key at [lotlytics.us/settings/api-keys](https://lotlytics.us/settings/api-keys) ($79/mo).

In the meantime, try `/lotlytics:market-report` on individual cities — it's free for the top 50 markets."

## Important

- Do NOT fabricate market data. Only use data returned by the MCP tools.
- `compare_markets` only accepts exactly two markets per call. For 3 markets, make 3 pairwise calls.
- Keep the analysis grounded in the actual data returned — don't speculate about industries or demographics unless the market data includes it.
