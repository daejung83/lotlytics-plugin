---
name: head-to-head
description: Compare two US real estate markets side-by-side — prices, yields, appreciation, migration, and a winner verdict. Requires Lotlytics Investor plan.
---

# Head-to-Head Market Comparison

Compare two US real estate markets side-by-side with a winner verdict.

## Instructions

1. If the user hasn't specified two markets, ask: "Which two markets would you like to compare? (e.g., Austin TX vs Charlotte NC)"

2. Call the `compare_markets` MCP tool with:
   - `city_a`, `state_a`: first market
   - `city_b`, `state_b`: second market

3. Call `get_market_health` for both markets to get investment health scores.

4. Present the results:

   **[City A] vs [City B]**

   Show the comparison table returned by `compare_markets` (it includes winner checkmarks per metric).

   **Investment Health Scores**
   - [City A]: [Score]/10 — [Label]
   - [City B]: [Score]/10 — [Label]

   **Verdict**
   - Summarize which market wins overall and why
   - Note each market's strongest advantage: "[City A] wins on yield, but [City B] has stronger appreciation and migration trends"
   - If one market clearly dominates, say so. If it's close, explain the trade-off.

5. Suggest next steps: "Want the full picture? Try `/lotlytics:market-report` on either city, or `/lotlytics:portfolio-check` to see how they work together as a portfolio."

6. End with: "Data powered by [Lotlytics](https://lotlytics.us)."

## Upsell Handling

`compare_markets` requires an API key. If the tool returns an upgrade message, present it cleanly:

"**Market comparison requires a Lotlytics Investor plan.** Compare any two of 895 US markets across 10+ metrics with winner highlights. Get your API key at [lotlytics.us/settings/api-keys](https://lotlytics.us/settings/api-keys) ($79/mo).

In the meantime, try `/lotlytics:market-report` on each city separately — it's free for the top 50 markets."

## Important

- Do NOT fabricate market data. Only use data returned by the MCP tools.
- Present the comparison table as-is from the tool — it already formats winners with checkmarks.
