# Install PurchasePlus in Cursor

1. In Cursor, open **Plugins** / **Customize**.
2. Add the GitHub repo `https://github.com/marketboomer/purchaseplus-mcp` (or install from that git URL). Skills and the MCP connections ship with the plugin.
3. On first use, Cursor opens PurchasePlus sign-in so you can complete OAuth with your account.

Dual-role users: connect the surface that matches the active organisation (`https://purchaseplus.com/mcp` for purchaser, `https://purchaseplus.com/mcp/supplier` for supplier). Supplier MCP is list/inspect plus entitled report export only.

## Manual fallback

If you prefer to add the server yourself, put this in `~/.cursor/mcp.json` or the project `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "purchaseplus": {
      "url": "https://purchaseplus.com/mcp"
    },
    "purchaseplus-supplier": {
      "url": "https://purchaseplus.com/mcp/supplier"
    }
  }
}
```

Sign-in is OAuth only.
