- [Serverless Computing](#serverless-computing)
- [Serverless Providers](#serverless-providers)
- [Function Types](#function-types)
  - [Restful](#restful)
  - [Reactive](#reactive)
- [Code Structure](#code-structure)

> ⓘ TODO: _very_ incomplete, based on 30 minutes of research on the topic for familiarity

# Serverless Computing

Serverless is a misnomer used to describe servers "in the cloud" that require zero configuration and zero maintenance from a developer.

More information can be found at the [Serverless Computing Wikipedia Page](https://en.wikipedia.org/wiki/Serverless_computing) and Fireship has a pretty good introductory video titled [Serverless Computing in 100 Seconds](https://www.youtube.com/watch?v=W_VV2Fx32_Y) that has a tutorial on setting up a backend using Serverless at the end.

# Serverless Providers

- AWS Lambda
- Microsoft Azure Functions
- Google Cloud Functions
- Cloudflare Workers
- Netlify Functions
- Vercel Functions

# Function Types

Every function is stored in its own file. The functions are either RESTful or Reactive.

## Restful

Restful functions run when an http request is made.

## Reactive

A Reactive function will only run when something has changed. For example, when a document has been uploaded, or an entry in the database has changed.

# Code Structure

Refer to the Serverless Provider's documentation. The following information is for Firebase Functions.

1. Mandatory 1 file for every function; it is useful to name the file the same as the function or endpoint.
2. The file will be placed in a `restful` or `reactive` folder
3. Split the backend into resource groups

```
📂 functions
  📂 orders
    📂 reactive
      📄 onOrderCreated.function.ts
      📄 onOrderStatusChanged.function.ts
    📂 restful
      📄 addOrderToQueue.endpoint.ts
  📁 payments
  📁 users
```
