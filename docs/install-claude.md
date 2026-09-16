# Install PurchasePlus in Claude

## Claude.ai and Claude Desktop

1. Open **Settings → Connectors**.
2. Choose **Add custom connector**.
3. Enter `https://purchaseplus.com/mcp` for purchaser, or `https://purchaseplus.com/mcp/supplier` for supplier.
4. Complete OAuth in the browser.

Dual-role users add the surface that matches the active organisation (or both). Supplier MCP is list/inspect plus entitled report export only.

## Claude Code

Add the marketplace, then install the plugin:

```text
/plugin marketplace add marketboomer/purchaseplus-mcp
/plugin install purchaseplus@purchaseplus
```

Skills come with the plugin.
