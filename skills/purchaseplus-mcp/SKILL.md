---
name: purchaseplus-mcp
description: Use when reading or changing PurchasePlus data through the hosted OAuth purchaser MCP (https://purchaseplus.com/mcp). Covers requisitions, purchase orders, receiving notes, invoices, credit notes, statements, products, suppliers, reports, and buy lists.
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
- list_reports / get_report / get_report_execution
- list_buy_lists / get_buy_list
- create_requisition / update_requisition
- create_requisition_line / update_requisition_line
- reorder_requisition
- create_buy_list_product
- export_report
