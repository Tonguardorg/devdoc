## Errors

Requests are made using the POST, GET, PATCH and DELETE methods.

## Response Status codes

This API uses HTTP status codes to communicate with the API consumer

| HTTP Status Code | Description              | Meaning                                                                                     |
|------------------|--------------------------|---------------------------------------------------------------------------------------------|
| `200`            | `OK`                     | response to a successful GET, PUT, PATCH or DELETE                                          | 
| `201`            | `Created`                | response to a POST that results in a creation                                               | 
| `204`            | `No Content`             | no content to return                                                                        |
| `400`            | `Bad Request`            | malformed request; request body validation errors                                           | 
| `401`            | `Unauthorized`           | when no or invalid authentication details are provided                                      |                             
| `403`            | `Forbidden`              | when authentication succeeded but authenticated user doesn't have access to the resource    | 
| `404`            | `Not Found`              | the requested resource could not be found                                                  |
| `428`            | `Requests Limit Reached` | when user reached their predefined maximum amount of requests                               | 
| `429`            | `Rate Limit Exceeded`    | when calls to a certain endpoint for a user are higher than predefined limits               | 
| `500`            | `Server Error`           | something went wrong on the API end                                                         | 
| `501`            | `Not Implemented`        | the server either does not recognize the request method, or it lacks the ability to fulfill | 



## Error codes

```json
{
  "code": "integer",
  "detail": "string"
}
```

| Code   | Code string                 | Detail                                                                                                        | 
|--------|:----------------------------|---------------------------------------------------------------------------------------------------------------|
| `0`    | `TOO_MANY_REQUESTS`        | too many requests                                                                                             |
| `1000` | `UNBOUND_ERROR`             | an unspecified or generic error occurred                                                                      |
| `1001` | `UNAVAILABLE`               | the service is temporarily unavailable for technical reasons                                                  |
| `1002` | `RATE_LIMIT_EXCEEDED`       | the limit on the number of available requests has been exhausted                                              | 
| `1003` | `INVALID_ADDRESS`           | the address length should be 48 characters long or an invalid address was provided                            |
| `1004` | `AUTH_ERROR`                | a generic authorization error occurred                                                                        |
| `1005` | `AUTH_FAILED`               | invalid user credentials                                                                                      |
| `1006` | `SESSION_EXPIRED`           | the session has expired                                                                                       |
| `1007` | `AUTH_INVALID_API_KEY`      | the provided api key is invalid                                                                               |
| `1008` | `AUTH_API_KEY_FAILED`       | the api key validation failed                                                                                 |
| `1009` | `AUTH_API_KEY_EXPIRED`      | the api key has expired                                                                                       |
| `1010` | `AUTH_API_KEY_MISSING`      | the api key is missing from the request                                                                       |
| `1011` | `NO_RECORDS_FOUND`          | no records were found (e.g., history records, claims records)                                                 |
| `1012` | `REQUEST_VALIDATION_FAILED` | the request did not pass validation due to incorrect parameters or data                                       |
| `1013` | `REQUEST_PROCESSING_FAILED` | the request could not be processed due to an internal error                                                   |
| `1014` | `SERVICE_MAINTENANCE_ERROR` | the service is undergoing maintenance and is temporarily unavailable                                          |
| `1015` | `INVALID_FILE_FORMAT`       | the uploaded file format is invalid                                                                           |
| `1016` | `INVALID_TOKEN`             | the provided token is invalid                                                                                |
| `1017` | `TOKEN_EXPIRED`             | the token has expired                                                                                         |
| `1018` | `TOKEN_MISSING`             | the token is missing from the request                                                                         |
| `1019` | `INVALID_WHITELIST`         | the whitelist is invalid                                                                                     |
| `1020` | `WHITELIST_NOT_FOUND`       | the whitelist could not be found                                                                              |
| `1021` | `INVALID_MONITORING_RULE`   | the monitoring rule is invalid                                                                               |
| `1022` | `MONITORING_RULE_NOT_FOUND` | the monitoring rule could not be found                                                                        |
| `1023` | `INVALID_CLAIM`             | the claim is invalid                                                                                           |
| `1024` | `CLAIM_NOT_FOUND`           | the claim could not be found                                                                                  |
| `1025` | `INVALID_USER`              | the user is invalid                                                                                           |
| `1026` | `USER_NOT_FOUND`            | the user could not be found                                                                                   |
| `1027` | `INVALID_TOP_HOLDER`        | the top holder is invalid                                                                                     |
| `1028` | `TOP_HOLDER_NOT_FOUND`      | the top holder could not be found                                                                              |
| `1029` | `INVALID_TOKEN_ADDRESS`     | the token address is invalid                                                                                 |
| `1030` | `TOKEN_NOT_FOUND`           | the token could not be found                                                                                  |



