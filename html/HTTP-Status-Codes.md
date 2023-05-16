- [HTTP Status Codes](#http-status-codes)
  - [Links](#links)
  - [Categories](#categories)
  - [Codes](#codes)

> TODO: Incomplete - Some descriptions are not filled in

# HTTP Status Codes

## Links

- [MDN HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

## Categories

| range | category      | description                                                                                    |
| ----- | ------------- | ---------------------------------------------------------------------------------------------- |
| 1XX   | Informational | Communicates transfer protocol-level information.                                              |
| 2XX   | Successful    | Indicates that the client’s request was accepted successfully.                                 |
| 3XX   | Redirection   | Indicates that the client must take some additional action in order to complete their request. |
| 4XX   | Client Error  | This category of error status codes points the finger at clients.                              |
| 5XX   | Server Error  | The server takes responsibility for these error status codes.                                  |

## Codes

| Code | Name                            | Description                                                                                           |
| ---- | ------------------------------- | ----------------------------------------------------------------------------------------------------- |
| 100  | Continue                        | Tell the client to continue the request or ignore this response if already finished                   |
| 101  | Switching Protocols             | Response to an "Upgrade" request from the client. eg: switch protocol from http to https              |
| 102  | Processing                      | Server is processing, no response is available yet                                                    |
| 103  | Early Hints                     | Intended to be used with the Link header to allow the client to preload resources                     |
| 200  | OK                              | GET, HEAD, PUT/POST, TRACE succeeded                                                                  |
| 201  | Created                         | POST (some PUT) request succeeded                                                                     |
| 202  | Accepted                        | Noncommittal- Some other processing must take place to determine success (eg: ffmpeg)                 |
| 203  | Non-Authoritative Information   | When interacting with a third party, such as a mirror                                                 |
| 204  | No Content                      | No content, but headers can be useful (Such as updating cached headers)                               |
| 205  | Reset Content                   | Reset the document which sent this request (Document, Clear Form, Reset Canvas, or Refresh UI)        |
| 206  | Partial Content                 | A response to the `Range` header (416 for error response)                                             |
| 207  | Multi-Status                    |                                                                                                       |
| 208  | Already Reported                |                                                                                                       |
| 226  | IM Used                         |                                                                                                       |
| 300  | Multiple Choices                |                                                                                                       |
| 301  | Moved Permanently               |                                                                                                       |
| 302  | Found                           |                                                                                                       |
| 303  | See Other                       |                                                                                                       |
| 305  | Use Proxy                       | **depreceated**                                                                                       |
| 306  | unused                          |                                                                                                       |
| 307  | Temporary Redirect              |                                                                                                       |
| 308  | Permanent Redirect              |                                                                                                       |
| 400  | Bad Request                     | Malformed request syntax, invalid request message framing, deceptive request routing, etc             |
| 401  | Unauthorized                    | Typically means 'unauthenticated'                                                                     |
| 402  | Payment Required                | Rarely used; intended for payment systems                                                             |
| 403  | Forbidden                       | Client does not have access rights                                                                    |
| 404  | Not found                       | Server is unable to locate the requested resource                                                     |
| 405  | Method Not Allowed              | Response method is known by the server but is not supported (eg: calling DELETE to remove a resource) |
| 406  | Not Acceptable                  |                                                                                                       |
| 407  | Proxy Authentication Required   | Similar to `401` but auth is needed to be done by a proxy                                             |
| 408  | Request Timeout                 | The server would like to close the connection; some servers just close the connection without message |
| 409  | Conflict                        | Request conflicts with the state of the server                                                        |
| 410  | Gone                            | Deleted from the server with no forwarding address                                                    |
| 411  | Length Required                 | `Content-Length` header field is not defined and the server requires it                               |
| 412  | Precondition Failed             |                                                                                                       |
| 413  | Payload Too Large               |                                                                                                       |
| 414  | URI Too Long                    |                                                                                                       |
| 415  | Unsupported Media Type          |                                                                                                       |
| 416  | Range Not Satisfiable           |                                                                                                       |
| 417  | Expectation Failed              |                                                                                                       |
| 418  | I'm a teapot                    |                                                                                                       |
| 421  | Misdirected Request             |                                                                                                       |
| 422  | Unprocessable Entity            |                                                                                                       |
| 423  | Locked                          |                                                                                                       |
| 424  | Failed Dependency               |                                                                                                       |
| 425  | Too Early                       |                                                                                                       |
| 426  | Upgrade Required                |                                                                                                       |
| 428  | Precondition Required           |                                                                                                       |
| 429  | Too Many Requests               |                                                                                                       |
| 431  | Request Header Fields Too Large |                                                                                                       |
| 451  | Unavailable for Legal Reasons   | eg: Web page censored by a government                                                                 |
| 500  | Internal Server Error           | Server encountered a situation it does not know how to handle (crash)                                 |
| 501  | Not Implemented                 |                                                                                                       |
| 502  | Bad Gateway                     |                                                                                                       |
| 503  | Service Unavailable             |                                                                                                       |
| 504  | Gateway Timeout                 |                                                                                                       |
| 505  | HTTP Version Not Supported      |                                                                                                       |
| 506  | Variant Also Negotiates         |                                                                                                       |
| 507  | Insufficient Storage            |                                                                                                       |
| 508  | Loop Detected                   |                                                                                                       |
| 510  | Not Extended                    |                                                                                                       |
| 511  | Network Authentication Required |                                                                                                       |
