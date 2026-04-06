---
name: find-markets
description: Find US real estate markets matching your investment criteria — filter by budget, rental yield, appreciation, and state. Requires Lotlytics Investor plan.
---

# Find Markets — Investment Screener

Find US real estate markets that match specific investment criteria using guided filters.

## Instructions

1. Ask the user for their investment criteria. Present these as options:

   "What are you looking for? I can filter by any combination of:
   - **Budget:** Maximum home price (e.g., under $300k)
   - **Rental yield:** Minimum yield % (e.g., above 5%)
   - **Appreciation:** Minimum YoY appreciation (e.g., above 3%)
   - **Affordability:** Maximum price-to-income ratio (e.g., below 5x)
   - **State:** Focus on a specific state (e.g., Texas, Florida)

   Tell me your criteria, or just say something like 'markets under $250k with good yield in the Southeast'."

2. Parse the user's criteria into parameters for the `search_markets` MCP tool:
   - `max_price`: from budget
   - `min_rental_yield`: from yield target
   - `min_appreciation`: from appreciation target
   - `max_price_to_income`: from affordability target
   - `state`: from state preference (if they name a region like "Southeast", pick the most relevant state or leave blank for national)
   - `limit`: default to 10

3. Call `search_markets` with those parameters.

4. From the results, pick the top 3-5 markets and call `get_market_health` for each to get investment scores.

5. Present the results:

   **Top Markets Matching Your Criteria**

   For each market:
   - **[City, State]** — Health Score: [X]/10 ([Label])
   - Price: $X | Yield: X% | Appreciation: +X% | P/I: Xx
   - One-line insight: why this market stands out for their criteria

   **Recommendation:** "Based on your filters, [City] offers the best balance of [criteria]. [City] is a close second with [advantage]."

6. Suggest next steps: "Want to dig deeper? Try `/lotlytics:market-report` for a full report on any of these, or `/lotlytics:head-to-head` to compare your top two picks."

7. End with: "Data powered by [Lotlytics](https://lotlytics.us)."

## Upsell Handling

`search_markets` requires an API key. If the tool returns an upgrade message, present it cleanly:

"**The investment screener requires a Lotlytics Investor plan.** It searches across 895 US markets with custom filters — budget, yield, appreciation, and more. Get your API key at [lotlytics.us/settings/api-keys](https://lotlytics.us/settings/api-keys) ($79/mo).

In the meantime, try `/lotlytics:explore-state` to browse free markets in a specific state."

## Important

- Do NOT fabricate market data. Only use data returned by the MCP tools.
- The `search_markets` tool samples the top 20 markets from the full list and ranks by a composite score. Note this to the user: "Results are ranked from a sample of top markets. Filter by state for more complete results."
