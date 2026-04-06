<p align="center">
  <img src="assets/logo.png" width="120" alt="Lotlytics" />
</p>

<h1 align="center">Lotlytics — Real Estate Intelligence for Claude</h1>

<p align="center">
  Investment scores, rental yields, and market data for <strong>895 US metros</strong>.<br/>
  Free for the top 50 markets. No account needed.
</p>

<p align="center">
  <a href="https://lotlytics.us">Website</a> &middot;
  <a href="https://lotlytics.us/pricing">Pricing</a> &middot;
  <a href="https://lotlytics.us/mcp">MCP Docs</a>
</p>

---

## What Can You Do?

> *"Is Nashville a good market to invest in right now?"*

```
## Nashville, TN — Market Health
🟢 Strong Buy (7.8/10)

Key signals:
- Appreciation: +5.2% YoY (72nd percentile)
- Rental yield: 6.1% (68th percentile)
- Market momentum: Balanced ⚖️
- Net migration: 81st percentile
- Employment: 74th percentile
```

> *"Compare Austin vs Charlotte for rental investing"*

> *"Find markets in Texas under $300k with yield above 5%"*

> *"I found a house at $285k in Tampa — is it a good investment?"*

---

## Quick Start

### Claude Code (Plugin)

```
/plugin marketplace add daejung83/lotlytics-plugin
/plugin install lotlytics@daejung83
```

Then use any skill: `/lotlytics:market-report`, `/lotlytics:analyze-property`, etc.

### Claude Desktop

Add to your config file:

**Mac:** `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "lotlytics": {
      "type": "sse",
      "url": "https://lotlytics-mcp-production.up.railway.app/sse"
    }
  }
}
```

Restart Claude Desktop. Look for the plugin icon. Done.

### Cursor / Windsurf

Add the same MCP config to your editor's MCP settings. The SSE endpoint works with any MCP-compatible client.

---

## Skills (Claude Code Plugin)

| Skill | Description | Tier |
|-------|-------------|------|
| `/lotlytics:market-report` | Full investment report for a city — prices, yield, health score, verdict | Free |
| `/lotlytics:analyze-property` | Analyze a specific property — price vs. market, estimated rent, cap rate | Free |
| `/lotlytics:explore-state` | Best markets in a state — ranked by investment health | Free |
| `/lotlytics:find-markets` | Guided screener — filter by budget, yield, appreciation, state | Premium |
| `/lotlytics:head-to-head` | Two markets side-by-side — comparison table with winner | Premium |
| `/lotlytics:portfolio-check` | 2-3 markets as a portfolio — diversification and risk analysis | Premium |

---

## MCP Tools

| Tool | Description | Tier |
|------|-------------|------|
| `get_market_health` | Investment health score (1-10) with bullish/bearish signals | Free (top 50) |
| `get_market_summary` | Full report: prices, appreciation, yield, momentum, migration | Free (top 50) |
| `list_markets` | List available markets, filter by state | Free (top 50) |
| `compare_markets` | Side-by-side comparison of two markets | Premium |
| `search_markets` | Filter 895 markets by investment criteria | Premium |

---

## Free vs Premium

| | Free | Premium ($79/mo) |
|---|---|---|
| Markets | Top 50 US metros | All 895 US metros |
| API key required | No | Yes (`X-API-Key` header) |
| Tools | 3 (health, summary, list) | 5 (+ compare, search) |
| Skills | 3 (report, property, state) | 6 (+ screener, comparison, portfolio) |
| Rate limit | 20/day per IP | 1,000/day per key |

**Get your API key:** [lotlytics.us/settings/api-keys](https://lotlytics.us/settings/api-keys) (requires Investor plan)

### Premium Setup

Same endpoint, just add your API key:

```json
{
  "mcpServers": {
    "lotlytics": {
      "type": "sse",
      "url": "https://lotlytics-mcp-production.up.railway.app/sse",
      "headers": {
        "X-API-Key": "YOUR_API_KEY"
      }
    }
  }
}
```

---

## Data Sources

Lotlytics aggregates data from 10+ government and commercial sources:

- **Zillow** — Home values (ZHVI) and rental values (ZRI)
- **Census Bureau** — Demographics, income, education (ACS)
- **Bureau of Labor Statistics** — Employment data
- **Federal Reserve (FRED)** — Economic indicators
- **IRS** — Tax filer migration flows
- **FEMA** — National Risk Index (climate hazards)
- **HUD** — Fair Market Rents
- **HMDA** — Mortgage lending data

---

## Links

- [lotlytics.us](https://lotlytics.us) — Full platform
- [lotlytics.us/pricing](https://lotlytics.us/pricing) — Plans & pricing
- [lotlytics.us/mcp](https://lotlytics.us/mcp) — MCP documentation
- [lotlytics.us/api](https://lotlytics.us/api) — REST API docs

---

## License

MIT
