##  Reports

Returns address risk score, risk level and query related info,including the usdt information. Each query exceeds remaining number of queries for the user.

### [GET]/v2/reports/wallet_risk_score

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter  | Type   | Description                                            | Requried |
|------------|--------|--------------------------------------------------------|----------|
| `address` | string | TON wallet address in any base64 form (urlsafe or not) | yes      |
| `source` | string | source of the request<br/>api, manual                  | no <br/>default: api|

**Headers**
```
// JWT token of authorised user
token: string
```

```
https://api-amlplatform-1733986985.dev-rtbst.com/v1/reports/wallet_risk_score?source=api&address=EQCzFTXpNNsFu8IgJnRnkDyBCL2ry8KgZYiDi3Jt31ie8EIQ
```

**Responses**

`200` **Risk score, risk level and query related info**

| Parameter                                   | Type   | Description                   | 
|---------------------------------------------|--------|-------------------------------|
| `uuid`                                      | string| universally unique identifier |
| `version`                                   | string| api's version                 |
| `whitelist`                                 | boolean|                               |
| `blacklist`                                 | boolean|                               |
| `address`                                   | string| TON wallet address            |
| `address_raw`                               | string | default: unknown              ||
| `address_non_bounceable`                    | string| default: unknown              |
| `address_type`                              | string | default: unknown              |
| `owner`                                     | string| default: unknown              |
| `risk_score`                                | integer|                               |
| `fraud_level`                               | enum[high, medium, low, lowest, unknown] | default: lowest               |                    
| `risk_category`                             | string[]|                               |
| `total_days`                                | integer|                               |
| `first_transaction_time`                    | string|                               |
| `last_transaction_time`                     | string|                               |
| `total_balance`                             | number|                               |
| `total_transactions_amount`                 | number|                               |
| `total_transactions_count`                  | integer|                               |
| `total_counterparts_count`                  | integer|                               |
| `total_sent_transactions_amount`            | number|                               |
| `total_sent_transactions_count`             | integer|                               |
| `total_sent_counterparts_count`             | integer|                               |
| `total_received_transactions_amount`        | number|                               |
| `total_received_transactions_count`         | integer|                               |
| `total_received_counterparts_count`         | integer|                               |
| `gambling_message_count`                    | integer|                               |
| `spam_message_count`                        | integer|                               |
| `scam_message_count`                        | integer|                               |
| `bridge_wallet_status`                      | string[]|                               |
| `exchange_wallet_status`                    | string[]|                               |
| `stacking_wallet_status`                    | string[]|                               |
| `miner_wallet_status`                       | string[]|                               |
| `nft_wallet_status`                         | string[]|                               |
| `total_usdt_transactions_amount`            | number|                               |
| `usdt_balance`                              | number|                               |
| `total_balance_in_usd`                      | number|                               |
| `total_transactions_amount_in_usd`          | number|                               |
| `total_received_transactions_amount_in_usd` | number|                               |
| `total_sent_transactions_amount_in_usd`     | number|                               |



**Content-Type** `application/json`

```json
{
  "uuid": "43380912-ce1b-4357-ba38-984b847e8e85",
  "version": "2.0.0",
  "whitelist": false,
  "blacklist": false,
  "address": "EQBhhJXZI8NVeJSTXhOQPbheJknVRaCqOQu9gHroK0Uu1Knw",
  "address_type": "highload_wallet",
  "address_raw": "0:618495d923c3557894935e13903db85e2649d545a0aa390bbd807ae82b452ed4",
  "address_non_bounceable": "UQBhhJXZI8NVeJSTXhOQPbheJknVRaCqOQu9gHroK0Uu1PQ1",
  "owner": "unknown",
  "fraud_level": "high",
  "risk_score": 81,
  "risk_category": [
    {
      "code": 20,
      "name": "Spam",
      "type": "RISK",
      "description": "Related to spammers"
    }
  ],
  "info_category": [],
  "risky_connections": [
    {
      "last_transaction_time": "2022-02-02T11:00:40",
      "wallet_address": "0:618495d923c3557894935e13903db85e2649d545a0aa390bbd807ae82b452ed4",
      "neighbor_wallet_address": "EQCi3YNrsfLbf29nErUfdbFViDFqr/Cpvy68THMtWZiIr31u",
      "total_income": null,
      "total_outcome": null,
      "risk_score": 81,
      "fraud_level": "high",
      "total_transactions_count": 1,
      "total_transactions_amount": "1.0000000000000005e-09",
      "tags": [
        {
          "code": 20,
          "name": "Spam",
          "type": "RISK",
          "description": "Related to spammers"
        }
      ]
    }
  ],
  "source_of_funds": [
    {
      "category": "Custodial Exchange",
      "percentage": 25.5,
      "total_input_ton": 1000,
      "total_input_usdt": 5000
    },
    {
      "category": "Decentralized Exchange",
      "percentage": 14.5,
      "total_input_ton": 600.15,
      "total_input_usdt": 3000
    },
    {
      "category": "Bridge",
      "percentage": 10,
      "total_input_ton": 400,
      "total_input_usdt": 2000
    },
    {
      "category": "Financial Services",
      "percentage": 20,
      "total_input_ton": 800.15,
      "total_input_usdt": 4000
    },
    {
      "category": "Illegal addresses",
      "percentage": 5,
      "total_input_ton": 200,
      "total_input_usdt": 1000
    },
    {
      "category": "Unknown",
      "percentage": 25,
      "total_input_ton": 1000,
      "total_input_usdt": 5000
    }
  ],
  "total_days": 373,
  "first_transaction_time": "2022-01-20T10:18:16",
  "last_transaction_time": "2023-01-28T12:38:29",
  "total_balance": 34.560512763,
  "total_transactions_amount": 239.0957315920001,
  "total_transactions_count": 47079,
  "total_counterparts_count": 46813,
  "total_sent_transactions_amount": 0.00004704900000000002,
  "total_sent_transactions_count": 47049,
  "total_sent_counterparts_count": 46811,
  "total_received_transactions_amount": 239.09568454300012,
  "total_received_transactions_count": 30,
  "total_received_counterparts_count": 16,
  "gambling_message_count": 0,
  "spam_message_count": 47049,
  "scam_message_count": 0,
  "nft_wallet_status": [],
  "miner_wallet_status": [],
  "bridge_wallet_status": [],
  "exchange_wallet_status": [
    "Linked FTX",
    "Linked OKX",
    "Linked EXMO deposit"
  ],
  "stacking_wallet_status": []
}
```

**Errors**

```json
{
  "code": "integer",
  "detail": "string"
}
```

`400` **Bad Request** 

**Content-Type** `application/json`

```json
{
  "code": 1003,
  "detail": "The address length should be 48 characters long"
}
```

`401` **Unauthorized**

`application/json`

```json
{
  "code": 1005,
  "detail": "Invalid user credentials."
}
```

`402` **Payment Required**

`application/json`

```json
{
  "code": 1002,
  "detail": "The limit on the number of available requests has been exhausted."
}
```

`403` **Forbidden**

`application/json`

```json
{
  "code": "integer",
  "detail": "string"
}
```

`422` **Validation Error**

`application/json`

```json
{
  "detail": {
    "loc": "Partial(string) & Partial(integer)[]",
    "msg": "string",
    "type": "string"
  }
}
```

`429` **Too Many Requests**

`application/json`

```json
{
  "code": 0,
  "detail":"Too Many Requests"
}
```

***

### [GET]/v1/reports/risk_scoring_history

Returns risk scoring history for a specific user and address.

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter  | Type   | Description                                            | Requried |
|------------|--------|--------------------------------------------------------|----------|
| `address` | string | TON wallet address in any base64 form (urlsafe or not) | yes      |
| `source` | string | source of the request<br/>api, manual                  | no <br/>default: api|

**Headers**
```
// JWT token of authorised user
token: string
```

```
https://api-amlplatform-1733986985.dev-rtbst.com/v1/reports/wallet_risk_score?source=api&address=EQCzFTXpNNsFu8IgJnRnkDyBCL2ry8KgZYiDi3Jt31ie8EIQ
```

**Responses**

#### Parameters(Query)
| Parameter  | Type   | Description | Requried |
|------------|--------|-------------|----------|
| `username` | string | email       | yes      |
| `password` | string | password    | yes      |
```ts
// TON wallet address in any base64 form (urlsafe or not).
address: string
```

```ts
// Limit of records to return.
limit: integer //default: 10
```

```ts
// Offset of records to return.
offset: integer
```

```ts
// Limit of risk for filter.
risk_limit: integer
```

```ts
// Offset of risk for filter.
risk_offset: integer
```

```ts
// List of info tags for filter.
info_category: string
```

```ts
// List of risk tags for filter.
risk_category: string
```

```ts
// List of risk levels for filter.
risk: string
```

```ts
// Source of the request
source: string
```

```ts
// Date from for filter
date_from: string
```

```ts
// Date to for filter
date_to: string
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Risk scoring history successfully retrieved.

`application/json`

```ts
{
  history: {
    version: string
    uuid: string
    created_dt: string
    endpoint_used: string
    source: string //default: api
    whitelist: boolean
    blacklist: boolean
    address: string
    address_type: string //default: unknown
    address_raw: string
    address_non_bounceable: string
    owner: string //default: unknown
    fraud_level: string
    risk_score: integer
    info_category: integer[]
    risk_category: integer[]
    risky_connections: {
    }[]
    source_of_funds: {
    }[]
    first_transaction_time: string
    last_transaction_time: string
    total_balance: number
    total_balance_in_usd: number
    total_days: number
    total_transactions_amount: number
    total_transactions_amount_in_usd: number
    total_sent_transactions_amount: number
    total_sent_transactions_amount_in_usd: number
    total_received_transactions_amount: number
    total_received_transactions_amount_in_usd: number
    total_counterparts_count: integer
    total_sent_counterparts_count: integer
    total_received_counterparts_count: integer
    total_transactions_count: integer
    total_sent_transactions_count: integer
    total_received_transactions_count: integer
    bridge_wallet_status: string[]
    exchange_wallet_status: string[]
    stacking_wallet_status: string[]
    miner_wallet_status: string[]
    nft_wallet_status: string[]
    gambling_message_count: integer
    spam_message_count: integer
    scam_message_count: integer
    usdt_balance: number
    total_usdt_transactions_amount: number
  }[]
  count: integer
}
```

- 400 Bad Request

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 404 Not Found

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***
