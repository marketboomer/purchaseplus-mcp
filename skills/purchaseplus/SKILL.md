---
name: purchaseplus
description: Use when the user mentions PurchasePlus, Purchase Plus, P+, requisitions, purchase orders, POs, invoices, credit notes, receiving notes, suppliers, products, buy lists, stocktakes, or PurchasePlus MCP tools. Routes how-to questions to the help center skill and data/actions to the OAuth MCP skill.
---

# PurchasePlus

Entry-point router. Keep routing short; do not answer from this skill.

## Route

- If the user asks how to do something in the PurchasePlus UI / a how-to / walkthrough: use skill purchaseplus-how-to (fetch live docs from https://learn.purchaseplus.com/)
- If the user wants to read or change PurchasePlus data: use skill purchaseplus-mcp

## Rules

- Never invent IDs; confirm writes; cite tool results
- Never answer how-to from memory
