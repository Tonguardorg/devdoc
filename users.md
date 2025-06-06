# Users
User management system.

### [GET]/v1/users/me
Get current user information

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/users/me
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "email": "string",
  "first_name": "string",
  "last_name": "string",
  "organization": "string",
  "created_dt": "string"
}
```

### [PUT]/v1/users/me
Update current user information

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/users/me
```

**Request body**

| Parameter    | Type   | Description | Required |
|--------------|--------|-------------|----------|
| `first_name` | string | First name  | no       |
| `last_name`  | string | Last name   | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "email": "string",
  "first_name": "string",
  "last_name": "string",
  "organization": "string",
  "created_dt": "string"
}
```

### [PUT]/v1/users/me/password
Change current user password

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/users/me/password
```

**Request body**

| Parameter        | Type   | Description | Required |
|------------------|--------|-------------|----------|
| `old_password`   | string | Old password| yes      |
| `new_password`   | string | New password| yes      |

**Responses**

`204` **Success**

### [GET]/v1/users/queries
Get current user query history

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/users/queries
```

**Request parameters (Query)**

| Parameter | Type    | Description                                 | Required |
|-----------|---------|---------------------------------------------|----------|
| `offset`  | integer | Offset to paginate over. Default value is 0 | no       |
| `limit`   | integer | Limit to paginate. Default value is 10      | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "count": 0,
  "results": [
    {
      "id": 0,
      "address": "string",
      "created_dt": "string"
    }
  ]
}
```

### [GET]/v1/users/queries/{query_id}
Get detailed information about specific query

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/users/queries/{query_id}
```

**Request parameters (Path)**

| Parameter | Type    | Description | Required |
|-----------|---------|-------------|----------|
| `query_id`| integer | Query ID    | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "address": "string",
  "created_dt": "string"
}
```

### [GET]/v1/users/queries/export
Export query history as CSV

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/users/queries/export
```

**Responses**

`200` **Success**

**Content-Type** `text/csv`

**Error codes** see full specification [here](../errors.md) 