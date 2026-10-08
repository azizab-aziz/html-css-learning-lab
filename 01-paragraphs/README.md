# 01 — Paragraphs

Practicing how to structure written content in HTML: headings, paragraphs,
and text emphasis. Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A simple product-information page about a warehouse management system |
| `advanced.html` | Advanced | A structured technical article: *How a Warehouse Management System Works* |

## Intermediate version

**Goal:** get the basic syntax and organization right.

- One `<h1>` for the page title, `<h2>` for each question/section
- Short paragraphs with `<p>`
- `<strong>` for important words, `<em>` for emphasized or technical terms
- A short product description and an explanation of why inventory tracking matters

## Advanced version

**Goal:** build a logical information hierarchy, not just add more text.

Article structure:

1. Introduction
2. The Inventory Problem
3. How the System Works
4. Benefits
5. Limitations
6. Conclusion

- Content wrapped in `<article>` because it is a self-contained piece
- A single `<h1>`, with `<h2>` sections that follow a logical order
- `<mark>` and `<em>` to highlight the introduction label
- Related points (steps, benefits, limitations) grouped as lists instead of long paragraphs
- Realistic content written for a reader, not placeholder text

## What improved from intermediate to advanced

- **Structure:** from a loose set of headings to a defined article with a clear reading order
- **Semantics:** `<article>` describes what the content *is*, not just how it looks
- **Content quality:** each section communicates one idea in plain language
- **Scannability:** parallel items became lists so the page is easy to skim

## What I learned

- `<strong>` means *important* and `<em>` means *stressed*. They are about meaning, not looks.
- A `<p>` can only hold inline content. Block elements like `<ul>` or `<h3>` inside it are invalid, and the browser silently auto-closes the `<p>`.
- `<br>` for spacing is a shortcut; proper structure and (later) CSS do that job better.
- Heading levels describe hierarchy. Don't pick them for their size.

## Known issues / next improvements

- [ ] Fix spelling mistakes in `intermediate.html`
- [ ] Move `<ul>` elements out of `<p>` tags in `advanced.html`
- [ ] Turn the manually typed "•" limitation lines into a real `<ul>`
- [ ] Add an author name and a "Last updated" line to the article
- [ ] Replace `<u>` and `<br>` with better alternatives