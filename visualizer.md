## Visualizer
* Execute comprehensive investigations within the TON blockchain
* Intelligently search for potentially risky transactions
* Facilitate transactional investigations

`User can send requests to the visualizer only if he has at least one available request. 
If all requests are used up, access to the visualizer will be restricted until additional requests are allocated.`

**Reminder**
```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

### [GET]/v1/visualizer/get_transactions_graph
Method is used to create graph

**Content-Type** `application/json`

```
https://my.tonguard.org/api/v1/visualizer/get_transactions_graph?address=ADDRESS&limit=INTEGER&action=ACTION&risk=RISK&date_from=DATE_FROM&date_to=DATE_TO
```

**Request parameters (Query)**

| Parameter   | Type      | Description                                                                                                        | Required |
|-------------|-----------|--------------------------------------------------------------------------------------------------------------------|----------|
| `address`   | string    | TON wallet address in any base64 form (urlsafe or not). Accepts both address types - bounceable and non-bounceable | yes      |
| `limit`     | integer[] | limit of records to return, default: 10                                                                            | no       |
| `action`    | string    | user action, use 'view'                                                                                            | no       |
| `risk`      | string    | list of risk levels to return: high,medium,low,lowest,unknown                                                      | no       |
| `date_from` | string    | date from for filter, "DD.MM.YYYY" format                                                                          | no       |
| `date_to`   | string    | date to for filter, "DD.MM.YYYY" format                                                                                                  | no       |
| `depth`     | string    | depth of records to return, default: 10                                                                            | no       |


**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| **Parameter**                            | **Type**                             | **Description**                               |
|------------------------------------------|--------------------------------------|-----------------------------------------------|
| `address`                                | `string`                             | TON wallet address                            |
| **`nodes`**                              |                                      | graph nodes object                            |
| └ `id`                                   | `string`                             | TON wallet address                            |
| └ `alias`                                | `string (optional)`                  | default: null                                 |
| └ `name`                                 | `string`                             | TON wallet address                            |
| └ `type`                                 | `enum[input, output, custom]`        | type: `input`, `output`, `custom`             |
| └ `label`                                | `string`                             | TON wallet address                            |
| └ **`data`**                             | `object`                             | wallets extra data                            |
| &nbsp;&nbsp; └ `owner`                   | `string (optional)`                  | owner's public name, default: unknown         |
| &nbsp;&nbsp; └ `incoming_transactions`   | `integer (optional)`                 | number of incoming transactions               |
| &nbsp;&nbsp; └ `outgoing_transactions`   | `integer (optional)`                 | number of outgoing transactions               |
| &nbsp;&nbsp; └ `balance`                 | `number (optional)`                  | current balance of the wallet                 |
| &nbsp;&nbsp; └ `turnover`                | `number (optional)`                  | current turnover of the wallet                |
| &nbsp;&nbsp; └ `report`                  | `object`                             | report data                                   |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `fraud_level` | `string (optional)`                  | fraud level: high,medium,low,lowest,unknown   |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `risk_score`  | `integer (optional)`                 | last risk score value                         |
| **`edges`**                              |                                      |                                               |
| └ `id`                                   | `Partial(integer) & Partial(string)` | edge id                                       |
| └ `created_dt`                           | `string (optional)`                  | creation date '%d/%m/%Y, %H:%M:%S GMT' format |
| └ `source`                               | `string (optional)`                  | source address of the cryptocurrency funds    |
| └ `target`                               | `string (optional)`                  | target address of the cryptocurrency funds    |
| └ `label`                                | `Partial(number) & Partial(number)`  | text transaction sum                          |
| └ `value`                                | `Partial(number) & Partial(number)`  | transaction sum                               |
| └ `logical_time`                         | `integer (optional)`                 | unix time                                     |
| └ `transaction_hash`                     | `string (optional)`                  | transaction hash                              |
| └ `forward_fee`                          | `integer (optional)`                 | transaction fee                               |
| `action`                                 | `string (optional)`                  | view                                          |

```json
{
    "address": "EQBhhJXZI8NVeJSTXhOQPbheJknVRaCqOQu9gHroK0Uu1Knw",
    "nodes": [
        {
            "id": "EQCRm3dAvnQpuOAbh06YpYC7y-oflkiEuaKf4n5Di8D262YI",
            "alias": null,
            "name": "EQCRm3dAvnQpuOAbh06YpYC7y-oflkiEuaKf4n5Di8D262YI",
            "type": "input",
            "label": "EQCRm3dAvnQpuOAbh06YpYC7y-oflkiEuaKf4n5Di8D262YI",
            "data": {
                "owner": null,
                "incoming_transactions": null,
                "outgoing_transactions": null,
                "balance": 0.998851164,
                "turnover": null,
                "report": null
            }
        },
        {
            "id": "EQCmIxaA3gQXYFx6C13vIlo_OMuXdrbGmpfZFv-vLjYEcKMF",
            "alias": null,
            "name": "EQCmIxaA3gQXYFx6C13vIlo_OMuXdrbGmpfZFv-vLjYEcKMF",
            "type": "input",
            "label": "EQCmIxaA3gQXYFx6C13vIlo_OMuXdrbGmpfZFv-vLjYEcKMF",
            "data": {
                "owner": null,
                "incoming_transactions": 1,
                "outgoing_transactions": 1,
                "balance": 0.000004377,
                "turnover": 0.0012300010000000005,
                "report": null
            }
        },
        {
            "id": "EQBDiGuT0yU3kir5DBs6ILE2gqeYQpnvFZ3n_okSkYBuyj7-",
            "alias": null,
            "name": "EQBDiGuT0yU3kir5DBs6ILE2gqeYQpnvFZ3n_okSkYBuyj7-",
            "type": "input",
            "label": "EQBDiGuT0yU3kir5DBs6ILE2gqeYQpnvFZ3n_okSkYBuyj7-",
            "data": {
                "owner": null,
                "incoming_transactions": 1,
                "outgoing_transactions": 1,
                "balance": 146.822135576,
                "turnover": 2.000000000000001e-9,
                "report": null
            }
        }
    ],
    "edges": [
        {
            "id": 0,
            "created_dt": "2024-06-08T06:01:52+00:00",
            "source": "EQCRm3dAvnQpuOAbh06YpYC7y-oflkiEuaKf4n5Di8D262YI",
            "target": "EQBhhJXZI8NVeJSTXhOQPbheJknVRaCqOQu9gHroK0Uu1Knw",
            "label": "0.000000",
            "value": "0.000000",
            "logical_time": 46961599000010,
            "transaction_hash": "sVTPmh9iazlmj8MjgptbhQCt0gZobxbxVqUCONrdW54=",
            "forward_fee": 455471
        },
        {
            "id": 0,
            "created_dt": "2023-01-28T12:38:29+00:00",
            "source": "EQCmIxaA3gQXYFx6C13vIlo_OMuXdrbGmpfZFv-vLjYEcKMF",
            "target": "EQBhhJXZI8NVeJSTXhOQPbheJknVRaCqOQu9gHroK0Uu1Knw",
            "label": "0.001230",
            "value": "0.001230",
            "logical_time": 34839551000002,
            "transaction_hash": "nWkSeR5BdayZrzbHZoyaFsdXqLiZX5xYYYIRoZlKcuc=",
            "forward_fee": 666672
        }
    ],
    "action": "view"
}
```


**Error codes** see full specification [here ](../errors.md)

***

### [GET]/v1/visualizer/get_last_transactions_graph

Method is used to get last user's graph

**Content-Type** `application/json`


```
https://my.tonguard.org/v1/visualizer/get_last_transactions_graph
```

 **Responses**

see response [[GET]/v1/visualizer/get_transactions_graph](#getv1visualizerget_transactions_graph)

**Error codes** see full specification [here ](../errors.md)

***

### [PUT]/v1/visualizer/update_transactions_graph

Update graph's transactions

```
https://my.tonguard.org/v1/visualizer/update_transactions_graph?address=ADDRESS&graph_id=ID
```
**Request parameters (Query)**

| Parameter  | Type    | Description                                                                                                        | Required |
|------------|---------|--------------------------------------------------------------------------------------------------------------------|----------|
| `address`  | string  | TON wallet address in any base64 form (urlsafe or not). Accepts both address types - bounceable and non-bounceable | yes      |
| `graph_id` | integer |                                                                                                                    | no       |

**Request body Json**
**You have to send parameters as in response** [[GET]/v1/visualizer/get_transactions_graph](#getv1visualizerget_transactions_graph)


**Responses**

`204` **Successful Response**

**Content-Type** `application/json`

**Error codes** see full specification [here ](../errors.md)

***

### [GET]/v1/visualizer/get_visualizer_history
 
Get addresses history

```
https://my.tonguard.org/v1/visualizer/get_visualizer_history?offset=OFFSET&limit=LIMIT
```
**Request parameters (Query)**

| Parameter | Type    | Description                                 | Required |
|-----------|---------|---------------------------------------------|----------|
| `offset`  | integer | Offset to paginate over. Default value is 0 | no       |
| `limit`   | integer | Limit to paginate. Default value is 10      | no       |

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`


| Parameter      | Type    | Description                                   | 
|----------------|---------|-----------------------------------------------|
| `count`        | integer | total count                                   |
| **`data`**     |         |                                               | 
| └ `id`         | integer | id                                            |
| └ `address`    | string  | wallet address                                |
| └ `created_dt` | string  | creation date '%d/%m/%Y, %H:%M:%S GMT' format |


```json
{
  "count" : 0,
  "data" : {
    "id" : 0,
    "address":"string",
    "created_dt":"string"
  }
}
```
**Error codes** see full specification [here ](../errors.md)


***

### [GET]/v1/visualizer/get_transactions_graph_by_id

Get graph by id


```
https://my.tonguard.org/v1/visualizer/get_visualizer_history?graph_id=ID
```
**Request parameters (Query)**

| Parameter  | Type    | Description | Required |
|------------|---------|-------------|----------|
| `graph_id` | integer | graph id    | yes      |


**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| **Поле**                                             | **Тип**           | **Описание**                                  |
|------------------------------------------------------|-------------------|-----------------------------------------------|
| `address`                                            | string            | TON wallet address                            |
| **`nodes`**                                          |                   |                                               |
| └ `data`                                             | object            |                                               |
| &nbsp;&nbsp; └ `id`                                  | string            | TON wallet address                            |
| &nbsp;&nbsp; └ `alias`                               | string (optional) | Alias                                         |
| &nbsp;&nbsp; └ `name`                                | string            | TON wallet address                            |
| &nbsp;&nbsp; └ `type`                                | enum              | type: `input`, `output`, `custom`             |
| &nbsp;&nbsp; └ `label`                               | string            | TON wallet address                            |
| &nbsp;&nbsp; └ `data`                                | object            |                                               |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `owner`                   | string (optional) | owner's public name, default: unknown         |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `incoming_transactions`   | number (optional) | number of incoming transactions               |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `outgoing_transactions`   | number (optional) | number of outgoing transactions               |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `balance`                 | number (optional) | current balance of the wallet                 |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `turnover`                | number (optional) | current turnover of the wallet                |
| &nbsp;&nbsp;&nbsp;&nbsp; └ `report`                  | object            |                                               |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └ `fraud_level` | string (optional) | fraud level: high,medium,low,lowest,unknown   |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └ `risk_score`  | number (optional) | last risk score value                         |
| └ `position`                                         | object            |                                               |
| **`edges`**                                          |                   |                                               |
| └ `id`                                               | string/ number    | id                                            |
| └ `created_dt`                                       | string (optional) | creation date '%d/%m/%Y, %H:%M:%S GMT' format |
| └ `source`                                           | string (optional) | source address of the cryptocurrency funds    |
| └ `target`                                           | string (optional) | target address of the cryptocurrency funds    |
| └ `label`                                            | number (optional) | text                                          |
| └ `value`                                            | number (optional) | transaction sum                               |
| └ `logical_time`                                     | number (optional) | UNIX time                                     |
| └ `transaction_hash`                                 | string (optional) | transaction hash                              |
| └ `forward_fee`                                      | number (optional) | transaction fee                               |


```json
{
  "address": "EQBNegLeN_JSSFQ-Akj4Mfc5HrGvjmkwlPWMNBstm_5ZyJKy",
  "nodes": [
    {
      "data": {
        "id": "EQDpRB6L3L9izGNmLFvoVE8VndGqAXrSns4_fXeIpmSK0IYK",
        "alias": null,
        "name": "EQDpRB6L3L9izGNmLFvoVE8VndGqAXrSns4_fXeIpmSK0IYK",
        "type": "input",
        "label": "EQDpRB6L3L9izGNmLFvoVE8VndGqAXrSns4_fXeIpmSK0IYK",
        "data": {
          "owner": null,
          "incoming_transactions": null,
          "outgoing_transactions": null,
          "balance": 0.013406075,
          "turnover": null,
          "report": null
        }
      },
      "position": null
    },
    {
      "data": {
        "id": "EQBNegLeN_JSSFQ-Akj4Mfc5HrGvjmkwlPWMNBstm_5ZyJKy",
        "alias": null,
        "name": "EQBNegLeN_JSSFQ-Akj4Mfc5HrGvjmkwlPWMNBstm_5ZyJKy",
        "type": "input",
        "label": "EQBNegLeN_JSSFQ-Akj4Mfc5HrGvjmkwlPWMNBstm_5ZyJKy",
        "data": {
          "owner": null,
          "incoming_transactions": null,
          "outgoing_transactions": null,
          "balance": 29991.312572377,
          "turnover": null,
          "report": null
        }
      },
      "position": null
    }
  ],
  "edges": [
    {
      "id": "b7f7b458-1878-49f8-b54e-80cfb1287045",
      "created_dt": "2023-10-17T12:32:45+00:00",
      "source": "EQDpRB6L3L9izGNmLFvoVE8VndGqAXrSns4_fXeIpmSK0IYK",
      "target": "EQBNegLeN_JSSFQ-Akj4Mfc5HrGvjmkwlPWMNBstm_5ZyJKy",
      "label": "0.972348",
      "value": "0.972348",
      "logical_time": 41794822000002,
      "transaction_hash": "5579211cc25e66cb539c7cd064082e7866c3ff1979463e745595dcd90d6c4946",
      "forward_fee": 946674
    }
  ]
}
```

**Error codes** see full specification [here ](../errors.md)

***