[figure-headings]: ./.project/figures/markdown/headings.png

# Markdown <!-- omit in toc -->

# 🚧 Work In Progress (07JUL2023)

- [🚧 Work In Progress (07JUL2023)](#-work-in-progress-07jul2023)
- [Markdown ➡ PDF](#markdown--pdf)
- [Git README.md](#git-readmemd)
- [Headings](#headings)
- [Links](#links)
  - [Link Definitions](#link-definitions)
- [🚧 Mermaid](#-mermaid)
  - [State Diagram](#state-diagram)
    - [An example State Diagram (Graph)](#an-example-state-diagram-graph)
- [Reference Links](#reference-links)

The constraints provided by Markdown force "good" note-taking habits. I will not claim to have the "best notes," but what I will say is that the quality of my notes improved when I started using markdown.

Markdown is not complicated. But there is a bit of an art to managing a large markdown project. It's a skill that I am still developing. For the most part, Markdown is "just" understanding what is possible within the constraints of the 'language.'

# Markdown ➡ PDF

```bash
pandoc ./footprints.md -o test.pdf
pandoc ./footprints.md -V geometry:landscape -o test.pdf
```

# Git README.md

The `README.md` is the public face for your project. The ability to write a good one is a _fantastic_ skill to have.

🚧 Here are some guidelines I am curating in regard to writing a good README.md.

1. Use Media in READMEs
   - Photos
   - Videos
   - Gifs
   - Audio
2. Provide installation instructions
3. Provide instructions for operation of the software
   - Configuration
   - Options
   - Standard / Non-standard use cases
   - CLI Switches
4. List out the technologies you used
5. (If applicable) Provide information on how to contribute towards the project
6. (if applicable) License information
7. (if applicable) Credit any resources being used (images, boiler plate / starter code, etc.)
8. (optional/blog) Explain your development process
9. (optional/blog) Explain your motivation behind the project

# Headings

```markdown
# Heading Level 1

## Heading Level 2

### Heading Level 3

#### Heading Level 4

##### Heading Level 5

###### Heading Level 6
```

![Heading Example][figure-headings]

# Links

## Link Definitions

You can think of a link definition as a sort of link variable that is stripped from the document in the HTML output.

```
[arbitrary case-insensitive reference text]: https://with.some.uri "And an Optional Title ... Or Not"
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

# 🚧 Mermaid

This is possibly the coolest addition to markdown.

> 🚧 TODO: Add examples in for each mermaid module

## State Diagram

A state diagram is a type of diagram used in computer science and related fields to describe the behavior of systems. They require that the system described is composed of a finite number of states.

### An example State Diagram (Graph)

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

# Reference Links

| Title                                                                                                                                                          | Site            | Description                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ---------------------------------------------------------------------------------------------------- |
| [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) | Github          | Markdown guide, produced by the site that is rendering this markdown; github.                        |
| [Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)                                                                                                      | Markdown Guide  | Has a lot of concise examples, and an "extended syntax" page that is very good for table formatting. |
| [Extended Syntax](https://www.markdownguide.org/cheat-sheet/)                                                                                                  | Markdown Guide  | Great for making tables behave reasonably in Gitea and on GitHub                                     |
| [CommonMark](https://commonmark.org/)                                                                                                                          | Common Mark     | Advocate for a common specification for markdown                                                     |
| [Markdown in 60 sec](https://commonmark.org/help/)                                                                                                             | Common Mark     | Learn Markdown in 60 seconds (It really is this easy to get started.)                                |
| [Markdown in 10 min](https://commonmark.org/help/tutorial/)                                                                                                    | Common Mark     | A tutorial that has you practice markdown, meant to take about ten minutes.                          |
| ...[Variables?](https://stackoverflow.com/questions/24580042/github-markdown-are-macros-and-variables-possible)                                                | StackOverflow   | I learned many things from the discussion on this page.                                              |
| [Markdown: Syntax](https://daringfireball.net/projects/markdown/syntax)                                                                                        | Daring Fireball | A very strong syntax resource.                                                                       |
