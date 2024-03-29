# NextJS

# Useful Packages

| package                      | description                                                                                           |
| ---------------------------- | ----------------------------------------------------------------------------------------------------- |
| `npm i --save-dev cross-env` | Allow using path in package.json `"dev": "cross-env NODE_OPTIONS='--inspect' next dev"` for debugging |

## API

[API Routes Introduction](https://nextjs.org/docs/api-routes/introduction)

API routes are defined based on folder structure in the `api/` directory in the project root.

Example:

```js
export default (req, res) => {
  // req.cookies
  // req.query
  // req.body

  // res.status(200)
  // res.json({})
  // res.send('HTTP Response')

  if(req.method === "POST")
    return res.status(200).json([
      id: 1,
      email: "some@email.com",
      name: "Some Dude",
    ]);
}
```
