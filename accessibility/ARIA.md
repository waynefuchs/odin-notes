- [WAI-ARIA (Accessibility Tree)](#wai-aria-accessibility-tree)
  - [Links](#links)
  - [Hiding Content from the Accessibility Tree](#hiding-content-from-the-accessibility-tree)
  - [ARIA Properties](#aria-properties)
    - [Name Property](#name-property)
      - [`aria-label`](#aria-label)
      - [`aria-labeledby`](#aria-labeledby)
    - [Description Property](#description-property)
      - [`aria-describedby`](#aria-describedby)
  - [ARIA Guidelines](#aria-guidelines)
  - [ARIA Limitations](#aria-limitations)
  - [ARIA Roles](#aria-roles)
    - [Live Region Roles](#live-region-roles)
      - [`aria-live="<politeness>"`](#aria-livepoliteness)
    - [Landmark Roles](#landmark-roles)
    - [Abstract Roles](#abstract-roles)
    - [Document Structure Roles](#document-structure-roles)
    - [Widget Roles](#widget-roles)
      - [Widgets](#widgets)
      - [Composite Widgets (containers for widgets)](#composite-widgets-containers-for-widgets)
    - [Window Roles](#window-roles)
    - [`Restricted Use` Role Tags](#restricted-use-role-tags)

# WAI-ARIA (Accessibility Tree)

WAI-ARIA: Web Accessibility Initiative’s Accessible Rich Internet Applications specification, often referred to as just "ARIA."

After the DOM is generated, an _Accessibility Tree_ is created, which is used by the OS to provide accessibility through assistive technologies. ARIA is the interface that is used to interact with the accessibility tree.

## Links

| Title                                                                                                  | Site        | Description                                                     |
| ------------------------------------------------------------------------------------------------------ | ----------- | --------------------------------------------------------------- |
| [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/)                      | W3C         | How to use ARIA for every applicable HTML element               |
| [Accessibility tree](https://developer.mozilla.org/en-US/docs/Glossary/Accessibility_tree)             | MDN         | Short Accessibility tree overview                               |
| [WAI-ARIA Roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)                | MDN         | ARIA role reference including semantic HTML equivalent elements |
| [An in-depth guide to ARIA roles](https://www.a11yproject.com/posts/an-indepth-guide-to-aria-roles/)   | a11yproject | Explanation of and examples for usage for ARIA roles.           |
| [ARIA Important Terms](https://www.w3.org/TR/wai-aria/#dfn-landmark)                                   | W3C         | Glossary of ARIA Terms                                          |
| [ARIA live regions](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) | MDN         | How to announce page content changes                            |

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

> ⓘ Note: on "native labels": This is just the Aria Name that an element has. (example: `<h1>Native Label</h1>`)

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
<label>
  Password:
  <input type="password" aria-describedby="password-requirements" />
</label>
<span id="password-requirements">
  Password must be at least 10 characters long.
</span>
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

## ARIA Roles

Manually, **roles** are used to describe elements by setting [ARIA states and properties](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes) in a way that is not implemented or does not have full support using semantic HTML to fill gaps in assistive technologies.

> ⚠️ Caution: Do not manually set `role="<role>"` if at all possible.

### Live Region Roles

Present dynamic content changes in a way that can be announced by assistive technologies (see also [`aria-live="<politeness>"`](#aria-livepoliteness))

> ⓘ Note: These roles are used to define _**dynamic**_ elements with information that is normally visually conveyed.

| Role    | Description                                                                                                                   |
| ------- | ----------------------------------------------------------------------------------------------------------------------------- |
| alert   | For an important element with (usually) time-sensitive information                                                            |
| log     | Information in this element is added in a logical order and older messages may disappear over time                            |
| marquee | denotes non-essential information which changes frequently                                                                    |
| status  | contains advisory information for the user that is not important enough to be an alert                                        |
| timer   | denotes a numerical counter listing the amount of elapsed time from a starting point or the remaining time until an end point |

#### `aria-live="<politeness>"`

| Politeness | Description                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| off        | suppress element announcement. **default** for most elements, usually does not have to be explicitly set |
| polite     | Normally the "correct" choice. Announce when accessibility is idle.                                      |
| assertive  | Used for time-sensitive/critical notifications. Can be extremely annoying and disruptive. Use sparingly. |

### Landmark Roles

Landmarks mark regions of a page.

> ⓘ Note: See my [Semantic HTML](./SemanticHTML.md) page.

| name          | description                                                                                                                      |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| banner        | `<header>`: Contains things like a logo, identity of the site sponsor, site-specific search, etc                                 |
| complementary | `<aside>`: Content that complements the main content.                                                                            |
| contentinfo   | `<footer>`: Copyright, privacy, and accessibility statements                                                                     |
| form          | `<form>`: Grouped inputs, except search (see search landmark)<br/>Form should be identified in an `h` tag using `aria-labeledby` |
| main          | `main`: primary content on the page                                                                                              |
| navigation    | `nav`: list of links that are intended to be used for navigation of the website or page                                          |
| region        | `<section aria-labelledby="region-label-id">`                                                                                    |
| search        | search functionality for a website (`role=search` is required for this landmark)                                                 |

### Abstract Roles

Only to be used by the browser to organize and streamline a document.

> ⚠️ WARNING: Do not use abstract roles.

> ⓘ Note: All data taken from this [ARIA role types](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles) page. I typed it here to spend some time looking up the elements and attributes that I'm not familiar with.

### Document Structure Roles

| Role                    | Description                                                                                          |
| ----------------------- | ---------------------------------------------------------------------------------------------------- |
| toolbar                 | A parent element containing toolbar elements                                                         |
| tooltip                 | An element containing a text bubble description, appearing on pointer hover or keyboard focus        |
| feed                    | A dynamic scrollable list of articles (bi-directional first-in-first-out)                            |
| math                    | Represents a mathematical equation                                                                   |
| presentation / ~~none~~ | (Synonyms) Remove an elements's implicit ARIA semantics from being exposed to the accessibility tree |
| note                    | Content is parenthetic or ancillary to the main content                                              |

### Widget Roles

#### Widgets

| Role       | Description                                                                                |
| ---------- | ------------------------------------------------------------------------------------------ |
| scrollbar  | element controls scrolling of content within viewing area                                  |
| searchbox  | use `<input type="search">` instead if at all possible                                     |
| separator  | a divider; between tools or content (use `<hr>` where possible)                            |
| slider     | element is an input type and has a range (min/max)                                         |
| spinbutton | an input type that has several discrete choices                                            |
| switch     | Similar to a checkbox, but with 'on' and 'off' instead of 'checked' and 'unchecked'        |
| tab        | indicates an interactive element inside a tablist that will display an associated tabpanel |
| tabpanel   | a container for an associated tab (label)                                                  |
| treeitem   | an item in a hierarchial tree (list)                                                       |

#### Composite Widgets (containers for widgets)

| Role     | Description                                                                     |
| -------- | ------------------------------------------------------------------------------- |
| combobox | A named input field with a popup providing possible values for that input field |
| menu     | a list of choices for the user                                                  |
| menubar  | a list of choices to the user of actions or functions                           |
| tablist  | A container for a set of tabs                                                   |
| tree     | A container to hold a list of tree items                                        |
| treegrid | An container element whose children can be expanded and collapsed               |

### Window Roles

| Role        | Description                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------- |
| alertdialog | Modal alert dialog that interrupts a user's workflow to communicate an important message with required response or action |
| dialog      | A dialog element that is separate from teh rest of the page's content. Can be modal or non-modal.                         |

### `Restricted Use` Role Tags

This is a list of roles that are not recommended for use (not listed above), grouped by type and acceptability.

- ❌ No reason to use
- ⚠️ Only use when an appropriate semantic tag does not exist

| Role                     | Type               | Use | Consider Alternative               |
| :----------------------- | ------------------ | --- | ---------------------------------- |
| command                  | Abstract           | ❌  |                                    |
| composite                | Abstract           | ❌  |                                    |
| input                    | Abstract           | ❌  |                                    |
| landmark                 | Abstract           | ❌  |                                    |
| range                    | Abstract           | ❌  |                                    |
| roletype                 | Abstract           | ❌  |                                    |
| section                  | Abstract           | ❌  |                                    |
| sectionhead              | Abstract           | ❌  |                                    |
| select                   | Abstract           | ❌  |                                    |
| structure                | Abstract           | ❌  |                                    |
| widget                   | Abstract           | ❌  |                                    |
| window                   | Abstract           | ❌  |                                    |
| application              | Document Structure | ⚠️  |                                    |
| article                  | Document Structure | ⚠️  | `<article>`                        |
| cell                     | Document Structure | ⚠️  | `<td>`                             |
| columnheader             | Document Structure | ⚠️  | `<th scope="col">`                 |
| definition               | Document Structure | ⚠️  | `<dfn>`                            |
| directory                | Document Structure | ⚠️  |                                    |
| document                 | Document Structure | ⚠️  |                                    |
| figure                   | Document Structure | ⚠️  | `<figure>`                         |
| group                    | Document Structure | ⚠️  |                                    |
| heading                  | Document Structure | ⚠️  | `<h1>` .. `<h6>`                   |
| img                      | Document Structure | ⚠️  | `<img>` or `<picture>`             |
| list                     | Document Structure | ⚠️  | `<ul>` or `<ol>`                   |
| listitem                 | Document Structure | ⚠️  | `<li>`                             |
| meter                    | Document Structure | ⚠️  | `<meter>`                          |
| row                      | Document Structure | ⚠️  | `<tr>` with `<table>`              |
| rowgroup                 | Document Structure | ⚠️  | `<thead>`, `<tfoot>`, or `<tbody>` |
| rowheader                | Document Structure | ⚠️  | `<th scope="row">`                 |
| separator                | Document Structure | ⚠️  | `<hr>`                             |
| table                    | Document Structure | ⚠️  | `<table>`                          |
| term                     | Document Structure | ⚠️  | `<dfn>`                            |
| associationlist          | Document Structure | ❌  |                                    |
| associationlistitemkey   | Document Structure | ❌  |                                    |
| associationlistitemvalue | Document Structure | ❌  |                                    |
| blockquote               | Document Structure | ❌  |                                    |
| caption                  | Document Structure | ❌  |                                    |
| code                     | Document Structure | ❌  |                                    |
| deletion                 | Document Structure | ❌  |                                    |
| emphasis                 | Document Structure | ❌  |                                    |
| insertion                | Document Structure | ❌  |                                    |
| paragraph                | Document Structure | ❌  |                                    |
| strong                   | Document Structure | ❌  |                                    |
| subscript                | Document Structure | ❌  |                                    |
| superscript              | Document Structure | ❌  |                                    |
| time                     | Document Structure | ❌  |                                    |
| button                   | Widget             | ❌  |                                    |
| checkbox                 | Widget             | ❌  |                                    |
| gridcell                 | Widget             | ❌  |                                    |
| link                     | Widget             | ❌  |                                    |
| menuitem                 | Widget             | ❌  |                                    |
| menuitemcheckbox         | Widget             | ❌  |                                    |
| menuitemradio            | Widget             | ❌  |                                    |
| option                   | Widget             | ❌  |                                    |
| progressbar              | Widget             | ❌  |                                    |
| radio                    | Widget             | ❌  |                                    |
| textbox                  | Widget             | ❌  |                                    |
| grid                     | Composite Widget   | ❌  |                                    |
| listbox                  | Composite Widget   | ❌  |                                    |
| radiogroup               | Composite Widget   | ❌  |                                    |
