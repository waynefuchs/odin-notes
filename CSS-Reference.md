- [CSS Notes](#css-notes)
  - [Browser Default CSS](#browser-default-css)
  - [CSS Resets](#css-resets)
  - [Specificity](#specificity)
  - [Selectors](#selectors)
    - [Links](#links)
    - [My Selector Notes](#my-selector-notes)
    - [Examples](#examples)
  - [Positioning](#positioning)
  - [CSS Functions](#css-functions)
    - [`calc()`](#calc)
    - [`clamp` and `min` and `max`](#clamp-and-min-and-max)
      - [`clamp(smallest, ideal, largest)`](#clampsmallest-ideal-largest)
      - [`min(a, b, ...)`](#mina-b-)
      - [`max(a, b, ...)`](#maxa-b-)

# CSS Notes

## Browser Default CSS

You can look at the default.css file for each of the browsers.

* [Chrome](https://chromium.googlesource.com/chromium/blink/+/refs/heads/main/Source/core/css/html.css)

## CSS Resets

* [The Meyer Reset](https://meyerweb.com/eric/tools/css/reset/): Simple and basically removes every default style.
* [Normalize.css](https://nicolasgallagher.com/about-normalize-css/): Attempts to give all browsers the same starting point.
* [History on Resets](https://css-tricks.com/reboot-resets-reasoning/): Interesting and a few other options.
* [Browser Default Styles](https://browserdefaultstyles.com/): Type in an element, get the differences between browsers

## Specificity

* [Specifics on CSS Specificity](https://css-tricks.com/specifics-on-css-specificity/): eg:(0,0,0,0)

## Selectors

### Links

[Complex Selectors](https://learn.shayhowe.com/advanced-html-css/complex-selectors/)

### My Selector Notes

* `*`: Selects all elements
* `.class`: select all elements with specified class
* `.classA.classB`: select all elements with both classA and classB
* `.classA .classB`: select all elements with classB that is a descendant of an element with classA. (Does *not* have to be a direct descendant! eg: <body class="classA"><div><span><p><img class="classB">... is valid!)
* `#id`: select the element with specified id
* `element.class` (`div.class-name`): select all elements that also have specified class
* `element, element` (`div, p`): select all <div> and <p>
* `element element`: (`div p`): select all <p> inside of <div>.
* `element1 > element2`: select all elements of type element2 that are direct children of element1. (selectors, such as #id and .class can be used)
* `element1 + element2`: select the first element2 that is placed immediately after element1 elements.
* `element1 ~ element2`: select all element2 siblings that are placed after element1.
* `[attribute]` (`[class]`): select all elements with a class assigned.)
* `[attribute=value]` (`[target=_blank]`): Select all anchor tags that open a new tab.
* `[attribute^="value"]`: attribute's assigned value begins with `value` (an example would be to change the styling for 'https' links vs 'http' links - not that you would want to do this?)
* `[attribute$="value"]`: attribute's assigned value ends with `value`
* `[attribute*="value"]`: attribute contains `value` (eg: match all `sitename.com` links, and highlight them.)
* `element:nth-child(2n-1)` (2n=even; 2n-1=odd): style every 'nth' child, as specified by the formula in parenthesis.

### Examples

``` css
[src] {
  /* This will target any element that has a src attribute. */
}

img[src] {
  /* This will only target img elements that have a src attribute. */
}

img[src="puppy.jpg"] {
  /* This will target img elements with a src attribute that is exactly "puppy.jpg" */
}

[class^='aus'] {
  /* Classes are attributes too!
    This will target any class that begins with 'aus':
    class='austria'
    class='australia'
  */
}

[src$='.jpg'] {
  /* This will target any src attribute that ends in '.jpg':
  src='puppy.jpg'
  src='kitten.jpg'
  */
}

[for*='ill'] {
  /* This will target any for attribute that has 'ill' anywhere inside it:
  for="bill"
  for="jill"
  for="silly"
  for="ill"
  */
}
```

## [Positioning](test/position.html)

The css property: `position: [static|absolute|relative|fixed|sticky]`

Accessibility: `fixed` and `absolute` can obscure other content when the page is zoomed and can create accessibility issues.

Performance: `fixed` and `sticky` can cause stutter and lag, depending on the elements' contents. One fix is to add `will-change: transform;` to that element's styling.

* `static`

  Static is the default.

* `relative`
  
  Behaves like static, except 'top|right|bottom|left' moves the element, keeping the initial reserved positioning intact.

  Note: relative positioning is rarely used in conjunction with 'top|right|bottom|left' due to the issues that would cause, and instead is usually paired with a child of position type absolute in order to create a container for another element to position absolutely inside of.

* `absolute`

  An absolute positioning removes the element from the document flow, and everything else on the page will render as if the absolutely positioned element does not exist.

  The 'top|right|bottom|right' properties will absolutely position the element to an x,y position space in that parent container. The parent to be positioned inside of can not have a position property set to static, it must be 'relative|absolute|sticky|fixed', and it will traverse upwards through the DOM until it arrives at an appropriate parent, likely 'head'.

* `fixed`

  Behaves similar to absolute positioning with a few caveats.

  1. Even during a scroll event, the element will remain stationary on the screen in the prescribed position.
  2. The top|right|bottom|left position is based on the viewport. not a parent element.

* `sticky`

  Combination of relative and fixed into an interesting positioning property.

  Allows you to put an element onto the page and it will stay there as you (attempt to) scroll past it.


## CSS Functions

[ALL CSS Functions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions)

### `calc()`

* Mix Units
* Nesting: `calc(10vw + calc(var(--header-height) + var(--footer-height)));`
* Keep in mind that calc() is a tool to be used, but there are likely better solutions and tools available.

### `clamp` and `min` and `max`

[web.dev: demonstration](https://web.dev/min-max-clamp/)

* Inputs to these functions can be combined with each other.
* +, -, *, and / may be used.

#### `clamp(smallest, ideal, largest)`

A way to clamp values into a range.

#### `min(a, b, ...)`

Will return the low value from a list of values. Useful in situations such as: `min(150px, 100%);` where an image may be allowed to use 150px if they are available, and otherwise the image will scale with the width being the available space.

You can perform basic math inside this function. eg: `min(150px, 100vw - 2rem);`.

#### `max(a, b, ...)`

Functions the same way as min, except returning the larger of the two supplied inputs. It can function as a guard clause against someone that has set a large font to prevent some important bit of information from being lost off screen.

`width: max(100px, 4em, 50%);` - in this case it is possible for the user to size their viewport to a size less than 100px, and 4em could be very small if the user has chosen a default font size to be very small, at which point 100px would be chosen here as kind of a guard clause.