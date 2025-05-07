##  Authorization

User authorization. **Does not reduce** remaining number of queries for the user.

## Generating a Token
Before using our API, you must generate an authentication token by making a one-time request. 

Below is an example request for obtaining a token:

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

**Content-Type** `application/json`

```json
{
  "token": "string",
  "token_type": "JWT",
  "expiry": "2025-01-28T07:57:37.892Z",
  "risk_queries_count_left": 0,
  "visualizer_queries_count_left": 0,
  "monitoring_addresses_count_left": 0
}
```

| Parameter                         | Type    | Description                                          | 
|-----------------------------------|---------|------------------------------------------------------|
| `token`                           | string  | token                                                | 
| `token_type`                      | string  | default: JWT                                         | 
| `expiry`                          | string  | token expiry time in '%d/%m/%Y, %H:%M:%S GMT' format | 
| `risk_queries_count_left`         | integer | risk score queries left                              |
| `visualizer_queries_count_left`   | integer | visualizer queries left                              |
| `monitoring_addresses_count_left` | integer | monitoring addresses left                            |

***

### Authorization errors

see full specification [here ](../errors.md)

***
## Using the Token
The obtained token must be included in every API request in the Authorization header.
Example:
```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Do not request a token for every API call**. This is redundant and may result in your account being blocked for violating 
the API usage rules. Instead, store the token securely and reuse it for all requests until it expires (`expires_in`).

## Refreshing the Token
When the token expires, you can request a new one.

### [POST]/v2/login
**Login to the system**

**Example**
```
https://api.tonguard.org/v2/login
```

**Content-Type** `application/json`

**Request Body**

| Parameter   | Type   | Description                | Required |
|-------------|--------|----------------------------|----------|
| `email`     | string | user email                 | yes      |
| `password`  | string | user password              | yes      |

**Responses**

| Parameter | Type   | Description                |
|-----------|--------|----------------------------|
| `token`   | string | JWT token for authorization|

### [POST]/v2/reset-password/email
**Send password reset email**

**Example**
```
https://api.tonguard.org/v2/reset-password/email
```

**Content-Type** `application/json`

**Request Body**

| Parameter | Type   | Description                | Required |
|-----------|--------|----------------------------|----------|
| `email`   | string | user email                 | yes      |

**Responses**

| Parameter | Type    | Description                |
|-----------|---------|----------------------------|
| `success` | boolean | Whether email was sent     |

### [POST]/v2/reset-password/check-token
**Check if reset token is valid**

**Example**
```
https://api.tonguard.org/v2/reset-password/check-token
```

**Content-Type** `application/json`

**Request Body**

| Parameter | Type   | Description                | Required |
|-----------|--------|----------------------------|----------|
| `token`   | string | Reset token from email     | yes      |

**Responses**

| Parameter | Type    | Description                |
|-----------|---------|----------------------------|
| `valid`   | boolean | Whether token is valid     |

### [POST]/v2/reset-password/change-password
**Change password using reset token**

**Example**
```
https://api.tonguard.org/v2/reset-password/change-password
```

**Content-Type** `application/json`

**Request Body**

| Parameter    | Type   | Description                | Required |
|--------------|--------|----------------------------|----------|
| `token`      | string | Reset token from email     | yes      |
| `password`   | string | New password               | yes      |

**Responses**

| Parameter | Type    | Description                |
|-----------|---------|----------------------------|
| `success` | boolean | Whether password was changed|

***