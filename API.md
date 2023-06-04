- [API (Application Programming Interface)](#api-application-programming-interface)
- [Links](#links)
- [Nodejs+Express Project Structure](#nodejsexpress-project-structure)
  - [Routes](#routes)
- [Authentication](#authentication)
  - [JSON Web Tokens (JWT)](#json-web-tokens-jwt)
    - [Cons](#cons)
    - [Pros](#pros)
  - [Passport.js](#passportjs)
- [REST (Representational State Transfer)](#rest-representational-state-transfer)
  - [The Seven Restful Routes](#the-seven-restful-routes)
- [Nodejs specifics](#nodejs-specifics)
- [CORS (Cross Origin Resource Sharing)](#cors-cross-origin-resource-sharing)
- [Jamstack](#jamstack)

> ⓘ TODO: This document has gone **way** out of scope from API. Clean this up.

# API (Application Programming Interface)

An API is a way for two or more pieces of software to communicate. Specifically, a **Web API** is a way to separate back end program logic, such as database interfaces, in a 'black box' of sorts; only exposing the parts (endpoints) that a user interface would find useful. This allows freedom to change things in the back end implementation without affecting reliant software. A strong use case is the ability to use the endpoints to retrieve data for a react website, android, and iOS applications all while maintaining a single API to serve data.

# Links

| Website                                                                                                                                          | Organization         | Odin | Description                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------- | ---- | -------------------------------------------------------------------------------------------------------------------------------------- |
| [HTTP Status Codes](./html/HTTP-Status-Codes.md)                                                                                                 | My Notes             |      | HTTP Reponse / Status Codes                                                                                                            |
| [Representational state transfer (REST)](https://en.wikipedia.org/wiki/Representational_state_transfer)                                          | Wikipedia            | ✔️   | An overview of REST                                                                                                                    |
| [The Little Book on REST Services](https://kennethlange.com/the-little-book-on-rest-services/)                                                   | Kenneth Lange        |      | Free e-book, linked from wikipedia.                                                                                                    |
| [The Ultimate Checklist for REST APIs](http://www.kennethlange.com/posts/The-Ultimate-Checklist-for-REST-APIs.html)                              | Kenneth Lange        |      | A good reference when developing an API                                                                                                |
| [Best pracitces for REST API design](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)                                  | The Overflow         | ✔️   | Good practices using express/node to develop REST APIs                                                                                 |
| [Same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)                                                   | MDN                  | ✔️   | Security policy information to prevent CORS                                                                                            |
| [CORS Middleware](https://expressjs.com/en/resources/middleware/cors.html#enabling-cors-pre-flight)                                              | expressjs            | ✔️   | Documentation for a middleware that enables CORS                                                                                       |
| [How to create a REST API with Express.js in Node.js](https://www.robinwieruch.de/node-express-server-rest-api/)                                 | Robin Wieruch        | ✔️   | Tutorial listed in the "API Basics" lesson                                                                                             |
| [PassportJS](https://www.passportjs.org/)                                                                                                        | Passport             |      | The official PassportJS site.                                                                                                          |
| [The Ultimate Guide to Passport JS](https://dev.to/zachgoll/the-ultimate-guide-to-passport-js-k2l)                                               | Zach Gollwitzer      |      | Amazing resource for understanding PassportJS with LocalStrategy                                                                       |
| [Learn the MERN Stack](https://www.youtube.com/watch?v=-0exw-9YJBo&list=PLillGF-RfqbbQeVSccR9PGKHzPJSWqcsm)                                      | Traversy Media       |      | YouTube Playlist tutorial, demonstrating the MERN stack. (including JWT)                                                               |
| [JWT: The Right way of implementing](https://siddharthac6.medium.com/json-web-token-jwt-the-right-way-of-implementing-with-node-js-65b8915d550e) | Siddhartha Chowdhury |      | (2018) Found this on stackoverflow in a comment and it has some good ideas, specifically around easy / quick generation of secret keys |

# Nodejs+Express Project Structure

- src/
  - config/
  - controllers/
    - {a}Controller.js
    - {b}Controller.js
  - middleware/
    - errorMiddleware.js
    - authMiddleware.js
    - {a}Middleware.js
    - {b}Middleware.js
  - models/
    - {a}Models.js
    - {b}Models.js
  - routes/
    - {a}Routes.js
    - {b}Routes.js
  - index.js

## Routes

Using [express-async-handler](https://www.npmjs.com/package/express-async-handler) to handle thrown errors inside middleware, and Mongoose for MongoDB fetch.

```js
import asyncHandler from "express-async-handler";
// @desc    Authenticate a user
// @route   POST /api/v1/users/login
// @access  Public
const loginUser = asyncHandler(async (req, res) => {
  const { email, password } = req.body;
  const user = await User.findOne({ email });
  if (!user || !(await bcrypt.compare(password, user.password))) {
    res.status(400);
    throw new Error("Invalid credentials");
  }

  res.json({
    _id: user.id,
    name: user.name,
    email: user.email,
  });
});
```

# Authentication

I find this is one of the more interesting (and frustrating) topics covered in all of The Odin Project.

## JSON Web Tokens (JWT)

Odin pushes Oauth 2.0 and JWT. While reading up on JWT's usage, I find myself disinclined to use them in the manner presented for TOP. For example, in [JWT Best practices and when to use](https://blog.logrocket.com/jwt-authentication-best-practices/) it is recommended not to use them for authentication.

They are best used to verify that the data contained in an object is genuine and not tampered with. But an SSL site already has this feature built-in.

### Cons

XSS used to be an issue, but less so with modern browser built-in protections. Overhead increases trending towards the exponential as the data stored in the token increases, especially when used in conjunction with cookies. The token can not easily be revoked.

### Pros

You don't have to hit the database to pull data from the token. Once a user is authenticated, they can remain so indefinitely, as long as the token is refreshed. This could be seen as a 'con' from a security standpoint, but a 'pro' from a usability standpoint.

## Passport.js

Once authenticated, the `req.user` object contains the user object. In the `passport.serializeUser` and `passport.deserializeUser` functions, ensure that you are returning versions that do not contain the password hash or salt.

See my [Odin API Tutorial](https://github.com/waynefuchs/odin-api-tutorial) project and the Zach Gollwitzer write up, linked above for PassportJS implementation details.

# REST (Representational State Transfer)

REST APIs refer directly to the resource and use HTTP verbs to determine the action. This usually means that you end up with two URI's per resource; the first for a collection and the second for individual objects in that collection. HTTP verbs determine whether the operation is (**C**)reate (**R**)ead (**U**)pdate or (**D**)elete.

## The Seven Restful Routes

| Action  | Verb   | Method Verb | JSON Route | HTML Route | PATH                   | Task                               |
| ------- | ------ | ----------- | :--------: | :--------: | ---------------------- | ---------------------------------- |
| Create  | POST   | `create`    |     ✔️     |            | `/customers`           | Create a new customer              |
| Read    | GET    | `index`     |     ✔️     |            | `/customers`           | Search customer information        |
| Read    | GET    | `show`      |     ✔️     |            | `/customers/{id}`      | Fetch a specific customer          |
| Update  | PUT    | `update`    |     ✔️     |            | `/customers/{id}`      | Update an existing customer's data |
| Delete  | DELETE | `destroy`   |     ✔️     |            | `/customers/{id}`      | Delete an existing customer        |
| Display | GET    | `new`       |            |     ✔️     | `/customers/{id}/new`  | Show form to create a new customer |
| Display | GET    | `edit`      |            |     ✔️     | `/customers/{id}/edit` | Show form to edit a new customer   |

# Nodejs specifics

Use `res.json()` instead of `res.send()` / `res.render()`.

# CORS (Cross Origin Resource Sharing)

CORS exists to prevent a site from performing malicious actions. If I have a site, and I write some javascript code to direct your browser to give me your contact list from your e-mail service, except your browser detects that the request is not originating from your e-mail and blocks that request.

You typically want to block all access from any origin except your frontend website. However, during development it is common to allow access from all origins to make testing and general development easier.

# Jamstack

> ⓘ Note: I am still having difficulty moving this concept from abstract concept to concrete implementation. This section should be considered `work-in-progress`

(**J**)avascript, (**A**)PIs and (**M**)arkdown (**Stack**).

| Website                                                         | Organization | Odin | Description                                            |
| --------------------------------------------------------------- | ------------ | ---- | ------------------------------------------------------ |
| [What is Jamstack](https://www.youtube.com/watch?v=Y8PXMbr0Kqo) | Academind    |      | I didn't understand Jamstack until I saw this video.   |
| [Jamstack](https://jamstack.org/what-is-jamstack/)              | Jamstack     | ✔️   | The official jamstack resource.                        |
| [Jamstack Explained](https://bejamas.io/blog/jamstack/)         | Bejamas      |      | The resource that finally told me what 'jamstack' was. |

Odin introduces the concept of "Jamstack," which is described as 'static, pre-rendered content' without the need for worrying about database security or slow database operations. If you need dynamic content with jamstack, that is provided by an API.

In essence, as I understand it, the philosophy behind this "stack" is to maintain static content wherever possible, and move away from managing server configurations and towards utilizing services. For example: Your Nextjs project stored on github, pulled and built by heroku, utilizing a CDN for media (images, fonts, js packages), with database access provided by Atlas, and content pre-rendered from markdown by a tool such as hugo or gatsby.
