# PurchasePlus Agent Plugin

Official Marketboomer plugin and connection package for PurchasePlus AI assistants.

Use it to connect Cursor, Claude, ChatGPT, and other MCP-capable clients to PurchasePlus. With purchaser access, an assistant can search catalogues, draft requisitions, add items to a buy list, and export reports. With supplier access, an assistant can list and inspect connections, catalogues, catalogued products, customer purchase orders, and invoices, and export entitled reports.

## Sign-in

Authentication is OAuth only. Sign in with your PurchasePlus account.

Purchaser MCP: [https://purchaseplus.com/mcp](https://purchaseplus.com/mcp)

Supplier MCP: [https://purchaseplus.com/mcp/supplier](https://purchaseplus.com/mcp/supplier)

Dual-role users: connect the surface that matches the active organisation. Organisation is the authorize snapshot (or the personal API key default org). There is no org switch.

Supplier MCP is list/inspect plus entitled report export only.

## Skills

Skills ship with the plugin. They tell agents to fetch live how-to documentation from [https://learn.purchaseplus.com/](https://learn.purchaseplus.com/).

## Install

- [Cursor](docs/install-cursor.md)
- [Claude](docs/install-claude.md)
- [ChatGPT](docs/install-chatgpt.md)

See [Security](docs/security.md).

## License

MIT. Copyright PurchasePlus.
