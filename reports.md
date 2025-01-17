##  Reports

Returns address risk score, risk level and query related info,including the usdt information. 
Each request reduces the remaining number of user's requests.

### [GET]/v2/reports/wallet_risk_score
**Risk score, risk level and query related info**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
**Example**
```
https://api.tonguard.org/v2/reports/wallet_risk_score?source=api&address=ADRESS
```

**Content-Type** `application/json`

**Parameters (Query)**

| Parameter | Type   | Description                                            | Required             |
|-----------|--------|--------------------------------------------------------|----------------------|
| `address` | string | TON wallet address in any base64 form (urlsafe or not) | yes                  |
| `source`  | string | source of the request<br/>options: api, manual         | no <br/>default: api |


**Responses**

| Parameter                                   | Type      | Description                                                                                                                                                                                                   | 
|---------------------------------------------|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uuid`                                      | string    | universally unique identifier for risk scoring, use it as report id                                                                                                                                           |
| `version`                                   | string    | api version                                                                                                                                                                                                   |
| `whitelist`                                 | boolean   | an indication that the address is on the whitelist, if address is included in the private whitelist, it's Risk level is automatically lowered to a low level                                                  |
| `blacklist`                                 | boolean   | an indication that the address is on the blacklist                                                                                                                                                            |
| `address`                                   | string    | TON wallet address bounceable format                                                                                                                                                                          |
| `address_raw`                               | string    | TON wallet address raw format, default: unknown                                                                                                                                                               |
| `address_non_bounceable`                    | string    | TON wallet address non-bounceable format, default: unknown                                                                                                                                                    |
| `address_type`                              | string    | default: unknown                                                                                                                                                                                              |
| `owner`                                     | string    | default: unknown                                                                                                                                                                                              |
| `risk_score`                                | integer   | risk score level                                                                                                                                                                                              |
| `fraud_level`                               | enum      | risk levelss: <br/>lowest risk (0 - 12),<br/>low risk (12 - 46), <br/>medium risk (46 – 82), <br/>high risk (82 – 100). <br/>Wallets with no clear activity may beclassified as Unknown. <br/>Default: lowest |                    
| `risk_category`                             | string [] | see dictionary [risk category ](../dictionary.md), <br/> structure <br/>{ <br/>"code": 20, <br/>"name": "Spam", <br/>"type": "RISK", <br/>"description": "Related to spammers" <br/>}                         |
| `total_days`                                | integer   | the number of days the address has existed since the first transaction with the analyzed address                                                                                                              |
| `first_transaction_time`                    | string    | date of the first analyzed transaction                                                                                                                                                                        |
| `last_transaction_time`                     | string    | date of the last analyzed transaction                                                                                                                                                                         |
| `total_balance`                             | number    | current balance value of the analyzed address                                                                                                                                                                 |
| `total_transactions_amount`                 | number    | current turnover value for the analyzed address                                                                                                                                                               |
| `total_transactions_count`                  | integer   | total number of transactions made with the analyzed address                                                                                                                                                   |
| `total_counterparts_count`                  | integer   | total number of addresses that have ever interacted with the analyzed address                                                                                                                                 |
| `total_sent_transactions_amount`            | number    | amount of cryptocurrency sent by the analyzed address                                                                                                                                                         |
| `total_sent_transactions_count`             | integer   | total number of addresses that sent cryptocurrency to the analyzed address                                                                                                                                    |
| `total_sent_counterparts_count`             | integer   | total number of addresses that received cryptocurrency from the analyzed address                                                                                                                              |
| `total_received_transactions_amount`        | number    |                                                                                                                                                                                                               |
| `total_received_transactions_count`         | integer   | amount of cryptocurrency received by the analyzed address                                                                                                                                                     |
| `total_received_counterparts_count`         | integer   |                                                                                                                                                                                                               |
| `gambling_message_count`                    | integer   |                                                                                                                                                                                                               |
| `spam_message_count`                        | integer   |                                                                                                                                                                                                               |
| `scam_message_count`                        | integer   |                                                                                                                                                                                                               |
| `bridge_wallet_status`                      | string[]  |                                                                                                                                                                                                               |
| `exchange_wallet_status`                    | string[]  |                                                                                                                                                                                                               |
| `stacking_wallet_status`                    | string[]  |                                                                                                                                                                                                               |
| `miner_wallet_status`                       | string[]  |                                                                                                                                                                                                               |
| `nft_wallet_status`                         | string[]  |                                                                                                                                                                                                               |
| `total_usdt_transactions_amount`            | number    |                                                                                                                                                                                                               |
| `usdt_balance`                              | number    | current balance and turnover of USDT jettons for the analyzed address                                                                                                                                         |
| `total_balance_in_usd`                      | number    |                                                                                                                                                                                                               |
| `total_transactions_amount_in_usd`          | number    |                                                                                                                                                                                                               |
| `total_received_transactions_amount_in_usd` | number    |                                                                                                                                                                                                               |
| `total_sent_transactions_amount_in_usd`     | number    |                                                                                                                                                                                                               |



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

**Content-Type** `application/json`

```json
{
  "code": "integer",
  "detail": "string"
}
```

| code | detail                                                           | 
|------|------------------------------------------------------------------|
| 1003 | The address length should be 48 characters long                  |
| 1002 | The limit on the number of available requests has been exhausted | 
| 0    | Too Many Requests                                                |


***


### [GET]/v1/reports/risk_scoring_history

**Returns risk scoring history for a specific user and address**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
```
https://api.tonguard.org/v1/reports/risk_scoring_history?address=ADDRESS&limit=INTEGER&offset=INTEGER
&risk_limit=INTEGER&risk_offset=INTEGER&info_category=INTEGER&risk_category=INTEGER&risk=high%2Cmedium&source=api&date_from=01.01.2024&date_to=31.12.2024
```


**Content-Type** `application/json`

**Parameters (Query)**

| Parameter       | Type    | Description                                            | Required |
|-----------------|---------|--------------------------------------------------------|----------|
| `address`       | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `limit`         | string  | Limit of records to return                             | no       |
| `offset`        | integer | Offset of records to return                            | no       |
| `risk_limit`    | integer | Limit of risk for filter                               | no       |
| `risk_offset`   | integer | Offset of risk for filter                              | no       |
| `info_category` | string  | List of info tags for filter                           | no       |
| `risk_category` | string  | List of risk tags for filter                           | no       |
| `risk`          | string  | List of risk levels for filter                         | no       |
| `source`        | string  | Source of the request                                  | no       |
| `date_from`     | string  | Date from for filter                                   | no       |
| `date_to`       | string  | Date to for filter                                     | no       |





**Responses**

`200` **Risk scoring history successfully retrieved**

**Content-Type** `application/json`

| Parameter                                   | Type                                     | Description                                                                                                                                                  | 
|---------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uuid`                                      | string                                   | universally unique identifier                                                                                                                                |
| `version`                                   | string                                   | api version                                                                                                                                                  |
| `created_dt`                                | string                                   | date when the report was generated                                                                                                                           |
| `endpoint_used`                             | string                                   | endpoint_used                                                                                                                                                |
| `source`                                    | string                                   | default: api                                                                                                                                                 |
| `whitelist`                                 | boolean                                  | an indication that the address is on the whitelist, if address is included in the private whitelist, it's Risk level is automatically lowered to a low level |
| `blacklist`                                 | boolean                                  |                                                                                                                                                              |
| `address`                                   | string                                   | TON wallet address                                                                                                                                           |
| `address_raw`                               | string                                   | default: unknown                                                                                                                                             |
| `address_non_bounceable`                    | string                                   | default: unknown                                                                                                                                             |
| `address_type`                              | string                                   | default: unknown                                                                                                                                             |
| `owner`                                     | string                                   | default: unknown                                                                                                                                             |
| `risk_score`                                | integer                                  |                                                                                                                                                              |
| `risky_connections: {}`                     | []                                       |                                                                                                                                                              |
| `info_category`                             | integer[]                                |                                                                                                                                                              |
| `fraud_level`                               | enum[high, medium, low, lowest, unknown] | default: lowest                                                                                                                                              |                    
| `risk_category`                             | string[]                                 |                                                                                                                                                              |
| `total_days`                                | integer                                  |                                                                                                                                                              |
| `first_transaction_time`                    | string                                   |                                                                                                                                                              |
| `last_transaction_time`                     | string                                   |                                                                                                                                                              |
| `total_balance`                             | number                                   |                                                                                                                                                              |
| `total_transactions_amount`                 | number                                   |                                                                                                                                                              |
| `total_transactions_count`                  | integer                                  |                                                                                                                                                              |
| `total_counterparts_count`                  | integer                                  |                                                                                                                                                              |
| `total_sent_transactions_amount`            | number                                   |                                                                                                                                                              |
| `total_sent_transactions_count`             | integer                                  |                                                                                                                                                              |
| `total_sent_counterparts_count`             | integer                                  |                                                                                                                                                              |
| `total_received_transactions_amount`        | number                                   |                                                                                                                                                              |
| `total_received_transactions_count`         | integer                                  |                                                                                                                                                              |
| `total_received_counterparts_count`         | integer                                  |                                                                                                                                                              |
| `gambling_message_count`                    | integer                                  |                                                                                                                                                              |
| `spam_message_count`                        | integer                                  |                                                                                                                                                              |
| `scam_message_count`                        | integer                                  |                                                                                                                                                              |
| `bridge_wallet_status`                      | string[]                                 |                                                                                                                                                              |
| `exchange_wallet_status`                    | string[]                                 |                                                                                                                                                              |
| `stacking_wallet_status`                    | string[]                                 |                                                                                                                                                              |
| `miner_wallet_status`                       | string[]                                 |                                                                                                                                                              |
| `nft_wallet_status`                         | string[]                                 |                                                                                                                                                              |
| `total_usdt_transactions_amount`            | number                                   |                                                                                                                                                              |
| `usdt_balance`                              | number                                   |                                                                                                                                                              |
| `total_balance_in_usd`                      | number                                   |                                                                                                                                                              |
| `total_transactions_amount_in_usd`          | number                                   |                                                                                                                                                              |
| `total_received_transactions_amount_in_usd` | number                                   |                                                                                                                                                              |
| `total_sent_transactions_amount_in_usd`     | number                                   |                                                                                                                                                              |
| `count`                                     | integer                                  |                                                                                                                                                              |



```json
{
  "history": [
    {
      "version": "2.0.0",
      "uuid": "b380a114-00e1-4fc2-a80a-740355b3df87",
      "created_dt": "2024-12-12T14:01:11.437630+00:00",
      "endpoint_used": "/v1/reports/wallet_risk_score",
      "source": "api",
      "whitelist": false,
      "blacklist": false,
      "address": "EQBhhJXZI8NVeJSTXhOQPbheJknVRaCqOQu9gHroK0Uu1Knw",
      "address_type": "highload_wallet",
      "address_raw": null,
      "address_non_bounceable": null,
      "owner": "unknown",
      "fraud_level": "high",
      "risk_score": 81,
      "info_category": [],
      "risk_category": [
        20
      ],
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
      "first_transaction_time": "2022-01-20T10:18:16+00:00",
      "last_transaction_time": "2023-01-28T12:38:29+00:00",
      "total_balance": 34.56051276,
      "total_balance_in_usd": null,
      "total_days": 373,
      "total_transactions_amount": 239.09573159,
      "total_transactions_amount_in_usd": null,
      "total_sent_transactions_amount": 0.00004705,
      "total_sent_transactions_amount_in_usd": null,
      "total_received_transactions_amount": 239.09568454,
      "total_received_transactions_amount_in_usd": null,
      "total_counterparts_count": 46813,
      "total_sent_counterparts_count": 46811,
      "total_received_counterparts_count": 16,
      "total_transactions_count": 47079,
      "total_sent_transactions_count": 47049,
      "total_received_transactions_count": 30,
      "bridge_wallet_status": [],
      "exchange_wallet_status": [
        "Linked FTX",
        "Linked OKX",
        "Linked EXMO deposit"
      ],
      "stacking_wallet_status": [],
      "miner_wallet_status": [],
      "nft_wallet_status": [],
      "gambling_message_count": 0,
      "spam_message_count": 47049,
      "scam_message_count": 0,
      "usdt_balance": null,
      "total_usdt_transactions_amount": null
    }
  ],
  "count": 8
}
```
***
### [GET]/v1/reports/risk_history.csv

**Returns risk scoring history in a csv file**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
```
https://api.tonguard.org/v1/reports/risk_history.csv?address=ADDRESS
&risk_limit=INTEGER&risk_offset=INTEGER&info_category=INTEGERrisk_category=INTEGER&risk=RISK_LEVEL1,RISK_LEVEL2&source=SOURCE
&date_from=DATE_FROM&date_to=DATE_TO
```
**Content-Type** `application/json`

**Parameters(Query)**

| Parameter       | Type    | Description                                            | Required |
|-----------------|---------|--------------------------------------------------------|----------|
| `address`       | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `risk_limit`    | integer |                                                        |          |
| `risk_offset `  | integer | Offset of risk for filter                              |          |          
| `info_category` | string  | List of info tags for filter.                          |          |         
| `risk_category` | string  | List of risk tags for filter.                          |          |          
| `risk`          | string  | List of risk levels for filter.                        |          |          
| `source`        | string  | Source of the request                                  |          |          
| `date_from`     | string  | Date from for filter                                   |          |          
| `date_to`       | string  | Date to for filter                                     |          |          

**Responses**

`200` **Risk scoring history successfully retrieved**

***

### [GET]/v1/reports/risk_scoring_report

**Return risk scoring report for a specific uuid**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
```
https://api.tonguard.org/v1/reports/risk_scoring_report?uuid=UUID
```
**Content-Type** `application/json`

**Parameters (Query)**

| Parameter | Type   | Description               | Required |
|-----------|--------|---------------------------|----------|
| `uuid`    | string | id of risk scoring report | yes      |

**Responses**

| Parameter                              | Type             | Description | 
|----------------------------------------|------------------|-------------|
| version                                | string           |             |
| uuid                                   | string           |             |
| created_dt                             | string           |             |
| endpoint_used                          | string           |             |
| source                                 | string | api/manual  |
| whitelist                              | boolean          |             |
| blacklist                              | boolean          |             |
| address                                | string           |             |
| address_type                           | string //default | unknown     |
| address_raw                            | string           |             |
| address_non_bounceable                 | string           |             |
| owner                                  | string //default | unknown     |
| fraud_level                            | string           |             |
| risk_score                             | integer          |             |
| info_category                          | integer[]        |             |
| risk_category                          | integer[]        |             |
| risky_connections                      |[]               |             |
| first_transaction_time                 | string           |             |
| last_transaction_time                  | string           |             |
| total_balance                          | number           |             |
| total_balance_in_usd                   | number           |             |
| total_days                             | number           |             |
| total_transactions_amount              | number           |             |
| total_transactions_amount_in_usd       | number           |             |
| total_sent_transactions_amount         | number           |             |
| total_sent_transactions_amount_in_usd  | number           |             |
| total_received_transactions_amount     | number           |             |
| total_received_transactions_amount_in_usd | number           |             |
| total_counterparts_count               | integer          |             |
| total_sent_counterparts_count          | integer          |             |
| total_received_counterparts_count      | integer          |             |
| total_transactions_count               | integer          |             |
| total_sent_transactions_count          | integer          |             |
| total_received_transactions_count      | integer          |             |
| bridge_wallet_status                   | string[]         |             |
| exchange_wallet_status                 | string[]         |             |
| stacking_wallet_status                 | string[]         |             |
| miner_wallet_status                    | string[]         |             |
| nft_wallet_status                      | string[]         |             |
| gambling_message_count                 | integer          |             |
| spam_message_count                     | integer          |             |
| scam_message_count                     | integer          |             |
| usdt_balance                           | number           |             |
| total_usdt_transactions_amount         | number           |             |


**Content-Type** `application/json`
```json
{
  "report": {
    "version": "2.0.0",
    "uuid": "fcf31537-794b-4a25-ae66-d5454b1eb545",
    "created_dt": "2024-12-13T00:50:43.791818+00:00",
    "endpoint_used": "/v2/reports/wallet_risk_score",
    "source": "api",
    "whitelist": true,
    "blacklist": false,
    "address": "EQDug2S5evQ3jPR1wZJX3qq9BluTdVhoOCQ2-_Guy9oy4Jhi",
    "address_type": "unknown",
    "address_raw": "0:ee8364b97af4378cf475c19257deaabd065b93755868382436fbf1aecbda32e0",
    "address_non_bounceable": "UQDug2S5evQ3jPR1wZJX3qq9BluTdVhoOCQ2-_Guy9oy4MWn",
    "owner": "unknown",
    "fraud_level": null,
    "risk_score": null,
    "info_category": [],
    "risk_category": [],
    "risky_connections": [],
    "first_transaction_time": null,
    "last_transaction_time": null,
    "total_balance": 0.01794588,
    "total_balance_in_usd": null,
    "total_days": null,
    "total_transactions_amount": null,
    "total_transactions_amount_in_usd": null,
    "total_sent_transactions_amount": null,
    "total_sent_transactions_amount_in_usd": null,
    "total_received_transactions_amount": null,
    "total_received_transactions_amount_in_usd": null,
    "total_counterparts_count": null,
    "total_sent_counterparts_count": null,
    "total_received_counterparts_count": null,
    "total_transactions_count": null,
    "total_sent_transactions_count": null,
    "total_received_transactions_count": null,
    "bridge_wallet_status": [],
    "exchange_wallet_status": [],
    "stacking_wallet_status": [],
    "miner_wallet_status": [],
    "nft_wallet_status": [],
    "gambling_message_count": null,
    "spam_message_count": null,
    "scam_message_count": null,
    "usdt_balance": null,
    "total_usdt_transactions_amount": null
  }
}
```
***
### [GET]/v1/reports/risk_scoring_report_{uuid}.pdf

**Download risk scoring report as a pdf-file**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
```
https://api.tonguard.org/v1/reports/risk_scoring_report_UUID.pdf
```
**Content-Type** `application/json`

**Parameters (Query)**

| Parameter | Type   | Description               | Required |
|-----------|--------|---------------------------|----------|
| `uuid`    | string | id of risk scoring report | yes      |

**Responses**
`200` **Data successfully downloaded**

***

