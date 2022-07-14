# npm

## Commands

`npm init -y`: Initialize a new project without all the questions

`npm install <package> --save`: Download a package, and save it to the `package.json`.

`npm install webpack webpack-cli --save-dev`: Install webpack

`npx webpack --mode=production`: generates a webpack (with default / no config)

`npx webpack --mode=development`: Use `webpack.config.js` as the config file by default if it exists, but `--config webpack.config.js` can be used to specify a different config.

`npm run build`: Will tell npm to run webpack (and others tools!) automatically.

`npm uninstall <packages>`: Uninstall npm packages


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
touch src/index.js dist/index.html 
```

```javascript test

```

## Dev Packages

[webpack](https://webpack.js.org/): See my [webpack](webpack.md) notes.



## Packages

[Lodash](https://lodash.com/): A utility library delivering modularity, performance & extras. (?)

[moment](https://momentjs.com/): Parse, validate, manipulate, and display dates and times in JavaScript. Note: This project is "done" and other recommendations are made in the site's [project status](https://momentjs.com/docs/#/-project-status/)





## Explain what npm is and where it was commonly used before being adopted on the frontend.

> npm is a package manager for JavaScript packages. It was originally 'node package manager' to manage packages for node.js.


## Describe what npm init does and what package.json is.

> `npm init` initializes (creates) a new node project, including the `package.json`. That json file is the configuration file for the project, so you don't have to share all of your dependencies, just the project file, and node will handle downloading and arranging all of the files into a deployable project.


## Know how to install packages using npm.

> `npm install <package> --save`
> `npm install <package> --save-dev`



## Describe what a JavaScript module bundler like webpack is.

> Webpack will assemble and minify many javascript files into a single transpiled package.




## Explain what the concepts “entry” and “output” mean as relates to webpack.

> Entry, in this context, is where webpack goes to start processing files.
> Output is where the transpiled code is going to be placed.



## Briefly explain what a development dependency is.

> A development dependency is some tool, module, or bit of code that is essential to the build or development process. Webpack is a development dependency and not a normal dependency because webpack is not required to run a site in production, once the site has been transpiled.



## Explain what “transpiling code” means and how it relates to frontend development.

> Transpiling code is the conversion of code from one language to the same language or similar language. This can be some form of near-CSS to CSS, or even javascript to javascript with specific browser support added in.



## Briefly describe what a task runner is and how it’s used in frontend development.

> A tool that automates steps in the build process.



## Describe how to write an npm automation script.

> By adding the following bit of json to the `package.json` file:

    ```json
        "build": "webpack --progress --mode=production",  
        "watch": "webpack --progress --watch" 
    ```

> This sets up the project to build for production, and watches the project and rebuilds every time the specified `.js` file changes.



## Explain one of the main benefits of writing code in modules.

> You can copy and reuse bits of code easily.



## Explain “named exports” and “default exports”.

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