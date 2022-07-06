- [Grid](#grid)
  - [Links](#links)
  - [Good to Know](#good-to-know)
    - [Invalid Properties](#invalid-properties)
  - [Terms](#terms)
    - [Grid Container](#grid-container)
    - [Grid Item](#grid-item)
    - [Grid Line](#grid-line)
    - [Grid Cell](#grid-cell)
    - [Grid Track](#grid-track)
    - [Grid Area](#grid-area)
    - [Implicit vs. Explicit](#implicit-vs-explicit)
  - [Properties](#properties)
    - [`display: grid` or `display: inline-grid`](#display-grid-or-display-inline-grid)
    - [`grid-template-row:` or `grid-template-column:` or `grid-template:` (shortcut)](#grid-template-row-or-grid-template-column-or-grid-template-shortcut)
    - [`column-gap:` or `row-gap:` or `gap:` (shortcut)](#column-gap-or-row-gap-or-gap-shortcut)
    - [`grid-auto-rows:` or `grid-auto-columns:`](#grid-auto-rows-or-grid-auto-columns)
    - [`grid-template-areas`](#grid-template-areas)
    - [`grid-area`](#grid-area-1)
    - [`grid-template` (shortcut)](#grid-template-shortcut)
    - [`justify-items` and `align-items` or `place-items` (shortcut)](#justify-items-and-align-items-or-place-items-shortcut)
    - [`justify-content` and `align-content` or `place-content` (shortcut)](#justify-content-and-align-content-or-place-content-shortcut)
    - [`grid-auto-columns` and `grid-auto-rows`](#grid-auto-columns-and-grid-auto-rows)
    - [`grid-auto-flow`](#grid-auto-flow)
    - [`grid` (shortcut)](#grid-shortcut)

# Grid

## Links

[A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

## Good to Know

### Invalid Properties

The following properties have no effect on a grid item.

* float, 
* display: inline-block, 
* display: table-cell, 
* vertical-align and 
* column-*

## Terms

### Grid Container

The element with `display: grid;` on it.

### Grid Item

Anything that is a direct child of the grid container.

### Grid Line

The dividing lines between grid items, either *column grid lines* (horizontal) or *row grid lines* (vertical).

### Grid Cell

The space between grid lines.

### Grid Track

Either a row or a column. If you highlighted a row or column in a spreadsheet, you would be highlighting the grid track.

### Grid Area

The total space surrounded by four grid lines. (Think: Rectangle or square shape of selected grid cells.)

### Implicit vs. Explicit

Grid will use the templates it has been provided to overflow any 'cells' that have not been defined *implicitly*. Size values that have been established using grid-template(x) will not be carried over into implicit grid tracks. To define those tracks, you must use grid-auto(x).


## Properties

### `display: grid` or `display: inline-grid`

Defines the element as a grid container and create a block or inline level grid.

### `grid-template-row:` or `grid-template-column:` or `grid-template:` (shortcut)

* Define rows (specify heights)
* Define columns (specify widths)
* Define rows / columns

Note1 that the columns and rows can be named.

``` css
.container {
  grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
  grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
}
```

Note2 that `grid-column-gap` and `grid-row-gap` are deprecated versions of the same thing and may show up in legacy code.


### `column-gap:` or `row-gap:` or `gap:` (shortcut)

* Space between column
* Space between rows
* Equal space between columns and rows


### `grid-auto-rows:` or `grid-auto-columns:`

* Explicitly state what implicit row height should be.
* Explicitly state what implicit column width should be.


### `grid-template-areas`

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

### `grid-area`

Assign a grid-area label to a css element. In the example below it happens to be a class, but could be any selector for an applicable element in the grid.

```css
.item-n {
    grid-area: footer;
}
```

### `grid-template` (shortcut)

Combines `grid-template-rows`, `grid-template-columns`, and `grid-template-areas` into a single declaration.

TODO: Learn this later. css-tricks says that the `grid` property is recommended over this shortcut. It looks interesting, but is outside of my comfort to use at the moment.


### `justify-items` and `align-items` or `place-items` (shortcut)

* `justify-items`: align items along the inline (row) axis
* `align-items`: align items along the block (column) axis
* `place-items: <align-items> / <justify-items> | <align AND justify-items>`: Does both in one property shortcut.

Options
* `stretch`: fills the whole width of the cell **(DEFAULT)**
* `start`: align to the start edge
* `end`: align to the ending edge
* `center`: center elements in their cell
* `align-items` specific: `baseline`: can be `first baseline` or `last baseline`


### `justify-content` and `align-content` or `place-content` (shortcut)

Similarly to the `*-items` variant of these properties, this adjusts the alignment of the entire grid.


### `grid-auto-columns` and `grid-auto-rows`

Specify the size of implicitly generated columns or rows.


### `grid-auto-flow`

Control how the auto-placement algorithm works for implicitly defined cells.


### `grid` (shortcut)

A shorthand that allows the use of most grid properties in a single declaration.

TODO: Dig into this after a bit more experience with grid, perhaps. This, again, is beyond my ability to utilize.