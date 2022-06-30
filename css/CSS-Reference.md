- [CSS Notes](#css-notes)
  - [Browser Default CSS](#browser-default-css)
  - [CSS Resets](#css-resets)
  - [Specificity](#specificity)
  - [Selectors](#selectors)
    - [Links](#links)
    - [My Selector Notes](#my-selector-notes)
    - [Examples](#examples)

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

