## Top Holders

Получение информации о топ-холдерах токенов TON.

### [GET]/v1/top_holders
Получить список топ-холдеров

**Parameters(Query)**

| Parameter  | Type    | Description                                     | Required |
|------------|---------|-------------------------------------------------|----------|
| `limit`    | string  | limit of records to return, default: 10         | no       |
| `offset`   | integer | offset of records to return, Default value is 0 | no       |
| `token`    | string  | Адрес токена                                    | no       |
| `date_from`| string  | Дата начала периода (YYYY-MM-DD)                | no       |
| `date_to`  | string  | Дата конца периода (YYYY-MM-DD)                 | no       |

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
      "token": "string",
      "balance": "string",
      "percentage": 0,
      "created_dt": "string",
      "updated_dt": "string"
    }
  ]
}
```

### [GET]/v1/top_holders/{holder_id}
Получить детальную информацию о конкретном холдере

**Parameters(Path)**

| Parameter  | Type    | Description     | Required |
|------------|---------|-----------------|----------|
| `holder_id`| integer | ID холдера      | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "address": "string",
  "token": "string",
  "balance": "string",
  "percentage": 0,
  "created_dt": "string",
  "updated_dt": "string",
  "transactions": [
    {
      "id": 0,
      "hash": "string",
      "type": "string",
      "amount": "string",
      "created_dt": "string"
    }
  ]
}
```

### [GET]/v1/top_holders/export
Экспорт списка топ-холдеров в CSV

**Parameters(Query)**

| Parameter  | Type    | Description                     | Required |
|------------|---------|---------------------------------|----------|
| `token`    | string  | Адрес токена                    | no       |
| `date_from`| string  | Дата начала периода (YYYY-MM-DD)| no       |
| `date_to`  | string  | Дата конца периода (YYYY-MM-DD) | no       |

**Responses**

`200` **Success**

**Content-Type** `text/csv`

```
id,address,token,balance,percentage,created_dt,updated_dt
```

### [GET]/v1/top_holders/tokens
Получить список доступных токенов

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "count": 0,
  "results": [
    {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0
    }
  ]
}
```

**Error codes** see full specification [here](../errors.md) 