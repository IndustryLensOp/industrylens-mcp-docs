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

### Quick install

| App | How |
|-----|-----|
| Claude (web, desktop, mobile) | Add from the [Claude Connectors Directory](https://claude.ai/directory/industrylens) (signs in to your IndustryLens account), or add a custom connector with the public URL above. |
| Claude Code | `claude mcp add industrylens --transport http https://api.industry-lens.com/mcp/public` |
| Gemini CLI | `gemini extensions install https://github.com/IndustryLensOp/industrylens-mcp-docs` |
| Cursor | [Cursor Directory](https://cursor.directory/plugins/industrylens-mcp), or add the `mcp.json` above. |
| Any MCP app | Use the public URL above (Streamable HTTP, no auth). |

### Signed-in account endpoint

IndustryLens customers can connect `https://api.industry-lens.com/mcp` (OAuth 2.0 with dynamic client registration). Sign in with your IndustryLens email and the 6-digit code we send, then approve access. This adds your own tracked competitors, battlecards, comparisons and recommendations. Most tools only read data; three save something when you ask (a battlecard note, an intelligence tip for review, a newsletter subscription). Revoke access any time at https://connect.industry-lens.com/keys.

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
| `get_competitor_moves_diff` | A competitor's dated change feed: every detected was → now strategic shift, newest first, each stamped with its real analysis date. |
| `get_pricing_changes` | Recent pricing and packaging changes across tracked markets — change type, severity, materiality score, plain-language summary, and detection date. |
| `list_markets` | The B2B SaaS markets IndustryLens monitors; each item returns a `slug` usable with `get_market_landscape`. |
| `get_market_landscape` | Whole-category map for a market: the published category overview plus every player tracked in it — not a self-selected competitor set. |

## Resources

| Resource | What it does |
|----------|--------------|
| `industrylens://reports` | The catalog of published competitive-intelligence reports as JSON (slug, title, url). |
| `industrylens://reports/{slug}` | Read pattern for a single report: the full body of the report with that slug. |

## Prompts

| Prompt | What it does |
|--------|--------------|
| `market_brief` | Builds a dated, cited competitive brief for one company, using `get_competitive_profile` and `get_competitor_moves_diff`. Argument: `company` (required) — name or domain, e.g. `Apollo` or `apollo.io`. |
| `compare_two` | Produces a head-to-head comparison of two companies, preferring a published IndustryLens comparison and falling back to each company's profile. Arguments: `company_a` and `company_b` (both required) — name or domain. |

The public tier returns facts about companies and the existence of strategic shifts (with real analysis dates), never a customer's private data. Deeper, per-account intelligence (full reasoning, recommendations, weekly briefings) lives in an IndustryLens account: https://industry-lens.com/pricing

## Registry and directories

This server is published to the official MCP Registry as `com.industry-lens/mcp-public` (see [`server.json`](./server.json)). It is also listed in the [Claude Connectors Directory](https://claude.ai/directory/industrylens), [Cursor Directory](https://cursor.directory/plugins/industrylens-mcp), [Glama](https://glama.ai/mcp/servers/IndustryLensOp/industrylens-mcp-docs) and [Smithery](https://smithery.ai/servers/industrylens/mcp). This repo also works as a Gemini CLI extension ([`gemini-extension.json`](./gemini-extension.json)) and an Agent Plugin ([`plugin.json`](./plugin.json), [`mcp.json`](./mcp.json)).

## License

The documentation and manifest in this repository are MIT-licensed (see [`LICENSE`](./LICENSE)). The server implementation is private.

## Links

- Documentation & install: https://industry-lens.com/mcp
- Reports: https://industry-lens.com/reports
- Comparisons: https://industry-lens.com/compare
- Website: https://industry-lens.com
