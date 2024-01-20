# Webpack

A tool for bundling modules. [Config](https://webpack.js.org/configuration/) docs. 

My github repo is following the official [Webpack Guides](https://webpack.js.org/guides/) tutorial series.

1. Getting Started
2. Asset Management
3. Output Management
4. Development

## CSS: style-loader and css-loader

`npm install --save-dev style-loader css-loader`

[style-loader](https://webpack.js.org/loaders/style-loader/): Inject CSS into the DOM 

[css-loader](https://webpack.js.org/loaders/css-loader/): interpret @import and url() like mport/requre() and resolve them.

```javascript
// webpack.config.js
{
    test: /\.css$/i,
    use: ['style-loader', 'css-loader'],
},
```

```javascript
// One of your entry point js files
import css from "file.css";
```

## IMAGES: Asset Modules

This is built-in, no npm required. It just needs to be set up in the `webpack.config.js`.

[Asset Modules](https://webpack.js.org/guides/asset-modules/)

```javascript
{
    test: /\.(png|svg|jpg|jpeg|gif)$/i,
    type: 'asset/resource'
},
```
Then reference the image in a CSS file directly
```css
.background {
  background: url('./icon.png');
}
```

Or, in one of the `.js` files:
```javascript
const myIcon = new Image();
myIcon.src = Icon;
```


## Loading Fonts

No additional modules to install, just add config

```javascript
{
    test: /\.(woff|woff2|eot|ttf|otf)$/i,
    type: 'asset/resource',
},
```

## Loading Data

### CSV and XML

`npm install --save-dev csv-loader xml-loader`

Note: This is unnecessary for Json, you can load json without any additional packages or webpack rules.

This will allow loading csv and xml files in as data files to be used in javascript.

```javascript
{
    test: /\.(csv|tsv)$/i,
    use: ['csv-loader'],
},
{
    test: /\.(xml)$/i,
    use: ['xml-loader'],
},
```

### TOML, YAMLJS, and JSON5 (Custom Loaders)

`npm install toml yamljs json5 --save-dev`

Addition to `webpack.config.js`:

```javascript
const toml = require('toml');
const yaml = require('yamljs');
const json5 = require('json5');

///... (rules)

      {
        test: /\.toml$/i,
        type: 'json',
        parser: {
          parse: toml.parse,
        },
      },
      {
        test: /\.yaml$/i,
        type: 'json',
        parser: {
          parse: yaml.parse,
        },
      },
      {
        test: /\.json5$/i,
        type: 'json',
        parser: {
          parse: json5.parse,
        },
      },

/// ...
```


### [HtmlWebpackPlugin](https://github.com/jantimon/html-webpack-plugin)

Generate HTML files to serve webpack bundles. (using generation or templates)

`npm install --save-dev html-webpack-plugin`

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');

// ...

    plugins: [
        new HtmlWebpackPlugin({
            title: 'WebpageTitle',
        }),
    ],

// output: ...

```


### webpack-dev-server

`npm install --save-dev webpack-dev-server`


### webpack-dev-middleware

`npm install --save-dev express webpack-dev-middleware`





## TOP Questions:

[](https://www.theodinproject.com/lessons/node-path-javascript-webpack#knowledge-check)

* How do you load CSS using webpack?

  > [Loading CSS](https://webpack.js.org/guides/asset-management/#loading-css)
  > 1. using `style-loader` and `css-loader` npm packages
  > 2. adding a rule to handle `.css` files in the `webpack.config.js`
  > 3. using the line `import css from "file.css";` in one of the entry point `.js` files.

* How do you load images using webpack?

  > [Loading Images](https://webpack.js.org/guides/asset-management/#loading-images)
  > 1. Add a `webpack.config.js` rule to handle image files (image loading functionality is built-in)
  > 2. Reference the image in a CSS file directly (`background: url('./icon.png');`) or js file (`const myIcon = new Image(); myIcon.src = Icon;`)


* How do you load fonts using webpack?

  > [Loading Fonts](https://webpack.js.org/guides/asset-management/#loading-fonts)
  > 1. Add a `webpack.config.js` rule to match font files
  > 2. Reference the font in your CSS.

  ```css
  @font-face {
    font-family: 'MyFont';
    src: url('./my-font.woff2') format('woff2'),
      url('./my-font.woff') format('woff');
    /* Or just a TTF or whatever */
    font-weight: 600;
    font-style: normal;
  }
  .body {
    font-family: 'MyFont';
  }
  ```

* How do you load data using webpack?

  > [Loading Data](https://webpack.js.org/guides/asset-management/#loading-data)
  > The instructions are pretty much the same as above. Depending on the type of data, a npm package may be required.


* How would you track errors in bundled source code?

  > Using [source maps](https://webpack.js.org/guides/development/#using-source-maps).