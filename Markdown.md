# Markdown

While markdown is not complicated, these resources really helped me get started and taught me what formatting is possible. Using markdown to take notes almost forces "good" note-taking habits. I'm not claiming to have the best notes, at all, but what I _am_ saying is that the quality of my notes improved when I started using markdown.

# Links

| Title                                                                                                                                                                                 | Site           | Description                                                                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Official Github Markdown Syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) | Github         | Markdown guide, produced by the site that is rendering this markdown; github.                                                                                                                                                                                            |
| [A Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)                                                                                                                  | Markdown Guide | Has a lot of conicse examples, and an "extended syntax" page that is very good for table formatting.                                                                                                                                                                     |
| [CommonMark](https://commonmark.org/)                                                                                                                                                 | CommonMark     | Several individuals advocating for a common specification for markdown, with a [Learn Markdown in 60 seconds](https://commonmark.org/help/) and [10 minute markdown tutorial](https://commonmark.org/help/tutorial/) resource. Provides interesting history of Markdown. |
| [GitHub Markdown: Are Macros and Variables Possible?](https://stackoverflow.com/questions/24580042/github-markdown-are-macros-and-variables-possible)                                 | StackOverflow  | No. And Yes. I actually learned several things from the discussion on this page.                                                                                                                                                                                         |

==highlight words==

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
