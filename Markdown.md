[figure-heading](.project/_images-for-notes/)

- [Markdown](#markdown)
- [Bookmarks](#bookmarks)
- [graph](#graph)
- [Headings](#headings)
- [Reference Links](#reference-links)
  - ["Markdown Variables"](#markdown-variables)

# Markdown

Markdown is not complicated. But there is a bit of an art to managing a large markdown project. It's a skill that I am still working on. For the most part, Markdown is understanding what is possible within the constraints of the 'language.'

The constraints provided by Markdown force "good" note-taking habits. I'm not claiming to have the "best notes," but what I _am_ claiming is that the quality of my notes improved when I started using markdown.

# Bookmarks

| Title                                                                                                                                                          | Site           | Description                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ---------------------------------------------------------------------------------------------------- |
| [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) | Github         | Markdown guide, produced by the site that is rendering this markdown; github.                        |
| [Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)                                                                                                      | Markdown Guide | Has a lot of conicse examples, and an "extended syntax" page that is very good for table formatting. |
| [Extended Syntax](https://www.markdownguide.org/cheat-sheet/)                                                                                                  | Markdown Guide | Great for making tables behave reasionably in Gitea and on GitHub                                    |
| [CommonMark](https://commonmark.org/)                                                                                                                          | Common Mark    | Advocate for a common specification for markdown                                                     |
| [Markdown in 60 sec](https://commonmark.org/help/)                                                                                                             | Common Mark    | Learn Markdown in 60 seconds (It really is this easy to get started.)                                |
| [Markdown in 10 min](https://commonmark.org/help/tutorial/)                                                                                                    | Common Mark    | A tutorial that has you practice markdown, meant to take about ten minutes.                          |
| ...[Variables?](https://stackoverflow.com/questions/24580042/github-markdown-are-macros-and-variables-possible)                                                | StackOverflow  | I learned many things from the discussion on this page.                                              |

# graph

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

# Headings

```markdown
# Heading Level 1

## Heading Level 2

### Heading Level 3

#### Heading Level 4

##### Heading Level 5

###### Heading Level 6
```

![Heading Example](.project/_images-for-notes/../../markdown/headings.png)
_figure-heading_

# Reference Links

## "Markdown Variables"

```markdown
[arbitrary case-insensitive reference text]: https://www.somewebsite.org
```

This defines a "markdown variable" with the key-value pair of:

|                     key                     |             value             |
| :-----------------------------------------: | :---------------------------: |
| `arbitrary case-insensitive reference text` | `https://www.somewebsite.org` |

[arbitrary case-insensitive reference text]: https://www.somewebsite.org

> ⓘ The example code is also inserted into the markdown document between this quote and the table above; inserting the `https://www.somewebsite.org` link, invisibly into the document.

> ⓘ I use this technique to link all the figures used in my markdown. I locate them at the top of the document.
>
> 1. This allows me to see what figures are in the document at a glance (While editing the markdown)
> 2. I can easily update the links where necessary

| Link                                                                                        | Description             |
| ------------------------------------------------------------------------------------------- | ----------------------- |
| [I'm an inline-style link](https://www.somewebsite.com)                                     | Normal Link             |
| [I'm an inline-style link with title](https://www.somewebsite.com "somewebsite's Homepage") | Mouse over to see title |
| [I'm a reference-style link][Arbitrary case-insensitive reference text]                     | Variable                |
| [I'm a relative reference to a repository file](../blob/master/LICENSE)                     |                         |
| [You can use numbers for reference-style link definitions][1]                               |                         |
| Or leave it empty and use the [link text itself]                                            |                         |
| Some text to show that the reference links can follow later.                                |                         |

Link will direct user here.

[1]: http://somewebsite.org
[link text itself]: http://www.somewebsite.com
