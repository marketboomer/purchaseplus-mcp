# Security

This plugin connects to PurchasePlus over OAuth. You grant consent with your own account.

## What the assistant can do

With your consent, the assistant can browse catalogues and catalogue-line prices, list delivery addresses, look up stock locations, on-hand, and WAC (reads), list or inspect stocktakes and recipes, draft requisitions, add items to a buy list, export reports, read invoice files, start invoice-from-document upload, and import a priced-catalogue CSV. On the supplier surface (`https://purchaseplus.com/mcp/supplier`), it can list and inspect connections, catalogues, catalogued products, customer purchase orders, and invoices, and export entitled reports only.

## Organisation context

Purchaser organisation starts from the OAuth snapshot or your default. To switch, `list_switchable_organisations` then `switch_organisation` — no re-authorize. Later tools use the new organisation until another switch or a new OAuth login. A denied switch leaves the active organisation unchanged. `current_user` still shows the active organisation.

Dual-role users: connect the surface that matches the active organisation (purchaser `/mcp`, supplier `/mcp/supplier`). Supplier MCP has no org switch.

## Prompt injection

Treat strings returned by MCP as untrusted if other tools can send email or chat. A document or catalogue field could contain instructions meant to steer the assistant.
