# Install PurchasePlus in Cursor

1. In Cursor, open **Plugins** / **Customize**.
2. Add the GitHub repo `https://github.com/marketboomer/purchaseplus-mcp` (or install from that git URL). Skills and the MCP connection ship with the plugin.
3. On first use, Cursor opens PurchasePlus sign-in so you can complete OAuth with your account.

## Manual fallback

If you prefer to add the server yourself, put this in `~/.cursor/mcp.json` or the project `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "purchaseplus": {
      "url": "https://purchaseplus.com/mcp"
    }
  }
}
```

Sign-in is OAuth only. This fallback does not install the plugin. Call `list_plugin_skills` first and follow those texts.
