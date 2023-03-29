- [WAI-ARIA](#wai-aria)
  - [Links](#links)
  - [Accessibility Tree](#accessibility-tree)
  - [Aria Properties](#aria-properties)
    - [Name](#name)
      - [`aria-label`](#aria-label)
    - [Description](#description)
      - [`aria-describedby`](#aria-describedby)
  - [ARIA Guidelines](#aria-guidelines)
  - [ARIA Limitations](#aria-limitations)

# WAI-ARIA

WAI-ARIA: Web Accessibility Initiative’s Accessible Rich Internet Applications specification, often referred to as just "ARIA."

## Links

| Title                                                                                      | Site | Description                                       |
| ------------------------------------------------------------------------------------------ | ---- | ------------------------------------------------- |
| [Accessibility tree](https://developer.mozilla.org/en-US/docs/Glossary/Accessibility_tree) | MDN  | Accessibility tree                                |
| [ARIA Important Terms](https://www.w3.org/TR/wai-aria/#dfn-landmark)                       | W3C  | Glossary of ARIA Terms                            |
| [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/)          | W3C  | How to use ARIA for every applicable HTML element |

## Accessibility Tree

After the DOM is generated, an _Accessibility Tree_ is created, which is used by the OS to provide accessibility through assistive technologies. The Accessibility tree can not be directly queried or modified, except through the ARIA attributes.

## Aria Properties

### Name

The "accessible name." What assistive tech announces to a user, and what separates elements of the same type from one another. This is what assistive technologies announce in addition to its accessible name.

#### `aria-label`

Overrides native labels and modifies the ARIA "Name" property.

This attribute does not work on every element. (Notably has no effect on `<div>` or `<span>` elements).

Do **NOT** use this (or any other) attribute to work around phonetic (mis)pronunciation.

```html
<!-- "X" has less meaning than "close menu" to someone that is visually impaired -->
<button type="button" aria-label="Close menu">X</button>

<!-- Another example is to differentiate between navigation elements -->
<nav aria-label="site navigation">...</nav>
<nav aria-label="page navigation">...</nav>

<!-- Here's how to use another element as the label -->
<!-- This button will be read as: Shirts, shop now, button -->
<!-- Even if the #label element is hidden, the screen reader will correctly read the button label -->
<h2 id="label">Shirts</h2>
<button id="shop-btn" aria-labelledby="label shop-btn">Shop Now</button>
```

### Description

#### `aria-describedby`

## ARIA Guidelines

1. Always use native HTML elements and attributes over ARIA wherever possible
2. Never change native semantics, unless you have no other choice
3. All interactive ARIA controls must be usable with a keyboard
4. Never use `role='presentation'` or `aria-hidden='true'` on focusable elements
5. All interactive elements must have an accessible name

## ARIA Limitations

- Can not modify an element's appearance
- Can not modify an element's behavior
- Can not add focusability
- Can not add keyboard event handling
