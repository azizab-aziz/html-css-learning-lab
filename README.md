# HTML & CSS Learning Lab

A hands-on learning repository: eight HTML topics, each built twice (an intermediate
and an advanced version) around one theme, a **warehouse management system**.
The goal is not to memorize tags but to choose the right one for the meaning of the
content, and to build pages that are accessible, well structured, and connected.

**Status:** all eight HTML topics are done. CSS, Tailwind, JavaScript, and React
versions are planned next.

## Topics

| # | Topic | Levels | What it covers |
|---|---|---|---|
| 01 | [Paragraphs](./01-paragraphs) | Intermediate, advanced | Headings, paragraphs, emphasis, and a structured technical article |
| 02 | [Links](./02-links) | Intermediate, advanced (5 pages) | Internal, external, `mailto:`, `tel:`, anchors, skip links, breadcrumbs, and a connected documentation site |
| 03 | [Lists](./03-lists) | Intermediate, advanced | Ordered, unordered, nested, and description lists, and an operations manual |
| 04 | [Images](./04-images) | Intermediate, advanced | `<img>`, alt text, dimensions, `<figure>`, and a six-product catalog |
| 05 | [Semantic tags](./05-semantic-tags) | Intermediate, advanced (4 pages), extra-advanced | Landmarks, sections, articles, asides, `<address>`, `<time>`, `<details>`, and named sections |
| 06 | [Tables](./06-tables) | Intermediate, advanced, extra-advanced, schedule | Captions, headers and `scope`, `<tfoot>`, `colspan`, `rowspan`, and a monthly inventory report |
| 07 | [Forms and inputs](./07-Forms-and-inputs) | Intermediate, advanced, extra-advanced | Labels, fieldsets, input types, validation attributes, and a delivery check-in form |
| 08 | [Mini-page](./08-Mini-page) | Intermediate, advanced (4 pages) | Everything combined into one product page, then a small multi-page site |

Each topic folder has its own README that explains what the exercise contains, what
improved between levels, what I learned, and what is still open.

## How each topic is built

| Level | Purpose |
|---|---|
| **Intermediate** | Correct syntax and basic organization, covering exactly what the exercise asks for |
| **Advanced** | Better structure, realistic content, semantic HTML, accessibility, and clear navigation |
| **Extra-advanced** | One idea pushed further, built only for some topics |

The advanced level is not "more tags". It is more thought about structure, meaning,
and the reader.

## What this repo shows

- **Semantic HTML:** tags chosen for what content *is*, not for how it looks
- **Accessibility:** visible labels on every control, meaningful `alt` text, named landmarks with `aria-label` and `aria-labelledby`, `aria-current`, skip links, and status written in words
- **Real data structures:** tables with row and column headers, totals, and grouped rows
- **Forms that validate:** `required`, `pattern`, `min`, `max`, `step`, `maxlength`, and the right input type for each field
- **Connected pages:** shared navigation, cross-page anchors such as `index.html#demo`, and relative paths that stay correct as folders change
- **A consistent dataset:** the same products, SKUs, and locations appear across topics (for example `LAP-001`, `SCN-001`, shelf `A-01`, prices in TND)

## Repository structure

```
html-css-learning-lab/
├── README.md
├── 01-paragraphs/
├── 02-links/
│   └── advanced/
├── 03-lists/
├── 04-images/
│   └── images/
├── 05-semantic-tags/
│   └── advanced/
├── 06-tables/
├── 07-Forms-and-inputs/
└── 08-Mini-page/
    ├── assets/
    └── advanced/
```

Naming rules: the number lives on the folder, and the file name tells the level
(`intermediate.html`, `advanced.html`). When an advanced version needs several
pages, it gets its own `advanced/` subfolder with an `index.html`.

## Running it locally

1. Clone the repository and open the **root folder** in VS Code.
2. Install the **Live Server** extension.
3. Right-click any `.html` file and choose **Open with Live Server**.

Open the whole repo, not a single topic folder. Some pages point to files in other
topics (the mini-page uses the product photos from `04-images/` and links to
`02-links/` and `03-lists/`), so the folders must stay where they are.

## CSS in this repo so far

The plan is HTML first, then CSS. Two table pages are a deliberate exception, each
linked to its own stylesheet so the tables can be seen with borders:

- `06-tables/extra-advanced.html` with `extra-advanced.css` (dark theme)
- `06-tables/schedule.html` with `schedule.css` (light theme)

Every other page is intentionally unstyled.

## Roadmap

- [x] HTML fundamentals: topics 01 to 08, both levels
- [ ] CSS: layout, spacing, typography, responsive design, and shared stylesheets
- [ ] Tailwind CSS, after the CSS fundamentals
- [ ] JavaScript version of the mini-page
- [ ] React version of the mini-page
- [ ] A deployed version of the repository (GitHub Pages)

Later versions of the mini-page will live in their own subfolders, so the HTML
versions stay untouched for comparison.

## Working method

- One topic at a time, intermediate first, then advanced
- A separate commit for each exercise and for each README, using messages such as `feat: create advanced lists exercise` and `docs: document tables exercises`
- Every topic ends with a written review of what improved and what was learned
- Lowercase names with hyphens and no spaces, so paths work on every system

## License

Released under the MIT License.
