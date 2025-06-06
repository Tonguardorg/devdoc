## Claims

The Claim tool enables users to classify addresses on the TON blockchain:
* data labeling for machine learning algorithms;
* implementation of a specialized tagging system for the classification of different types of illegal activity;
* utilization as a blacklisting tool;
* manual marking of custodial addresses.

### [POST]/v1/claims/report_wallets
Method is used to **Create wallet claim**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Request body JSON**

| Parameter          | Type      | Description                                                                                          | Required |
|--------------------|-----------|------------------------------------------------------------------------------------------------------|----------|
| `wallet_address`   | string    | TON wallet address, bounced or non-bounced format                                                    | yes      |
| `tags`             | integer[] | array of high category tags, [risk category](../dictionary.md)                                      | yes      |
| `comment`          | string    | comment                                                                                              | no       |
| `transaction_link` | string    | link to transaction in https://tonviewer.com/,https://tonscan.org/,https://tonwhales.com/ru/explorer | no       |

```json
{
  "wallet_address": "string",
  "tags": [tagID1,tagID2],
  "comment": "string",
  "transaction_link": "string"
}
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "uuid": "string",
  "address": "string",
  "created_dt": "string"
}
```

### [PUT]/v1/claims/update_wallet_claim/{uuid}
Method is used to **update wallet claim**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Request body**

| Parameter          | Type      | Description                                                                                                    | Required |
|--------------------|-----------|----------------------------------------------------------------------------------------------------------------|----------|
| `tags`             | integer[] | array of risk category tags, [risk category](../dictionary.md)                                                | yes      |
| `comment`          | string    | fill with comment                                                                                              | no       |
| `transaction_link` | string    | fill with link to transaction in https://tonviewer.com/,https://tonscan.org/,https://tonwhales.com/ru/explorer | no       |

**Responses**

`204` **Success**

### [GET]/v1/claims/my
Method is used to obtain **list of claims**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Example**
```
https://api.tonguard.org/v1/claims/my?limit=INTEGER&offset=INTEGER&address=ADDRESS&date_from=DATE_FROM&date_to=DATE_TO&tags=INTEGER,INTEGER
```

**Parameters (Query)**

| Parameter   | Type    | Description                                            | Required |
|-------------|---------|--------------------------------------------------------|----------|
| `address`   | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `limit`     | string  | limit of records to return                             | no       |
| `offset`    | integer | offset of records to return                            | no       |
| `tags`      | integer | risk categories for filter                             | no       |
| `date_from` | string  | date from for filter, 'YYYY-MM-DD' format              | no       |
| `date_to`   | string  | date to for filter, 'YYYY-MM-DD' format                | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "count": 0,
  "results": [
    {
      "uuid": "string",
      "address": "string",
      "created_dt": "string",
      "transaction_link": "string",
      "comment": "string",
      "tags": [
        {
          "code": 0,
          "name": "string",
          "type": "INFO",
          "description": "string"
        }
      ]
    }
  ]
}
```

### [DELETE]/v1/claims/delete
Method is used to **delete claims**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter | Type   | Description | Required |
|-----------|--------|-------------|----------|
| `uuid`    | string | claim uuid  | yes      |

**Responses**

`204` **Success**

### [GET]/v1/claims/wallets_tags
**Dictionary Wallets Tags**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
[
  {
    "code": 0,
    "name": "string",
    "type": "INFO",
    "description": "string"
  }
]
```

Risk category dictionary - [Dictionary](dictionary)

### [GET]/v1/claims/claim_history.csv
Method **returns claims history in a csv file**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "title": "Response Download"
}
```

**Error codes** see full specification [here](../errors.md)
