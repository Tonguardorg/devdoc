## Authorization

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
  "username": "username",
  "password": "password"
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

### [POST]/v1/auth/token

OAuth2 compatible token endpoint. Use for Swagger UI login form and SDK authentication.

**Content-Type** `application/x-www-form-urlencoded`

**Request Body**

| Parameter      | Type   | Description                | Required |
|----------------|--------|----------------------------|----------|
| `grant_type`   | string | Must be "password"         | no      |
| `username`     | string | User email                 | yes      |
| `password`     | string | User password              | yes      |
| `scope`        | string | OAuth2 scope               | no       |
| `client_id`    | string | OAuth2 client ID           | no       |
| `client_secret`| string | OAuth2 client secret       | no       |

**Responses**

`200` **Returns OAuth2 token response**

**Content-Type** `application/json`

```json
{
  "access_token": "string",
  "token_type": "bearer",
  "expiry": "2025-01-28T07:57:37.892Z",
  "risk_queries_count_left": 0,
  "visualizer_queries_count_left": 0,
  "monitoring_addresses_count_left": 0
}
```

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

## Password Reset Flow

### [POST]/v2/reset-password/email
**Send password reset email**

**Content-Type** `application/json`

**Request Body**

| Parameter         | Type   | Description                 | Required |
|-------------------|--------|-----------------------------|----------|
| `email`           | string | User email                  | yes      |
| `recaptcha_token` | string | reCAPTCHA verification token| yes      |

**Example**
```
POST https://api.tonguard.org/v2/reset-password/email
Content-Type: application/json
{
  "email": "user@example.com",
  "recaptcha_token": "token"
}
```

**Responses**

`200` **Success**

---

### [POST]/v2/reset-password/check-token
**Check if reset token is valid**

**Content-Type** `application/json`

**Request Body**

| Parameter | Type   | Description            | Required |
|-----------|--------|------------------------|----------|
| `token`   | string | Reset token from email | yes      |

**Example**
```
POST https://api.tonguard.org/v2/reset-password/check-token
Content-Type: application/json
{
  "token": "reset-token"
}
```

**Responses**

| Parameter | Type    | Description           |
|-----------|---------|-----------------------|
| `valid`   | boolean | Whether token is valid|

`200` **Success**

---

### [POST]/v2/reset-password/change-password
**Change password using reset token**

**Content-Type** `application/json`

**Request Body**

| Parameter  | Type   | Description            | Required |
|------------|--------|------------------------|----------|
| `token`    | string | Reset token from email | yes      |
| `password` | string | New password           | yes      |

**Example**
```
POST https://api.tonguard.org/v2/reset-password/change-password
Content-Type: application/json
{
  "token": "reset-token",
  "password": "new-password"
}
```

**Responses**

| Parameter | Type    | Description                 |
|-----------|---------|-----------------------------|
| `success` | boolean | Whether password was changed|

`200` **Success**