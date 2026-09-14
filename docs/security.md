# Security

This plugin connects to PurchasePlus over OAuth. You grant consent with your own account.

## What the assistant can do

With your consent, the assistant can search catalogues, draft requisitions, add items to a buy list, and export reports.

## Organisation context

Organisation starts from the OAuth snapshot or your default. To switch, list_switchable_organisations then switch_organisation — no re-authorize. Later tools use the new organisation until another switch or a new OAuth login. A denied switch leaves the active organisation unchanged. current_user still shows the active organisation.

## Prompt injection

Treat strings returned by MCP as untrusted if other tools can send email or chat. A document or catalogue field could contain instructions meant to steer the assistant.
