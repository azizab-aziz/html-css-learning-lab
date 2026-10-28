# 02 — Links

Practicing how pages connect to each other and to the outside world:
internal links, external links, email and phone links, anchors, and links
that help people navigate. Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A warehouse navigation page with six link types |
| `inventory.html` | Intermediate | A small destination page, with a link back to the navigation page |
| `advanced/` | Advanced | A five-page documentation site that feels like one connected website |
| `advanced/files/receiving-checklist.txt` | Advanced | A file offered as a download |

## Intermediate version

**Goal:** use every basic link type correctly, with meaningful link text.

| Link type | Example `href` |
|---|---|
| Internal link to another exercise | `../01-paragraphs/advanced.html` |
| Internal link, same folder | `inventory.html` |
| External link, new tab | `https://developer.mozilla.org/` with `target="_blank" rel="noopener"` |
| Email link | `mailto:contact@warehouse-lab.com` |
| Phone link | `tel:+21612345678` |
| Same-page anchor | `#contact`, which jumps to `<section id="contact">` |

- The links sit inside a `<ul>` so each one stacks on its own line without CSS
- Link text describes the destination ("View inventory records", not "Click here")
- `inventory.html` links back to `intermediate.html`, so navigation works in both directions

## Advanced version

**Goal:** make separate files feel like one website, and use links to help people get around.

```
advanced/
├── index.html
├── products.html
├── inventory.html
├── receiving.html
├── contact.html
└── files/
    └── receiving-checklist.txt
```

Every page includes:

- The same `<nav aria-label="Main navigation">`, with `aria-current="page"` on the current page's link
- A skip link (`#main-content`) that jumps past the menu to `<main id="main-content">`
- A breadcrumb in its own `<nav aria-label="Breadcrumb">` (not on the home page)
- Previous and Next links with `rel="prev"` and `rel="next"`
- A "Back to top" link using `id="top"` on the `<body>`
- An external link to MDN with `rel="noopener"`
- A link to this GitHub repository
- A contact link
- A footer with its own `<nav aria-label="Footer navigation">`

Page-specific links:

| Page | Extra links |
|---|---|
| `receiving.html` | An "On this page" contents list, a download link, and a link to `inventory.html#low-stock` |
| `inventory.html` | The `id="low-stock"` section that receiving links to |
| `contact.html` | `mailto:` links, with a pre-filled subject on some |

## What improved from intermediate to advanced

- **Scope:** from one page with a list of links to five pages that all reference each other
- **Consistency:** the same navigation block and footer on every page, so the site feels unified
- **Accessibility:** a skip link, named navigation landmarks, and `aria-current` tell keyboard and screen reader users where they are
- **Orientation:** breadcrumbs and Previous/Next links show where each page sits in the site
- **Precision:** a cross-page anchor (`inventory.html#low-stock`) sends the reader to the exact section, not just the page
- **File links:** a `download` link offers a file instead of opening a page

## What I learned

- `href` changes meaning with its value: a file path, a full URL, `mailto:`, `tel:`, or `#id`
- `#contact` only works if an element has exactly `id="contact"`, with the same spelling and casing
- A skip link needs two parts in the same file: the link, and a matching `id` on `<main>`
- `page.html#section` loads another page and scrolls to a section of it
- `target="_blank"` should always be paired with `rel="noopener"`
- A page with several `<nav>` landmarks needs a different `aria-label` on each, so screen reader users can tell them apart
- `aria-current="page"` goes on one link per menu, and moves on every page
- Relative paths depend on where the file sits: `../` goes up one folder, no prefix means the same folder
- Windows ignores upper and lower case in folder names, but Git and many web servers do not. A folder named `02-Links` instead of `02-links` caused a long debugging session, so I now keep every name lowercase.

## Known issues / next improvements

- [ ] Confirm the skip link works on every page. It was confirmed on `receiving.html` only.
- [ ] Rename `inventory.html` in this folder to lowercase (Git still tracks it as `Inventory.html`)
- [ ] Check that every GitHub link points to the real repository
- [ ] Use CSS later to hide the skip link until it gets keyboard focus
- [ ] Add a short paragraph of real content to each advanced page
