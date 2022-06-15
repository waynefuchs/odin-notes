# Back End

## Glossary

REST: Representational State Transfer
    - Separation of Concerns (server/client code can completely change as long as the protocol between them remains the same)
    - to be RESTful, the client must make a request to the server, *usually consisting of*:
        1. An HTTP verb (GET/POST/PUT/DELETE)
        2. A header (such as: `text/html` or `image/jpeg`)
        3. A path to a resource (such as: `/user/put/{username}`)
        4. An optional message

    
    an HTTP verb, which defines what kind of operation to perform
a header, which allows the client to pass along information about the request
a path to a resource
an optional message body containing data

## CRUD

- Create
- Read
- Update
- Delete

## Common Response Codes
| Code | Meaning |
| ---- | ----- |
| 200 (OK) | This is the standard response for successful HTTP requests. |
| 201 (CREATED) | This is the standard response for an HTTP request that resulted in an item being successfully created. |
| 204 (NO CONTENT) | This is the standard response for successful HTTP requests, where nothing is being returned in the response body. |
| 400 (BAD REQUEST) | The request cannot be processed because of bad request syntax, excessive size, or another client error. |
| 403 (FORBIDDEN) | The client does not have permission to access this resource. |
| 404 (NOT FOUND) | The resource could not be found at this time. It is possible it was deleted, or does not exist yet. |
| 500 (INTERNAL SERVER ERROR) | The generic answer for an unexpected failure if there is no more specific information available. |