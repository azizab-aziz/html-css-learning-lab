# 02 — Links

Practicing how pages connect to each other and to the outside world:
internal links, external links, email and phone links, and same-page anchors.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A warehouse navigation page with six link types |
| `inventory.html` | Intermediate | A small destination page, with a link back to the navigation page |
| `advanced/` | Advanced | A five-page documentation site that feels like one connected website |

## Intermediate version

**Goal:** use every basic link type correctly, with meaningful link text.

Six links in one `<nav>`, each a different type:

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

**Goal:** make separate files feel like one website.

```
advanced/
├── index.html
├── products.html
├── inventory.html
├── receiving.html
└── contact.html
```

Every page includes:

- The same `<nav aria-label="Main navigation">` menu
- `aria-current="page"` on the link for the page you are currently on
- Links between related pages (Products to Inventory, Inventory to Receiving)
- A "Back to top" link using `id="top"` on the `<body>`
- An external link to MDN, opened with `rel="noopener"`
- A link to this GitHub repository
- A contact link

## What improved from intermediate to advanced

- **Scope:** from one page with a list of links to five pages that all reference each other
- **Consistency:** the navigation block is identical on every page, so the site feels unified
- **Accessibility:** `aria-label` names the navigation landmark, and `aria-current` tells screen readers where the user is
- **Usability:** every page offers a way back to the top and a way to make contact

## What I learned

- `href` changes meaning with its value: a file path, a full URL, `mailto:`, `tel:`, or `#id`
- `#contact` only works if an element has exactly `id="contact"`, with the same spelling and casing
- `target="_blank"` should always be paired with `rel="noopener"`
- Relative paths depend on where the file sits: `../` goes up one folder, no prefix means the same folder
- Windows ignores upper and lower case in folder names, but Git and many web servers do not. A folder named `02-Links` instead of `02-links` caused a long debugging session, so I now keep every name lowercase.

## Known issues / next improvements

- [ ] Rename `inventory.html` in this folder to lowercase (Git still tracks it as `Inventory.html`)
- [ ] Check that every GitHub link points to the real repository, not a placeholder username
- [ ] Add a short paragraph of real content to each advanced page
- [ ] Add CSS to the navigation once the CSS topics start