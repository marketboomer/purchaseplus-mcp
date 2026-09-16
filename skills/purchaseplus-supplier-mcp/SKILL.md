---
name: purchaseplus-supplier-mcp
description: Use when reading supplier-organisation PurchasePlus data through the hosted OAuth supplier MCP (https://purchaseplus.com/mcp/supplier). Covers connections, catalogues, catalogued products, customer purchase orders, invoices, and entitled report export.
---

# PurchasePlus Supplier MCP

## Auth

Auth is OAuth to https://purchaseplus.com/mcp/supplier (same mcp:read as purchaser). Organisation is the authorize snapshot, or the personal API key default org. There is no org switch on this surface.

Dual-role: use this skill and `/mcp/supplier` for the supplier org. Use purchaseplus-mcp / https://purchaseplus.com/mcp for the purchaser org.

## Writes

List/inspect plus entitled report export only. Confirm before export_report. Cite IDs after actions. Never invent IDs.

Never approve, send, or hard-delete. Do not invent rankings, fill rate, or with/without-catalogue filters.

How-to → purchaseplus-how-to / https://learn.purchaseplus.com/ (For Suppliers).

Route-away (marketshare packs, fee-reconcile, commercials): decline and point at the help centre or list_reports.

## Pagination

List tools accept first/after pagination plus optional filters and sorts. Get tools take a numeric id.

## Supplier tools

- current_user
- list_connections / get_connection / list_connection_catalogs
- list_catalogs / get_catalog / list_catalog_products / get_catalog_product
- list_purchase_orders / get_purchase_order
- list_invoices / get_invoice
- list_reports / get_report / export_report / get_report_execution / download_report_execution

After export_report, poll get_report_execution until completed, then
download_report_execution. Open downloadUrl as a top-level browser navigation;
do not fetch() (S3 CORS). The tool does not return file bytes.
