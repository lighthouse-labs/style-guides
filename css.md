# CSS Style Guide

## Table of Contents

- [Specificity](#specificity)
- [Block, Element, Modifier (BEM)](#block,-element,-modifier-(bem))
- [ID Selectors](#id-selectors)
- [Flat Selectors](#flat-selectors)
- [License](#license)

## Specificity

**A note about [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity).**

Overly specific CSS rules can cause a lot of frustration when our css doesn't work as intended. For example, in the following code snippet, what will the color of the title be? 

```css
.header h1 {
  color: blue;
}
.highlight {
  color: yellow;
}
```
```html
<div class="header">
  <h1 class="highlight">What color will I be?</h1>
</div>
```

We want it to be yellow, but because of a specificity mistake, it will be blue.

> For more on this subject:
>   * [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) on dealing with specificity.
>   * [CSS trick's article](https://css-tricks.com/strategies-keeping-css-specificity-low/) on keeping css specificity low.

## Block, Element, Modifier (BEM)

**BEM**, or “Block-Element-Modifier”, is a _naming convention_ for classes in HTML and CSS.

> For a more detailed description of BEM, check out CSS Trick's [BEM 101](https://css-tricks.com/bem-101/)

We encourage using them BEM naming convention for classes in HTML and CSS for these reasons:

* It helps create clear, strict relationships between CSS and HTML
* It allows for less nesting and lower specificity
* It helps in building scalable stylesheets

**Bad**

```html
<article class="tweet featured">
  <header class="header">
    <img class="avatar">
  </header>
</article>
```

**Good**

```html
<article class="tweet tweet--featured">
  <header class="tweet__header">
    <img class="tweet__avatar">
  </header>
</article>
```

```css
.tweet { } /* block */
.tweet--featured { } /* modifier */
.tweet__header { } /* element */
.tweet__avatar { } /* element */
```

* `.tweet` is the "block" and represents an entire component
* `.tweet__header` is an "element" and represents a descendant of `.tweet` that helps compose the block as a whole.
* `.tweet--featured` is a "modifier" and represents a different state or variation on the `.tweet` block.

## Flat Selectors

Avoid unnecessarily increasing the specificity by nesting selectors. Instead, try using a single selector. 

**Bad**

```css
body .module .title {
  color: red;
}
```

**Good**

```css
.module__title {
  color: red;
}
```

## ID selectors

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of specificity to your rule declarations, and they are not reusable.

**Bad**

```css
#page__title {
  color: red;
}
```

**Good**

```css
.page__title {
  color: red;
}
```



**[⬆ back to top](#table-of-contents)**
