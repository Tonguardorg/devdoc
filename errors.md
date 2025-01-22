## Errors

Requests are made using the POST, GET, PATCH and DELETE methods.

## Response Status codes

This API uses HTTP status codes to communicate with the API consumer

| HTTP Status Code | Description              | Meaning                                                                                     |
|------------------|--------------------------|---------------------------------------------------------------------------------------------|
| `200`            | `OK`                     | Response to a successful GET, PUT, PATCH or DELETE                                          | 
| `201`            | `Created`                | Response to a POST that results in a creation                                               | 
| `204`            | `No Content`             |                                                                                             |
| `400`            | `Bad Request`            | Malformed request; request body validation errors                                           | 
| `401`            | `Unauthorized`           | When no or invalid authentication details are provided                                      |                             
| `403`            | `Forbidden`              | When authentication succeeded but authenticated user doesn't have access to the resource    | 
| `428`            | `Requests Limit Reached` | When user reached his predefined maximum amount of requests                                 | 
| `429`            | `Rate Limit Exceeded`    | When calls to certain endpoint for user are higher than predefined limits                   | 
| `500`            | `Server Error`           | Something went wrong on the API end                                                         | 
| `501`            | `Not Implemented`        | The server either does not recognize the request method, or it lacks the ability to fulfill | 



## Error codes

```json
{
  "code": "integer",
  "detail": "string"
}
```

| Code   | Code string                 | Detail                                                                                                        | 
|--------|:----------------------------|---------------------------------------------------------------------------------------------------------------|
| `0`    |                             | Too Many Requests                                                                                             |
| `1000` | `UNBOUND_ERROR`             | An unspecified or generic error occurred.                                                                     |
| `1001` | `UNAVAILABLE`               | The service is temporarily unavailable for technical reasons.                                                 |
| `1002` | `RATE_LIMIT_EXCEEDED`       | The limit on the number of available requests has been exhausted.                                             | 
| `1003` | `INVALID_ADDRESS`           | The address length should be 48 characters long or an invalid address was provided.                           |
| `1004` | `AUTH_ERROR`                | A generic authorization error occurred.                                                                       |
| `1005` | `AUTH_FAILED`               | Invalid user credentials.                                                                                     |
| `1006` | `SESSION_EXPIRED`           | The session has expired.                                                                                      |
| `1007` | `AUTH_INVALID_API_KEY`      | The provided API key is invalid.                                                                              |
| `1008` | `AUTH_API_KEY_FAILED`       | The API key validation failed.                                                                                |
| `1009` | `AUTH_API_KEY_EXPIRED`      | The API key has expired.                                                                                      |
| `1010` | `AUTH_API_KEY_MISSING`      | The API key is missing from the request.                                                                      |
| `1011` | `NO_RECORDS_FOUND`          | No records were found (e.g., history records, claims records).                                                |
| `1012` | `REQUEST_VALIDATION_FAILED` | The request did not pass validation due to incorrect parameters or data.                                      |
| `1013` | `REQUEST_PROCESSING_FAILED` | The request could not be processed due to an internal error.                                                  |
| `1014` | `SERVICE_MAINTENANCE_ERROR` | The service is undergoing maintenance and is temporarily unavailable.                                         |
| `1015` | `INVALID_FILE_FORMAT`       | The uploaded file format is invalid.                                                                          |


***



