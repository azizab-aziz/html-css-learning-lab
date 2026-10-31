# 07 — Forms and Inputs

Practicing how to collect information from people with HTML forms, so every
control is labeled, grouped, and validated, and works for keyboard and screen
reader users. Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A contact form with name, email, phone, message, and a submit button |
| `advanced.html` | Advanced | An "Add inventory item" form with twelve controls in four groups |

## How a form works

- `<form>` wraps the controls, and the submit button sends them together
- Each control needs a `name`. **No `name`, no data sent.**
- `id` connects a label to its input and is for the page. `name` labels the data and is for the server.
- The forms use `method="get"` so the submitted data shows in the address bar. Live Server can't receive a `post`, so a real contact form needs a backend before it can use `post`.

## Intermediate version: contact form

**Goal:** build a small form where every field has a label and the right type.

| Field | Type | Validation |
|---|---|---|
| Full name | `text` | `required`, `autocomplete="name"` |
| Email address | `email` | `required`, the browser checks the shape |
| Phone number | `tel` | Optional, with a hint connected by `aria-describedby` |
| Message | `<textarea>` | `required`, `minlength="10"` |

- `<label for="...">` matches each input's `id`, so clicking a label focuses its field
- Labels say "(required)" and "(optional)" in words, not by color or a symbol alone
- The form is named by its heading with `aria-labelledby`
- The page sits inside `<header>`, `<main>`, and `<footer>`

## Advanced version: add inventory form

**Goal:** build a complete form where related controls are grouped and validated.

| Group (`<fieldset>`) | Controls |
|---|---|
| Product information | Product name, SKU, category, description |
| Stock and location | Quantity, reorder threshold, warehouse location |
| Purchase details | Supplier, purchase date |
| Product condition | Three radio buttons: New, Used, Refurbished |

Outside the groups: an agreement checkbox, a submit button, and a reset button.

| Control | Element and attributes | Why |
|---|---|---|
| Product name | `text`, `maxlength`, `required` | Limits the length |
| SKU | `text`, `pattern="[A-Z]{3}-[0-9]{3}"`, `title`, `required` | Must look like `SCN-001` |
| Category | `<select>` with `<optgroup>`, empty first `<option value="">` | The empty option makes `required` work |
| Quantity and reorder threshold | `number`, `min="0"`, `step="1"` | Whole numbers from 0 up |
| Location | `text`, `pattern="[A-Z]-[0-9]{2}"`, `title`, `required` | Must look like `A-01` |
| Supplier | `text` with `<datalist>` | Suggests suppliers but accepts any name |
| Purchase date | `date`, `required` | A date picker |
| Condition | `radio` group sharing `name="condition"`, one with `required` | One choice, and the group is required |
| Description | `<textarea>`, `maxlength="500"` | Optional, with a length hint |
| Agreement | `checkbox`, `required` | Must be ticked before sending |

Details:

- Related controls are grouped with `<fieldset>` and `<legend>`, so a screen reader says "Product condition, New, radio button"
- `aria-describedby` connects the hint under a field to the field
- A placeholder appears only on SKU, as an example. Every field keeps a visible label, because a placeholder disappears as you type.
- The reset button is labeled "Clear form" and sits after the submit button, so it's harder to hit by accident

## What improved from intermediate to advanced

- **Scale:** from four fields to twelve, in four meaningful groups
- **Control types:** a dropdown, radio buttons, a checkbox, number and date inputs, and a datalist
- **Validation:** `pattern`, `min`, `step`, `maxlength`, and `required`, with `title` text that explains the rule when a field fails
- **Accessibility:** fieldsets and legends name each group, and hints are connected to their fields
- **Realistic rules:** SKU and location formats follow the codes used in the other topics

## What I learned

- Every control needs a visible label. A placeholder is not a label.
- `for` and `id` must match exactly, or clicking the label does nothing
- A control without a `name` sends nothing
- Radio buttons in one group share a `name`, and `required` on one makes the whole group required
- A required `<select>` needs an empty first option, or the first real choice counts as already picked
- `type="email"` and `type="tel"` give better validation and keyboards than plain `text`
- `type="tel"` does not validate. Only `pattern` can.
- `<fieldset>` and `<legend>` give a group of controls a name for assistive technology
- The browser validates before sending, but this can't be trusted alone. A real site must check the data on the server too.
- A reset button can wipe a long form with one click, so use it with care
- Forms have no layout until CSS. Labels and fields sit side by side, and fieldsets show a default border.

## Known issues / next improvements

- [ ] Change `method="get"` to `post` when there is a backend to receive the data
- [ ] Limit the purchase date to today or earlier. HTML can't do this, so it needs JavaScript.
- [ ] Check that every field shows up in the address bar after submitting, since a missing one has no `name`
- [ ] Add CSS later to line up labels and fields, style the fieldsets, and show invalid fields
- [ ] Add server-side validation when the backend exists