# Set Up VSCode

## Web Development Extensions

| Package Name         | Author               | Description                                  |
| -------------------- | -------------------- | -------------------------------------------- |
| Prettier             | Prettier             | Format code with the push of a button.       |
| Markdown All In One  | Yu Zhang             | Markdown tools                               |
| Overtype             | DrMerfy              | Implements Insert / Overtype mode            |
| REST Client          | Huachao Mao          | Perform HTTP calls and see raw output.       |
| Code Spell Checker   | Street Side Software | Spell Checking                               |
| Live Server          | Ritwick Dey          | Built-in http server to test raw html/css/js |
| EJS language support | DigitalBrainstem     | EJS language support                         |
| pug                  | amandeepmittal       | pug formatting                               |

### Python

> Note: These are packages that tend to automatically get installed when I write anything in python.

| Package Name               | Author    | Description              |
| -------------------------- | --------- | ------------------------ |
| Python                     | Microsoft | Python language support. |
| Pylance                    | Microsoft |                          |
| Jupyter Slide Show         | Microsoft |                          |
| Jupyter Notebook Renderers | Microsoft |                          |
| Jupyter Cell Tags          | Microsoft |                          |
| Jupyter Keymap             | Microsoft |                          |
| Jupyter                    | Microsoft |                          |
| isort                      | Microsoft |                          |

## File -> Preferences -> Settings

| Setting                   | Value                     | Description                                     |
| ------------------------- | ------------------------- | ----------------------------------------------- |
| Editor: Default Formatter | Prettier - Code Formatter | Set prettier as the code formatter              |
| Format On Save            | Enabled                   | Saving formats code                             |
| Window: Title Bar Style   | custom                    | Gets rid of the incredibly ugly gnome title bar |

## Ctrl-K Ctrl-S: Keybinds

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
