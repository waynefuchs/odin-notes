- [Set Up VSCode](#set-up-vscode)
- [Web Development Extensions](#web-development-extensions)
- [File -\> Preferences -\> Settings](#file---preferences---settings)
- [File -\> Preferences -\> Keyboard Shortcuts](#file---preferences---keyboard-shortcuts)
  - [Snippets](#snippets)
    - [API Controller Description Helper](#api-controller-description-helper)

# Set Up VSCode

My personal settings preferences, as (mostly) recommended by The Odin Project and to play nice with the Prettier extension.

# Web Development Extensions

| Package Name                           | Author               | Description                                         |
| -------------------------------------- | -------------------- | --------------------------------------------------- |
| Prettier                               | Prettier             | Format code with the push of a button. (or on save) |
| Markdown All In One                    | Yu Zhang             | Markdown tools                                      |
| Markdown Preview Mermaid Support       | Matt Bierner         | Add Mermaid support for Markdown                    |
| Overtype                               | DrMerfy              | Implements Insert / Overtype mode                   |
| REST Client                            | Huachao Mao          | Perform HTTP calls and see raw output.              |
| Code Spell Checker                     | Street Side Software | Spell Checking                                      |
| Prisma                                 | Prisma               | Syntax highlighting for `.prisma` files.            |
| Live Server                            | Ritwick Dey          | Built-in http server to test raw html/css/js        |
| ES7+ React/Redux/React-Native snippets | dsznajder            | Provides snippets for React-related things (`rfce`) |
| Rewrap                                 | stkb                 | Allow (hard) word wrapping comments with `alt-q`    |
| VSCode Great Icons                     | Emmanuel Béziat      | Change VSCode File Browser Icons                    |
| pug                                    | amandeepmittal       | pug formatting                                      |
| EJS language support                   | DigitalBrainstem     | EJS language support                                |

# File -> Preferences -> Settings

`Ctrl` + `,`

| Setting                   | Value                     | Description                                     |
| ------------------------- | ------------------------- | ----------------------------------------------- |
| Editor: Default Formatter | Prettier - Code Formatter | Set prettier as the code formatter              |
| Editor: tabSize           | 2                         | Set the spacing to be 2 spaces instead of 4     |
| Editor: detectIndentation | false                     | Force spaces, don't base on file contents       |
| Editor: insertSpaces      | true                      | Don't use the tab character                     |
| Format On Save            | Enabled                   | Saving formats code                             |
| Window: Title Bar Style   | custom                    | Gets rid of the incredibly ugly gnome title bar |

# File -> Preferences -> Keyboard Shortcuts

`Ctrl-K` + `Ctrl-S`

| Keybinding                               | Value               | Description                                    |
| ---------------------------------------- | ------------------- | ---------------------------------------------- |
| prettier.forceFormatDocument             | ScrollLock          | Force a code format without saving             |
| workbench.action.toggleEditorWidths      | Shift + Alt + Enter | Make focused window _nearly_ full window width |
| editor.emmet.action.wrapWithAbbreviation | Ctrl+e Ctrl+w       | Wrap html tag                                  |
| editor.emmet.action.removeTag            | Ctrl+e Ctrl+d       | Remove html tag                                |

## Snippets

Under `File > Preferences > Configure User Snippets` choose `javascript.json` from the drop down menu. This snippet will set up documentation for a controller function, to define the intended purpose in comments.

### API Controller Description Helper

This helper snippet makes it very easy to define a controller for a route.

```json
{
  "API Controller Description": {
    "prefix": ["api-define-controller"],
    "body": [
      "////////////////////////////////////////////////////////////////////////////////",
      "// @desc    ${1:Write a description}",
      "// @route   ${2:GET} /api/${3:endpoint}",
      "// @access  ${4:Public}",
      "export const ${5:verb}${6:noun} = asyncHandler(async (req, res) => {",
      "  res.json({ message: '$1'})",
      "})"
    ],
    "description": "Boilerplate to create a controller function"
  }
}
```

Generates (example):

```js
////////////////////////////////////////////////////////////////////////////////
// @desc    Get logged in user data
// @route   GET /api/session
// @access  Private
export const getSession = asyncHandler(async (req, res) => {
  res.json({ message: "Get logged in user data" });
});
```
