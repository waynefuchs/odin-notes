- [Node.js + Express](#nodejs--express)
  - [Quick Notes (Get to the point)](#quick-notes-get-to-the-point)
  - [Installation](#installation)
    - [Global (One Time):](#global-one-time)
    - [New Project Reminder](#new-project-reminder)
    - [New Project Commands](#new-project-commands)
    - [`package.json`](#packagejson)
    - [Run the node project](#run-the-node-project)
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
  - [MongoDB](#mongodb)
  - [Links](#links)
  - [Glossary](#glossary)

# Node.js + Express

## Quick Notes (Get to the point)

> Note: `app.use()` is used to load middleware; call order matters.

Typical boilerplate express setup

```js
const express = require("express");
const app = express();
app.set("view engine", "ejs");                // EJS middleware
app.use(express.static("public"));            // Middleware to route static content
const userRouter = require("./routes/users"); // ...not defined here
app.use("/users", userRouter);                // Middleware module to handle `/users` routing
app.use(express.urlencoded({extended: true})) // Middleware to access form data (`req.body.<form-element-name>` :: inside some route)


app.get("/", (req, res) => {
  // do something...
  res.send("This is the home page.");
});

// param middleware
router.param("id", (req, res, next, id) => {
  // could do user validation here
  console.log(id);
  next();
});

// Individual Routing...
app.get("/user/:id", (req, res) => {
  res.send(`Got user with ID ${req.params.id}`);
});
app.put("/user/:id", (req, res) => {
  res.send(`Update user with ID ${req.params.id}`);
});
app.delete("/user/:id", (req, res) => {
  res.send(`Deleted user with ID ${req.params.id}`);
});

// Chained Routing...
router
  .route("/user/:id")
  .get((req, res), => {
    res.send(`Got user with ID ${req.params.id}`);
  }).put((req, res) => {
    res.send(`Update user with ID ${req.params.id}`);
  }).delete((req, res) => {
    res.send(`Deleted user with ID ${req.params.id}`);
  });
```

| res method                     | description                                                                          |
| ------------------------------ | ------------------------------------------------------------------------------------ |
| `res.send(<message>)`          | Send text to the client                                                              |
| `res.json(<object>)`           | Send json to the client                                                              |
| `res.sendStatus(<statusCode>)` | Send a status code, can be chained :: `res.sendStatus(500).json({message: 'Error'})` |
| `res.download(<file>)`         | `<file>` is a string, relative path to project root                                  |
| `res.render(<file>)`           | render                                                                               |
| `res.redirect(<path>)`         | redirect the client                                                                  |

## Installation

### Global (One Time):

```bash
npm i -g nodemon              # A package to monitor changes in node project source (and restart the application for you)
npm i -g express-generator    # Project template set-up: `express <new-express-project-name>` (similar to create-react-app.. for express)
```

### New Project Reminder

Just to remind myself exactly what each package is doing...

| package | description                                        |
| ------- | -------------------------------------------------- |
| express | makes routing a lot cleaner                        |
| mongodb | the MongoDB database driver                        |
| ejs     | Embedded JavaScript (View Templates / View Engine) |

### New Project Commands

```bash
# Maybe start this as a github project and download a Node .gitignore(?)
git clone <your-project-uri>
curl https://raw.githubusercontent.com/github/gitignore/main/Node.gitignore > .gitignore

# Using express-generator:
# This installs quite a few packages by default
express <new-project-name> --view=ejs   # or --view=pug (or whatever view engine)
cd <new-project-name>
npm install
npm i --save-dev nodemon
# DEBUG=<new-project-name>:* npm start # meh...
# Edit the package.json (see below)
npm run devstart  # (for nodemon)

# otherwise...do it manually
mkdir <your-project-name>
cd <your-project-name>
mkdir views   # This is where EJS files go
mkdir public  # This is where static files go
mkdir routes  # This is where routing modules go
npm init -y
npm i express mongodb ejs
npm i --save-dev nodemon
```

### `package.json`

```js
  // after "main"
  "private:" true,

  // if used express-generator
  "scripts": {
    "start": "node ./bin/www",
    "devstart": "nodemon ./bin/www",
    "serverstart": "DEBUG=express-locallibrary-tutorial:* npm run devstart"
  },

  // ...if manual
  "scripts": {
    "devStart": "nodemon <main-startup-file-name>.js"   // WebDevSimplified suggests `server.js`
  }
```

### Run the node project

```bash
npm run devStart
```

## Environment Variables

Here are a few ways to access environment variables from within a node script.

I'm not even sure how relevant this is. I'm many lessons in, and have yet to use this.

### 1. Passed in from command line:

> $ `USER_ID=239482 USER_KEY=foobar node app.js`

### 2. Using an `.env` file:

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

- [VSCode Node.js Debugging](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

  Press `Ctrl-Shift-P` to search for `Toggle Auto Attach`, then choose a suitable option.

- [Debugging a Node.js app using Chrome Dev Tools](https://www.section.io/engineering-education/debug-node-devtools/)

- [Youtube Node.js Debugging Tutorial](https://www.youtube.com/watch?v=2oFKNL7vYV8)

- [brave://inspect/](brave://inspect/) For Brave Browser
- [chrome://inspect/](chrome://inspect/) For Chrome

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

## MongoDB

```js
// Example mongodb connection in Node
const MongoClient = require("mongodb").MongoClient;

MongoClient.connect("mongodb://localhost:27017/animals", (err, client) => {
  if (err) throw err;

  const db = client.db("animals");
  db.collection("mammals")
    .find()
    .toArray((err, result) => {
      if (err) throw err;
      console.log(result);
      client.close();
    });
});
```

## Links

- [Serving Static Files](https://expressjs.com/en/starter/static-files.html)
- [Error Handling Middleware](https://expressjs.com/en/guide/error-handling.html)
- [Express Maintained Middleware](https://expressjs.com/en/resources/middleware.html)
- [Database Integration](https://expressjs.com/en/guide/database-integration.html)
- [Request (req) Object](https://expressjs.com/en/4x/api.html#req) documentation
- [Response (res) Object](https://expressjs.com/en/4x/api.html#res) documentation

## Glossary

| Term       | Definition                                                                                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Node       | JavaScript without a browser, based on Chrome's V8 engine.                                                                        |
| Express    | Node.js framework that implements middleware and DRY concepts                                                                     |
| Module     | A javascript library / file that can be imported into other js files / code                                                       |
| Middleware | A JavaScript function that Express calls for you between the time it receives a network request and the time it fires a response. |
| req        | request object -- contains data from the incoming request                                                                         |
| res        | response objcet -- used to interact with the client                                                                               |
