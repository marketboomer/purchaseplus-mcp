---
name: purchaseplus-mcp
description: Use when reading or changing PurchasePlus data through the hosted OAuth purchaser MCP (https://purchaseplus.com/mcp). Covers requisitions, purchase orders, receiving notes, invoices, credit notes, statements, products, suppliers, reports, buy lists, and recipes.
---

# PurchasePlus MCP

## Auth

Auth is OAuth. Organisation is set at authorize time; user must re-authorize to switch org.

## Writes

Draft requisitions, buy-list add, report export, and recipe add-line (live, like buy-list add). Confirm before writes. Cite IDs after actions.

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
- list_recipes / get_recipe
- create_requisition / update_requisition
- create_requisition_line / update_requisition_line
- reorder_requisition
- create_buy_list_product
- create_recipe_line
- export_report

After export_report, poll get_report_execution until completed, then
download_report_execution. Open downloadUrl as a top-level browser navigation;
do not fetch() (S3 CORS). The tool does not return file bytes.

Recipes are list/inspect plus add-line only. list_recipes browses; get_recipe
inspects one. create_recipe_line is the same live add as the Recipes UI.
