---
name: purchaseplus-mcp
description: Use when reading or changing PurchasePlus data through the hosted OAuth purchaser MCP (https://purchaseplus.com/mcp). Covers requisitions, purchase orders, receiving notes, invoices, invoice files, credit notes, statements, products, suppliers, catalogues, reports, buy lists, recipes, inventory, stocktakes, invoice-from-document upload, and priced-catalogue CSV import.
---

# PurchasePlus MCP

## Auth

Auth is OAuth. Organisation starts from the OAuth snapshot or default. Call list_switchable_organisations (id, name, current) then switch_organisation with organisation_id. Later tools use the new org until another switch or a new OAuth login. Denied switch does not change org. Nothing destructive. Supplier-org users should use purchaseplus-supplier-mcp / https://purchaseplus.com/mcp/supplier.

## Writes

Draft requisitions, buy-list add, report export, recipe add-line (live, like buy-list add), invoice-from-document upload, and priced-catalogue CSV import. Confirm before writes. Cite IDs after actions.

File uploads: pass an HTTPS `file_url`. Never paste file contents or base64 into the tool.

Ask when supplier/product is ambiguous. Never invent IDs.

Before create_requisition / reorder_requisition, call list_delivery_addresses and use a returned id as delivery_address_id. Do not map ordinals ("1", "#7") to cities.

Point UI how-to questions at purchaseplus-how-to / https://learn.purchaseplus.com/

## Pagination

List tools accept first/after pagination plus optional filters and sorts. Get
tools take a numeric id; inventory gets also page nested stockLevels
(stock_levels_first / stock_levels_after from pageInfo.endCursor when
hasNextPage).

## Procure-to-pay chain

Requisition → Purchase Order → Receiving Note → Invoice → Credit Note → Statement

## Inventory

List/inspect only. No create, adjust, count, transfer, delete, or stock move.
Do not invent IDs, aggregates, or spend rankings.

- Location: list_stock_locations then get_stock_location. Nested stockLevels
  have balanceQuantity (on-hand) and unitValue (WAC where Inventory shows it).
- Named product: list_stock_items with filters.search_text (plus paging) then
  get_stock_item. Returns totalBalanceQuantity and per-location balanceQuantity /
  unitValue. averageUnitValue is the existing stock-item field (unweighted
  average of unit values — not a new weighted rollup).
- If stockLevels pageInfo.hasNextPage, pass stock_levels_after so on-hand/WAC
  is not under-reported.

## Stocktakes

List/inspect only — no create, update, close, import, export, delete, or submit. Do not invent aggregates or spend rankings.

`list_stock_takes` then `get_stock_take`. Filters: `filters.search_text`, `filters.status` (`IN_PROGRESS` / `CLOSED`), `filters.period_month`, `filters.period_year`, `filters.locations`. MCP JSON-RPC is snake_case (`searchText` is rejected).

`get_stock_take` returns header plus paginated `stockCounts`. `quantity` is counted qty; `expectedQuantity` and `variance` are existing stock-count fields, not a new formula. Nested paging: `stock_counts_first` (default 25, max 50) / `stock_counts_after` from `pageInfo.endCursor` when `hasNextPage`. Stock location is on the header (`stockLocation { id name }`) and on count `stockLevel.location`.

## Purchaser tools

Connectors that do not install the plugin should call list_plugin_skills first and follow those texts.

- list_plugin_skills
- current_user
- list_switchable_organisations / switch_organisation
- list_requisitions / get_requisition
- list_purchase_orders / get_purchase_order
- list_receiving_notes / get_receiving_note
- list_invoices / get_invoice
- list_invoice_files / get_invoice_file
- list_credit_notes / get_credit_note
- list_statements / get_statement
- list_products
- list_suppliers
- list_catalogs / get_catalog / list_catalog_products
- list_reports / get_report / get_report_execution / download_report_execution
- list_buy_lists / get_buy_list
- list_delivery_addresses
- list_stock_locations / get_stock_location
- list_stock_items / get_stock_item
- list_stock_takes / get_stock_take
- list_recipes / get_recipe
- create_requisition / update_requisition
- create_requisition_line / update_requisition_line
- reorder_requisition
- create_buy_list_product
- create_recipe_line
- export_report
- create_invoice_from_document
- create_catalogue_import

After export_report, poll get_report_execution until completed, then
download_report_execution. Open downloadUrl as a top-level browser navigation;
do not fetch() (S3 CORS). The tool does not return file bytes.

Invoice files (invoice screen only — not receiving-note files):
list_invoice_files then get_invoice_file. Omit file_id (or use "supplier")
for the supplier invoice PDF as contentBase64 so the assistant can read it.
Do not OCR or invent size codes. User-added attachments return downloadUrl
and howToDownload only; open that URL in a top-level browser navigation and
do not inline those bytes.

`create_invoice_from_document` starts the app's create-invoice-from-uploaded-document
action. Requires `file_url` (HTTPS PDF). Optional supplier_id / document_number /
currency. Not for attaching a file to an existing invoice. Invoice birth is async
as in the app; there is no extra confirm.

`create_catalogue_import` starts a priced-catalogue CSV import. Requires `file_url`
(HTTPS CSV) and `catalogue_id`. Not buy lists or other import kinds. Follow-up is
in the app.

Catalogues are list/inspect only. list_catalogs → get_catalog (header
only) → list_catalog_products (needs catalogue_id; lines and prices).
Named product: filters.search_text. Prices are catalogue-line
sellUnitPrice / sellUnitTax / sellUnitTaxPercentage, not buy-list
availableQuotes. Do not invent cheapest-price or UOM comparisons.

Recipes are list/inspect plus add-line only. list_recipes browses; get_recipe
inspects one. create_recipe_line is the same live add as the Recipes UI.
