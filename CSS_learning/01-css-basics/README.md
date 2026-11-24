# 01 — CSS Basics

Connecting a stylesheet to HTML and writing the first rules.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate/` | Intermediate | A warehouse intro page, styled with one rule per element |
| `advanced/` | Advanced | A technical article with a sectioned, documented stylesheet |

Each level folder has its own `index.html` and `style.css`, so it opens on its own.

## Key syntax

| Part | Example |
|---|---|
| Rule | `h1 { color: #0b57d0; }` |
| Selector | `h1` |
| Declaration | `color: #0b57d0;` |
| Property and value | `color` and `#0b57d0` |
| Comment | `/* explains why */` |

## Three ways to add CSS

| Way | Affects | Used here |
|---|---|---|
| Inline `style=""` | One element | No |
| `<style>` block | One page | No |
| External `<link>` file | Many pages | Yes |

## Intermediate version

**Goal:** connect a stylesheet and style text with simple rules.

- `<link rel="stylesheet" href="style.css">` in the `<head>`
- Defaults on `body` that the other elements inherit
- A fallback `font-family` list, hex colors, and a unitless `line-height`
- Sizes in `rem`

## Advanced version

**Goal:** write the same skills so the file is easy to read and change.

- A contents list and numbered section comments
- Grouped selectors (`h1, h2`) instead of repeating declarations
- A readable line length with `max-width: 65ch`
- Colors checked in DevTools

## What improved from intermediate to advanced

- **Organization:** the file reads like a document, in numbered sections
- **No repetition:** shared declarations are written once
- **Readability:** a controlled line length and spacing between sections
- **Process:** values were tried in DevTools before being written down

## What I learned

- A rule is a selector plus declarations, and each declaration ends with `;`
- External stylesheets are linked with a path relative to the HTML file
- Properties set on `body` are inherited by the elements inside it
- `font-family` is a fallback list, not one font
- `line-height` without a unit scales with the font size
- DevTools changes are temporary until copied into the file
- A comment should explain why, not repeat the code

## Known issues / next improvements

- [ ] Replace the previewed `max-width`, `margin`, and `padding` once module 05 is done
- [ ] Re-check contrast on every color after module 03