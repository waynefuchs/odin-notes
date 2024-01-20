# Vim <!-- omit from toc -->

- [Commands](#commands)
- [Movement](#movement)
- [Buffer Manipulation](#buffer-manipulation)
- [Visual Mode](#visual-mode)
- [Enter Insert Mode](#enter-insert-mode)
- [Config](#config)

# Commands

| key                   | desc                                           |
| --------------------- | ---------------------------------------------- |
| `:q`, `:q!`           | quit, quit without saving                      |
| `:wq`, `ZZ`           | write and quit                                 |
| `:Sex`, `:Vex`, `:Ex` | Split explore, Vertical-split Explore, Explore |

| key                        | desc                                         |
| -------------------------- | -------------------------------------------- |
| `<tab>`                    | autocomplete command                         |
| `<ctrl>`-`d`               | show command autocomplete list in popup view |
| `<ctrl>`-`p`, `<ctrl>`-`n` | Previous, next while auto-completing         |
| `<ctrl>`-`w` `s`/`v`       | Open a new window split / vertical           |
| `<ctrl>`-`w` `o`           | Close all but the selected window            |

# Movement

| key                | desc                       |
| ------------------ | -------------------------- |
| `h`, `j`, `k`, `l` | left, up, down, right      |
| `w`, `b`           | word hop forward, backward |
| `gg`               | move to start of file      |
| `G`                | move to end of file        |

# Buffer Manipulation

| key      | desc             |
| -------- | ---------------- |
| `yy`     | yank             |
| `dd`     | yank and delete  |
| `p`, `P` | paste belo/above |

# Visual Mode

| key | desc                                      |
| --- | ----------------------------------------- |
| `v` | Enter visual mode                         |
| `V` | Enter visual mode and select current line |

# Enter Insert Mode

| key      | desc                                                                          |
| -------- | ----------------------------------------------------------------------------- |
| `i`, `a` | enter insert at cursor, right of cursor                                       |
| `I`, `A` | enter insert before the first non-whitespace character in a line, end of line |
| `o`, `O` | enter insert below, above current line                                        |

# Config

| key                            | desc                                            |
| ------------------------------ | ----------------------------------------------- |
| `:set scrolloff=8`             | Keep padding as you scroll down                 |
| `:set number`                  | Show line numbers                               |
| `:set relativenumber`          | Change the line numbers to show relative offset |
| `:set tabstop=4 softtabstop=4` | Set the tab display to 4 spaces                 |
| `:set shiftwidth=4`            | Code indentation amount                         |
| `set expandtab`                | Inserts spaces instead of the tab character     |
| `set smartindent`              | Indents to scope                                |
