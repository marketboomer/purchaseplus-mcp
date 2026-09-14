# Install PurchasePlus in Claude

## Claude.ai and Claude Desktop

1. Open **Settings → Connectors**.
2. Choose **Add custom connector**.
3. Enter `https://purchaseplus.com/mcp`.
4. Complete OAuth in the browser.

These connectors do not get bundled skills. Call `list_plugin_skills` first and follow those texts.

## Claude Code

Add the marketplace, then install the plugin:

```text
/plugin marketplace add marketboomer/purchaseplus-mcp
/plugin install purchaseplus@purchaseplus
```

Skills come with the plugin.
