# CSS Positioning

CSS `position` controls how an element is placed on a webpage. It becomes especially useful when we want to move elements, place them on top of other elements, or keep them fixed while scrolling.

The main positioning values I learned are:

* `static`
* `relative`
* `absolute`
* `fixed`

---

## 1. `position: static`

`static` is the **default position** of an HTML element.

The element stays in the normal flow of the webpage, and properties such as `top`, `right`, `bottom`, and `left` do not affect it.

```css
.box {
  position: static;
}
```

For example:

```html
<div>Box 1</div>
<div>Box 2</div>
<div>Box 3</div>
```

The boxes will naturally appear one after another.

```text
Box 1
Box 2
Box 3
```

You normally don't need to write `position: static` because it is already the default.

---

## 2. `position: relative`

`relative` keeps the element in its **original position in the normal document flow**, but allows us to move it relative to that original position.

For example:

```css
.box {
  position: relative;
  left: 30px;
  top: 10px;
}
```

This moves the box:

* 30px to the right
* 10px down

The important thing is that the element's **original space is still preserved**.

```text
Original:

[ Box ]

After moving:

    [ Box ]
```

The page still treats the box as if it were occupying its original position.

### Why is `relative` important?

One of its most useful purposes is creating a **positioning reference for an absolutely positioned child**.

For example:

```html
<div class="parent">
  <div class="child">Hello</div>
</div>
```

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

Here, the `.child` is positioned relative to `.parent`.

This is one of the most common uses of `position: relative`.

---

## 3. `position: absolute`

`absolute` removes the element from the normal document flow.

The element is positioned relative to its **nearest positioned ancestor**.

A positioned ancestor is generally an ancestor whose `position` is something other than `static`, such as:

```css
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

The most common pattern is:

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

The child will be placed at the top-right of the parent.

### Example

```html
<div class="card">
  <h2>My Card</h2>
  <button class="close">X</button>
</div>
```

```css
.card {
  position: relative;
  width: 300px;
  height: 200px;
  background-color: lightblue;
}

.close {
  position: absolute;
  top: 10px;
  right: 10px;
}
```

The button will appear in the top-right corner of the card.

```text
+---------------------------+
|                   [ X ]   |
|                           |
|       My Card             |
|                           |
|                           |
+---------------------------+
```

If the `.card` did **not** have a positioned ancestor, the browser would look further up the HTML hierarchy for one. If it cannot find one, the element is positioned relative to the initial containing block (effectively the page's coordinate system).

### `z-index`

`z-index` can be used to control which overlapping elements appear in front of others.

```css
.box1 {
  position: absolute;
  z-index: 1;
}

.box2 {
  position: absolute;
  z-index: 2;
}
```

Here, `.box2` will generally appear above `.box1` when they overlap.

`z-index` is not limited to `absolute` elements, though. It can also work with other positioned elements such as `relative` and `fixed`.

---

## 4. `position: fixed`

`fixed` positions an element relative to the **browser's viewport**.

Unlike an absolutely positioned element, a fixed element does not move along with the normal document when the page is scrolled.

For example:

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```

This can be used to create a navigation bar that stays at the top of the screen.

```text
+----------------------------------+
|          NAVIGATION              | <- stays here
+----------------------------------+

        Page content

        Page content

        Page content
```

Even when the user scrolls down, the navigation bar remains attached to the viewport.

Another simple example:

```css
.help-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
}
```

This could create a help button that always stays in the bottom-right corner of the screen.

---

## Quick Comparison

| Position   | Stays in normal flow? | Positioned relative to      |
| ---------- | --------------------- | --------------------------- |
| `static`   | Yes                   | Normal document flow        |
| `relative` | Yes                   | Its original position       |
| `absolute` | No                    | Nearest positioned ancestor |
| `fixed`    | No                    | Browser viewport            |

### A simple way to remember them

**Static** → "Just stay where you normally would."

**Relative** → "Stay in the flow, but I can move you from your original position."

**Absolute** → "Leave the normal flow and position yourself inside a positioned ancestor."

**Fixed** → "Stick to the browser window."

---

## What I Learned

CSS positioning makes much more sense when thinking about **what an element is positioned relative to**.

The most useful relationship to remember is:

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
}
```

This lets us position the child precisely inside the parent.

This concept is commonly used for things like badges, close buttons, icons, overlays, dropdowns, cards, and other UI elements.
