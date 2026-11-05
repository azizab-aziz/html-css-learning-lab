# 06 — Tables

Practicing how to present data that has real rows and columns, so it can be
compared and read by anyone, including screen reader users.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | An inventory table with six products |
| `advanced.html` | Advanced | A monthly inventory report grouped by category, with totals |
| `extra-advanced.html` | Extra advanced | Four warehouse tables on one page, styled by its own stylesheet |
| `extra-advanced.css` | Extra advanced | A dark-theme stylesheet: borders, font, and padding for the tables |
| `schedule.html` | Own exercise | Two exam timetables (weeks 1 and 2), outside the warehouse theme |
| `schedule.css` | Own exercise | A light-theme stylesheet for the schedule page |

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

## Extra-advanced version: four tables and a stylesheet

**Goal:** practice several table shapes on one page, and see tables with borders for the first time.

**A deliberate exception:** the plan is HTML first and CSS later. This page is linked to its own file, `extra-advanced.css`, so the tables can be seen with borders. Only the pages in this topic that have their own stylesheet use CSS so far.

The stylesheet gives every table part a light border, a monospace font, collapsed borders, and padding. A few small rules were added for a dark page background and spacing between tables.

| Table | Topic | What it practices |
|---|---|---|
| 1 | Daily warehouse schedule | `<time>` for time ranges and `rowspan` on "All other times" |
| 2 | Weekly staff roster | Column headers and row headers together, with `&nbsp;` in the empty corner cell |
| 3 | Delivery log | `rowspan` on a supplier with two deliveries, and a totals row in `<tfoot>` |
| 4 | Shelf zone capacity | Numbers that add up, with a total row in `<tfoot>` |

Elements used on the page: `<table>`, `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, `<th scope="col">`, `<th scope="row">`, `<td>`, `<time>`, and `&nbsp;`.

## Own exercise: exam schedule

**Goal:** apply the table skills to real data that has nothing to do with the warehouse: a two-week exam timetable.

**Another deliberate exception:** like the extra-advanced page, this page is linked to its own stylesheet, `schedule.css`. It uses a light page (`#ddd9d9` background, near-black text and borders), where `extra-advanced.css` uses a dark one.

| Table | Content | What it practices |
|---|---|---|
| 1 | Week 1 exams: Monday, Tuesday, Wednesday, Friday | `<time>` pairs for time ranges, the day as `<th scope="row">`, and a `<tfoot>` note with `colspan="3"` |
| 2 | Week 2 exams | `rowspan="2"` on a row header: Tuesday has two exams, so its day cell covers both rows |

How the page is built:

- Each table sits in its own `<section>` with an `<h2>`
- Every table has a `<caption>`, a `<thead>` with three columns (Day, Time, Exam), a `<tbody>`, and a `<tfoot>`
- The page has a `<header>` and a `<main>`
- In table 2, the second Tuesday row has only two cells, because the day header reaches down from the row above. Every row still adds up to three columns.

## What improved from intermediate to advanced

- **Structure:** from one flat table to a report with groups and a summary section
- **Accessibility:** `scope="col"`, `scope="row"`, and `scope="rowgroup"` let a screen reader announce "Electronics, Widescreen Monitor, Quantity, 8"
- **Meaning:** units live in the headers, and status is text, so nothing depends on color
- **Real logic:** the totals come from the rows, and the reorder rule is written next to the table
- **Clarity:** abbreviations and terms are explained on the page

## What improved from advanced to extra-advanced

- **Variety:** four different tables on one page, each with a different job
- **Merged cells:** `rowspan` joins cells downward, where `colspan` joined them across
- **Seeing the structure:** borders make rows, columns, and merged cells visible, so mistakes show up quickly
- **Time and totals:** times use `<time>`, and each footer row carries a total or a note

## What the exam schedule added

- **Different subject:** the same table structure works for any data with rows and columns, not only inventory
- **`rowspan` on a row header:** one `<th scope="row" rowspan="2">` covers two rows, where earlier `rowspan` was
