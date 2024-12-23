##  Claims

### [POST]/v1/claims/report_wallets
**Create Wallet Claim**

```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Request body JSON**

| Parameter          | Type      | Description | Requried |
|--------------------|-----------|-------------|----------|
| `wallet_address`   | string    |             | yes      |
| `tags`             | integer[] |             | yes      |
| `comment`          | string    |             |          |
| `transaction_link` | string    |             |          |



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

| Parameter    | Type   | Description                     | 
|--------------|--------|---------------------------------|
| `uuid`       | string | t                               | 
| `address`    | string |                                 | 
| `created_dt` | string | '%d/%m/%Y, %H:%M:%S GMT' format | 


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
| Parameter          | Type      | Description | Requried |
|--------------------|-----------|-------------|----------|
| `uuid`   | string    |             | yes      |
| `tags`             | integer[] |             | yes      |
| `comment`          | string    |             |          |
| `transaction_link` | string    |             |          |

 **Responses**

`200` **Successful Response**

**Content-Type** `application/json`

***

### [GET]/v1/claims/my
```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

**Parameters (Query)**

| Parameter   | Type    | Description                                            | Required |
|-------------|---------|--------------------------------------------------------|----------|
| `address`   | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `limit`     | string  | Limit of records to return                             | no       |
| `offset`    | integer | Offset of records to return                            | no       |
| `tags`      | integer | Limit of risk for filter                               | no       |
| `date_from` | string  | Date from for filter                                   | no       |
| `date_to`   | string  | Date to for filter                                     | no       |

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter                                                                                            | Type   | Description                     | 
|------------------------------------------------------------------------------------------------------|--------|---------------------------------|
| `count`                                                                                              |        |                                 |
| `uuid`                                                                                               | string | t                               | 
| `address`                                                                                            | string |                                 | 
| `created_dt`                                                                                         | string | '%d/%m/%Y, %H:%M:%S GMT' format | 
| `transaction_link`                                                                                   |        |                                 |
| `comment`                                                                                            |        |                                 |
| `tags` <br/>`code`: `integer` <br/>`name`: `string`<br/>`type`: `enum`[INFO, RISK]<br/>`description` | string |                                 |


***

### [DELETE]/v1/claims/delete

**Delete Claims**

```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter          | Type      | Description | Requried |
|--------------------|-----------|-------------|----------|
| `string`   | string    |             | yes      |

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

| Parameter              | Type   | Description | 
|------------------------|--------|-------------|
| `code`                 |        |             |
| `name`                 | string |             | 
| `type`enum[INFO, RISK] | string |             | 
| `description`          | string |             |


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
