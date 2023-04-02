# Semantic HTML

HTML Semantics are important because they provide _meaning_ and _context_ to content.

A tag like `<p></p>` provides meaning, but not context. That paragraph could be your company motto, a sales pitch, or a paragraph in an article. The browser doesn't know.

> Note: In forms, always use `type="<intended use>"`. (See: #type in [forms.md](forms.md#type))

## Semantic HTML Tags

## Headings `<h1>` ... `<h6>`

Headings mark sections of a page. Headings are important to get right for accessibility. A visually impaired person will typically listen to the headings of a page first to orient themselves to the content on the page before proceeding. Sort of like a telephone menu, or like a book index.

Use the heading numbers in nested sequential order.

## Button `<button>`

Screen readers will pronounce as: "Button Text, Button." (eg: "Submit, Button")

## Table `<table>`

If you are providing tabular data to your user, use the `<table>` element to make it easier to navigate and understand the data being presented.

## Label `<label>`

Provide labels for form elements to give a larger surface area to click on and bring the form element into focus and provide context to the field.

## Semantic HTML Landmark Elements

There are [seven HTML sectioning elements](https://en.wikipedia.org/wiki/HTML_landmarks) which inherit default landmark roles.

> NOTE:
> `role="<role>"` is rarely needed due to semantic html and should not be set manually, with few exceptions.
> Use the proper semantic element wherever possible. See [Sectioning HTML Element Misuse](https://en.wikipedia.org/wiki/HTML_landmarks#Misuse) from wikipedia.

|     | html element | associated landmark role                                                                        |
| --- | ------------ | ----------------------------------------------------------------------------------------------- |
| 1   | aside        | [complementary](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/complementary.html) |
| 2   | footer       | [contentinfo](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/contentinfo.html)     |
| 3   | form         | [form](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/form.html)                   |
| 4   | header       | [banner](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/banner.html)               |
| 5   | main         | [main](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/main.html)                   |
| 6   | nav          | [navigation](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/navigation.html)       |
| 7   | section      | [region](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/region.html)               |

## Landmark Roles

Landmarks mark regions of a page.

| name          | description                                                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| banner        | `header`: Contains things like a logo, identity of the site sponsor, site-specific search, etc                                 |
| complementary | `aside`: Content that complements the main content.                                                                            |
| contentinfo   | `footer`: Copyright, privacy, and accessibility statements                                                                     |
| form          | `form`: Grouped inputs, except search (see search landmark)<br/>Form should be identified in an `h` tag using `aria-labeledby` |
| main          | `main`: primary content on the page                                                                                            |
| navigation    | `nav`: list of links that are intended to be used for navigation of the website or page                                        |
| region        | `<section aria-labelledby="region-name">`                                                                                      |
| search        | search functionality for a website (`role=search` is required for this landmark)                                               |
