# HTTP Status Codes

| range | category description   |
| ----- | ---------------------- |
| 1XX   | Information Responses  |
| 2XX   | Successful Responses   |
| 3XX   | Redirection Messages   |
| 4XX   | Client Error Responses |
| 5XX   | Server Error Responses |

| Code     | Name                | Description                                                                              |
| -------- | ------------------- | ---------------------------------------------------------------------------------------- |
| 100      | Continue            | Tell the client to continue the request or ignore this response if already finished      |
| 101      | Switching Protocols | Response to an "Upgrade" request from the client. eg: switch protocol from http to https |
| 102      | Processing          | Server is processing, no response is available yet                                       |
| 103      | Early Hints         | Intended to be used with the Link header to allow the client to preload resources        |
| 200      | OK                  | GET, HEAD, PUT/POST, TRACE succeeded                                                     |
