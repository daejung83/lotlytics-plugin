---
name: analyze-property
description: Analyze a specific property for investment potential — provide details or paste a Zillow link. Compares property price against market data. Free for top 50 markets.
---

# Property Investment Analysis

Analyze a specific property's investment potential by combining property details with Lotlytics market data.

## Instructions

### Gathering Property Details

**If the user provides a Zillow URL:**
1. Attempt to fetch the listing page using the WebFetch tool to extract: asking price, city, state, bedrooms, square footage, and address.
2. If WebFetch fails or returns incomplete data (Zillow frequently blocks automated requests), tell the user: "I couldn't pull the listing details automatically. Can you share the key info? I need: asking price, city/state, bedrooms, and square footage."

**If the user provides details directly (or after fallback):**
1. Confirm you have at minimum: asking price, city, and state.
2. Bedrooms and square footage are helpful but optional.

### Market Analysis

3. Call the `get_market_summary` MCP tool with the property's city and state.

4. Call the `get_market_health` MCP tool with the same city and state.

### Investment Report

5. Present the analysis with these sections:

   **Property Details**
   - Asking price, beds, sqft, address (if available)

   **Property vs. Market**
   - Asking price vs. market median — is this above, below, or at market value?
   - Calculate the delta: "This property is X% [above/below] the market median of $Y"

   **Estimated Rental Income**
   - Use the market's median rent from `get_market_summary`
   - Note: "This is the metro-level median rent. Actual rent depends on property condition, neighborhood, and bedroom count."

   **Investment Metrics**
   - Gross rental yield: (annual rent / asking price) * 100
   - Monthly cash flow estimate: monthly rent - estimated mortgage (from market summary)
   - Note these are rough estimates for screening, not financial advice

   **Market Context**
   - Health score and label from `get_market_health`
   - Market momentum (buyer's vs. seller's market)
   - Appreciation trend

   **Verdict**
   - 2-3 sentences: Is this property worth deeper due diligence?
   - Flag any concerns (overpriced vs. market, weak market momentum, low yield)

6. End with: "Data powered by [Lotlytics](https://lotlytics.us). For ZIP-level analysis and migration data, visit lotlytics.us."

## Upsell Handling

If the MCP tool returns a message about the market not being available on the free tier, present it cleanly:

"**[City] is a premium market.** Lotlytics covers 895 US metros — the free tier includes the top 50. Unlock all markets with an Investor plan ($79/mo) at [lotlytics.us/pricing](https://lotlytics.us/pricing)."

Do not present this as an error.

## Important

- Do NOT fabricate property data or market data. Only use data from the listing and MCP tools.
- Always note that estimates are for screening purposes, not financial advice.
- If the Zillow fetch works, great — but never promise it will. The manual input flow is the primary path.
