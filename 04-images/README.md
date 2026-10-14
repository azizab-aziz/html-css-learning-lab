# 04 — Images

Practicing how to add images to a page so they load correctly, stay accessible,
and keep the layout stable. Theme: the **Warehouse Management Learning Lab**.

**Status:** intermediate and advanced versions done.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A product gallery with three captioned images |
| `advanced.html` | Advanced | A product catalog with six product cards |
| `images/` | Shared | Product photos plus one decorative banner |

## Intermediate version: product gallery

**Goal:** use `<img>` correctly with a proper path, alt text, and dimensions.

- Three product images (laptop, monitor, keyboard) loaded from the local `images/` folder
- Relative paths such as `src="images/laptop.jpg"`
- `alt` text that describes what is actually visible
- `width` and `height` set on each image
- Each image wrapped in `<figure>` with a `<figcaption>`

## Advanced version: product catalog

**Goal:** build a realistic catalog where images support the text instead of replacing it.

- Six product cards, each an `<article>` with a name, product code, category, short description, image, and a details link
- Each image wrapped in `<figure>` with a caption that includes the SKU
- One decorative banner with an empty `alt=""`, because it carries no information
- The same `width` and `height` on every product image
- Consistent lowercase filenames with hyphens and no spaces (`barcode-scanner.jpg`, `label-printer.jpg`)
- `<header>`, `<main>`, and `<footer>` around the content
- Every "View product details" link points to the documentation site from topic 02

## What improved from intermediate to advanced

- **Structure:** from a loose list of figures to a catalog where each product is a self-contained `<article>`
- **Content:** each product has a code, category, and description as real text, so the page still works if an image fails to load
- **Alt text decisions:** informative images get descriptive `alt`, and the decorative banner gets an empty `alt` so screen readers skip it
- **Consistency:** shared dimensions and a filename convention across all images
- **Connection:** product cards link into the pages built in topic 02

## What I learned

- `src` is relative to the HTML file, so `images/laptop.jpg` means "the `images` folder next to this page"
- `alt` describes the content of the image. Don't start with "image of", because screen readers already announce an image.
- A decorative image uses `alt=""`. That is different from leaving `alt` out, which makes screen readers read the filename.
- `width` and `height` reserve space before the image loads, so the page doesn't jump
- Keep the width-to-height ratio close to the real image, or the browser stretches it
- `<figure>` and `<figcaption>` tie an image and its caption together as one unit
- Never put important information only inside an image
- Use lowercase filenames without spaces, so paths work on every system

## Known issues / next improvements

- [ ] Confirm each `alt` text matches the photo actually used
- [ ] Check that every image uses the same width-to-height ratio as its real file
- [ ] Check file sizes and compress any image that is unusually large
- [ ] Point each "View product details" link to its own product once individual product pages exist
- [ ] Add CSS later to lay the cards out in a grid