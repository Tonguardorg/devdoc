## Reports

Returns address risk score, risk level and query related info, including the USDT information. 

Each request reduces the remaining number of user's requests.

The platform's algorithms will analyze the address for spam, scams, and gambling-related transactions. 
The total number of transactions between the analyzed address and its immediate and distant counterparts 
in the TON blockchain will also be considered. Based on these factors, the algorithm will calculate a probability
that the address is dishonest, ranging from 0 to 100.

Probabilities are converted into risk levels, which can take one of four values: 
* lowest risk (0 - 12),
* low risk (12 - 46), 
* medium risk (46 – 82), 
* high risk (82 – 100), 
* wallets with no clear activity may be classified as Unknown

`User may access the risk scoring only if he has at least one available request remaining. 
Once all requests are exhausted, access to the visualizer will be temporarily restricted until additional requests are replenished.`

### [GET]/v2/reports/wallet_risk_score
**Risk score, risk level and query related info**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Example**
```
https://api.tonguard.org/v2/reports/wallet_risk_score?source=api&address=ADDRESS
```

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter | Type   | Description                                            | Required             |
|-----------|--------|--------------------------------------------------------|----------------------|
| `address` | string | TON wallet address in any base64 form (urlsafe or not) | yes                  |
| `source`  | string | source of the request<br/>options: api, manual         | no <br/>default: api |

**Responses**

| Parameter                                   | Type      | Description                                                                                                                                                                                                              | 
|---------------------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uuid`                                      | string    | universally unique identifier for risk scoring, use it as report id                                                                                                                                                      |
| `version`                                   | string    | api version                                                                                                                                                                                                              |
| `whitelist`                                 | boolean   | an indication that the address is on the whitelist, if address is included in the private whitelist, it's Risk level is automatically lowered to a low level                                                             |
| `blacklist`                                 | boolean   | an indication that the address is on the blacklist                                                                                                                                                                       |
| `address`                                   | string    | TON wallet address bounceable format                                                                                                                                                                                     |
| `address_raw`                               | string    | TON wallet address raw format, default: unknown                                                                                                                                                                          |
| `address_non_bounceable`                    | string    | TON wallet address non-bounceable format, default: unknown                                                                                                                                                               |
| `address_type`                              | string    | smart contract type <br/>default: unknown                                                                                                                                                                                |
| `owner`                                     | string    | owner's public name <br/>default: unknown                                                                                                                                                                                |
| `risk_score`                                | integer   | risk score level (0-100)                                                                                                                                                                                                 |
| `fraud_level`                               | enum      | risk levelss: <br/>* lowest risk (0 - 12),<br/>* low risk (12 - 46), <br/>* medium risk (46 – 82), <br/>* high risk (82 – 100), <br/> * wallets with no clear activity may beclassified as Unknown. <br/>Default: lowest |                    
| `risk_category`                             | string [] | `code`: `integer` <br/>`name`: `string`<br/>`type`: `enum`[INFO, RISK]<br/>`description` : description <br/>[risk category ](../dictionary.md)                                                                           |
| `info_category`                             | string [] | `code`: `integer` <br/>`name`: `string`<br/>`type`: `enum`[INFO, RISK]<br/>`description` : description <br/>[info category ](../dictionary.md)                                                                           |
| `total_days`                                | integer   | the number of days the address has existed since the first transaction with the analyzed address                                                                                                                         |
| `first_transaction_time`                    | string    | date of the first analyzed transaction                                                                                                                                                                                   |
| `last_transaction_time`                     | string    | date of the last analyzed transaction                                                                                                                                                                                    |
| `total_balance`                             | number    | current balance value of the analyzed address                                                                                                                                                                            |
| `total_transactions_amount`                 | number    | current turnover value for the analyzed address                                                                                                                                                                          |
| `total_transactions_count`                  | integer   | total number of transactions made with the analyzed address                                                                                                                                                              |
| `total_counterparts_count`                  | integer   | total number of addresses that have ever interacted with the analyzed address                                                                                                                                            |
| `total_sent_transactions_amount`            | number    | amount of cryptocurrency sent by the analyzed address                                                                                                                                                                    |
| `total_sent_transactions_count`             | integer   | total number of transactions sent by the analyzed address                                                                                                                                                                |
| `total_sent_counterparts_count`             | integer   | total number of transactions  that have ever interacted by the analyzed address (sending transactions)                                                                                                                   |
| `total_received_transactions_amount`        | number    | amount of cryptocurrency received by the analyzed address                                                                                                                                                                |
| `total_received_transactions_count`         | integer   | number of cryptocurrency transactions received by the analyzed address                                                                                                                                                   |
| `total_received_counterparts_count`         | integer   | number of cryptocurrency transactions that have ever interacted by the analyzed address (receiving transactions)                                                                                                         |
| `gambling_message_count`                    | integer   | gambling transactions count for the analyzed address                                                                                                                                                                     |
| `spam_message_count`                        | integer   | spam transactions count for the analyzed address                                                                                                                                                                         |
| `scam_message_count`                        | integer   | scam transactions count for the analyzed address                                                                                                                                                                         |
| `bridge_wallet_status`                      | string[]  | this field is not currently in use                                                                                                                                                                                       |
| `exchange_wallet_status`                    | string[]  | exchanges info                                                                                                                                                                                                           |
| `stacking_wallet_status`                    | string[]  | this field is not currently in use                                                                                                                                                                                       |
| `miner_wallet_status`                       | string[]  | this field is not currently in use                                                                                                                                                                                       |
| `nft_wallet_status`                         | string[]  | this field is not currently in use                                                                                                                                                                                       |
| `total_jetton_transactions_amount`          | number    | USDT jettons transactions balance recalculated to USD at the current rate                                                                                                                                                |
| `jetton_balance`                            | number    | current balance and turnover of USDT jettons for the analyzed address                                                                                                                                                    |
| `total_balance_in_usd`                      | number    | USDT jettons balance recalculated to USD **at the current rate**                                                                                                                                                         |
| `total_transactions_amount_in_usd`          | number    | USDT jettons transactions balance recalculated to USD **at the current rate**                                                                                                                                            |
| `total_received_transactions_amount_in_usd` | number    | USDT jettons received balance recalculated to USD **at the current rate**                                                                                                                                                |
| `total_sent_transactions_amount_in_usd`     | number    | USDT jettons sent balance recalculated to USD **at the current rate**                                                                                                                                                    |
| `risky_connections`                         | array     | Array of risky connections with other addresses. Each connection contains:<br/>- `last_transaction_time`: string<br/>- `wallet_address`: string<br/>- `neighbor_wallet_address`: string<br/>- `total_income`: integer<br/>- `total_outcome`: integer<br/>- `risk_score`: integer<br/>- `fraud_level`: string<br/>- `total_transactions_count`: integer<br/>- `total_transactions_amount`: string<br/>- `tags`: array |
| `source_of_funds`                           | array     | Array of fund sources. Each source contains:<br/>- `category`: string<br/>- `percentage`: number<br/>- `total_input_ton`: number<br/>- `total_input_usdt`: number |
| `jettons_info`                              | array     | Array of jetton information. Each jetton contains:<br/>- `jetton_address`: string<br/>- `name`: string<br/>- `symbol`: string<br/>- `description`: string<br/>- `balance`: number<br/>- `balance_in_ton`: number<br/>- `balance_in_usd`: number<br/>- `turnover`: number<br/>- `turnover_in_ton`: number<br/>- `turnover_in_usd`: number<br/>- `transactions_count`: integer<br/>- `counterparts_count`: integer<br/>- `received_counterparts_count`: integer<br/>- `sent_counterparts_count`: integer<br/>- `received_transactions_count`: integer<br/>- `sent_transactions_count`: integer<br/>- `first_transaction_time`: string<br/>- `last_transaction_time`: string |



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
  "stacking_wallet_status": [],
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
  "source_of_funds": [],
  "jettons_info": []
}
```

### [POST]/v2/reports/bulk_wallet_fraud_score

Returns address risk score, risk level and query related info for multiple addresses (bulk request). Maximum 100 address in one request. 

**Content-Type** `application/json`

**Example**
```
POST https://api.tonguard.org/v2/reports/bulk_wallet_fraud_score?source=api
Content-Type: application/json
[
  "EQAU2bNfz8E-YRLZozcrLVr-JeUqZmdQWoUt01IsYaykGlWS",
  "EQA3_TOT0UZzI43yBSfbv1KSnT9qutqbrOyGlIy4mubyRkX7"
]
```

**Parameters (Query)**

| Parameter | Type   | Description              | Required |
|-----------|--------|--------------------------|----------|
| `source`  | string | api/manual, default: api | no       |

**Request body**

| Parameter | Type   | Description                                            | Required |
|-----------|--------|--------------------------------------------------------|----------|
|           | string | TON wallet address in any base64 form (urlsafe or not) | yes      |

**Responses**

| Parameter | Type   | Description                                            |
|-----------|--------|--------------------------------------------------------|
| `count`   | integer| Number of addresses processed                          |
| `data`    | array  | Array of risk scores for each address in bulk request  |

`200` **Success**

**Content-Type** `application/json`

```json
{
  "count": 2,
  "data": [ ... ]
}
```

### [GET]/v1/reports/wallet_risk_score
**Get risk score, risk level and query related info**

**Content-Type** `application/json`

**Example**
```
GET https://api.tonguard.org/v1/reports/wallet_risk_score?source=api&address=ADDRESS
Authorization: Bearer <jwt token>
```

**Parameters (Query)**

| Parameter | Type   | Description                                            | Required             |
|-----------|--------|--------------------------------------------------------|----------------------|
| `address` | string | TON wallet address in any base64 form (urlsafe or not) | yes                  |
| `source`  | string | source of the request<br/>options: api, manual         | no <br/>default: api |

**Responses**

`200` **Success**

**Content-Type** `application/json`



### [GET]/v1/reports/wallet_fraud_score
**Get fraud score for a wallet**

**Content-Type** `application/json`

**Example**
```
GET https://api.tonguard.org/v1/reports/wallet_fraud_score?address=ADDRESS
Authorization: Bearer <jwt token>
```

**Parameters (Query)**

| Parameter | Type   | Description                                            | Required |
|-----------|--------|--------------------------------------------------------|----------|
| `address` | string | TON wallet address in any base64 form (urlsafe or not) | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "uuid": "string",
  "version": "2.0.0",
  "address": "string",
  ...
}
```

### [POST]/v1/reports/wallet_fraud_score_bulk
**Get fraud scores for multiple wallets in bulk**

**Content-Type** `application/json`

**Example**
```
POST https://api.tonguard.org/v1/reports/wallet_fraud_score_bulk
Authorization: Bearer <jwt token>
Content-Type: application/json
{
  "addresses": ["ADDRESS1", "ADDRESS2"]
}
```

**Request Body**

| Parameter   | Type     | Description                                      | Required |
|-------------|----------|--------------------------------------------------|----------|
| `addresses` | string[] | Array of TON wallet addresses in any base64 form  | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "results": [ ... ]
}
```

### [GET]/v1/reports/risk_scoring_history
**Returns risk scoring history for a specific user and address**

**Content-Type** `application/json`

**Example**
```
GET https://api.tonguard.org/v1/reports/risk_scoring_history?address=ADDRESS&limit=10
Authorization: Bearer <jwt token>
```

**Parameters (Query)**

| Parameter       | Type    | Description                                            | Required |
|-----------------|---------|--------------------------------------------------------|----------|
| `address`       | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `limit`         | string  | limit of records to return                             | no       |
| `offset`        | integer | offset of records to return                            | no       |
| `risk_limit`    | integer | limit of risk for filter                               | no       |
| `risk_offset`   | integer | offset of risk for filter                              | no       |
| `info_category` | string  | list of info tags for filter                           | no       |
| `risk_category` | string  | list of risk tags for filter                           | no       |
| `risk`          | string  | list of risk levels for filter                         | no       |
| `source`        | string  | source of the request                                  | no       |
| `date_from`     | string  | date from for filter, "DD.MM.YYYY" format              | no       |
| `date_to`       | string  | date to for filter, "DD.MM.YYYY" format                | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "results": [ ... ]
}
```

### [GET]/v1/reports/risk_history.csv
**Returns risk scoring history in a csv file**

**Content-Type** `application/json`

**Example**
```
GET https://api.tonguard.org/v1/reports/risk_history.csv?address=ADDRESS&date_from=2024-01-01&date_to=2024-01-31
Authorization: Bearer <jwt token>
```

**Parameters (Query)**

| Parameter       | Type    | Description                                            | Required |
|-----------------|---------|--------------------------------------------------------|----------|
| `address`       | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `risk_limit`    | integer | send risk level to filter                              | no       |
| `risk_offset `  | integer | offset of risk for filter                              | no       |
| `info_category` | string  | list of info tags for filter.                          | no       |
| `risk_category` | string  | list of risk tags for filter.                          | no       |
| `risk`          | string  | list of risk levels for filter.                        | no       |
| `source`        | string  | source of the request                                  | no       |
| `date_from`     | string  | date from for filter, "DD.MM.YYYY" format              | no       |
| `date_to`       | string  | date to for filter, "DD.MM.YYYY" format                | no       |

**Responses**

`200` **Risk scoring history successfully retrieved**

### [GET]/v1/reports/risk_scoring_report
**Return risk scoring report for a specific uuid**

**Content-Type** `application/json`

**Example**
```
GET https://api.tonguard.org/v1/reports/risk_scoring_report?uuid=UUID
Authorization: Bearer <jwt token>
```

**Parameters (Query)**

| Parameter | Type   | Description               | Required |
|-----------|--------|---------------------------|----------|
| `uuid`    | string | id of risk scoring report | yes      |

**Responses**

`200` **Success**

### [GET]/v1/reports/risk_scoring_report_{uuid}.pdf
**Download risk scoring report as a pdf-file**

**Content-Type** `application/json`

**Example**
```
GET https://api.tonguard.org/v1/reports/risk_scoring_report_UUID.pdf?uuid=UUID
Authorization: Bearer <jwt token>
```

**Parameters (Query)**

| Parameter | Type   | Description               | Required |
|-----------|--------|---------------------------|----------|
| `uuid`    | string | id of risk scoring report | yes      |

**Responses**

`200` **Data successfully downloaded**
