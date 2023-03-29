# Keyboard Accessibility

## Links

| Title                                                                                                                                 | Description                                       |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| [ARIA Landmarks Example](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/HTML5.html)                                      | An example of how to use ARIA Landmarks on a page |
| StackOverflow: [Which elements can receive focus?](https://stackoverflow.com/questions/1599660/which-html-elements-can-receive-focus) | An old question, but has some interesting answers |
| [Focusable Elements - Browser Compatibility Table](https://allyjs.io/data-tables/focusable.html)                                      | Test based results, as there is no official list  |

## Keyboard Accessibility Guidelines

- Never remove styling for `:focus` pseudo-classes
  - Doing so makes keyboard navigation impossible.
  - Either leave them alone, tweak them if you must, such as changing `transition: scale()`
- (Best practice) Place tabbable elements in your HTML document in the order that they should be selected
- Do not mess with `tabindex=''` order (`0` should be used (`-1` to hide elements), if used at all)
- Setting `tabindex` to -1 will not allow keyboard users to tab into an element
  - Useful for preventing keyboard tabbing into hidden menus, and can be set to `0` to allow tabbing again (**_BUT_**)
    - `.focus()` can still be called on that element
    - if the user is already focused on that element when the value is set, the keyboard user may lose track of where they are on the page
    - **_a better solution_** is to use the `display:none` or `visibility:hidden` CSS properties, which affects all accessibility methods, not just keyboard input
- Non-Semantic HTML does not allow focus (?)

## Skip Links

Skip links exist to allow people using a screen reader the ability to skip past content, such as navigation menus, directly to some other (main) content.

Here is a [Codepen Skip Link Demo](https://codepen.io/waynefuchs/full/gOdEJNG).

Here is the [WebAIM Skipnav Page](https://webaim.org/techniques/skipnav/) that I used to learn most of this information.

### Skip Link Guidelines

- The first link on the page, activated with the tab key, should be the skip link.
- When activated, it should be very visible.
- Multiple skip links are unnecessary / undesirable (adding several more links does not solve the issue of having a lot of links)

### Skip Link Verbiage

1. Skip to main content
2. Skip navigation
3. Skip main navigation
4. Skip navigation links
5. Skip to content

## Link Text Guidelines

> Note: Is helpful to read link text aloud, or (better) have a screen reader read the link text aloud to ensure guidelines are met and the site is navigable.

### Abbreviated Link Text Guidelines

1. The `text content` in the `<a></a>` tag should

   - indicate where the link is taking the user
   - be brief (around 100 characters)
   - avoid using phrases such as "click here" or "this page"

2. If the link opens or downloads a file, include text that tells the user what kind of file it is as well as the file size
3. If a link opens a new tab or window with the `target="_blank"` attribute, this should be indicated to the user in some way

### Expanded Link Text Guidelines

1. Don't use the word "link" in links
2. Don't capitalize link text, even using CSS rules
3. Avoid ASCII characters, or if required use aria like so: `<span class="sr-only">Smiley face</span><span aria-hidden="true">:-)</span>`
4. Avoid using URLs as link text
5. Keep link text concise (&lt; 100 characters)
6. Restrict the number of links on a page
7. Don't link directly to downloads
8. Always alert the user when opening new windows (in link text)
9. Be aware of pagination and alphabetized links (eg: "search results page.. 1 2 3 4" or "last name: A B C ...")
10. Be mindful when using anchor links (link to anchor on same page)
11. The case for underlining links (note: the source page does not use underlined links)
12. Design with keyboard-only users in mind
    - using the `title` attribute
    - generally, apply `:hover` to `:focus`
    - never script `<a>` behavior to other HTML elements
13. Be mindful when using images as links (`alt` attribute text of "Search", "Find", or "Submit" is good, "Go" is bad)
14. Eliminate
    - broken (`<a href="http://doesNotExist">best website ever</a>`) links
    - empty (`<a href="validPage.html"></a>`) links
15. Make your links consistent
16. Test link color contrast

> NOTE: The following HTML / CSS does not appear to work in Mar 2023 in Orca Screen Reader, but is referenced in the above linked article several times as a solution.
>
> TODO: Find a working, current solution

```html
<a href="http://www.google.com/" target="_blank"
  >Google
  <span class="sr-only">Opens in new window</span>
  <i aria-hidden="true" class="fa fa-edit fa-external-link"></i>
</a>
```

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
```

> TODO: Fix the links in this entire project... 😂😅 Oof. (!!!)

```html
<!--a id="BAD1a" href='...'>this</a> is a great place to start your career in web development! -->
<!--a id="BAD1b" href='...'>a site that i used, called The Odin Project, is a great place to learn how to make websites and you might like to check it!</a> -->
<!--a id="BAD1c" href='...'>click here</a> to visit The Odin Project -->
<a id="example1" href="...">The Odin Project</a> is a great place to learn!
<a id="example2" href="...">2021 Sign Up Statistics (PDF, 1MB)</a>
<a id="example3" href="...">GitHub (opens in new tab)</a>
```

### [Form Error Text Guidelines](https://webaim.org/techniques/formvalidation/)

In the error message include:

1. Which form element contains invalid input
2. Why the input is invalid
3. How to fix the problem

```html
<div class="input-error">
  Error: Provided e-mail 'JohnSmith@@test.com' is not valid due to it containing
  multiple "@" symbols. Example of a valid email: example@yourdomain.com
</div>
```
