##  Authentication

User authentication. Does not exceed remaining number of queries for the user

### [POST]/v1/auth/login

**Content-Type** `application/json`

**Request body JSON**

| Parameter  | Type   | Description | Requried |
|------------|--------|-------------|----------|
| `username` | string | email       | yes      |
| `password` | string | password    | yes      |

**Request**

```json
{
  "login": "user@example.com",
  "password": "string"
}
```

**Responses**

`200` **Returns JWT token related info and remaining number of queries**

| Parameter  | Type   | Description                                          | 
|------------|--------|------------------------------------------------------|
| `token` | string | token                                                | 
| `token_type` | string | default: JWT                                      | 
| `expiry` | string | token expiry time in '%d/%m/%Y, %H:%M:%S GMT' format | 
| `queries_count_left` | integer | Risk score queries left             |


**Content-Type** `application/json`

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NDIsImVtYWlsIjoicmdheWJhZHVsbGluYUB0b25ndWFyZC5vcmciLCJuYW1lIjoiUml0YSIsInN1cm5hbWUiOiJHYXliYWR1bGxpbmEiLCJleHAiOjE3MzM5NjAxMDUsInNjb3BlcyI6WzJdLCJ0eXBlIjoiYWNjZXNzX3Rva2VuIiwicHQiOlsiLyIsIi9yaXNrLXNjb3JpbmctaGlzdG9yeSIsIi9jbGFpbSIsIi92aXN1YWxpemVyIiwiL215LWNsYWltcyIsIi9hZGRyZXNzZXMiLCIvd2hpdGVsaXN0IiwiL21lIiwiL3RvcF9ob2xkZXJzIiwiL3RvcC1hY2NvdW50cyIsIi9tb25pdG9yaW5nLXJ1bGUiXX0.xLEODITLAtMpBbOQV3B7uoHccGZkfNTb2asfMA48vfU",
  "token_type": "JWT",
  "expiry": "2024-12-11T23:35:05.256362",
  "queries_count_left": 999936
}
```
***
### Authorization errors
***
`401` **Unauthorized**

**Content-Type** `application/json`

```json
{
  "code": 1005,
  "detail": "Invalid user credentials."
}
```
***
`422` **Validation Error**

**Content-Type** `application/json`

```json
[
  {
    "type": "json_invalid",
    "loc": [
      "body",
      44
    ],
    "msg": "JSON decode error",
    "input": {},
    "ctx": {
      "error": "Invalid control character at"
    },
    "code": 1000
  }
]
```
***
`429` **Too Many Requests**

**Content-Type** `application/json`

```json
{
  "code": 0,
  "detail":"Too Many Requests"
}
```
