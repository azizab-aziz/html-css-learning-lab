# 06 — Tables

Practicing how to present data that has real rows and columns, so it can be
compared and read by anyone, including screen reader users.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | An inventory table with six products |
| `advanced.html` | Advanced | A monthly inventory report grouped by category, with totals |

## When to use a table

Use a table when data has **rows and columns that are compared or cross-referenced**. Do not use one for page layout. Layout is a job for semantic tags and, later, CSS.

## Intermediate version: inventory table

**Goal:** build a clear table with correct headers and a caption.

- Six columns: product, SKU, category, quantity, location, stock status
- `<caption>` as the table's title
- `<thead>` for the header row and `<tbody>` for the data rows
- `<th scope="col">` for column headers
- `<th scope="row">` for the product name, so every cell in a row belongs to a product
- Stock status written as words (In stock, Low stock, Out of stock), not shown by color alone
- The page sits inside `<header>`, `<main>`, and `<footer>`

## Advanced version: monthly inventory report

**Goal:** build a report that is understandable without any styling.

Seven columns: product, SKU, quantity, unit price, stock value, reorder level, reorder status.

| Feature | What it does |
|---|---|
| Descriptive `<caption>` | Names the table and its reporting period |
| Three `<tbody>` groups | One group per category: Electronics, Office supplies, Storage equipment |
| `<th scope="rowgroup" colspan="7">` | A category label that spans the full width and applies to its group |
| `<tfoot>` with three rows | Total units, total stock value, and products needing reorder |
| `colspan` | Makes one cell cover several columns, so every row still adds up to seven |
| Units in column headers | "Quantity (units)" and "Unit price (TND)", so no cell repeats the unit |
| `<abbr title="...">` | Explains SKU in the header |
| `<time datetime="2026-09">` | Marks the reporting month |
| `<dl>` under the table | Explains SKU, TND, stock value, reorder level, and reorder status |

The report logic:

- **Stock value** = quantity multiplied by unit price
- **Reorder status** is "OK" at or above the reorder level, "Reorder" below it, and "Out of stock" at 0
- Totals: 189 units, 39,780 TND, and 4 of 9 products need attention

## What improved from intermediate to advanced

- **Structure:** from one flat table to a report with groups and a summary section
- **Accessibility:** `scope="col"`, `scope="row"`, and `scope="rowgroup"` let a screen reader announce "Electronics, Widescreen Monitor, Quantity, 8"
- **Meaning:** units live in the headers, and status is text, so nothing depends on color
- **Real logic:** the totals come from the rows, and the reorder rule is written next to the table
- **Clarity:** abbreviations and terms are explained on the page

## What I learned

- A `<caption>` belongs to the table, so assistive technology announces it with the data
- `scope` links each data cell to its headers
- Row headers are `<th>`, not `<td>`, when they identify the row
- A table can have several `<tbody>` groups, and one `<tfoot>`
- `colspan` merges cells across columns. Every row must still add up to the same number of columns.
- A missing or extra cell shifts the rest of that row out of line with the headers
- Tables have no borders until CSS. The table must still make sense without them.
- Status shown only by color is invisible to some readers, so write it as words too

## Known issues / next improvements

- [ ] Add borders, spacing, and alignment with CSS later
- [ ] Right-align the number columns with CSS
- [ ] Recalculate the totals if any quantity or price is changed
- [ ] Check that every row in the advanced table adds up to seven columns
- [ ] Wrap the table so it scrolls sideways on small screens (CSS)