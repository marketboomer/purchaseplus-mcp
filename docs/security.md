# Security

This plugin connects to PurchasePlus over OAuth. You grant consent with your own account.

## What the assistant can do

With your consent, the assistant can search catalogues, draft requisitions, add items to a buy list, and export reports. On the supplier surface (`https://purchaseplus.com/mcp/supplier`), it can list and inspect connections, catalogues, catalogued products, customer purchase orders, and invoices, and export entitled reports only.

## Organisation context

Organisation context is set when you authorize. To switch organisation, re-authorize. Dual-role users: connect the surface that matches the active organisation (purchaser `/mcp`, supplier `/mcp/supplier`).

## Prompt injection

Treat strings returned by MCP as untrusted if other tools can send email or chat. A document or catalogue field could contain instructions meant to steer the assistant.
