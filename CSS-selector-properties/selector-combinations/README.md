# Combining CSS Selectors

This folder contains my practice code for learning how different CSS selectors can be combined to target elements more precisely.

I practiced **grouping selectors, child selectors, descendant selectors, chaining selectors, and combinations of these techniques**.

## 1. Group Selector

The group selector lets me apply the same style to multiple selectors.

I used:

```css
h1, h2 {
  color: blueviolet;
}
```

This applies the same `color` to both `<h1>` and `<h2>` without writing two separate rules.

## 2. Child Selector

The `>` symbol selects an element that is a **direct child** of another element.

I used:

```css
.box > .done {
  color: chocolate;
}
```

This targets an element with the `.done` class only when it is directly inside `.box`.

## 3. Descendant Selector

A space between selectors targets matching elements that occur **anywhere inside** another element, not necessarily as a direct child.

I used:

```css
.box .list {
  color: rgb(18, 52, 206);
}
```

This finds `.list` elements that are descendants of `.box`.

I also used:

```css
.box li {
  color: greenyellow;
}
```

This targets `<li>` elements anywhere inside `.box`.

## 4. Chaining Selectors

Chaining selectors allows me to target an element that matches multiple selectors at the same time.

I used:

```css
li.done {
  color: green;
}
```

This means: select `<li>` elements that also have the `done` class.

It does **not** select every `.done` element—only `<li>` elements with that class.

## 5. Combining Multiple Selector Rules

I also practiced combining element, class, and relationship selectors:

```css
ul p.done {
  font-size: 0.5rem;
}
```

Here:

* `ul` identifies the ancestor.
* `p` identifies the element type.
* `.done` further restricts the target to elements with the `done` class.

Together, they select a `<p class="done">` that is inside a `<ul>`.

## What I Practiced

This project helped me understand that CSS selectors can be combined to make targeting much more precise.

The main patterns I practiced were:

**Group:** `h1, h2`

**Child:** `.box > .done`

**Descendant:** `.box .list`

**Chaining:** `li.done`

**Multiple combinations:** `ul p.done`

These rules gave me a better understanding of how CSS can target elements based not only on **what the element is**, but also on its **classes and position within the HTML hierarchy**.
