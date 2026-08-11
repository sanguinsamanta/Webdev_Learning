# CSS Hierarchy and Cascade

This folder contains my practice code for understanding how CSS decides which styles are applied when multiple rules target the same element.

I learned that the CSS cascade can be understood through **specificity, source order/position, style type, and importance**.

## 1. Specificity

When multiple selectors target the same element, the more specific selector generally wins.

The basic order I learned is:

**Element selector → Class / Attribute selector → ID selector**

For example, in my code:

```css
p {
  color: yellow;
}

.white-text {
  color: white;
}

#outer-box {
  border: 20px solid purple;
}
```

* `p` is an **element selector**.
* `.white-text` is a **class selector** and is more specific than `p`.
* `#outer-box` is an **ID selector** and has greater specificity than either.

This is why the `<p class="white-text">` elements display **white text** instead of the yellow color assigned by `p`.

## 2. Position / Source Order

When competing CSS rules have the **same specificity and importance**, the rule appearing later in the stylesheet wins.

This helped me understand why the order of CSS declarations can matter when selectors have equal strength.

## 3. Type of CSS

I also learned about the different ways CSS can be applied:

* External CSS
* Internal CSS
* Inline CSS

In this project, I used **external CSS** through:

```html
<link rel="stylesheet" href="./style.css">
```

When rules have otherwise comparable priority, the cascade considers how the styles are introduced and their position in the cascade.

## 4. `!important`

I learned that adding `!important` gives a declaration very high priority compared with normal declarations.

For example:

```css
p {
  color: yellow !important;
}
```

This can override normal competing declarations, although it should be used carefully because excessive use makes CSS harder to maintain.

## What I Practiced

This project helped me understand that CSS does not simply apply every rule independently. When multiple rules target the same element, the **cascade determines which declaration wins** based on priority, specificity, and source order.
