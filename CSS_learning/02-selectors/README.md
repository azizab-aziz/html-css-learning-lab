# 02 — Selectors

Choosing which elements a rule applies to, and understanding which rule wins.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate/` | Intermediate | A product features page styled with element, class, ID, grouping, and descendant selectors |
| `advanced/` | Advanced | An operations manual styled with child, sibling, attribute, and previewed pseudo selectors |

Each level folder has its own `index.html` and `style.css`.

## Selector reference

| Selector | Example | Matches |
|---|---|---|
| Element | `p` | Every `<p>` |
| Class | `.card` | Every element with `class="card"` |
| ID | `#main-title` | The one element with `id="main-title"` |
| Grouping | `h2, h3` | Both selectors, one rule |
| Descendant | `.card p` | Any `<p>` inside `.card`, at any depth |
| Element + class | `p.note` | `<p>` elements that also have class `note` |
| Child | `.menu > li` | Only direct children |
| Adjacent sibling | `h2 + p` | The `<p>` immediately after an `<h2>` |
| Attribute | `a[target="_blank"]` | Links with exactly that attribute value |
| Starts with | `a[href^="mailto:"]` | Links whose `href` starts with that text |
| Pseudo-class | `.button:hover` | An element in a given state |
| Pseudo-element | `a::after` | A generated part of an element |

## Specificity

| Selector type | Score |
|---|---|
| Element, pseudo-element | 0,0,1 |
| Class, attribute, pseudo-class | 0,1,0 |
| ID | 1,0,0 |

Scores add up, so `.card p` is 0,1,1. The higher score wins, whatever the order. When scores are equal, the later rule wins.

## Intermediate version

**Goal:** target elements with the core selectors.

- Element selectors set the page defaults
- A grouped selector styles `h2` and `h3` together
- `#main-title` practices the ID selector. Style with classes in real work, because an ID is hard to override.
- Classes style the intro and the cards, and `.card-highlight` is a second class on the same element
- `.card p` and `.category-list ul` are descendant selectors
- `p.note` combines an element with a class

## Advanced version

**Goal:** target exactly the elements you mean, with the lowest specificity that works.

- `.menu > li` and `.steps > li` use the child selector, so nested items are skipped
- `h2 + p` styles the first paragraph after each heading
- `.menu-link[aria-current="page"]` marks the current page, using the attribute from the links topic
- `a[href^="mailto:"]` and `a[href^="tel:"]` style links by type, and `a[target="_blank"]::after` adds a small "opens in a new tab" note
- `input[type="email"]` styles fields without adding classes
- `:hover` is always paired with `:focus-visible`

### The specificity bug

| | Selector | Score |
|---|---|---|
| Menu links | `.menu a` | 0,1,1 |
| Button | `.button` | 0,1,0 |

The menu link rule won, so the "Contact us" button text stayed blue on a blue background. Raising the button's score would only start an arms race. The fix was to give menu links their own class, `.menu-link`. Both rules now score 0,1,0, and the later one wins.

## What improved from intermediate to advanced

- **Precision:** child, sibling, and attribute selectors target elements without extra classes
- **Specificity:** a real conflict was found and solved by keeping scores flat
- **Accessibility:** every hover has a focus equivalent, and `aria-current` became a styling hook
- **Rules:** the stylesheet states its own rules at the top

## What I learned

- The higher specificity wins, whatever the order. Equal specificity is settled by order.
- Style with classes, and keep IDs for anchor targets
- A space means "any depth" and `>` means "direct child only"
- An attribute selector can target an element without adding a class
- A hover effect needs a `:focus-visible` equivalent for keyboard users
- Generated content is for decoration or small supplements, and the page must still make sense without it
- A strong selector is not a good fix. Lowering the score of the other rule is.
- Inherited properties such as `color` and `font-weight` pass to children whether or not the selector matches them

## Known issues / next improvements

- [ ] Replace the previewed `padding`, `margin`, and `border-radius` after module 05
- [ ] Hide the skip link until it gets focus (module 13)
- [ ] Revisit pseudo-classes and pseudo-elements in module 19
- [ ] Learn `~`, `$=`, `*=`, `:not()`, and `:nth-child()`
- [ ] Re-check contrast after module 03# 02 — Selectors

Choosing which elements a rule applies to, and understanding which rule wins.
Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate/` | Intermediate | A product features page styled with element, class, ID, grouping, and descendant selectors |
| `advanced/` | Advanced | An operations manual styled with child, sibling, attribute, and previewed pseudo selectors |

Each level folder has its own `index.html` and `style.css`.

## Selector reference

| Selector | Example | Matches |
|---|---|---|
| Element | `p` | Every `<p>` |
| Class | `.card` | Every element with `class="card"` |
| ID | `#main-title` | The one element with `id="main-title"` |
| Grouping | `h2, h3` | Both selectors, one rule |
| Descendant | `.card p` | Any `<p>` inside `.card`, at any depth |
| Element + class | `p.note` | `<p>` elements that also have class `note` |
| Child | `.menu > li` | Only direct children |
| Adjacent sibling | `h2 + p` | The `<p>` immediately after an `<h2>` |
| Attribute | `a[target="_blank"]` | Links with exactly that attribute value |
| Starts with | `a[href^="mailto:"]` | Links whose `href` starts with that text |
| Pseudo-class | `.button:hover` | An element in a given state |
| Pseudo-element | `a::after` | A generated part of an element |

## Specificity

| Selector type | Score |
|---|---|
| Element, pseudo-element | 0,0,1 |
| Class, attribute, pseudo-class | 0,1,0 |
| ID | 1,0,0 |

Scores add up, so `.card p` is 0,1,1. The higher score wins, whatever the order. When scores are equal, the later rule wins.

## Intermediate version

**Goal:** target elements with the core selectors.

- Element selectors set the page defaults
- A grouped selector styles `h2` and `h3` together
- `#main-title` practices the ID selector. Style with classes in real work, because an ID is hard to override.
- Classes style the intro and the cards, and `.card-highlight` is a second class on the same element
- `.card p` and `.category-list ul` are descendant selectors
- `p.note` combines an element with a class

## Advanced version

**Goal:** target exactly the elements you mean, with the lowest specificity that works.

- `.menu > li` and `.steps > li` use the child selector, so nested items are skipped
- `h2 + p` styles the first paragraph after each heading
- `.menu-link[aria-current="page"]` marks the current page, using the attribute from the links topic
- `a[href^="mailto:"]` and `a[href^="tel:"]` style links by type, and `a[target="_blank"]::after` adds a small "opens in a new tab" note
- `input[type="email"]` styles fields without adding classes
- `:hover` is always paired with `:focus-visible`

### The specificity bug

| | Selector | Score |
|---|---|---|
| Menu links | `.menu a` | 0,1,1 |
| Button | `.button` | 0,1,0 |

The menu link rule won, so the "Contact us" button text stayed blue on a blue background. Raising the button's score would only start an arms race. The fix was to give menu links their own class, `.menu-link`. Both rules now score 0,1,0, and the later one wins.

## What improved from intermediate to advanced

- **Precision:** child, sibling, and attribute selectors target elements without extra classes
- **Specificity:** a real conflict was found and solved by keeping scores flat
- **Accessibility:** every hover has a focus equivalent, and `aria-current` became a styling hook
- **Rules:** the stylesheet states its own rules at the top

## What I learned

- The higher specificity wins, whatever the order. Equal specificity is settled by order.
- Style with classes, and keep IDs for anchor targets
- A space means "any depth" and `>` means "direct child only"
- An attribute selector can target an element without adding a class
- A hover effect needs a `:focus-visible` equivalent for keyboard users
- Generated content is for decoration or small supplements, and the page must still make sense without it
- A strong selector is not a good fix. Lowering the score of the other rule is.
- Inherited properties such as `color` and `font-weight` pass to children whether or not the selector matches them

## Known issues / next improvements

- [ ] Replace the previewed `padding`, `margin`, and `border-radius` after module 05
- [ ] Hide the skip link until it gets focus (module 13)
- [ ] Revisit pseudo-classes and pseudo-elements in module 19
- [ ] Learn `~`, `$=`, `*=`, `:not()`, and `:nth-child()`
- [ ] Re-check contrast after module 03