## Monitoring
Setting up monitoring of TON addresses' risk score via API.

Monitoring allows users to monitor and receive real-time alerts on AML risks for all specified addresses.

The system provides 3 types of alerts:
* re-screening addresses; 
* tracking increases in risk score;
* tracking changes in risk categories.

Set up notifications via email or API. 

To set up monitoring rules follow steps below. 


**`Reminder`**
```
HTTP request header provide  with `token` in the following format:

token: "Bearer <jwt token>"
```

### [POST]/v2/monitoring/notify_setting
Set up notify, use urlencoded parameters

**Content-Type** `application/json`

**Example**
```
https://api.tonguard.org/v2/monitoring/notify_setting?notify_url=URL&email=EMAIL
```

**Query parameters**

| Parameter    | Type   | Description      | Required                                 |
|--------------|--------|------------------|------------------------------------------|
| `notify_url` | string | notification url | either email or url is required, or both |
| `email`      | string | emails           | either email or url is required, or both |

**Responses**

`201` **Success**

**Content-Type** `application/json`

```json
{
  "id": 0
}
```


**Error codes** see full specification [here ](../errors.md)

***

### [GET]/v2/monitoring/user_rule
Get user notify settings

**Example**

```
https://api.tonguard.org/v2/monitoring/user_rule
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
      "notify_url": "string",
      "email": "string",
      "created_dt": "string"
    }
  ]
}
```

**Error codes** see full specification [here ](../errors.md)


***

### [POST]/v2/monitoring/user_rule

Set up alerting configurations

**Content-Type** `application/json`

**Example**
```
https://api.tonguard.org/v2/monitoring/user_rule?notify_url=URL&email=EMAIL,EMAIL1
```

**Request body**

| Parameter                      | Type    | Description                                                                                                                                                                                                                 | Required |
|--------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| `monitoring_notify_setting_id` | integer | id from [POST/v2/monitoring/user_rule](#postv2monitoringnotify_setting) or [GET/v2/monitoring/user_rule](#getv2monitoringuser_rule)                                                                                         | yes      |
| `monitoring_rule_info_key`     | string  | choose rule type: <br/> `rescreening`: re-screening addresses, <br/> `risk_category`: tracking increases in risk score, <br/> `risk_threshold`:tracking changes in risk categories                                          | yes      |
| `custom_parameter`             | string  | depend on `monitoring_rule_info_key`: <br/> `rescreening`: {"interval": hours}, <br/> `risk_category`: {"risk_categories": [[risk category](../dictionary.md)]}, <br/> `risk_threshold`:{"risk_threshold": integer <=100} | yes      |
| `rule_name_custom`             | string  | name of alert configuration                                                                                                                                                                                                 | yes      |
| `comment`                      | string  | comment                                                                                                                                                                                                                     | no       |

```json
{
  "monitoring_notify_setting_id": 0,
  "monitoring_rule_info_key": "string",
  "custom_parameter": {},
  "rule_name_custom": "string",
  "comment": "string"
}
```

**Responses**

`201` **Success**

**Content-Type** `application/json`

```json
{}
```

**Error codes** see full specification [here ](../errors.md)


***
### [GET]/v2/monitoring/user_rule
Get user rules

```
https://api.tonguard.org/v2/monitoring/user_rule?limit=INTEGER&offset=INTEGER
```

**Parameters(Query)**

| Parameter | Type    | Description                                     | Required |
|-----------|---------|-------------------------------------------------|----------|
| `limit`   | string  | limit of records to return, default: 10         | no       |
| `offset`  | integer | offset of records to return, Default value is 0 | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "count": 0,
  "results": [
    {
      "id": 0,
      "monitoring_notify_setting_id": 0,
      "monitoring_rule_info_key": "string",
      "custom_parameter": {},
      "addresses_count": 0,
      "rule_name": "string",
      "comment": "string",
      "created_dt": "string",
      "is_enabled": true
    }
  ]
}
```

**Error codes** see full specification [here ](../errors.md)

***

### [DELETE]/v2/monitoring/user_rule
Delete user rule

**Content-Type** `application/json`

**Request body JSON**

| Parameter                 | Type    | Description                | Required |
|---------------------------|---------|----------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id ypu want to delete | yes      |

```json
{
  "monitoring_user_rule_id": 0
}
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{}
```

**Error codes** see full specification [here ](../errors.md)

***

### [POST]/v2/monitoring/address_under_rule
Attach a user rule to a wallet

**Content-Type** `application/json`

**Request body JSON**

| Parameter                 | Type    | Description                          | Required |
|---------------------------|---------|--------------------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id you want to attach to wallet | yes      |
| `address`                 | string  | TON wallet address                   | yes      |

```json
{
  "monitoring_user_rule_id": 0,
  "address": "string"
}
```

**Responses**

`201` **Success**

**Content-Type** `application/json`

```json
{}
```

**Error codes** see full specification [here ](../errors.md)

***

### [DELETE]/v2/monitoring/address_under_rule
Delete address from rule

**Content-Type** `application/json`

**Request body JSON**

| Parameter                 | Type    | Description                          | Required |
|---------------------------|---------|--------------------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id you want to attach to wallet | yes      |
| `address`                 | string  | TON wallet address                   | yes      |

```json
{
  "monitoring_user_rule_id": 0,
  "address": "string"
}
```

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{}
```

**Error codes** see full specification [here ](../errors.md)

***
### [GET]/v2/monitoring/address_under_rule
Get addresses under rule

```
https://api.tonguard.org/v2/monitoring/address_under_rule?monitoring_user_rule_id=ID&limit=INTEGER&offset=INTEGER
```

**Parameters(Query)**

| Parameter                 | Type    | Description                                     | Required |
|---------------------------|---------|-------------------------------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id you want to attach to wallet            | yes      |
| `limit`                   | string  | limit of records to return, default: 10         | no       |
| `offset`                  | integer | offset of records to return, Default value is 0 | no       |

**Responses**

`200` **Success**

**Content-Type** `application/json`

```json
{
  "count": 0,
  "results": [
    {
      "id": 0,
      "monitoring_user_rule_id": 0,
      "address": "string",
      "created_dt": "string"
    }
  ]
}
```

**Error codes** see full specification [here](../errors.md)


***
### [GET]/v1/monitoring/user_rule_statistics

Get user rule statistics

**Content-Type** `application/json`

**Parameters(Query)**

| Parameter       | Type    | Description                                            | Required |
|-----------------|---------|--------------------------------------------------------|----------|
| `limit`         | string  | limit of records to return                             | no       |
| `offset`        | integer | offset of records to return                            | no       |


**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter         | Type    | Description                                  | 
|-------------------|---------|----------------------------------------------|
| `count`           | integer | total addresses found                        | 
| `created_dt`      | string  | date created,'%d/%m/%Y, %H:%M:%S GMT' format |
| `rule_name`       | string  | rule name                                    | 
| `alert_count`     | integer | numbers of notification sent                 |          
| `delivered_count` | integer | numbers of notification delivered to user    |           
| `comment`         | string  | comment                                      |          


```json
{
  "count": integer,
  "user_rule_statistics": [
  {
    "created_dt": "string",
    "rule_name": "string",
    "alert_count": integer,
    "delivered_count": integer,
    "comment": "string"
  }
  ]
}
```
