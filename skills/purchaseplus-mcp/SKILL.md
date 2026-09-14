---
name: purchaseplus-mcp
description: Use when reading or changing PurchasePlus data through the hosted OAuth purchaser MCP (https://purchaseplus.com/mcp). Covers requisitions, purchase orders, receiving notes, invoices, credit notes, statements, products, suppliers, reports, buy lists, and stocktakes.
---

# PurchasePlus MCP

## Auth

Auth is OAuth. Organisation is set at authorize time; user must re-authorize to switch org.

## Writes

Draft requisitions, buy-list add, and report export. Confirm before writes. Cite IDs after actions.

Ask when supplier/product is ambiguous. Never invent IDs.

Point UI how-to questions at purchaseplus-how-to / https://learn.purchaseplus.com/

## Pagination

List tools accept first/after pagination plus optional filters and sorts. Get tools take a numeric id.

## Procure-to-pay chain

Requisition → Purchase Order → Receiving Note → Invoice → Credit Note → Statement

## Purchaser tools

- current_user
- list_requisitions / get_requisition
- list_purchase_orders / get_purchase_order
- list_receiving_notes / get_receiving_note
- list_invoices / get_invoice
- list_credit_notes / get_credit_note
- list_statements / get_statement
- list_products
- list_suppliers
- list_reports / get_report / get_report_execution / download_report_execution
- list_buy_lists / get_buy_list
- list_stock_takes / get_stock_take
- create_requisition / update_requisition
- create_requisition_line / update_requisition_line
- reorder_requisition
- create_buy_list_product
- export_report

After export_report, poll get_report_execution until completed, then
download_report_execution. Open downloadUrl as a top-level browser navigation;
do not fetch() (S3 CORS). The tool does not return file bytes.

## Stocktakes

List/inspect only — no create, update, close, import, export, delete, or submit. Do not invent aggregates or spend rankings.

`list_stock_takes` then `get_stock_take`. Filters: `filters.search_text`, `filters.status` (`IN_PROGRESS` / `CLOSED`), `filters.period_month`, `filters.period_year`, `filters.locations`. MCP JSON-RPC is snake_case (`searchText` is rejected).

`get_stock_take` returns header plus paginated `stockCounts`. `quantity` is counted qty; `expectedQuantity` and `variance` are existing stock-count fields, not a new formula. Nested paging: `stock_counts_first` (default 25, max 50) / `stock_counts_after` from `pageInfo.endCursor` when `hasNextPage`. Stock location is on the header (`stockLocation { id name }`) and on count `stockLevel.location`.
