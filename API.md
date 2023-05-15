- [API (Application Programming Interface)](#api-application-programming-interface)
  - [Links](#links)
  - [Authentication](#authentication)
    - [Passport.js](#passportjs)
  - [REST (Representational State Transfer)](#rest-representational-state-transfer)
  - [Nodejs specifics](#nodejs-specifics)
  - [CORS (Cross Origin Resource Sharing)](#cors-cross-origin-resource-sharing)
  - [Jamstack](#jamstack)

# API (Application Programming Interface)

An API is a way for two or more pieces of software to communicate. Specifically, a **Web API** is a way to separate back end program logic, such as database interfaces, in a 'black box' of sorts; only exposing the parts (endpoints) that a user interface would find useful. This allows freedom to change things in the back end implementation without affecting reliant software. A strong use case is the ability to use the endpoints to retrieve data for a react website, android, and iOS applications all while maintaining a single API to serve data.

## Links

| Website                                                                                                             | Organization  | Odin | Description                                            |
| ------------------------------------------------------------------------------------------------------------------- | ------------- | ---- | ------------------------------------------------------ |
| [HTTP Status Codes](./html/HTTP-Status-Codes.md)                                                                    | My Notes      |      | HTTP Reponse / Status Codes                            |
| [Jamstack](https://jamstack.org/what-is-jamstack/)                                                                  | Jamstack      | ✔️   | The official jamstack resource.                        |
| [Jamstack Explained](https://bejamas.io/blog/jamstack/)                                                             | Bejamas       |      | The resource that finally told me what 'jamstack' was. |
| [Representational state transfer (REST)](https://en.wikipedia.org/wiki/Representational_state_transfer)             | Wikipedia     | ✔️   | An overview of REST                                    |
| [The Little Book on REST Services](https://kennethlange.com/the-little-book-on-rest-services/)                      | Kenneth Lange |      | Free e-book, linked from wikipedia.                    |
| [The Ultimate Checklist for REST APIs](http://www.kennethlange.com/posts/The-Ultimate-Checklist-for-REST-APIs.html) | Kenneth Lange |      | A good reference when developing an API                |
| [Best pracitces for REST API design](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)     | The Overflow  | ✔️   | Good practices using express/node to develop REST APIs |
| [Same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)                      | MDN           | ✔️   | Security policy information to prevent CORS            |
| [CORS Middleware](https://expressjs.com/en/resources/middleware/cors.html#enabling-cors-pre-flight)                 | expressjs     | ✔️   | Documentation for a middleware that enables CORS       |
| [How to create a REST API with Express.js in Node.js](https://www.robinwieruch.de/node-express-server-rest-api/)    | Robin Wieruch | ✔️   | Tutorial listed in the "API Basics" lesson             |

## Authentication

I find this is one of the more interesting topics in all of the Odin work that I've worked on. It is also one of the most difficult topics that I've studied.

### Passport.js

Once authenticated, the `req.user` object contains the user object. In the `passport.serializeUser` and `passport.deserializeUser` functions, ensure that you are returning versions that do not contain the password hash or salt.

## REST (Representational State Transfer)

REST APIs refer directly to the resource and use HTTP verbs to determine the action. This usually means that you end up with two URI's per resource; the first for a collection and the second for individual objects in that collection. HTTP verbs determine whether the operation is (**C**)reate (**R**)ead (**U**)pdate or (**D**)elete.

| Action | Verb   | PATH              | Task                               |
| ------ | ------ | ----------------- | ---------------------------------- |
| Create | POST   | `/customers`      | Create a new customer              |
| Read   | GET    | `/customers`      | Search customer information        |
| Read   | GET    | `/customers/{id}` | Fetch a specific customer          |
| Update | PUT    | `/customers/{id}` | Update an existing customer's data |
| Delete | DELETE | `/customers/{id}` | Delete an existing customer        |

## Nodejs specifics

Use `res.json()` instead of `res.send()` / `res.render()`.

## CORS (Cross Origin Resource Sharing)

CORS exists to prevent a site from performing malicious actions. If I have a site, and I write some javascript code to direct your browser to give me your contact list from your e-mail service, except your browser detects that the request is not originating from your e-mail and blocks that request.

You typically want to block all access from any origin except your frontend website. However, during development it is common to allow access from all origins to make testing and general development easier.

## Jamstack

Odin introduces the concept of "Jamstack," which is described as 'static, pre-rendered content' without the need for worrying about database security or slow database operations. The reason for this is that someone else is managing that for you. If you need dynamic content with jamstack, that is provided by an API using SaaS such as Heroku.

In essence, it's the desire to move away from managing server configurations and towards utilizing a service
