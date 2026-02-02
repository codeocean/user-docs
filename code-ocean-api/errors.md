---
description: >-
  Code Ocean utilizes conventional HTTP response codes to indicate the success
  or failure of an API request.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/code-ocean-api/errors
---

# Errors

Codes in the `2xx` range indicate success. Codes in the `4xx` range indicate an error that failed given the information provided. Codes in the `5xx` range indicate an error with Code Ocean's internal servers.

| Code               | Status            | Summary                                                                                                              |
| ------------------ | ----------------- | -------------------------------------------------------------------------------------------------------------------- |
| 200                | OK                | Everything is okay.                                                                                                  |
| 204                | No Content        | Everything is okay. Response doesn't include a body.                                                                 |
| 400                | Bad Request       | The request was unacceptable. Could be a missing required parameter, misspelled word or bad format.                  |
| 401                | Unauthorized      | No valid access token provided.                                                                                      |
| 403                | Forbidden         | The access token doesn’t have permissions to perform the request.                                                    |
| 404                | Not Found         | The requested resource doesn’t exist.                                                                                |
| 429                | Too Many Requests | The Computation API may get overloaded with requests. We recommend a back off period before sending another request. |
| 500, 502, 503, 504 | Server Errors     | Code Ocean servers have an issue.                                                                                    |
