# PurchasePlus Agent Plugin

Official Marketboomer plugin and connection package for PurchasePlus AI assistants.

Use it to connect Cursor, Claude, ChatGPT, and other MCP-capable clients to PurchasePlus. With purchaser access, an assistant can browse catalogues and catalogue-line prices, list delivery addresses, look up inventory (stock locations, on-hand, and WAC), list or inspect stocktakes and recipes, draft requisitions, add items to a buy list, export reports, read invoice files, start invoice-from-document upload, and import a priced-catalogue CSV (HTTPS file URL — never paste the file into chat). With supplier access, an assistant can list and inspect connections, catalogues, catalogued products, customer purchase orders, and invoices, and export entitled reports.

## Sign-in

Authentication is OAuth only. Sign in with your PurchasePlus account.

Purchaser MCP: [https://purchaseplus.com/mcp](https://purchaseplus.com/mcp)

Supplier MCP: [https://purchaseplus.com/mcp/supplier](https://purchaseplus.com/mcp/supplier)

Dual-role users: connect the surface that matches the active organisation.

Purchaser organisation starts from the OAuth snapshot or your default. Switch with `list_switchable_organisations` then `switch_organisation` — no re-authorize. Supplier MCP has no org switch.

Supplier MCP is list/inspect plus entitled report export only.

## Skills

Skills ship with the plugin. They tell agents to fetch live how-to documentation from [https://learn.purchaseplus.com/](https://learn.purchaseplus.com/). Clients that do not install the plugin should fetch skills on demand via `list_plugin_skills`. It returns named full texts: purchaseplus (router), purchaseplus-how-to (help centre), purchaseplus-mcp (tool-use), purchaseplus-supplier-mcp (supplier tool-use).

## Install

- [Cursor](docs/install-cursor.md)
- [Claude](docs/install-claude.md)
- [ChatGPT](docs/install-chatgpt.md)

See [Security](docs/security.md).

## License

MIT. Copyright PurchasePlus.
