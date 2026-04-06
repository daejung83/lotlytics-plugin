---
name: explore-state
description: Discover the best real estate investment markets in a US state — ranked by investment health score. Free tier shows major metros only.
---

# Explore a State

Discover the best real estate investment markets in a US state, ranked by investment health score.

## Instructions

1. If the user hasn't specified a state, ask: "Which state would you like to explore? (e.g., Texas, Florida, Ohio)"

2. Call the `list_markets` MCP tool with `state` set to the user's chosen state (use the full state name or 2-letter abbreviation).

3. From the results, pick up to 5 markets. If the tool returns fewer than 5, use all of them.

4. For each market, call the `get_market_health` MCP tool with that market's city and state. Do NOT call more than 5 times — this keeps the response fast.

5. Rank the markets by their health score (highest first) and present them:

   **Top Markets in [State]**

   For each market:
   - **[City]** — [Score]/10 ([Label]: Strong Buy / Favorable / Neutral / Caution / Avoid)
   - Key signal: the single most notable metric (e.g., "7.2% rental yield" or "+8.1% appreciation")

6. After the rankings, add a brief summary: "Based on investment health scores, [City] stands out for [reason]. [City] is also worth watching for [reason]."

7. End with: "Data powered by [Lotlytics](https://lotlytics.us). Unlock all 895 markets at lotlytics.us/pricing."

## Free Tier Behavior

The free tier covers the top 50 US metros. Most states have 0-3 markets in this list. For example:
- **Texas:** Dallas, Houston, San Antonio, Austin (4 free markets)
- **Florida:** Miami, Tampa, Orlando, Jacksonville (4 free markets)
- **Montana:** 0 free markets

If `list_markets` returns no free markets for a state, or if all `get_market_health` calls return upgrade messages, present it honestly:

"The free tier doesn't include markets in [State]. Lotlytics covers [N] markets in [State] on the Investor plan ($79/mo). [Unlock all markets →](https://lotlytics.us/pricing)"

If only some markets are available, show those and note how many more are available with premium.

## Important

- Do NOT fabricate market data. Only use data returned by the MCP tools.
- Do NOT call `get_market_health` more than 5 times. If there are more markets, note: "Showing top 5. Use `/lotlytics:find-markets` with premium to search all [N] markets in [State]."
