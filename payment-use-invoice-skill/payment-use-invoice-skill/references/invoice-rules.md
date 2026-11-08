# Payment Use Invoice rules

## Sources

- Y070 invoice: format and fixed accessory/Fascia data only.
- Current Order List & QTY: order identity, sequence, quantities, font-color classification, materials, notes, accessories, and special-window evidence.
- Finished-window price workbook: the only source for normal shutter rates.

Never modify source workbooks or substitute historic invoice data.

## Header and dates

- Company: `XIAMEN SUNLAND INTERNATIONAL TRADE CO.,LTD.`
- Product heading: `PVC SHUTTER`
- Invoice Number and P.O. number: current container extracted from the order filename.
- Date: execution date in Asia/Shanghai, formatted like Y070.
- ETD: Date plus five calendar days, retaining the template suffix such as `(Subject to B/L)`.
- Apply yellow fill only to the ETD date cell, not the Date cell.

## Normal orders

- Preserve current top-to-bottom order exactly through the row before `Fascia (PVC )`.
- Clean Chinese parenthetical suffixes from the displayed order number only.
- Original black order font = PVC; original red order font = Wood. Preserve black/red font.
- Original IDs beginning with `P` or `p` receive purple fill in column C only.
- For Wood explicitly marked Pine/松木 in source H, append ` Pine`; blank Wood material defaults to Basswood for pricing only.
- If source I says `工厂免费重做`, prefix `Free replacement:`, set rate and amount to zero, and preserve its position.

### Immutable remarks

For every normal order, copy source H → invoice G and source I → invoice H exactly. Require equality including blanks, spaces, punctuation, case, line breaks, Chinese/English wording, and unexpanded item ranges. Analysis may read these cells but never rewrite them.

## Pricing

Read actual rates from the price workbook on every run.

- PVC: classify only normal versus full Gear Rod. Do not use material or three-digit color logic.
- Wood: classify Gear Rod, wood type, and final three-digit color code. Codes beginning with 2 are Stained; other valid codes are Standard Color.
- Free replacement overrides all pricing and is zero.
- Partial Gear Rod or unsupported/ambiguous combinations are `TBC`; fill the rate yellow and leave amount blank.
- A P-order that is TBC keeps purple in C; use yellow on rate and another relevant cell for the partial-Gear warning.
- Exclude blank reserved rows and unknown amounts from the confirmed subtotal.

## Accessories and special windows

Build these sections from current notes, not a historic hardcoded list. Expand item ranges only in these independent sections.

- Lock: include order, expanded items, and explicit lock/set quantity.
- Hidden hinges: include order, expanded item scope when stated, and source hinge quantity.
- Place cutout before arch-related entries.
- Use exactly `cutout window`, `sunburst window`, `arch window`, and `Octagon Window`.
- Exclude every Free replacement order from Lock, Hidden Hinges, Cutout, Arch, Sunburst, and Octagon sections. Keep its normal-order row and raw G/H remarks.
- Never infer accessory quantities from item counts unless the source explicitly supports it.

## Fixed and reserved rows

After normal orders, retain Y070 values and formulas for:

1. `Fascia (PVC )`
2. `Extra 3 boxes(30 pcs) fascia, Snow White`
3. `Extra 1 box(15 pcs) buildout, Snow White`

Fill the full invoice-table range of the first Fascia row yellow. From that row onward, G/H stay blank.

Then add, in order:

1. exactly two fully blank yellow rows;
2. exactly five yellow rows containing `extra buildout for 4" Crown Out frame`, rate `0.58`, blank quantity, and blank amount.

These seven rows retain borders and standard height, use no purple, and contribute nothing until quantities are entered.

## Validation

- Use Y070 standard row height for ordinary rows; increase only genuinely long description rows without changing column widths.
- Keep A4 portrait printing, one page wide, and a compact page count appropriate to content.
- Verify exact order sequence, no missing/duplicate orders, fonts, fills, fixed rows, formulas, print area, merges, and no formula errors.
- Compare every source H/I value with invoice G/H and report 100% consistency before delivery.
- Visually inspect all pages for clipped or overlapping content.
