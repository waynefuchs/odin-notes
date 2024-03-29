[figure-css-auto-fit]: ../.project/figures/css/auto-fit_vs_auto-fill.png

- [🚧 Work In Progress (14JUN2023)](#-work-in-progress-14jun2023)
- [Grid](#grid)
- [Links](#links)
- [⚠️ This page is scuffed](#️-this-page-is-scuffed)
- [Terms](#terms)
- [Properties](#properties)
  - [`display: grid` | `display: inline-grid`](#display-grid--display-inline-grid)
  - [`grid-template-row:` | `grid-template-column:` | `grid-template:` (shortcut)](#grid-template-row--grid-template-column--grid-template-shortcut)
  - [`column-gap:` or `row-gap:` or `gap:` (shortcut)](#column-gap-or-row-gap-or-gap-shortcut)
  - [`grid-auto-rows:` or `grid-auto-columns:`](#grid-auto-rows-or-grid-auto-columns)
  - [`grid-template-areas`](#grid-template-areas)
  - [`grid-area`](#grid-area)
  - [`grid-column` and `grid-row`](#grid-column-and-grid-row)
  - [`justify-items` and `align-items` or `place-items` (shortcut)](#justify-items-and-align-items-or-place-items-shortcut)
  - [`justify-content` and `align-content` or `place-content` (shortcut)](#justify-content-and-align-content-or-place-content-shortcut)
  - [`grid-auto-flow`](#grid-auto-flow)
  - [`minmax()`](#minmax)
  - [`resize`](#resize)
  - [`overflow`](#overflow)
  - [`grid` (shortcut)](#grid-shortcut)
- [Recipes](#recipes)
  - [Stretch an item across the grid](#stretch-an-item-across-the-grid)

# 🚧 Work In Progress (14JUN2023)

# Grid

A two dimensional grid-based layout system entirely configurable with CSS properties. It is not a competitor to Flexbox, it is a complementary tool with different use cases.

# Links

| Title                                                                                                            | Site       | Description                                              |
| ---------------------------------------------------------------------------------------------------------------- | ---------- | -------------------------------------------------------- |
| [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)                             | css-tricks | **_The_** grid guide.                                    |
| [Difference Between Flexbox & Grid](https://css-tricks.com/quick-whats-the-difference-between-flexbox-and-grid/) | css-tricks | I wish I had read this before learning Flexbox and Grid. |

# ⚠️ This page is scuffed

If you are wanting to learn grid, use "**_The_** grid guide" at css-tricks. 🡅

Everything below this message is a bit... unpolished. 🚧🚧🚧🚧

> 🚧 TODO: I need to rework this page.

# Terms

| Term           | Description                                                                                                                                                                                                                                                                                          |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Grid Container | The element providing the CSS property `display: grid;`                                                                                                                                                                                                                                              |
| Grid Item      | Anything that is a direct child element of the grid container.                                                                                                                                                                                                                                       |
| Grid Line      | The dividing lines between grid items, either _column grid lines_ (horizontal) or _row grid lines_ (vertical).                                                                                                                                                                                       |
| Grid Cell      | The space between grid lines.                                                                                                                                                                                                                                                                        |
| Grid Track     | Either a row or a column. If you highlighted a row or column in a spreadsheet, you would be highlighting the grid track.                                                                                                                                                                             |
| Grid Area      | The total space surrounded by four grid lines. (Think: Rectangle or square shape of selected grid cells.)                                                                                                                                                                                            |
| Explicit Grid  | A fixed number of lines and tracks can be defined that form a grid by using the properties `grid-template-rows`, `grid-template-columns`, and `grid-template-areas`. This manually defined grid is called the explicit grid.                                                                         |
| Implicit Grid  | The implicit grid is automatically generated by the grid container whenever grid items are positioned outside of the explicit grid. The grid container generates implicit grid tracks by adding implicit grid lines to the grid. These lines together with the explicit grid form the implicit grid. |

# Properties

> 🚧 TODO: This is a disaster and would likely work a lot better as a series of tables. Maybe. It's too messy to find anything here, and just referencing the css-tricks page has worked far better than these notes.
>
> I don't really want to remove this information, because there are some good things here that I've compiled from multiple sources. I will come back to this and fix in the future.

## `display: grid` | `display: inline-grid`

Defines the element as a grid container and create a block or inline level grid.

## `grid-template-row:` | `grid-template-column:` | `grid-template:` (shortcut)

- Define rows (specify heights)
- Define columns (specify widths)
- Define rows / columns

> ⓘ The columns and rows can be named.

```css
.container {
  grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
  grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
}
```

> ⓘ `grid-template` (shortcut): Combines `grid-template-rows`, `grid-template-columns`, and `grid-template-areas` into a single declaration.

> 🚧 TODO: Learn this later. css-tricks says that the `grid` property is recommended over this shortcut. It looks interesting, but is outside of my comfort to use at the moment.

## `column-gap:` or `row-gap:` or `gap:` (shortcut)

- Space between column
- Space between rows
- Equal space between columns and rows

## `grid-auto-rows:` or `grid-auto-columns:`

Specify the size of implicitly generated columns or rows.

## `grid-template-areas`

A way to lay out the page:

```css
.container {
  display: grid;
  grid-template-areas:
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer";
}
```

Note: You also need to define a `grid-area`.

## `grid-area`

Can be used to assign a name to an item.

```css
.item-n {
  grid-area: footer;
}
```

Can also be used as a shorthand for `grid-row-start` / `grid-column-start` / `grid-row-end` / `grid-column-end:` to define an area of cells between lines.

```css
.item-d {
  grid-area: 1 / col4-start / last-line / 6;
}
```

## `grid-column` and `grid-row`

Shorthand for defining how many cells an item in the grid should occupy.

- `grid-column: <start-line> / <end-line> | <start-line> / span <value>;`
- `grid-row: <start-line> / <end-line> | <start-line> / span <value>;`

```css
.item-c {
  grid-column: 3 / span 2;
  grid-row: third-line / 4;
}
```

## `justify-items` and `align-items` or `place-items` (shortcut)

- `justify-items`: align items along the inline (row) axis
- `align-items`: align items along the block (column) axis
- `place-items: <align-items> / <justify-items> | <align AND justify-items>`: Does both in one property shortcut.

Options

- `stretch`: fills the whole width of the cell **(DEFAULT)**
- `start`: align to the start edge
- `end`: align to the ending edge
- `center`: center elements in their cell
- `align-items` specific: `baseline`: can be `first baseline` or `last baseline`

## `justify-content` and `align-content` or `place-content` (shortcut)

Similarly to the `*-items` variant of these properties, this adjusts the alignment of the entire grid.

## `grid-auto-flow`

Control how the auto-placement algorithm works for implicitly defined cells.
For example, add new flex-items as a new row or column.

```css
.container {
  grid-auto-flow: column | row;
}
```

## `minmax()`

Can only be used in:

- `grid-template-columns`
- `grid-template-rows`
- `grid-auto-columns`
- `grid-auto-rows`

Minmax benefits significantly from `auto-fit` and `auto-fill`.

- `auto-fit`: will fill all available space in the grid container, sizing the items up
- `auto-fill`: will stop item size expansion above the minmax value

```css
.item {
  /* cell width will be between 150px and 200px */
  grid-template-columns: repeat(5, minmax(150px, 200px));
}
```

![Example][figure-css-auto-fit]

## `resize`

```css
.element {
  resize: both | horizontal | vertical | none;
}
```

## `overflow`

What to do when the content of an element extends beyond the element bounds.

```css
.element {
  overflow: visible | hidden | clip | scroll | auto | hidden visible;
}
```

- visible: render outside the padding box
- hidden: clip content at the padding / border.
- scroll: provide scroll bars if content extends
- auto: leave it up to the browser (desktop provides scroll bars)
- overlay: behaves the same as auto but with scroll bars drawn on top instead of taking up space.
- hidden visible: no idea...(?) [source](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow)

## `grid` (shortcut)

A shorthand that allows the use of most grid properties in a single declaration.

> 🚧 TODO: Dig into this after a bit more experience with grid, perhaps. This, again, is beyond my ability to utilize at the moment.

# Recipes

> 🚧 TODO: Figure out a different way to handle some of these examples. When I first started taking notes for Odin, I felt like the "Recipes" section on each page was going to be one of the more useful sections. That did not age well.

## Stretch an item across the grid

```css
.item {
  grid-column: 1 / -1; /* start / end */
}
```
