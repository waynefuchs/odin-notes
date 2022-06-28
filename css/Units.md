- [Units](#units)

# Units

## Absolute Units

Where possible in reactive web design, use Relative units. Padding, Margin, and Borders can benefit from using `px`, as when the page is resized, if a relative unit has been specified, the page can scale in odd ways. The designer should be responsible for determining spacing between elements and whether padding around UI elements should be dependent on things like font size.

| Unit | Use | Reason | Description |
| ---- | --- | ------ | ----------- |
| `cm` | 🛑 | Print unit. | Centimeter |
| `in` | 🛑 | Print unit. | Inch |
| `pc` | 🛑 | | 1pc = 1/6 of 1in |
| `pt` | 🛑 | | 1pt = 1/72nd of 1in |
| `px` | ✔️ | Use sparingly. | 1px = 1/96 of 1in |
| `Q` | 🛑 | | 1Q = 1/40th of 1cm |


## Relative Units

If the user changes the font size for your website, if you have used Relative Units and responsive design properties, all the page elements will likewise scale.

| Unit | Use | Reason | Description |
| ---- | --- | ------ | ----------- |
| `ch` | 🛑 | Limited use | Width of the "0" glyph in font. |
| `dvh` `dvw` | 🛑 | Performance and Scrolling Issues | Similar to vh and vw. (?) |
| `em` | ⚠️ | Prefer `rem` to not worry about DOM context | EleMent `font-size`. |
| `ex` | 🛑 | Limited use | Height of 'x' character in font. |
| `lh` | 🛑 | Limited use | Line height of the element. |
| `rem` | ✅ | Based on :root or html | Root EleMent `font-size`. |
| `rlh` | 🛑 | Limited Use | Initial line height of the root element. |
| `svh` `svw` | ⚠️ | Limited Use | Same as vh/vw returning the smaller of width/height. |
| `lvh` `lvw` | ⚠️ | Limited Use | Same as vh/vw returning the larger of width/height. |
| `vh` | ✔️ | Useful when you want something scaled to the viewport. | Percent of viewport height. |
| `vmin` | ⚠️ | Keep font size (specifically HERO) under control | 1% of the viewport's smaller dimension (Portrait / Landscape). |
| `vmax` | ⚠️ | Keep font size (specifically HERO) under control | 1% of the viewport's larger dimension. (Portrait / Landscape) |
| `vb` | ⚠️ | Similar to vh for roman language | 1% of the size of the viewport in the block direction. |
| `vi` | ⚠️ | Similar to vw for roman language | 1% of the size of the viewport in the inline direction. |
| `vw` | ✔️ | Viewport scaling is good for full-height/width full screen interfaces. | Percent of viewport width. |
