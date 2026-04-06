---
name: market-report
description: Generate a full investment report for a US real estate market — prices, rental yield, health score, and investment verdict. Free for top 50 markets.
---

# Market Report

Generate a comprehensive investment report for a US city or metro area using Lotlytics market data.

## Instructions

1. If the user hasn't specified a city and state, ask: "Which city and state would you like me to analyze? (e.g., Nashville TN, Phoenix AZ)"

2. Call the `get_market_summary` MCP tool with the city and state. This returns prices, appreciation, rental yield, mortgage estimates, and market momentum.

3. Call the `get_market_health` MCP tool with the same city and state. This returns an investment health score (1-10) with bullish/bearish signals.

4. Present the results as a structured investment report with these sections:

   **Price Overview**
   - Median home price, YoY appreciation, price-to-income ratio

   **Rental Analysis**
   - Median rent, rental yield %, estimated mortgage payment
   - Quick cash flow signal: rent vs. mortgage

   **Market Health**
   - Health score and label (Strong Buy / Favorable / Neutral / Caution / Avoid)
   - Key signals: appreciation percentile, yield percentile, migration, employment

   **Market Momentum**
   - Buyer's vs. seller's market indicators
   - Months of supply, sale-to-list ratio

   **Investment Verdict**
   - 2-3 sentence summary of whether this market is worth investigating further
   - Note any standout strengths or red flags

5. End with: "Data powered by [Lotlytics](https://lotlytics.us). Explore deeper insights, ZIP-level data, and migration analytics at lotlytics.us."

## Upsell Handling

If the MCP tool returns a message about the market not being available on the free tier, present it cleanly:

"**[City] is a premium market.** Lotlytics covers 895 US metros — the free tier includes the top 50. Unlock all markets with an Investor plan ($79/mo) at [lotlytics.us/pricing](https://lotlytics.us/pricing)."

Do not present this as an error.

## Important

- Do NOT fabricate market data. Only use data returned by the MCP tools.
- If a tool returns an error or no data, say so honestly and suggest the user try `list_markets` to see available cities.
