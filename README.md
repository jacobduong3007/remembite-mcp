# Remembite MCP connector

Remembite is a food log your AI writes to. You tell Claude or ChatGPT what you ate. Your AI works out the grams, calories, protein, carbs and fat, and Remembite saves the meal with the values it sends. If an item's macros add up to more calories than the item, or its calories are far from a USDA-based reference food, nothing is saved and your AI asks you first.

- Website: https://remembite.com
- Setup guide: https://remembite.com/connect
- MCP endpoint: `https://remembite.com/mcp` (Streamable HTTP)
- Auth: OAuth (scopes `meal:read`, `meal:write`). Clients that cannot sign in can use a personal access token, see https://remembite.com/connect
- Official MCP Registry name: `com.remembite/remembite`
- Price: free, no ads

This repository holds the public listing metadata (`server.json`) and setup notes. Remembite is a hosted remote MCP server: there is nothing to install or run on your own computer, and the server code is not published here.

## Connect

**Claude:** open Customize > Connectors, choose + Add, then Add custom connector, paste `https://remembite.com/mcp`, and sign in. Steps may change; https://remembite.com/connect has the current ones.

**ChatGPT (beta, via developer mode):** see https://remembite.com/connect.

**Other MCP clients:** add a remote server with the URL `https://remembite.com/mcp`. A POST without a token returns `401` with a `WWW-Authenticate` header that points to the OAuth metadata (`resource_metadata`). This is expected.

## Tools

| Group | Tools |
|---|---|
| Meals | `log_meal`, `resolve_meal`, `update_meal`, `update_meal_item`, `delete_meal`, `repeat_meal`, `save_template`, `search_food`, `lookup_barcode` |
| Reading your log | `get_day`, `get_history`, `get_summary` |
| Goals | `get_goals`, `set_goals` |
| Food memory | `remember_food`, `list_memory`, `forget_memory` |
| Water and weight | `log_water`, `delete_water`, `log_weight`, `get_weight`, `update_weight`, `delete_weight` |

The live list is in the server card: https://remembite.com/.well-known/mcp/server-card.json

## Privacy and support

- Privacy policy: https://remembite.com/privacy
- Terms: https://remembite.com/terms (13 or older)
- Support: https://remembite.com/support

Remembite is not medical advice and does not replace a doctor or dietitian.
