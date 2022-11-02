- [Node](#node)
  - [Installation](#installation)
    - [Global (One Time):](#global-one-time)
    - [Each Project:](#each-project)
    - [Environment Variables](#environment-variables)
      - [1. Passed in from command line:](#1-passed-in-from-command-line)
      - [2. Using an `.env` file:](#2-using-an-env-file)
      - [3. Bypass the require in your <somefile>.js:](#3-bypass-the-require-in-your-somefilejs)
    - [Debugging](#debugging)
  - [Global Variable](#global-variable)
  - [HTTP Requests](#http-requests)
    - [Axios](#axios)
      - [GET](#get)
      - [POST](#post)
    - [Node.js Standard Modules](#nodejs-standard-modules)
      - [GET](#get-1)
      - [POST](#post-1)
  - [File Access](#file-access)
    - [Writing to file](#writing-to-file)
    - [Reading from a file](#reading-from-a-file)
  - [URL Parsing](#url-parsing)

# Node

## Installation

### Global (One Time):

```bash
npm i -g nodemon
```

### Each Project:

Create a directory, and `npm init` inside of it, using defaults or changing options as desired. Ensure that `"private": true,` is added to the package.json file.

`app.js`:

```js
# If using an absolute Path:
#!/usr/bin/node

# Preferred to use environment variable
#!/usr/bin/env node
```

1. Install nodemon as a development dependency.
2. Make `app.js` executable.

```
npm i express
npm i --save-dev nodemon
chmod u+x app.js
```

### Environment Variables

Here are a few ways to access environment variables from within a node script.

#### 1. Passed in from command line:

> $ `USER_ID=239482 USER_KEY=foobar node app.js`

#### 2. Using an `.env` file:

> `.env`
>
> ```
> USER_ID="239482"
> USER_KEY="foobar"
> NODE_ENV="development"
> ```
>
> `<somefile>.js`
>
> ```js
> require("dotenv").config();
>
> process.env.USER_ID; // "239482"
> process.env.USER_KEY; // "foobar"
> process.env.NODE_ENV; // "development"
> ```

#### 3. Bypass the require in your <somefile>.js:

> $ `node -r dotenv/config index.js`


### Debugging

* [VSCode Node.js Debugging](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

  Press `Ctrl-Shift-P` to search for `Toggle Auto Attach`, then choose a suitable option.

* [Debugging a Node.js app using Chrome Dev Tools](https://www.section.io/engineering-education/debug-node-devtools/)


* [Youtube Node.js Debugging Tutorial](https://www.youtube.com/watch?v=2oFKNL7vYV8)


* [brave://inspect/](brave://inspect/) For Brave Browser
* [chrome://inspect/](chrome://inspect/) For Chrome

## Global Variable

[Node Global Objects](https://nodejs.org/docs/latest-v16.x/api/globals.html#global-objects) documentation.

In the browser, the global variable is `window`. In Node, the global variable is `global`. Anything you can reference with `global.<thing>` can be referenced, instead, with `thing` directly.

Here is a list of some of the objects that are available, by default, but using node.

> NOTE: `window` and `window.document` are notably missing. But that's okay since DOM manipulation is not desired server-side.

| object                                       | description                                             |
| -------------------------------------------- | ------------------------------------------------------- |
| \_\_dirname                                  | The directory name of the current module                |
| \_\_filename                                 | The file name of the current mdoule                     |
| exports                                      | (?) See what exports are available (in this module?)    |
| module                                       | An object containing information about the module.      |
| require()                                    | A way to import modules, JSON, and local files.         |
| to0 = setImmediate(callback[,...args])       | Fire callback immediately at the end of this event loop |
| to1 = setTimeout(callback, delay[,...args])  | Fire a one-off event                                    |
| to2 = setInterval(callback, delay[,...args]) | Fire an event every (delay) ms                          |
| clearImmediate(to0)                          | cancel an immediate callback using timeout object       |
| clearTimeout(to1)                            | cancel a timeout using timeout object                   |
| clearInterval(to2)                           | cancel an interval using timeout object                 |

## HTTP Requests

### Axios

[Axios](https://github.com/axios/axios): Promise based HTTP client for the browser and node.js

#### GET

```js
const axios = require("axios");

axios
  .get("https://example.com/todos")
  .then((res) => {
    console.log(`statusCode: ${res.status}`);
    console.log(res);
  })
  .catch((error) => {
    console.error(error);
  });
```

#### POST

```js
axios
  .post("https://whatever.com/todos", {
    todo: "Buy the milk",
  })
  .then((res) => {
    console.log(`statusCode: ${res.status}`);
    console.log(res);
  })
  .catch((error) => {
    console.error(error);
  });
```

### Node.js Standard Modules

#### GET

```js
const https = require("https");

const options = {
  hostname: "example.com",
  port: 443,
  path: "/todos",
  method: "GET",
};

const req = https.request(options, (res) => {
  console.log(`statusCode: ${res.statusCode}`);

  res.on("data", (d) => {
    process.stdout.write(d);
  });
});

req.on("error", (error) => {
  console.error(error);
});

req.end();
```

#### POST

```js
const https = require("https");

const data = JSON.stringify({
  todo: "Buy the milk",
});

const options = {
  hostname: "whatever.com",
  port: 443,
  path: "/todos",
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Content-Length": data.length,
  },
};

const req = https.request(options, (res) => {
  console.log(`statusCode: ${res.statusCode}`);

  res.on("data", (d) => {
    process.stdout.write(d);
  });
});

req.on("error", (error) => {
  console.error(error);
});

req.write(data);
req.end();
```

## File Access

| function                 | description                                                                                                  |
| ------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `fs.access()`            | check if the file exists and Node.js can access it with its permissions                                      |
| `fs.appendFile()`        | append data to a file. If the file does not exist, it's created                                              |
| `fs.chmod()`             | change the permissions of a file specified by the filename passed. Related: `fs.lchmod()`, `fs.fchmod()`     |
| `fs.chown()`             | change the owner and group of a file specified by the filename passed. Related: `fs.fchown()`, `fs.lchown()` |
| `fs.close()`             | close a file descriptor                                                                                      |
| `fs.copyFile()`          | copies a file                                                                                                |
| `fs.createReadStream()`  | create a readable file stream                                                                                |
| `fs.createWriteStream()` | create a writable file stream                                                                                |
| `fs.link()`              | create a new hard link to a file                                                                             |
| `fs.mkdir()`             | create a new folder                                                                                          |
| `fs.mkdtemp()`           | create a temporary directory                                                                                 |
| `fs.open()`              | opens the file and returns a file descriptor to allow file manipulation                                      |
| `fs.readdir()`           | read the contents of a directory                                                                             |
| `fs.readFile()`          | read the content of a file. Related: `fs.read()`                                                             |
| `fs.readlink()`          | read the value of a symbolic link                                                                            |
| `fs.realpath()`          | resolve relative file path pointers (`.`, `..`) to the full path                                             |
| `fs.rename()`            | rename a file or folder                                                                                      |
| `fs.rmdir()`             | remove a folder                                                                                              |
| `fs.stat()`              | returns the status of the file identified by the filename passed. Related: `fs.fstat()`, `fs.lstat()`        |
| `fs.symlink()`           | create a new symbolic link to a file                                                                         |
| `fs.truncate()`          | truncate to the specified length the file identified by the filename passed. Related: `fs.ftruncate()`       |
| `fs.unlink()`            | remove a file or a symbolic link                                                                             |
| `fs.unwatchFile()`       | stop watching for changes on a file                                                                          |
| `fs.utimes()`            | change the timestamp of the file identified by the filename passed. Related: `fs.futimes()`                  |
| `fs.watchFile()`         | start watching for changes on a file. Related: `fs.watch()`                                                  |
| `fs.writeFile()`         | write data to a file. Related: `fs.write()`                                                                  |

### Writing to file

| flag | description                                                                                                                          |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------ |
| r+   | open the file for reading and writing                                                                                                |
| w+   | open the file for reading and writing, positioning the stream at the beginning of the file. The file is created if it does not exist |
| a    | open the file for writing, positioning the stream at the end of the file. The file is created if it does not exist                   |
| a+   | open the file for reading and writing, positioning the stream at the end of the file. The file is created if it does not exist       |

```js
const fs = require("fs");
const content = "Some content!";

// Overwrite file if it exists
// Create a new file containing content if it doesn't exist
fs.writeFile("/Users/joe/test.txt", content, (err) => {
  if (err) console.error(err);
  // file written successfully
});

// Append to end of file
fs.writeFile("/Users/joe/test.txt", content, { flag: "a+" }, (err) => {});

// Or using the purpose-built function
fs.appendFile("file.log", content, (err) => {
  if (err) console.error(err);
  // done!
});
```

### Reading from a file

```js
const fs = require("fs");
try {
  const data = fs.readFileSync("/Users/joe/test.txt", "utf8");
  console.log(data);
} catch (err) {
  console.error(err);
}
```

## URL Parsing

Web Hypertext Application Technology Working Group (WHATWG)

[Node WHATWG URL](https://nodejs.org/api/url.html#url_the_whatwg_url_api)

[WHATWG URL Standard](https://url.spec.whatwg.org/#example-url-parsing)

```js
let myURL = new URL("https://asdf.com");
myURL.port = 80;
myURL.protocol = "http";
myURL.username = "itsme";
myURL.password = "thisisnotwise";
myURL.pathname = "a/path/to/visit";
myURL.hash = "scrolldowntothis";
console.log(myURL.href);
```
