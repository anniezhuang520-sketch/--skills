---
name: payment-use-invoice
description: Dynamically create a Plantation Shutters Payment Use Invoice from the latest `[container] Order List & QTY` workbook, the fixed Y070 invoice template, and the fixed finished-window price table. Use when the user asks to make, remake, validate, or update a Payment Use Invoice in the 制作发票 workspace. Do not use for unrelated invoices or general bookkeeping.
---

# Payment Use Invoice

Create one editable `.xlsx` invoice for the currently supplied container. Treat every run as fresh: rescan the source folder, reread the order workbook, and recalculate all classifications and amounts. Never reuse a prior container number, row count, order list, or calculated result.

## Required workflow

1. Use the spreadsheet workflow for workbook authoring and verification.
2. Scan `原始数据` for the fixed Y070 template, fixed price workbook, and latest valid `[container] Order List & QTY` workbook.
3. If more than one dynamic order workbook could reasonably be current, stop and ask which container to process. Never combine containers.
4. Extract the container from the selected filename and derive the Invoice Number and output filename from it.
5. If that output already exists, do not overwrite it without user confirmation.
6. Read every worksheet and identify the actual header row, order sheet, populated order rows, and relevant fields. Do not assume a fixed sheet name or last row.
7. Read [references/invoice-rules.md](references/invoice-rules.md) before building or validating the invoice.
8. Start from a copy of Y070 and preserve layout, styles, formulas, page setup, headers/footers, merges, images, and fixed commercial information except for required replacements.
9. Recalculate in Excel or a compatible engine, independently reconcile confirmed amounts, scan formula errors, and visually review every printed page.
10. Leave only the requested invoice in the project root. Never modify anything inside `原始数据`.

## Output

Save exactly `Original Invoice of [container] - Payment Use.xlsx`.

Report the selected source file, container and Invoice Number, order/category counts, TBC items and reasons, accessories and special-window summaries, Date/ETD, remark consistency, confirmed subtotal, exclusions, visual verification, and final file path.
