- [WAI-ARIA](#wai-aria)
  - [Links](#links)
  - [Gotchas](#gotchas)
  - [The Accessibility Tree](#the-accessibility-tree)
  - [Aria Properties](#aria-properties)
    - [Name](#name)
    - [Description](#description)
  - [ARIA Guidelines](#aria-guidelines)
  - [ARIA Limitations](#aria-limitations)

# WAI-ARIA

WAI-ARIA: Web Accessibility Initiative’s Accessible Rich Internet Applications specification, often referred to as just "ARIA."

## Links

| Title                                                                             | Site | Description                                       |
| --------------------------------------------------------------------------------- | ---- | ------------------------------------------------- |
| [ARIA Important Terms](https://www.w3.org/TR/wai-aria/#dfn-landmark)              | W3C  | Glossary of ARIA Terms                            |
| [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/) | W3C  | How to use ARIA for every applicable HTML element |

## Gotchas

- Don't work around screen reader mispronunciations using things like `aria-label`, as that changes the captions and is what will be displayed on braille readers. People using screen readers are used to the mispronunciation quirks and prefer that you leave things as they are and let them work around it in their software, if they choose.

## The Accessibility Tree

The Accessibility Tree exists, based upon the DOM, but outside of it and can only be interacted with through ARIA properties, and not directly.

## Aria Properties

### Name

The "accessible name." What assistive tech announce to a user, and what separates elements of the same type from one another.

### Description

This is what assistive technologies announce in addition to its accessible name.

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
