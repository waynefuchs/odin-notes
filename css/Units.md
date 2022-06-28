- [Units](#units)

# Units

## Absolute Units

Where possible in reactive web design, use Relative units where possible.

| Unit | Use | Reason | Description |
| ---- | --- | ------ | ----------- |
| `cm` | 🛑 | Print unit. | Centimeter |
| `in` | 🛑 | Print unit. | Inch |
| `pc` | 🛑 | | 1pc = 1/6 of 1in |
| `pt` | 🛑 | | 1pt = 1/72nd of 1in |
| `px` | ✔️ | Use sparingly. | 1px = 1/96 of 1in |
| `Q` | 🛑 | | 1Q = 1/40th of 1cm |


## Relative Units

🛑
⚠️
✔️
✅

If the user changes the font size for your website, if you have used Relative Units and responsive design properties, all the page elements will likewise scale.

| Unit | Use | Reason | Description |
| ---- | --- | ------ | ----------- |
| `em` | ⚠️ | Prefer `rem` to not worry about DOM context | EleMent `font-size`. |
| `rem` | ✅ | Root EleMent `font-size`. |
| `vh` | ✔️ | Useful when you want something scaled to the viewport. | Percent of viewport height. |
| `vw` | ✔️ | Viewport scaling is good for full-height/width full screen interfaces. | Percent of viewport width. |