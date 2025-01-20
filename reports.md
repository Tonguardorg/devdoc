##  Reports

Returns address risk score, risk level and query related info,including the usdt information. 

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

| Parameter                                   | Type      | Description                                                                                                                                                                                                              | 
|---------------------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uuid`                                      | string    | universally unique identifier for risk scoring, use it as report id                                                                                                                                                      |
| `version`                                   | string    | api version                                                                                                                                                                                                              |
| `whitelist`                                 | boolean   | an indication that the address is on the whitelist, if address is included in the private whitelist, it's Risk level is automatically lowered to a low level                                                             |
| `blacklist`                                 | boolean   | an indication that the address is on the blacklist                                                                                                                                                                       |
| `address`                                   | string    | TON wallet address bounceable format                                                                                                                                                                                     |
| `address_raw`                               | string    | TON wallet address raw format, default: unknown                                                                                                                                                                          |
| `address_non_bounceable`                    | string    | TON wallet address non-bounceable format, default: unknown                                                                                                                                                               |
| `address_type`                              | string    | smart contract type <br/>default: unknown                                                                                                                                                                                              |
| `owner`                                     | string    | owner's public name <br/>default: unknown                                                                                                                                                                              |
| `risk_score`                                | integer   | risk score level (0-100)                                                                                                                                                                                                 |
| `fraud_level`                               | enum      | risk levelss: <br/>* lowest risk (0 - 12),<br/>* low risk (12 - 46), <br/>* medium risk (46 – 82), <br/>* high risk (82 – 100), <br/> * wallets with no clear activity may beclassified as Unknown. <br/>Default: lowest |                    
| `risk_category`                             | string [] | `code`: `integer` <br/>`name`: `string`<br/>`type`: `enum`[INFO, RISK]<br/>`description` : description <br/>[risk category ](../dictionary.md)                                                                           |
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
| `gambling_message_count`                    | integer   | gambling transactions сount for the analyzed address                                                                                                                                                                     |
| `spam_message_count`                        | integer   | spam transactions сount for the analyzed address                                                                                                                                                                         |
| `scam_message_count`                        | integer   | scam transactions сount for the analyzed address                                                                                                                                                                         |
| `bridge_wallet_status`                      | string[]  |                                                                                                                                                                                                                          |
| `exchange_wallet_status`                    | string[]  |                                                                                                                                                                                                                          |
| `stacking_wallet_status`                    | string[]  |                                                                                                                                                                                                                          |
| `miner_wallet_status`                       | string[]  |                                                                                                                                                                                                                          |
| `nft_wallet_status`                         | string[]  |                                                                                                                                                                                                                          |
| `total_usdt_transactions_amount`            | number    | USDT jettons transactions balance recalculated to USD at the current rate                                                                                                                                                                                                                         |
| `usdt_balance`                              | number    | current balance and turnover of USDT jettons for the analyzed address                                                                                                                                                    |
| `total_balance_in_usd`                      | number    | USDT jettons balance recalculated to USD **at the current rate**                                                                                                                                                         |
| `total_transactions_amount_in_usd`          | number    | USDT jettons transactions balance recalculated to USD **at the current rate**                                                                                                                                            |
| `total_received_transactions_amount_in_usd` | number    | USDT jettons received balance recalculated to USD **at the current rate**                                                                                                                                                |
| `total_sent_transactions_amount_in_usd`     | number    | USDT jettons sent balance recalculated to USD **at the current rate**                                                                                                                                                    |



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
  "stacking_wallet_status": []
}
```

**Error codes** see full specification [here ](../errors.md)


***


### [GET]/v1/reports/risk_scoring_history

**Returns risk scoring history for a specific user and address**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Example**
```
https://api.tonguard.org/v1/reports/risk_scoring_history?address=ADDRESS&limit=INTEGER&offset=INTEGER&risk_limit=INTEGER&risk_offset=INTEGER&info_category=
INTEGER&risk_category=INTEGER&risk=high%2Cmedium&source=api&date_from=DATE_FROM&date_to=DATE_TO
```


**Content-Type** `application/json`

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

`200` **Risk scoring history successfully retrieved**

**Content-Type** `application/json`

| Parameter                                   | Type                                     | Description                                                                                                                                                  | 
|---------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uuid`                                      | string                                   | universally unique identifier, report id                                                                                                                     |
| `version`                                   | string                                   | api version                                                                                                                                                  |
| `created_dt`                                | string                                   | date when the report was generated                                                                                                                           |
| `endpoint_used`                             | string                                   | endpoint_used                                                                                                                                                |
| `source`                                    | string                                   | default: api , options: manual/api                                                                                                                           |
| `whitelist`                                 | boolean                                  | an indication that the address is on the whitelist, if address is included in the private whitelist, it's Risk level is automatically lowered to a low level |
| `blacklist`                                 | boolean                                  | an indication that the address is on the blacklist                                                                                                           |
| `address`                                   | string                                   | TON wallet address, bounceable format                                                                                                                        |
| `address_raw`                               | string                                   | TON wallet address raw format, default: unknown                                                                                                              |
| `address_non_bounceable`                    | string                                   | TON wallet address non-bounceable format, default: unknown                                                                                                   |
| `address_type`                              | string                                   | smart contract type <br/>default: unknown                                                                                                                    |
| `owner`                                     | string                                   | owner's public name <br/>default: unknown                                                                                                                    |
| `risk_score`                                | integer                                  | risk score level (0-100)                                                                                                                                     |
| `risky_connections: {}`                     | []                                       | high level risk addrees that have transactions with analyzed address                                                                                         |
| `info_category`                             | integer[]                                | [risk category ](../dictionary.md)                                                                                                                           |
| `fraud_level`                               | enum[high, medium, low, lowest, unknown] | default: lowest                                                                                                                                              |                    
| `risk_category`                             | string[]                                 | [risk category ](../dictionary.md)                                                                                                                           |
| `total_days`                                | integer                                  | the number of days the address has existed since the first transaction with the analyzed address                                                             |
| `first_transaction_time`                    | string                                   | date of the first analyzed transaction                                                                                                                       |
| `last_transaction_time`                     | string                                   | date of the last analyzed transaction                                                                                                                        |
| `total_balance`                             | number                                   | current balance value of the analyzed address                                                                                                                |
| `total_transactions_amount`                 | number                                   | current turnover value for the analyzed address                                                                                                              |
| `total_transactions_count`                  | integer                                  | total number of transactions made with the analyzed address                                                                                                  |
| `total_counterparts_count`                  | integer                                  | total number of addresses that have ever interacted with the analyzed address                                                                                |
| `total_sent_transactions_amount`            | number                                   | amount of cryptocurrency sent by the analyzed address                                                                                                        |
| `total_sent_transactions_count`             | integer                                  | total number of transactions sent by the analyzed address                                                                                                    |
| `total_sent_counterparts_count`             | integer                                  | total number of transactions that have ever interacted by the analyzed address (sending transactions)                                                        |
| `total_received_transactions_amount`        | number                                   | amount of cryptocurrency received by the analyzed address                                                                                                    |
| `total_received_transactions_count`         | integer                                  | number of cryptocurrency transactions received by the analyzed address                                                                                       |
| `total_received_counterparts_count`         | integer                                  | number of cryptocurrency transactions that have ever interacted by the analyzed address (receiving transactions)                                             |
| `gambling_message_count`                    | integer                                  | gambling transactions сount for the analyzed address                                                                                                         |
| `spam_message_count`                        | integer                                  | spam transactions сount for the analyzed address                                                                                                             |
| `scam_message_count`                        | integer                                  | scam transactions сount for the analyzed address                                                                                                             |
| `bridge_wallet_status`                      | string[]                                 |                                                                                                                                                              |
| `exchange_wallet_status`                    | string[]                                 |                                                                                                                                                              |
| `stacking_wallet_status`                    | string[]                                 |                                                                                                                                                              |
| `miner_wallet_status`                       | string[]                                 |                                                                                                                                                              |
| `nft_wallet_status`                         | string[]                                 |                                                                                                                                                              |
| `total_usdt_transactions_amount`            | number                                   |                                                                                                                                                              |
| `usdt_balance`                              | number                                   | USDT jettons transactions balance recalculated to USD at the current rate                                                                                    |
| `total_balance_in_usd`                      | number                                   | current balance and turnover of USDT jettons for the analyzed address                                                                                        |
| `total_transactions_amount_in_usd`          | number                                   | USDT jettons balance recalculated to USD at the current rate                                                                                                 |
| `total_received_transactions_amount_in_usd` | number                                   | USDT jettons transactions balance recalculated to USD at the current rate                                                                                    |
| `total_sent_transactions_amount_in_usd`     | number                                   | USDT jettons received balance recalculated to USD at the current rate                                                                                        |
| `count`                                     | integer                                  | USDT jettons sent balance recalculated to USD at the current rate                                                                                            |



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

see [Wallet Risk Score](#getv2reportswallet_risk_score)

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

