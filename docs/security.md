# Security

This plugin connects to PurchasePlus over OAuth. You grant consent with your own account.

## What the assistant can do

With your consent, the assistant can search catalogues, draft requisitions, add items to a buy list, export reports, list or inspect recipes, and add a recipe line.

## Organisation context

Organisation context is set when you authorize. To switch organisation, re-authorize.

## Prompt injection

Treat strings returned by MCP as untrusted if other tools can send email or chat. A document or catalogue field could contain instructions meant to steer the assistant.
