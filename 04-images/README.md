# 04 — Images

Practicing how to add images to a page so they load correctly, stay accessible,
and keep the layout stable. Theme: the **Warehouse Management Learning Lab**.

**Status:** intermediate version done, advanced version planned.

## Files

| File | Level | Status |
|---|---|---|
| `intermediate.html` | Intermediate | Done |
| `advanced.html` | Advanced | Planned |
| `images/` | Shared | `laptop.jpg`, `monitor.jpg`, `keyboard.jpg` |

## Intermediate version: product gallery

**Goal:** use `<img>` correctly with a proper path, alt text, and dimensions.

- Three product images (laptop, monitor, keyboard) loaded from the local `images/` folder
- Relative paths such as `src="images/laptop.jpg"`
- `alt` text that describes what is actually visible
- `width` and `height` set on each image
- Each image wrapped in `<figure>` with a `<figcaption>`

## Advanced version (planned)

**Goal:** build a realistic product catalog.

- Six product cards, each with a product code, name, image, short description, and category
- A link from each card to product details
- A `<figure>` and caption for every image
- One decorative image with an empty `alt=""`
- Consistent image filenames and dimensions

## What I learned

- `src` is relative to the HTML file, so `images/laptop.jpg` means "the `images` folder next to this page"
- `alt` describes the content of the image. Don't start with "image of", because screen readers already announce an image.
- `width` and `height` reserve space before the image loads, so the page doesn't jump
- Keep the width-to-height ratio close to the real image, or the browser stretches it
- `<figure>` and `<figcaption>` tie an image and its caption together as one unit
- Use lowercase filenames without spaces, so paths work on every system

## Known issues / next improvements

- [ ] Confirm each `alt` text matches the photo actually used
- [ ] Check the width and height ratio against each real image
- [ ] Check file sizes and compress any image that is unusually large
- [ ] Build the advanced catalog version