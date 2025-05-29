## Whitelist

Управление белым списком адресов TON.

### [GET]/v1/whitelists/whitelist
Получить белый список

**Example**
```
https://api.tonguard.org/v1/whitelists/whitelist
```

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

### [DELETE]/v1/whitelists/whitelist_entity
Удалить адрес из белого списка

**Content-Type** `application/json`

**Request body**

| Parameter  | Type   | Description          | Required |
|------------|--------|----------------------|----------|
| `address`  | string | TON адрес кошелька   | yes      |

```json
{
  "address": "string"
}
```

**Responses**

`204` **Success**

### [GET]/v1/whitelists/whitelist.csv
Скачать белый список в формате CSV

**Responses**

`200` **Success**

**Content-Type** `text/csv`

```
id,address,created_dt
```

### [POST]/v1/whitelists/whitelist.csv
Загрузить данные белого списка

**Content-Type** `multipart/form-data`

**Request body**

| Parameter | Type   | Description          | Required |
|-----------|--------|----------------------|----------|
| `file`    | file   | CSV файл с адресами  | yes      |

**Responses**

`201` **Success**

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

**Error codes** see full specification [here](../errors.md)
