- [Units](#units)
  - [Links](#links)
  - [Absolute Units](#absolute-units)
  - [Relative Units](#relative-units)
  - [Modifiers to `vb`, `vi`, and (`vh` / `vw`)](#modifiers-to-vb-vi-and-vh--vw)
    - [Examples:](#examples)

# Units

## Links

- [All 24 CSS Viewport Units Explained](https://blog.webdevsimplified.com/2022-08/css-viewport-units/): Web Dev Simplified
- [Fun with Viewport Units](https://css-tricks.com/fun-viewport-units/): css-tricks.com
- [All CSS Units Compared And Explained](https://areknawo.com/all-css-units-compared-and-explained/)


## Absolute Units

Where possible in reactive web design, use Relative units. Padding, Margin, and Borders can benefit from using `px`, as when the page is resized, if a relative unit has been specified, the page can scale in odd ways. The designer should be responsible for determining spacing between elements and whether padding around UI elements should be dependent on things like font size.

| Unit | Use | Reason To Avoid Use               | Description                              |
| ---- | --- | --------------------------------- | ---------------------------------------- |
| `cm` | 🛑  | Print unit                        | Centimeter                               |
| `in` | 🛑  | Print unit                        | Inch                                     |
| `pc` | 🛑  | Antiquated typographic print unit | Picas: 1pc = 1/6 of 1in                  |
| `pt` | 🛑  | Font size unit for print          | Points: 1pt = 1/72nd of 1in              |
| `px` | ✔️  | **_Disrupts responsive design_**  | Pixels: Use sparingly; 1px = 1/96 of 1in |
| `Q`  | 🛑  | Not useful for anything(?)        | Quarter-millimeters: 1Q = 1/40th of 1cm  |

## Relative Units

If the user changes the font size for your website, if you have used Relative Units and responsive design properties, all the page elements will likewise scale.

| Unit        | Use | Reason to Use or Not Use                                                                                                      | Description                                                    |
| ----------- | --- | ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| `ch`        | 🛑  | Limited usefulness                                                                                                            | Width of the "0" glyph in font.                                |
| `dvh` `dvw` | ⚠️  | "New ([2021](https://github.com/w3c/csswg-drafts/issues/4329))" Unit, Performance and Scrolling Issues, **GREAT** for mobile! | Similar to vh and vw. (?)                                      |
| `em`        | ⚠️  | Prefer `rem` to not worry about DOM context                                                                                   | EleMent `font-size`.                                           |
| `ex`        | 🛑  | Limited use                                                                                                                   | Height of 'x' character in font.                               |
| `fr`        | ✔️  | Good for responsive **grid** layouts                                                                                          | Fraction                                                       |
| `lh`        | 🛑  | Limited use                                                                                                                   | Line height of the element.                                    |
| `rem`       | ✔️  | Based on :root or html                                                                                                        | Root EleMent `font-size`.                                      |
| `rlh`       | 🛑  | Limited Use                                                                                                                   | Initial line height of the root element.                       |
| `svh` `svw` | ⚠️  | Limited Use                                                                                                                   | Same as vh/vw returning the smaller of width/height.           |
| `lvh` `lvw` | ⚠️  | Limited Use                                                                                                                   | Same as vh/vw returning the larger of width/height.            |
| `vh`        | ✔️  | Useful when you want something scaled to the viewport.                                                                        | Percent of viewport height.                                    |
| `vmin`      | ⚠️  | Keep font size (specifically HERO) under control                                                                              | 1% of the viewport's smaller dimension (Portrait / Landscape). |
| `vmax`      | ⚠️  | Keep font size (specifically HERO) under control                                                                              | 1% of the viewport's larger dimension. (Portrait / Landscape)  |
| `vb`        | ⚠️  | Similar to vh for roman language                                                                                              | 1% of the size of the viewport in the block direction.         |
| `vi`        | ⚠️  | Similar to vw for roman language                                                                                              | 1% of the size of the viewport in the inline direction.        |
| `vw`        | ✔️  | Viewport scaling is good for full-height/width full screen interfaces.                                                        | Percent of viewport width.                                     |

## Modifiers to `vb`, `vi`, and (`vh` / `vw`)

| Modifier | Stands For| Description |
|--|--|--|
|`d`|Dynamic|Is the current size of the viewport to allow for reactive design on mobile|
|`l`|Large|Largest possible viewport size, ignoring whether the url bar is shown or not |
|`s`|Small|Smallest possible viewport size, taking into consideration the space for the url bar on mobile |

> Note: This is for the url bar overlay only, the keyboard is not factored into the size calculation

### Examples:

```css
height: 100dvh; /* Set the height to 100% of the current viewport */
height: 100svh; /* Set the height to 100% of the screen when the URL bar is shown, whether or not it is visible */
height: 100lvh; /* Set the height to 100% of the screen size without the URL bar */
```