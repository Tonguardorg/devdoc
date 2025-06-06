# Top Holders
Get information about top token holders in TON.

### [GET]/v1/top_holders
Get list of top holders

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/top_holders
```

**Request parameters (Query)**

| Parameter  | Type    | Description                                    | Required |
|------------|---------|------------------------------------------------|----------|
| `token`    | string  | Token address                                  | no       |
| `date_from`| string  | Start date of the period (YYYY-MM-DD)          | no       |
| `date_to`  | string  | End date of the period (YYYY-MM-DD)            | no       |

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
      "balance": 0,
      "created_dt": "string"
    }
  ]
}
```

### [GET]/v1/top_holders/{holder_id}
Get detailed information about specific holder

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/top_holders/{holder_id}
```

**Request parameters (Path)**

| Parameter  | Type    | Description | Required |
|------------|---------|-------------|----------|
| `holder_id`| integer | Holder ID   | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "address": "string",
  "balance": 0,
  "created_dt": "string"
}
```

### [GET]/v1/top_holders/export
Export list of top holders as CSV

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/top_holders/export
```

**Responses**

`200` **Success**

**Content-Type** `text/csv`

### [GET]/v1/top_holders/tokens
Get list of available tokens

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/top_holders/tokens
```

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
      "name": "string",
      "symbol": "string"
    }
  ]
}
```

**Error codes** see full specification [here](../errors.md) 