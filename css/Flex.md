- [Flexbox](#flexbox)
  - [Flex Container](#flex-container)
  - [Flex Item](#flex-item)
  - [`flex` Shortcut (`flex-flow` + `flex-shrink` + `flex-basis`)](#flex-shortcut-flex-flow--flex-shrink--flex-basis)
  - [`flex-flow` Shortcut (`flex-direction` + `flex-wrap`)](#flex-flow-shortcut-flex-direction--flex-wrap)
  - [Flex Direction](#flex-direction)
  - [Flex Wrap](#flex-wrap)
  - [Gap](#gap)
  - [Justify Content and Align Items](#justify-content-and-align-items)
  - [Recipes](#recipes)
  - [Full page alternative CSS box model](#full-page-alternative-css-box-model)

# Flexbox

## Flex Container

Use the `display` property to define a flex [block or inline] container.

``` css
.flex-container {
  display: flex;            /* block (full row) */
  display: inline-flex;     /* respects margins and width */

  /* v---- DEFAULTS: (for `display: flex;`) */
  display: flex;

  /* Items display in a row (the flex-direction property's default is row). */
  flex-direction: row;

  /*  The items start from the start edge of the main axis. */
  justify-content: start;

  /* The items do not stretch on the main dimension, but can shrink. */
  flex-grow: 0;
  flex-shrink: 1;

  /* The items will stretch to fill the size of the cross axis. */


  /* The flex-basis property is set to auto. */
  flex-basis: auto;

  /* The flex-wrap property is set to nowrap. */
    flex-wrap: nowrap;
}
```

## Flex Item

Place any element nested into a flex container to identify that element as a flex item.

## `flex` Shortcut (`flex-flow` + `flex-shrink` + `flex-basis`)

``` css
.flex-item {
  flex: auto: /* Equivilent to: `flex 1 1 0

  /* flex: (flex-grow) (flex-shrink) (flex-basis)%; */
  flex: 1 0 auto; /* grow with a factor of 1, don't shrink, auto initial size */

  /* EQUIVALENT */
  /* ratio to grow element as page is resized, relative to the grow value of sibling elements. */
  flex-grow: 1;
  
  /* ratio to shrink element as page is resized, relative to the shrink value of sibling elements. */
  flex-shrink: 0;

  /* This sets the initial size of the element before growing or shrinking and can affect behavior. Is overridden by the box-sizing property. */
  flex-basis: auto;
}
```
## `flex-flow` Shortcut (`flex-direction` + `flex-wrap`)

A shorthand property for `flex-direction` and `flex-wrap`, in that order.

``` css
.flex-container {
  flex-flow: column wrap;
}
```

## Flex Direction

When set to `row`, flex-basis refers to the initial `width` property and "main axis" set to left -> right, and cross axis set to top -> bottom.

`row-reverse` is just like `row`, except in the opposite reading direction.

When set to `column`, flex-basis refers to the initial `height` property and "main axis" set to top -> bottom, and cross axis set to left -> right.

`column-reverse` is just like `column`, except in the opposite reading direction.

``` css
.flex-container {
  flex-direction: row;    /* [default] horizontal */
  flex-direction: row-reverse;
  flex-direction: column; /* vertical */
  flex-direction: column-reverse;
}
```

## Flex Wrap

Mostly a boolean (with an additional reverse) to turn wrapping on and off.

``` css
.flex-container {
    flex-wrap: nowrap;
    flex-wrap: wrap;
    flex-wrap: wrap-reverse;
}
```

## Gap

`gap`: Applied to a flex container, will add a gap between items in the container, much like the `margin` property.

`column-gap`: Creates a gap along the **main axis**.

`row-gap`: Creates a gap along the **cross axis**.

``` css
.flex-container {
  gap: 8px;
  column-gap: 3px;
  row-gap: 20px;  
}
```

## Justify Content and Align Items

(Horizontal and Vertical alignment)

`justify-content`: Applied to a flex container to control item justification in the **main axis**.

There is no **main axis** single item property. Instead, margins can be used to add gaps in content, such as a menu bar where a gap between menu items is desired. This can be accomplished with something like: `margin-left: auto;` on the gap element.

`align-items`: Applied to a flex container to control the item justification in the **cross axis**.

`align-self`: Applied to a flex **item** to control that item's justification individually, apart from the others in the container on the **cross axis**.


``` css
.flex-container {
  /* Positional Alignment */
  justify-content: center;        /* center all items */
  justify-content: start;         /* pack items at the start (in main-axis direction) */
  justify-content: end;           /* pack items at the end */
  justify-content: flex-start;    /* getting deprecated(?) */
  justify-content: flex-end;      /* getting deprecated(?) */
  justify-content: left;          /* pack items at the left */
  justify-content: right;         /* pack items at the right */

  /* Distributed Alignment */
  justify-content: space-between; /* evenly place space between items in container */
  justify-content: space-around;  /* evenly place space between items in container with half size space at edges */
  justify-content: space-evenly;  /* evenly place space between and around items in container */
  justify-content: stretch;       /* distribute items evenly, stretching items with 'aut'-size property */

  /* Overflow Alignment */
  justify-content: safe center;
  justify-content: unsafe center;
}
```









## Recipes

## Full page alternative CSS box model

Default is "Standard Box Model", where you have to calculate margin, border, padding, and content. (margin + border + padding + content = size of box)

Alternative (border-box) Box Model is just (margin + width || height) for each dimension.

``` css
html {
  box-sizing: border-box;
}
*, *::before, *::after {
  box-sizing: inherit;
}
```