# 05 — Semantic Tags

Practicing how to structure a page by **meaning**: landmarks, sections, articles,
and asides instead of generic containers. Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A warehouse news page using the seven core semantic tags |
| `advanced/` | Advanced | A four-page documentation site built on a shared semantic skeleton |

## Choosing the tag

| Tag | Meaning | Used for |
|---|---|---|
| `<header>` | Introductory content | The page title and intro, or the byline of an article |
| `<nav>` | Navigation links | The main menu |
| `<main>` | The central content | Once per page |
| `<section>` | A themed group of content, with a heading | "Featured story", "Tracking stock" |
| `<article>` | A self-contained piece | A news story, a guide topic |
| `<aside>` | Related but non-essential content | Tips and side notes |
| `<footer>` | Closing information | The credit line, or the end of an article |

**Section or article?** If the piece would still make sense copied to another website, it is an `<article>`. If it is a themed chunk of this page, it is a `<section>`.

## Intermediate version: warehouse news page

**Goal:** use every core semantic tag once, in the right place.

- A `<header>` with the title and intro
- A `<nav aria-label="Main navigation">` with links to earlier exercises, wrapped in a `<ul>`
- One `<main>` holding two `<section>` blocks
- Each news story as an `<article>`
- An `<aside>` with a quick note
- A `<footer>` closing the page
- Heading levels: `<h1>` in the header, `<h2>` for sections, `<h3>` for stories

## Advanced version: documentation site

**Goal:** build several pages that share one semantic skeleton, and go beyond the seven core tags.

```
advanced/
├── index.html
├── getting-started.html
├── inventory.html
└── contact.html
```

Every page contains:

- One page-level `<header>`
- A `<nav aria-label="Main navigation">` that is identical on all pages, with `aria-current="page"` on the current page's link
- One `<main>` with multiple `<section>` blocks
- `<article>` elements for independent pieces of content
- An `<aside>` for related information
- A `<footer>`
- A heading hierarchy with no skipped levels

Extra semantic elements added:

| Element | Where | What it does |
|---|---|---|
| `<time datetime="...">` | `index`, `getting-started` | Marks a date in a form software can read |
| `<header>` and `<footer>` inside an `<article>` | `getting-started` | Introduces and closes one article, not the whole page |
| `aria-labelledby` on `<section>` | Every page | Names the section using its own heading, so it becomes a named region |
| `<address>` | `contact` | Marks contact information for the page owner |
| `<details>` and `<summary>` | `inventory` | A FAQ that expands and collapses with no CSS or JavaScript |
| `<small>` | Every footer | Marks fine print such as the credit line |

## What improved from intermediate to advanced

- **Scale:** from one page to four pages that follow the same structure
- **Consistency:** the same skeleton and navigation make separate files feel like one site
- **Decisions:** each page needed real choices about what is a section, an article, or an aside
- **Accessibility:** landmarks and named sections let screen reader users jump around the page
- **Precision:** `<time>`, `<address>`, and `<details>` say exactly what a piece of content is
- **Connection:** the pages link to the operations manual from topic 03

## What I learned

- Tags describe what content **is**, not how it looks
- A page has exactly one `<main>`
- A `<section>` should start with a heading. If it has no natural heading, it is probably the wrong tag.
- `<aside>` holds content the page still works without
- `<header>` and `<footer>` introduce and close their **parent**, so they can also sit inside an `<article>`
- `aria-labelledby` points to a heading's `id`, and the two must match exactly
- `<small>` means fine print, not "make this smaller"
- Heading levels follow the structure: `<h1>`, then `<h2>`, then `<h3>`, with no skipping
- Landmarks are not decoration. They are how assistive technology navigates a page.
- Not every project needs all seven tags. Use a tag only when the content has that meaning.

## Known issues / next improvements

- [ ] Check that the home page aside link opens the operations manual from topic 03
- [ ] Confirm the correct `aria-current="page"` link on each page using View Source
- [ ] Check that every `aria-labelledby` matches a heading `id` on its page
- [ ] Replace the placeholder text with content written for a real reader
- [ ] Add a real contact form in topic 07
- [ ] Add CSS later to lay out the header, navigation, main area, and aside
