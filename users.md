## Users

Управление пользователями системы.

### [GET]/v1/users/me
Получить информацию о текущем пользователе

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "username": "string",
  "email": "string",
  "first_name": "string",
  "last_name": "string",
  "company": "string",
  "position": "string",
  "phone": "string",
  "created_dt": "string",
  "last_login_dt": "string",
  "is_active": true,
  "queries_left": 0,
  "queries_total": 0
}
```

### [PUT]/v1/users/me
Обновить информацию о текущем пользователе

**Content-Type** `application/json`

**Request body**

| Parameter    | Type   | Description    | Required |
|--------------|--------|----------------|----------|
| `first_name` | string | Имя            | no       |
| `last_name`  | string | Фамилия        | no       |
| `company`    | string | Компания       | no       |
| `position`   | string | Должность      | no       |
| `phone`      | string | Телефон        | no       |

```json
{
  "first_name": "string",
  "last_name": "string",
  "company": "string",
  "position": "string",
  "phone": "string"
}
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "username": "string",
  "email": "string",
  "first_name": "string",
  "last_name": "string",
  "company": "string",
  "position": "string",
  "phone": "string",
  "created_dt": "string",
  "last_login_dt": "string",
  "is_active": true,
  "queries_left": 0,
  "queries_total": 0
}
```

### [PUT]/v1/users/me/password
Изменить пароль текущего пользователя

**Content-Type** `application/json`

**Request body**

| Parameter        | Type   | Description     | Required |
|------------------|--------|-----------------|----------|
| `old_password`   | string | Старый пароль   | yes      |
| `new_password`   | string | Новый пароль    | yes      |

```json
{
  "old_password": "string",
  "new_password": "string"
}
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{}
```

### [GET]/v1/users/queries
Получить историю запросов текущего пользователя

**Parameters(Query)**

| Parameter  | Type    | Description                                     | Required |
|------------|---------|-------------------------------------------------|----------|
| `limit`    | string  | limit of records to return, default: 10         | no       |
| `offset`   | integer | offset of records to return, Default value is 0 | no       |
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
      "endpoint": "string",
      "request_data": {},
      "response_data": {},
      "created_dt": "string",
      "status_code": 0
    }
  ]
}
```

### [GET]/v1/users/queries/{query_id}
Получить детальную информацию о конкретном запросе

**Parameters(Path)**

| Parameter | Type    | Description     | Required |
|-----------|---------|-----------------|----------|
| `query_id`| integer | ID запроса      | yes      |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0,
  "endpoint": "string",
  "request_data": {},
  "response_data": {},
  "created_dt": "string",
  "status_code": 0
}
```

### [GET]/v1/users/queries/export
Экспорт истории запросов в CSV

**Parameters(Query)**

| Parameter  | Type    | Description                     | Required |
|------------|---------|---------------------------------|----------|
| `date_from`| string  | Дата начала периода (YYYY-MM-DD)| no       |
| `date_to`  | string  | Дата конца периода (YYYY-MM-DD) | no       |

**Responses**

`200` **Success**

**Content-Type** `text/csv`

```
id,endpoint,request_data,response_data,created_dt,status_code
```

**Error codes** see full specification [here](../errors.md) 