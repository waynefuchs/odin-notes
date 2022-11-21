- [npm](#npm)
  - [Commands](#commands)
  - [Skeleton Project](#skeleton-project)
  - [Dev Packages](#dev-packages)
  - [Packages](#packages)
  - [eslint + prettier](#eslint--prettier)
    - [Installation](#installation)
    - [Running (manual)](#running-manual)
    - [Running (vscode)](#running-vscode)
  - [Babel](#babel)
    - [References](#references)
    - [Installation](#installation-1)
  - [Odin Questions](#odin-questions)
    - [Explain what npm is and where it was commonly used before being adopted on the frontend.](#explain-what-npm-is-and-where-it-was-commonly-used-before-being-adopted-on-the-frontend)
    - [Describe what npm init does and what package.json is.](#describe-what-npm-init-does-and-what-packagejson-is)
    - [Know how to install packages using npm.](#know-how-to-install-packages-using-npm)
    - [Describe what a JavaScript module bundler like webpack is.](#describe-what-a-javascript-module-bundler-like-webpack-is)
    - [Explain what the concepts “entry” and “output” mean as relates to webpack.](#explain-what-the-concepts-entry-and-output-mean-as-relates-to-webpack)
    - [Briefly explain what a development dependency is.](#briefly-explain-what-a-development-dependency-is)
    - [Explain what “transpiling code” means and how it relates to frontend development.](#explain-what-transpiling-code-means-and-how-it-relates-to-frontend-development)
    - [Briefly describe what a task runner is and how it’s used in frontend development.](#briefly-describe-what-a-task-runner-is-and-how-its-used-in-frontend-development)
    - [Describe how to write an npm automation script.](#describe-how-to-write-an-npm-automation-script)
    - [Explain one of the main benefits of writing code in modules.](#explain-one-of-the-main-benefits-of-writing-code-in-modules)
    - [Explain “named exports” and “default exports”.](#explain-named-exports-and-default-exports)

# npm

## Commands

| command                                      | description                                                                                                                                     |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `npm init -y`                                | Initialize a new project without all the questions                                                                                              |
| `npm install <package> --save`               | Download a package, and save it to the `package.json`.                                                                                          |
| `npm install webpack webpack-cli --save-dev` | Install webpack                                                                                                                                 |
| `npx webpack --mode=production`              | generates a webpack (with default / no config)                                                                                                  |
| `npx webpack --mode=development`             | Use `webpack.config.js` as the config file by default if it exists, but `--config webpack.config.js` can be used to specify a different config. |
| `npm run build`                              | Will tell npm to run webpack (and others tools!) automatically.                                                                                 |
| `npm uninstall <packages>`                   | Uninstall npm packages                                                                                                                          |
| `npm config set fund false`                  | Remove fund message spam (I'm all for funding open source projects, just don't want to see it every time i issue an npm command)                |
| `npm update`                                 | Update all packages in the project                                                                                                              |

## Skeleton Project

Create a github project. (Or gitea, or local git, or however you want to handle git...)

`git clone <project-url>`

And then:

```bash
touch README.md
curl https://raw.githubusercontent.com/github/gitignore/main/Node.gitignore > .gitignore
npm init -y
npm install webpack webpack-cli --save-dev
mkdir src dist
touch src/index.js dist/index.html webpack.config.js
```

webpack.config.js

```javascript
const path = require("path");

module.exports = {
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
  },
};
```

## Dev Packages

[webpack](https://webpack.js.org/): See my [webpack](webpack.md) notes.

## Packages

| npm package       | description                                                |
| ----------------- | ---------------------------------------------------------- |
| bootstrap         | feature packed front end toolkit                           |
| dotenv            | read environment variables                                 |
| express           | fast un-opinionated web framework for Node.js              |
| express-validator | wrapper for validator.js (validates and sanitizes strings) |
| luxon             | dates and times                                            |
| mongoose          | mongodb interface                                          |
| morgan            | request logger                                             |
| pug               | view template and markup language                          |

[PubSub-JS](https://github.com/mroderick/PubSubJS)

> `npm install pubsub-js` > `import PubSub from 'pubsub-js'`

[Lodash](https://lodash.com/): A utility library delivering modularity, performance & extras. (?)

[moment](https://momentjs.com/): Parse, validate, manipulate, and display dates and times in JavaScript. Note: This project is "done" and other recommendations are made in the site's [project status](https://momentjs.com/docs/#/-project-status/)

## eslint + prettier

### Installation

ESLint official installation [instructions](https://eslint.org/docs/user-guide/getting-started)

Prettier official installation [instructions](prettier.io/docs/en/install.html)

To install and configure:

```
npm init @eslint/config
npm install --save-dev --save-exact prettier
echo {}> .prettierrc.json
cp .gitignore .prettierignore
npm install --save-dev eslint-config-prettier
```

In the `.eslintrc.js`, change to:
`extends: ["airbnb-base", "prettier"],`

### Running (manual)

`npx eslint filename.js`

`npx prettier --write .` (Format all files)

### Running (vscode)

Install [this ESLint module](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).

Install [this Prettier Formatter module](github.com/prettier/prettier-vscode)

## Babel

### References

- [Github page](https://github.com/babel/babel-loader) can be found here.
- [What is @babel/preset-env and why do i need it](https://blog.jakoblind.no/babel-preset-env/)

### Installation

`npm install -D babel-loader @babel/core @babel/preset-env webpack`

Add to `webpack.config.js`:

```
module: {
  rules: [
    {
      test: /\.m?js$/,
      exclude: /node_modules/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: [
            ['@babel/preset-env', { targets: "defaults" }]
          ]
        }
      }
    }
  ]
}
```

## Odin Questions

### Explain what npm is and where it was commonly used before being adopted on the frontend.

> npm is a package manager for JavaScript packages. It was originally 'node package manager' to manage packages for node.js.

### Describe what npm init does and what package.json is.

> `npm init` initializes (creates) a new node project, including the `package.json`. That json file is the configuration file for the project, so you don't have to share all of your dependencies, just the project file, and node will handle downloading and arranging all of the files into a deployable project.

### Know how to install packages using npm.

> `npm install <package> --save` > `npm install <package> --save-dev`

### Describe what a JavaScript module bundler like webpack is.

> Webpack will assemble and minify many javascript files into a single transpiled package.

### Explain what the concepts “entry” and “output” mean as relates to webpack.

> Entry, in this context, is where webpack goes to start processing files.
> Output is where the transpiled code is going to be placed.

### Briefly explain what a development dependency is.

> A development dependency is some tool, module, or bit of code that is essential to the build or development process. Webpack is a development dependency and not a normal dependency because webpack is not required to run a site in production, once the site has been transpiled.

### Explain what “transpiling code” means and how it relates to frontend development.

> Transpiling code is the conversion of code from one language to the same language or similar language. This can be some form of near-CSS to CSS, or even javascript to javascript with specific browser support added in.

### Briefly describe what a task runner is and how it’s used in frontend development.

> A tool that automates steps in the build process.

### Describe how to write an npm automation script.

> By adding the following bit of json to the `package.json` file:

    ```json
        "build": "webpack --progress --mode=production",
        "watch": "webpack --progress --watch"
    ```

> This sets up the project to build for production, and watches the project and rebuilds every time the specified `.js` file changes.

### Explain one of the main benefits of writing code in modules.

> You can copy and reuse bits of code easily.

### Explain “named exports” and “default exports”.

> Named Exports: When you have multiple functions to export, you can specify them all like so:

    ```javascript
    export {
        functionOne,
        functionTwo
    };
    ```

> This also allows whatever is loading the module to pick and choose functionality to import.

> Default Export:
> Specify a variable to export.

    ```javascript
    const myName = (name) => `Hi! My name is ${name}!`;
    export default myName;
    ```
