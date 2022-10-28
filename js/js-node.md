- [Jode](#jode)
  - [Installation](#installation)
    - [Global (One Time):](#global-one-time)
    - [Each Project:](#each-project)
    - [Environment Variables](#environment-variables)
      - [1. Passed in from command line:](#1-passed-in-from-command-line)
      - [2. Using an `.env` file:](#2-using-an-env-file)
      - [3. Bypass the require in your <somefile>.js:](#3-bypass-the-require-in-your-somefilejs)
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

# Jode

## Installation

### Global (One Time):

```bash
npm i -g nodemon
```

### Each Project:

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
fs.writeFile('/Users/joe/test.txt', content, err => {
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
  const data = fs.readFileSync('/Users/joe/test.txt', 'utf8');
  console.log(data);
} catch (err) {
  console.error(err);
}
```