# 07 — Forms and Inputs

Practicing how to collect information from people with HTML forms, so every
control is labeled, grouped, and validated, and works for keyboard and screen
reader users. Theme: the **Warehouse Management Learning Lab**.

## Files

| File | Level | What it is |
|---|---|---|
| `intermediate.html` | Intermediate | A contact form with name, email, phone, message, and a submit button |
| `advanced.html` | Advanced | An "Add inventory item" form with twelve controls in four groups |
| `extra-advanced.html` | Extra advanced | A delivery check-in form that uses the less common input types and attributes |

## How a form works

- `<form>` wraps the controls, and the submit button sends them together
- Each control needs a `name`. **No `name`, no data sent.**
- `id` connects a label to its input and is for the page. `name` labels the data and is for the server.
- The forms use `method="get"` so the submitted data shows in the address bar. Live Server can't receive a `post`, so a real form needs a backend before it can use `post`.

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

## Extra-advanced version: delivery check-in form

**Goal:** practice the input types and attributes that the first two forms don't use.

The form records a delivery at the dock (`DLV-104`, purchase orders like `PO-2041`), in five groups. Like the other forms, it has no CSS.

| Group | Controls |
|---|---|
| Delivery reference | Delivery number, purchase order search, supplier website |
| Arrival | Date and time, unloading start time, container seal number |
| Goods received | Pallets, cargo temperature, packaging condition slider |
| Damage check | Four checkboxes, and a photo upload |
| Notification and notes | Email recipients, notes, supervisor approval |

New input types and attributes:

| Control | Element and attributes | What it does |
|---|---|---|
| Form version | `type="hidden"` | Sends a value the user never sees or edits |
| Delivery number | `type="text"` with `readonly` | Shows a value that can't be edited but **is** sent |
| Purchase order | `type="search"`, `pattern="PO-[0-9]{4}"` | A search-style box that must match `PO-2041` |
| Supplier website | `type="url"` | Must be a full address, such as `https://example.com` |
| Arrival | `type="datetime-local"` | A date and time picker in one |
| Unloading time | `type="time"`, `min="06:00"`, `max="18:00"` | A time picker limited to dock hours |
| Seal number | `type="text"`, `inputmode="numeric"`, `pattern="[0-9]{6}"` | A number keypad on phones that keeps leading zeros |
| Temperature | `type="number"`, `step="0.1"` | Allows one decimal place |
| Packaging condition | `type="range"` with a `<datalist>` | A slider from 1 to 5 with labeled tick marks |
| Damage types | Four checkboxes sharing `name="damage"` | Several ticked values sent under the same key |
| Photos | `type="file"`, `accept="image/*"`, `multiple` | Choose several image files |
| Notify | `type="email"` with `multiple` | Accepts several comma-separated addresses |
| Supervisor approval | `type="checkbox"` with `disabled` | Greyed out, and **not** sent |
| Buttons | Submit, "Save draft" with `formnovalidate`, and reset | Save draft skips validation. Each button has a `name` and `value`, so the address bar shows which one was pressed. |

Details:

- The seal number is **text**, not a number, because `type="number"` would turn `004821` into `4821`. A code is not a quantity.
- `readonly`, `disabled`, and `hidden` all keep a value out of the user's hands, but only `disabled` stops it from being sent.
- The form uses `method="get"`, so every value appears in the address bar. That's useful for learning, and it's why there is no password field.
- With `get`, a file input sends only the file name. A real upload needs `method="post"`, `enctype="multipart/form-data"`, and a server.

## What improved from intermediate to advanced

- **Scale:** from four fields to twelve, in four meaningful groups
- **Control types:** a dropdown, radio buttons, a checkbox, number and date inputs, and a datalist
- **Validation:** `pattern`, `min`, `step`, `maxlength`, and `required`, with `title` text that explains the rule when a field fails
- **Accessibility:** fieldsets and legends name each group, and hints are connected to their fields
- **Realistic rules:** SKU and location formats follow the codes used in the other topics

## What improved from advanced to extra-advanced

- **Range of input types:** search, url, datetime-local, time, range, file, hidden, and multiple email
- **Control over values:** `readonly`, `disabled`, and `hidden` do three different jobs, and the address bar shows which values are sent
- **Choosing the right type:** a seal number is text, and a quantity is a number
- **Several values under one name:** checkboxes that share a `name` send one key several times
- **Two ways to send:** a submit button that validates, and a draft button that doesn't

## What I learned

- Every control needs a visible label. A placeholder is not a label.
- `for` and `id` must match exactly, or clicking the label does nothing
- A control without a `name` sends nothing
- Radio buttons in one group share a `name`, and `required` on one makes the whole group required
- A required `<select>` needs an empty first option, or the first real choice counts as already picked
- `type="email"` and `type="tel"` give better validation and keyboards than plain `text`
- `type="tel"` does not validate. Only `pattern` can.
- `<fieldset>` and `<legend>` give a group of controls a name for assistive technology
- `readonly` is sent and `disabled` is not. `hidden` is sent too, but nobody sees it.
- Use `type="text"` with `inputmode="numeric"` for codes with leading zeros, and `type="number"` only for real quantities
- Checkboxes that share a `name` are all sent, each as its own key and value
- `formnovalidate` on a button lets a form be saved half-filled
- `type="url"` needs the start of the address, such as `https://`
- A `type="range"` slider shows no number by itself, and updating one takes JavaScript
- The `<datalist>` tick marks on a slider don't appear in every browser
- A file input with `method="get"` sends only the file name
- The browser validates before sending, but this can't be trusted alone. A real site must check the data on the server too.
- A reset button can wipe a long form with one click, so use it with care
- Forms have no layout until CSS. Labels and fields sit side by side, and fieldsets show a default border.

## Known issues / next improvements

- [ ] Change `method="get"` to `post` when there is a backend to receive the data
- [ ] Limit the purchase date to today or earlier. HTML can't do this, so it needs JavaScript.
- [ ] Check that every field shows up in the address bar after submitting, since a missing one has no `name`
- [ ] Show the slider's current value next to it with an `<output>` element and JavaScript
- [ ] Make a real file upload work with `post` and `multipart/form-data` on a server
- [ ] Add CSS later to line up labels and fields, style the fieldsets, and show invalid fields
- [ ] Add server-side validation when the backend exists
