# Whitelist Management
Management of TON addresses whitelist.

### [GET]/v1/whitelists/whitelist
Get whitelist

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/whitelists/whitelist
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
      "created_dt": "string"
    }
  ]
}
```

### [DELETE]/v1/whitelists/whitelist_entity
Delete address from whitelist

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/whitelists/whitelist_entity
```

**Request parameters (Query)**

| Parameter | Type   | Description                | Required |
|-----------|--------|----------------------------|----------|
| `address` | string | TON wallet address        | yes      |

**Responses**

`204` **Success**

### [GET]/v1/whitelists/whitelist.csv
Download whitelist as CSV

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/whitelists/whitelist.csv
```

**Responses**

`200` **Success**

**Content-Type** `text/csv`
