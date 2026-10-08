# 03 — Lists

Practicing how to group related content with the right list type.
The main skill in this topic is choosing the list by **meaning**, not by looks.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A warehouse procedures page with four list types |
| `advanced.html` | Advanced | A mini operations manual that combines every list type |

## Choosing the list type

| Content | List type | Why |
|---|---|---|
| Warehouse features, safety checklist | `<ul>` | The order does not matter |
| Receiving and stock movement steps | `<ol>` | Step 2 only makes sense after step 1 |
| Categories and departments | Nested `<ul>` | Sub-items belong to a parent item |
| Technical terms | `<dl>` with `<dt>` and `<dd>` | Each entry is a term plus its definition |

## Intermediate version

**Goal:** use each basic list type correctly on one page.

- An unordered list of warehouse features
- An ordered list showing how to receive a product
- A nested list of product categories (Electronics with Laptops and Monitors, Office Supplies with Desks and Chairs)
- A description list explaining SKU, stock level, and reorder threshold

## Advanced version

**Goal:** build a realistic operations manual where every list type has a clear job.

Sections:

1. Table of contents
2. Receiving procedure
3. Stock movement procedure
4. Safety checklist
5. Roles and responsibilities
6. Glossary
7. Related pages

- The table of contents is an ordered list of links. Each link jumps to a section `id` on the same page.
- The receiving and stock movement procedures are ordered lists because the sequence matters.
- The safety checklist is an unordered list because the items are independent.
- Departments and their responsibilities form a nested list.
- The glossary is a description list.
- The related pages are a list of links to the documentation pages from topic 02.

## What improved from intermediate to advanced

- **Purpose:** from demonstrating list syntax to using lists to organize a real document
- **Navigation:** a linked table of contents lets the reader jump to any section
- **Decision making:** each list type is chosen because of what the content means
- **Connection:** the manual links back to the pages built in topic 02

## What I learned

- `<ul>` for content where order does not matter, `<ol>` where it does
- A nested list goes **inside** the parent `<li>`, not after it
- `<dl>` is for term and definition pairs, which is a different shape from a list of items
- A table of contents is an ordered list because it follows the order of the page
- Never type bullet characters by hand. A real `<ul>` gives screen readers the list structure.

## Known issues / next improvements

- [ ] Add CSS later to control bullet style and spacing
- [ ] Check that every link in "Related pages" opens the right file
- [ ] Add a "Back to top" link to the long manual