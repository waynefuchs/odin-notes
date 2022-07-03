- [Grid](#grid)
  - [Implicit vs. Explicit](#implicit-vs-explicit)
  - [Properties](#properties)
    - [`display: grid`](#display-grid)
    - [`grid-template-row:`](#grid-template-row)
    - [`grid-template-column:`](#grid-template-column)
    - [`grid-template:` shortcut](#grid-template-shortcut)
    - [`grid-auto-rows:`](#grid-auto-rows)
    - [`grid-auto-columns:`](#grid-auto-columns)
    - [`column-gap:`](#column-gap)
    - [`row-gap:`](#row-gap)
    - [`gap:`](#gap)

# Grid

## Implicit vs. Explicit

Grid will use the templates it has been provided to overflow any 'cells' that have not been defined *implicitly*. Size values that have been established using grid-template(x) will not be carried over into implicit grid tracks. To define those tracks, you must use grid-auto(x).


## Properties

### `display: grid`

### `grid-template-row:`

Define rows (specify heights)

### `grid-template-column:`

Define columns (specify widths)

### `grid-template:` shortcut

Define rows / columns

### `grid-auto-rows:`

Explicitly state what implicit row height should be.

### `grid-auto-columns:`

Explicitly state what implicit column width should be.

### `column-gap:`

### `row-gap:`

### `gap:`