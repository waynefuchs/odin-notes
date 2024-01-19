[figure-headings]: ./.project/figures/markdown/headings.png

# Markdown <!-- omit in toc -->

# 🚧 Work In Progress <!-- omit in toc -->

- 07JUL2023
- 19JAN2024

---

Markdown is a Text-to-HTML _~~hack of a perl script~~_ translation tool. It allows for easily written and readable text documents that can be parsed into well organized and easily searchable formatted and styled documentation.

- [Github Profile](#github-profile)
- [Git README.md](#git-readmemd)
  - [Sections to include](#sections-to-include)
  - [Additionally Inlude (polish)](#additionally-inlude-polish)
- [Examples](#examples)
- [Headings](#headings)
- [🚧 Links](#-links)
  - [Internal / External Links](#internal--external-links)
  - [Link Definitions](#link-definitions)
- [🚧 Mermaid](#-mermaid)
  - [An example State Diagram in Mermaid](#an-example-state-diagram-in-mermaid)
- [Markdown ➡ PDF with CLI](#markdown--pdf-with-cli)
- [Reference Links](#reference-links)

# Github Profile

# Git README.md

The `README.md` is the public face for every project. Being able to write an eye catching project landing page is a great way to show off your work in a professional manner, and to prove that you have what it takes to work on production ready projects.

## Sections to include

> ⚠️ Do not undersell your project with negative words like "test", "toy", "just", or "learn". This is exceptionally important in the project title.

| Section         | Description                                                                                                                    |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Title**       | Make the title memorable and personal that makes it sound like a real project                                                  |
| **Description** | 1-3 sentences that describe what the project is in as simple and clear language as possible                                    |
| The "Why?"      | Motivation / Goal / The problem the project solves                                                                             |
| Quick Start     | Mention Prerequisites and Provide installation instructions                                                                    |
| Usage           | Provide instructions for operation of the software (Configuration, Options, Standard and Non-standard use cases, CLI Switches) |
| Contributing    |                                                                                                                                |

> ⓘ The title and the description **_need_** to be good. Comparable to thumbnail and title in a youtube video. This is what sells your project. If a hiring manager gets bored or perceives you are lacking confidence during the first few sentences of your project, there is a chance they will move on to the next applicant.

## Additionally Inlude (polish)

1. Media
   - Photos (screenshots, pictures, emoji, logos, etc)
   - Videos
   - Audio
2. List technologies used
3. (if applicable) License information
4. (if applicable) Credit any resources being used (images, boiler plate / starter code, libraries, etc.)
5. (optional/blog) Your development process
6. (optional/blog) Motivation and Passion behind the project

# Examples

- The [Fira Code](https://github.com/tonsky/FiraCode) github project

# Headings

Headings are not to be used for formatting. They are used for document structure.

```markdown
# Heading Level 1

## Heading Level 2

### Heading Level 3

#### Heading Level 4

##### Heading Level 5

###### Heading Level 6
```

![Heading Example][figure-headings]

# 🚧 Links

> 🚧 TODO: Links are so simple, and incredibly complicated because of the difference between markdown variants.

## Internal / External Links

```Markdown
[Internal Page Link](README.md): This Project's Landing Page
[External Page Link](https://www.google.com/): Google
```

[Internal Page Link](README.md): This Project's Landing Page
[External Page Link](https://www.google.com/): Google

## Link Definitions

> ⚠️ This feature is not implemented in all markdown renderers. It does work in _Gitea_ and on _Github_.

A link definition is a variable that is stripped from the document in the HTML output.

There are three parts to a link definition.

```markdown
<!-- [definition]: uri "title" -->

[arbitrary case-insensitive reference text]: https://with.some.uri "And an Optional Title"
```

Link Definition Example

```Markdown
[project-main-readme]: ./README.md "This Project"
[The main Readme in this project](project-main-readme)
```

[projectmainreadme]: ./README.md "This Project"

[The main Readme in this project](project-main-readme)

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

# 🚧 Mermaid

The official [Mermaid.js](https://mermaid.js.org/) website is where I get most of my mermaid info. I often find myself feeling like mermaid isn't _quite_ there yet, or that there are a few features that I wish that it had. But, the more that I use it, the more that I see the potential and possibility in simplistic diagrams.

## An example State Diagram in Mermaid

```mermaid
%% It is better to use actual markdown titles because there are circumstances that the title renders poorly
%% Unless this gets fixed, in the future. Uncomment the three lines below to see what that looks like
%%---
%%title: An example State Diagram (Graph)
%%---
stateDiagram
%%  direction TB
  direction LR

  %% Accessibility - Not required
  accTitle: This is the accessible title
  accDescr: This is an accessible description

  %% Set up CSS classes
  %% Note that CSS changes do not affect positioning, so oddities can occur
  classDef bad color:red,font-weight:900;
  %% add the following font-size styling in to see what 'oddities' I am talking about
  %% font-size:2em;

  %% Assign nodes to CSS classes
  class C bad

  %% Defining labels for nodes
  A : Car Stopped
  B : Car Moving
  C : Crash Occurred

  a : airbags deploy
  b : seatbelt engages

  %% Connecting nodes so they can be rendered
  [*] --> A
  A --> [*]
  A --> B
  B --> C
  C --> [*]

  state C {
    %% Uncomment next line for left to right
    %% direction LR
    a --> b
  }

```

# Markdown ➡ PDF with CLI

```bash
pandoc ./footprints.md -o test.pdf
pandoc ./footprints.md -V geometry:landscape -o test.pdf
```

# Reference Links

| Title                                                                                                                                                          | Site            | Description                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) | Github          | Markdown guide, produced by the site that is rendering this markdown; github.                                                                                                                                                          |
| [Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)                                                                                                      | Markdown Guide  | Has a lot of concise examples, and an "extended syntax" page that is very good for table formatting.                                                                                                                                   |
| [Extended Syntax](https://www.markdownguide.org/cheat-sheet/)                                                                                                  | Markdown Guide  | Great for making tables behave reasonably in Gitea and on GitHub                                                                                                                                                                       |
| [CommonMark](https://commonmark.org/)                                                                                                                          | Common Mark     | Advocate for a common specification for markdown                                                                                                                                                                                       |
| [Markdown in 60 sec](https://commonmark.org/help/)                                                                                                             | Common Mark     | Learn Markdown in 60 seconds (It really is this easy to get started.)                                                                                                                                                                  |
| [Markdown in 10 min](https://commonmark.org/help/tutorial/)                                                                                                    | Common Mark     | A tutorial that has you practice markdown, meant to take about ten minutes.                                                                                                                                                            |
| ...[Variables?](https://stackoverflow.com/questions/24580042/github-markdown-are-macros-and-variables-possible)                                                | StackOverflow   | I learned many things from the discussion on this page.                                                                                                                                                                                |
| [Markdown: Syntax](https://daringfireball.net/projects/markdown/syntax)                                                                                        | Daring Fireball | The original source of Markdown.                                                                                                                                                                                                       |
| [On why Markdown is not a good, or even a half-decent, markup language](https://news.ycombinator.com/item?id=36793694)                                         | Hacker News     | I disagree. The comments are a bit spicy and incredibly informative / interesting with a lot of very knowledgeable people providing links.<br />🚧 TODO: Finish gleaning what I can from the comments before the info is lost to time. |
