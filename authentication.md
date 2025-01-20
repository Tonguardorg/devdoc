##  Authentication

User authentication. Does not reduce remaining number of queries for the user.

### [POST]/v1/auth/login

**Content-Type** `application/json`

**Request body JSON**

| Parameter  | Type   | Description | Required |
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

| Parameter            | Type    | Description                                          | 
|----------------------|---------|------------------------------------------------------|
| `token`              | string  | token                                                | 
| `token_type`         | string  | default: JWT                                         | 
| `expiry`             | string  | token expiry time in '%d/%m/%Y, %H:%M:%S GMT' format | 
| `queries_count_left` | integer | risk score queries left                              |


**Content-Type** `application/json`

```json
{
  "token": "JWT",
  "token_type": "JWT",
  "expiry": "2024-12-11T23:35:05.256362",
  "queries_count_left": 999936
}
```
***

### Authorization errors

see full specification [here ](../errors.md)


