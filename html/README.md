- [HTML Notes](#html-notes)
  - [Generic Attributes](#generic-attributes)
  - [Elements](#elements)
    - [Anchor](#anchor)
    - [Comments](#comments)
    - [Content](#content)
    - [Figure and Caption](#figure-and-caption)
    - [Heading](#heading)
    - [Image](#image)
    - [Lists](#lists)
    - [List Items](#list-items)
    - [Description Lists](#description-lists)
    - [Paragraph](#paragraph)
    - [Text Options](#text-options)
  - [HTML Boilerplate](#html-boilerplate)
  - [HTML Styling](#html-styling)

# HTML Notes

## Generic Attributes

- `id=""`: Identify a _specific_ HTML element (**AVOID** where possible - example "allowed" uses: forms and accessibility)
- `class=""`: Identify a group of HTML elements

## Elements

### Anchor

Links to other locations on this page, or another page, with "[link text]" being the visible text on the page.

Note: Other elements can be placed inside the anchor tag to make them behave as a link.

```html
<a>link text</a>
```

- `href=""`: url to visit when clicked on.
- `target=""`: specifies where to open the linked document
  - \_blank: new window or tab
  - \_self: default
  - \_parent: targets the parent frame
  - \_top: opens in the full body of the window
  - \_framename: targets a specific iframe.

### Comments

```html
<!-- Single Line -->
<!-- 
    Multi Line
-->
```

### Content

Using proper content elements helps with Search Engine Optimization (SEO).

- `<address></address>`: A container to hold contact information.
- `<article></article>`: Can be considered as a self-contained widget or piece of content. (eg: each individual day in a weather forecast.)
- `<aside></aside>`: A container to separate content that is indirectly related to the document's main content.
- `<footer></footer>`: Bottom of the page.
- `<header></header>`: Top of the page.
- `<main></main>`: Identify the main section of the webpage. (Required for Reader mode)
- `<nav></nav>`: Site navigation
- `<section></section>`: General purpose container.

### Figure and Caption

```html
<figure>
  <img />
  <figcaption>captionText</figcaption>
</figure>
```

### Heading

`<h1></h1>` -> `<h6></h6>`: Number indicates importance.

### Image

`<img>`: Image element

- `src=""`: location of image
- `alt=""`: **REQUIRED** Text to be displayed in the event the image fails to load, or used by screen readers.

### Lists

Note: List containers require a list item child.

- `<ul></ul>`: Unordered List (bullet points)
- `<ol></ol>`: Ordered List (numeric)

### List Items

- `<li>itemText</li>`: display the item text

### Description Lists

- `<dl></dl>`: Description List, which requires a `<dt></dt>` or `<dd></dd>` tag. Behaves like `ul` or `ol`.
- `<dt>descriptionTitle</dt>`: display the item description title
- `<dd>descriptionText</dd>`: display the item description text

### Paragraph

`<p></p>`: Paragraph text.

### Text Options

`<em></em>`: Emphasize text (typically italic), screen readers with pronounce emphasized text using verbal stress. (Use this instead of `<i></i>`)
`<strong></strong>`: Identify text with strong importance. (Use this instead of `<b></b>`)

## HTML Boilerplate

Easily generated with the Emmet `!` shortcut.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><!--Document Title--></title>
  </head>
  <body></body>
</html>
```

## HTML Styling

[Google Style Guide](https://google.github.io/styleguide/htmlcssguide.html)
[Adobe Style Guide](https://developer.adobe.com/commerce/php/coding-standards/html-style-guide/)
