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

**Example**
```
GET https://api.tonguard.org/v1/visualizer/get_transactions_graph?address=ADDRESS&limit=10
Authorization: Bearer <jwt token>
```

**Request parameters (Query)**

| Parameter   | Type      | Description                                                                                                        | Required |
|-------------|-----------|--------------------------------------------------------------------------------------------------------------------|----------|
| `address`   | string    | TON wallet address in any base64 form (urlsafe or not). Accepts both address types - bounceable and non-bounceable | yes      |
| `limit`     | integer[] | limit of records to return, default: 10                                                                            | no       |
| `action`    | string    | user action, use 'view'                                                                                            | no       |
| `risk`      | string    | list of risk levels to return: high,medium,low,lowest,unknown                                                      | no       |
| `date_from` | string    | date from for filter, "DD.MM.YYYY" format                                                                          | no       |
| `date_to`   | string    | date to for filter, "DD.MM.YYYY" format                                                                            | no       |
| `depth`     | string    | depth of records to return, default: 10                                                                            | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "address": "string",
  "nodes": [
    {
      "id": "string",
      "alias": "string",
      "name": "string",
      "type": "input",
      "label": "string",
      "data": {
        "owner": "string",
        "incoming_transactions": 0,
        "outgoing_transactions": 0,
        "balance": 0,
        "turnover": 0,
        "report": {
          "fraud_level": "string",
          "risk_score": 0
        }
      }
    }
  ],
  "edges": [
    {
      "id": 0,
      "created_dt": "string",
      "source": "string",
      "target": "string",
      "label": "string",
      "value": "string",
      "logical_time": 0,
      "transaction_hash": "string",
      "forward_fee": 0
    }
  ],
  "action": "string"
}
```

### [GET]/v1/visualizer/get_last_transactions_graph
Method is used to get last user's graph

**Content-Type** `application/json`

```
https://api.tonguard.org/v1/visualizer/get_last_transactions_graph
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "address": "string",
  "nodes": [
    {
      "id": "string",
      "alias": "string",
      "name": "string",
      "type": "input",
      "label": "string",
      "data": {
        "owner": "string",
        "incoming_transactions": 0,
        "outgoing_transactions": 0,
        "balance": 0,
        "turnover": 0,
        "report": {
          "fraud_level": "string",
          "risk_score": 0
        }
      }
    }
  ],
  "edges": [
    {
      "id": 0,
      "created_dt": "string",
      "source": "string",
      "target": "string",
      "label": "string",
      "value": "string",
      "logical_time": 0,
      "transaction_hash": "string",
      "forward_fee": 0
    }
  ],
  "action": "string"
}
```

### [PUT]/v1/visualizer/update_transactions_graph
Update graph's transactions

```
https://api.tonguard.org/v1/visualizer/update_transactions_graph?address=ADDRESS&graph_id=ID
```

**Request parameters (Query)**

| Parameter  | Type    | Description                                                                                                        | Required |
|------------|---------|--------------------------------------------------------------------------------------------------------------------|----------|
| `address`  | string  | TON wallet address in any base64 form (urlsafe or not). Accepts both address types - bounceable and non-bounceable | yes      |
| `graph_id` | integer | graph id                                                                                                           | no       |

**Request body Json**
**You have to send parameters as in response** [[GET]/v1/visualizer/get_transactions_graph](#getv1visualizerget_transactions_graph)

**Responses**

`204` **Success**

### [GET]/v1/visualizer/get_visualizer_history
Get addresses history

```
https://api.tonguard.org/v1/visualizer/get_visualizer_history?offset=OFFSET&limit=LIMIT
```

**Request parameters (Query)**

| Parameter | Type    | Description                                 | Required |
|-----------|---------|---------------------------------------------|----------|
| `offset`  | integer | Offset to paginate over. Default value is 0 | no       |
| `limit`   | integer | Limit to paginate. Default value is 10      | no       |

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

### [GET]/v1/visualizer/get_transactions_graph_by_uuid
Get graph by UUID

```
https://api.tonguard.org/v1/visualizer/get_transactions_graph_by_uuid?uuid=UUID
```

**Request parameters (Query)**

| Parameter | Type   | Description | Required |
|-----------|--------|-------------|----------|
| `uuid`    | string | graph UUID  | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "address": "string",
  "nodes": [
    {
      "id": "string",
      "alias": "string",
      "name": "string",
      "type": "input",
      "label": "string",
      "data": {
        "owner": "string",
        "incoming_transactions": 0,
        "outgoing_transactions": 0,
        "balance": 0,
        "turnover": 0,
        "report": {
          "fraud_level": "string",
          "risk_score": 0
        }
      }
    }
  ],
  "edges": [
    {
      "id": 0,
      "created_dt": "string",
      "source": "string",
      "target": "string",
      "label": "string",
      "value": "string",
      "logical_time": 0,
      "transaction_hash": "string",
      "forward_fee": 0
    }
  ],
  "action": "string"
}
```

**Error codes** see full specification [here](../errors.md)