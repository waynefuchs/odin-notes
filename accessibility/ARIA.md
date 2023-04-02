- [WAI-ARIA (Accessibility Tree)](#wai-aria-accessibility-tree)
  - [Links](#links)
  - [Aria Live Regions](#aria-live-regions)
  - [Hiding Content from the Accessibility Tree](#hiding-content-from-the-accessibility-tree)
  - [ARIA Properties](#aria-properties)
    - [Name Property](#name-property)
      - [`aria-label`](#aria-label)
      - [`aria-labeledby`](#aria-labeledby)
    - [Description Property](#description-property)
      - [`aria-describedby`](#aria-describedby)
  - [ARIA Guidelines](#aria-guidelines)
  - [ARIA Limitations](#aria-limitations)

# WAI-ARIA (Accessibility Tree)

WAI-ARIA: Web Accessibility Initiative’s Accessible Rich Internet Applications specification, often referred to as just "ARIA."

After the DOM is generated, an _Accessibility Tree_ is created, which is used by the OS to provide accessibility through assistive technologies. ARIA is the interface that is used to interact with the accessibility tree.

## Links

| Title                                                                                                  | Site        | Description                                       |
| ------------------------------------------------------------------------------------------------------ | ----------- | ------------------------------------------------- |
| [Accessibility tree](https://developer.mozilla.org/en-US/docs/Glossary/Accessibility_tree)             | MDN         | Accessibility tree                                |
| [ARIA Important Terms](https://www.w3.org/TR/wai-aria/#dfn-landmark)                                   | W3C         | Glossary of ARIA Terms                            |
| [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/)                      | W3C         | How to use ARIA for every applicable HTML element |
| [ARIA live regions](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) | MDN         | How to announce page content changes              |
| [An in-depth guide to ARIA roles](https://www.a11yproject.com/posts/an-indepth-guide-to-aria-roles/)   | a11yproject |                                                   |

## Aria Live Regions

Make dynamic content changes in a way that can be announced by assistive technologies.

`aria-live=""`

| Politeness | Description                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| off        | suppress element announcement. **default** for most elements, usually does not have to be explicitly set |
| polite     | Normally the "correct" choice. Announce when accessibility is idle.                                      |
| assertive  | Used for time-sensitive/critical notifications. Can be extremely annoying and disruptive. Use sparingly. |

## Hiding Content from the Accessibility Tree

- `aria-hidden='true'` works for most elements and will leave the element visible to sighted users

> ⚠️ Warning: `aria-hidden='true'` will cause all children elements to also be hidden

> ⚠️ Warning: `aria-hidden='true'` should not be applied to elements that can receive focus (eg: form elements)

- `display: none` removes from visual dom and accessibility tree
- `visibility: hidden` hides from visual dom and accessibility tree (placeholder space is held)
- Any images or content added through CSS will be invisible to accessibility

## ARIA Properties

### Name Property

The "accessible name." The name that assistive tech presents to a user, and what separates elements of the same type from one another.

> Note: on "native labels": This is just the Aria Name that an element has. (example: `<h1>Native Label</h1>`)

#### [`aria-label`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label)

Overrides native labels and modifies the ARIA "Name" property **in cases where the label text is not visible on screen**. (prefer native labels or `aria-labeledby`)

This attribute does not work on every element. (Notably has no effect on `<div>` or `<span>` elements).

Do **NOT** use this (or any other) attribute to work around phonetic (mis)pronunciation.

```html
<!-- "X" has less meaning than "close menu" to someone that is visually impaired -->
<button type="button" aria-label="Close menu">X</button>

<!-- Another example is to differentiate between navigation elements -->
<nav aria-label="site navigation">...</nav>
<nav aria-label="page navigation">...</nav>
```

#### [`aria-labeledby`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby)

Overrides all other labels, including `aria-label` and is the preferred attribute, as it uses visible elements in labeling.

```html
<!-- This button will be read aloud as: Shirts, shop now, button -->
<!-- Even though the #label element is hidden, the screen reader will correctly read the button label -->
<h2 id="label" style="visibility: hidden">Shirts</h2>
<button id="shop-btn" aria-labelledby="label shop-btn">Shop Now</button>
```

### Description Property

An "accessible description" of an element, or an extension of the name / what type of information is contained in the element.

#### `aria-describedby`

Modify the ARIA Description Property.

```html
<!-- When the input password field gets focus, Orca reads:
    "Password colon. Password text. Password must be at least 10 characters long. Focus Mode." -->
<label
  >Password:
  <input type="password" aria-describedby="password-requirements" />
</label>
<span id="password-requirements"
  >Password must be at least 10 characters long.</span
>
```

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
