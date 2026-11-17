# 08 — Mini-page

Combining everything from topics 01 to 07 into one realistic page, then into a small
multi-page site. Theme: the **Warehouse Management Learning Lab**, now presented
as a fictional product called **StockFlow**.

**Status:** intermediate and advanced versions done. CSS, JavaScript, and React
versions are planned for later.

## Files

```
08-mini-page/
├── intermediate.html
├── assets/
│   └── favicon.ico
└── advanced/
    ├── index.html
    ├── products.html
    ├── pricing.html
    └── contact.html
```

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | One product page with navigation, introduction, features, image, inventory table, and a demo form |
| `advanced/index.html` | Advanced | A landing page with eight sections, a workflow article, a report table, a FAQ, and a long demo form |
| `advanced/products.html` | Advanced | A catalog of six products with images, grouped into two categories |
| `advanced/pricing.html` | Advanced | A comparison table of three plans, with a FAQ |
| `advanced/contact.html` | Advanced | Contact methods, a support-hours table, and an address |
| `assets/favicon.ico` | Shared | The browser tab icon, used by every advanced page |

The images are not copied here. Every page points to `04-images/images/`, so each
photo exists in only one place.

## Intermediate version: warehouse product page

**Goal:** prove that the separate skills work together on one page.

| Section | What it contains | Skill from |
|---|---|---|
| Header | Brand link and a navigation menu | 02 Links, 05 Semantic tags |
| Introduction | The `<h1>` and two paragraphs | 01 Paragraphs |
| Features | An unordered list and a captioned image | 03 Lists, 04 Images |
| Inventory | A table of four products with six columns | 06 Tables |
| Request a demo | A form with five fields | 07 Forms |
| Footer | A credit line | 05 Semantic tags |

- The menu uses anchor links (`#features`, `#inventory`), because the page is a single file
- Each section has an `id` that matches its menu link, and `aria-labelledby` pointing to its heading
- The brand name is a link, and the `<h1>` sits in the introduction, so the page has one `<h1>`

## Advanced version: landing page and site

**Goal:** a realistic product site with correct landmarks, accessible forms, and pages that feel connected.

### `index.html`: the landing page

| Section | Type | What it practices |
|---|---|---|
| Hero | `<section>` | The only `<h1>`, plus two calls to action |
| Problem | `<section>` | A paragraph and an unordered list |
| Features | `<section>` with four `<article>` blocks | Independent pieces of content |
| Workflow | `<article>` with its own `<header>` and `<footer>` | An ordered list, because the order matters, and `<time>` |
| Inventory | `<section>` | A grouped report table and a `<dl>` for terms |
| Gallery | `<section>` | Three captioned images with `loading="lazy"` |
| FAQ | `<section>` | Four `<details>` and `<summary>` pairs |
| Demo form | `<section>` | Five `<fieldset>` groups |

The inventory report uses three `<tbody>` groups with `scope="rowgroup"`, a three-row `<tfoot>`,
units in the column headers, and an `<abbr>` for SKU. The totals are 137 units, 31,580 TND, and
3 of 6 products needing a reorder.

The demo form has these groups:

| Group | Controls |
|---|---|
| About you | Name, work email, company, phone (optional, with a hint) |
| Your warehouse | A `<select>` for team size, with an empty first option |
| How do you track stock today? | Three radio buttons, with `required` on one |
| What interests you most? | Three checkboxes sharing `name="interest"` |
| Demo preferences | A date, and a message with a length hint |

A consent checkbox with `required` sits outside the groups, before the submit button. There is
no reset button, because one accidental click would wipe a long form.

### The other three pages

| Page | Main content | What it practices |
|---|---|---|
| `products.html` | Six `<article>` blocks in two sections, each with a `<figure>` | Consistent image sizes, product codes, and links that say which product they ask about |
| `pricing.html` | A comparison table with a feature column and three plan columns | A table with row headers, and status written as words ("Included", "Not included") |
| `contact.html` | Three contact articles, a support-hours table, an `<address>`, and an `<aside>` | `mailto:` with a pre-filled subject, `tel:`, and `<time>` |

### What every advanced page shares

- A skip link, and `<main id="main-content">` as its target
- The same `<nav aria-label="Main navigation">`, with `aria-current="page"` on the current page's link
- A footer with its own `<nav aria-label="Footer navigation">`
- A "Back to top" link, and a favicon
- Links to the documentation (topic 02) and operations manual (topic 03)
- Calls to action as `index.html#demo`, which load the landing page and scroll to its form

## What changed while building the advanced version

The advanced version started as one file, `advanced.html`. It grew into a site in these steps:

1. **One file became a folder.** `advanced.html` moved to `advanced/index.html`, and the other three pages were added beside it.
2. **Paths got longer.** The file moved one level deeper, so `../04-images/` became `../../04-images/`, and the same for `03-lists` and `02-links`.
3. **The menu changed meaning.** The old menu held anchors to sections of one page. The new menu links to the four pages, and the old anchors moved into a second navigation, `aria-label="On this page"`.
4. **The gallery was shortened.** The landing page shows three products and links to `products.html`, where all six live.
5. **A favicon was added** in a shared `assets/` folder, referenced as `../assets/favicon.ico`.
6. **The footer menu was rewritten** to link to the pages, not to sections.

## The header bug

A menu item was written as `<a href="products.html"></a>Products`. The closing `</a>` sat before the
word, so the link was empty and the word was plain text. Products, Pricing, and Contact looked
unclickable, and only Home and the brand name were underlined. The fix is to put the text inside the
tag: `<a href="products.html">Products</a>`.

Search the project for `"></a>` to find any other empty link.

## What improved from intermediate to advanced

- **Scale:** from one page to a four-page site
- **Content:** a problem section, a workflow, a report, a FAQ, a gallery, and a pricing comparison, written for a reader
- **Semantics:** named sections, articles with their own header and footer, and an `<address>`
- **Accessibility:** a skip link, named navigation landmarks, `aria-current`, grouped form controls, and hints connected with `aria-describedby`
- **Navigation:** page-to-page links, anchors inside pages, and calls to action that cross pages
- **Forms:** from five fields to fourteen controls in five groups, with radios, checkboxes, a select, and a consent checkbox

## What I practiced

| Topic | Where it shows up |
|---|---|
| 01 Paragraphs | The hero, problem, and introduction text |
| 02 Links | Anchors, cross-page links with `#id`, `mailto:`, `tel:`, skip link, and `aria-current` |
| 03 Lists | `<ul>` for features and problems, `<ol>` for the workflow, `<dl>` for terms |
| 04 Images | Captioned figures, consistent sizes, `loading="lazy"`, shared image folder |
| 05 Semantic tags | Landmarks, named sections, articles, `<aside>`, `<address>`, `<time>`, `<details>` |
| 06 Tables | A grouped report with a footer, a pricing comparison, and a support-hours table |
| 07 Forms | Fieldsets, a select, radios, checkboxes, required fields, and hints |

## What I learned

- A page has one `<h1>`. A brand link in the header is not the heading.
- A same-page menu uses `#id` links, and each target needs an `id` with the identical spelling
- `page.html#section` loads another page and scrolls to a section of it
- A closing `</a>` in the wrong place makes an empty link, and the text next to it stops being clickable
- Moving a file one folder deeper breaks every relative path in it. Each `../` has to be added, and Find and Replace is the safe way to do it.
- Two menus on one page need different `aria-label` values, so screen reader users can tell them apart
- `aria-current="page"` goes on one link and moves on every page
- Keep one copy of each image and point to it, so the files exist in only one place
- A table with a feature column and several plan columns needs row headers, and "Included" is better than a tick mark alone
- A long form is easier to use when it is grouped by meaning
- A long form should not have a reset button
- Pages built with the same skeleton feel like one site

## Known issues / next improvements

- [ ] Add the favicon to `intermediate.html` with `assets/favicon.ico`
- [ ] Confirm that the skip link works on every advanced page
- [ ] Search every page for `"></a>` to confirm no empty links remain
- [ ] Make the products page lead with `loading="lazy"` only below the first screen (the first image does not need it)
- [ ] Add a short paragraph of real content to each section instead of placeholder text
- [ ] Change `method="get"` to `post` when there is a backend
- [ ] Add CSS to lay out the header, the cards, the tables, and the forms
- [ ] Add JavaScript for the form, and a React version later
- [ ] Keep each later version in its own subfolder, so `intermediate.html` and `advanced/` stay untouched

## Planned versions

CSS, JavaScript, and React versions are planned after the two HTML levels. Each will live in its own
subfolder, so nothing here is overwritten. This section will change into real sections when they exist.