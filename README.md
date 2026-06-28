# IndustryLens MCP

> Live B2B competitive intelligence as an [MCP](https://modelcontextprotocol.io) server, competitor moves, head-to-head comparisons, and published market reports, available directly inside Claude, Cursor, ChatGPT, and any MCP-compatible app.

**Full documentation and one-click install guides:** https://industry-lens.com/mcp

This repository hosts the public documentation and connection manifest for the IndustryLens MCP server. The server implementation is private; everything you need to *use* the server is here and on the docs site above.

## Connect

Public endpoint (no account required):

```
https://api.industry-lens.com/mcp/public
```

Transport: **Streamable HTTP**. Add it to any MCP client. Example (Claude Desktop / generic `mcp.json`):

```json
{
  "mcpServers": {
    "industrylens": {
      "type": "streamable-http",
      "url": "https://api.industry-lens.com/mcp/public"
    }
  }
}
```

Per-client walkthroughs (Claude Desktop, Claude Code, Cursor, VS Code, ChatGPT, Gemini) with screenshots: **https://industry-lens.com/mcp**

## Tools (public tier)

| Tool | What it does |
|------|--------------|
| `get_competitive_profile` | Profile for a company: firmographics, recent strategic moves (was → now, with the real analysis date), and linked reports. |
| `list_competitor_moves` | A competitor's recent tracked moves, newest first. |
| `find_competitors` | Companies competing with a given company, in the same tracked market. |
| `list_reports` | Browse published competitive-intelligence reports (filter by industry / role). |
| `get_report` | Full body of a published report by slug. |
| `list_comparisons` | Browse head-to-head competitor comparisons. |
| `get_comparison` | Full structured body of a comparison by slug. |
| `subscribe_to_newsletter` | Subscribe to the weekly intelligence briefing (with consent). |

The public tier returns facts about companies and the existence of strategic shifts (with real analysis dates), never a customer's private data. Deeper, per-account intelligence (full reasoning, recommendations, weekly briefings) lives in an IndustryLens account: https://industry-lens.com/pricing

## Registry

This server is published to the official MCP Registry as `com.industry-lens/mcp-public`. See [`server.json`](./server.json).

## Links

- Documentation & install: https://industry-lens.com/mcp
- Reports: https://industry-lens.com/reports
- Comparisons: https://industry-lens.com/compare
- Website: https://industry-lens.com
