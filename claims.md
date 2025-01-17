##  Claims

### [POST]/v1/claims/report_wallets
**Create Wallet Claim**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Request body JSON**

| Parameter          | Type      | Description                                                                                          | Required |
|--------------------|-----------|------------------------------------------------------------------------------------------------------|----------|
| `wallet_address`   | string    | TON wallet address, bounced or non-bounced format                                                    | yes      |
| `tags`             | integer[] | array of high-risk tags, [risk category ](../dictionary.md)                                          | yes      |
| `comment`          | string    | comment                                                                                              | no       |
| `transaction_link` | string    | link to transaction in https://tonviewer.com/,https://tonscan.org/,https://tonwhales.com/ru/explorer | no       |



```json
{
  "wallet_address": "string",
  "tags": "integer[]",
  "comment": "string",
  "transaction_link": "string"
}
```

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter    | Type   | Description                                   | 
|--------------|--------|-----------------------------------------------|
| `uuid`       | string | claim id                                      | 
| `address`    | string | TON wallet address                            | 
| `created_dt` | string | creation date '%d/%m/%Y, %H:%M:%S GMT' format | 


**Error codes**

| code | detail                                                           | 
|------|------------------------------------------------------------------|
| 1003 | The address length should be 48 characters long                  |
| 1002 | The limit on the number of available requests has been exhausted | 
| 0    | Too Many Requests                                                |

***

### [PUT]/v1/claims/update_wallet_claim/{uuid}

**Update Wallet Claim**
```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Request body**

| Parameter          | Type      | Description                                                                                          | Required |
|--------------------|-----------|------------------------------------------------------------------------------------------------------|----------|
| `uuid`             | string    | claim id                                                                                             | yes      |
| `tags`             | integer[] | risk category tags                                                                                   | yes      |
| `comment`          | string    | comment                                                                                              | no       |
| `transaction_link` | string    | link to transaction in https://tonviewer.com/,https://tonscan.org/,https://tonwhales.com/ru/explorer | no       |


 **Responses**

`200` **Successful Response**

**Content-Type** `application/json`

***

### [GET]/v1/claims/my
```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```
```
https://my.tonguard.org/api/v1/claims/my?limit=INTEGER&offset=INTEGER&address=ADDRESS&date_from=DATE_FROM&date_to=DATE_TO&tags=INTEGER,INTEGER
```

**Parameters (Query)**

| Parameter   | Type    | Description                                            | Required |
|-------------|---------|--------------------------------------------------------|----------|
| `address`   | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `limit`     | string  | Limit of records to return                             | no       |
| `offset`    | integer | Offset of records to return                            | no       |
| `tags`      | integer | Limit of risk for filter                               | no       |
| `date_from` | string  | Date from for filter, 'YYYY-MM-DD' format              | no       |
| `date_to`   | string  | Date to for filter, 'YYYY-MM-DD' format                | no       |

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter          | Type    | Description                                                                                            | 
|--------------------|---------|--------------------------------------------------------------------------------------------------------|
| `count`            | integer | total claims found                                                                                     |
| `uuid`             | string  | claim id                                                                                               | 
| `address`          | string  | TON wallet address                                                                                     | 
| `created_dt`       | string  | '%d/%m/%Y, %H:%M:%S GMT' format                                                                        | 
| `transaction_link` | string  | link to transaction in https://tonviewer.com/,https://tonscan.org/,https://tonwhales.com/ru/explorer   |
| `comment`          | string  | comment                                                                                                |
| `tags`             | string  | `code`: `integer` <br/>`name`: `string`<br/>`type`: `enum`[INFO, RISK]<br/>`description` : description |


***

### [DELETE]/v1/claims/delete

**Delete Claims**

```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter | Type   | Description | Required |
|-----------|--------|-------------|----------|
| `string`  | string | claim uuid  | yes      |

 **Responses**

`200` **Successful Response**

**Content-Type** `application/json`

***

### [GET]/v1/claims/wallets_tags
 
**Dictionary Wallets Tags**

```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```
**Content-Type** `application/json`

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter     | Type                    | Description       | 
|---------------|-------------------------|-------------------|
| `code`        | integer                 | tag's id          |
| `name`        | string                  | tag's name        | 
| `type`        | string enum[INFO, RISK] | tag's type        | 
| `description` | string                  | tag's description |


Risk category dictionary - [Dictionary](dictionary)

***

### [GET]/v1/claims/claim_history.csv
 
**Return claims history in a csv file**

```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

**Responses**

`200` **Claim history successfully retrieved**


```json
{
  "title": "Response Download"
}
```

***
