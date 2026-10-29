# IndustryLens

Use the IndustryLens tools when the user asks about a B2B SaaS company's competitors, recent strategic moves, pricing or packaging changes, or the shape of a market.

- Start with `get_competitive_profile` (domain or name) for a company overview, or `find_competitors` for who competes with it.
- Use `list_competitor_moves` or `get_competitor_moves_diff` for what a company has done recently, and `get_pricing_changes` for pricing.
- Use `list_markets` and `get_market_landscape` for a whole market, and `list_reports` / `list_comparisons` to find published reports and head-to-head comparisons.
- Every fact has a date and a source link. Quote them back so the user can check.
- A `covered: false` result means IndustryLens does not track that company publicly yet. Say so; don't guess.
- Only call `subscribe_to_newsletter` when the user explicitly asks to subscribe.
