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

### [POST] v1/monitoring/notify_setting
Set up notify, use urlencoded parameters

**Content-Type** `application/json`

**Example**
```
https://my.tonguard.org/v1/monitoring/notify_setting?notify_url=URL&email=EMAIL
```

**Query parameters**

| Parameter    | Type   | Description      | Required                                 |
|--------------|--------|------------------|------------------------------------------|
| `notify_url` | string | notification url | either email or url is required, or both |
| `email`      | string | emails           | either email or url is required, or both |

**Responses**

`201` **Successful Response**

**Content-Type** `application/json`

| Parameter | Type    | Description                          | 
|-----------|---------|--------------------------------------|
| `id`      | integer | notify url id, use it to create rule |

```json
{
  "id": 13
}
```


**Error codes** see full specification [here ](../errors.md)

***

### [GET]/v1/monitoring/user_rule
Get user notify settings

**Example**

```
https://my.tonguard.org/api/v1/monitoring/user_rule
```
**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter    | Type    | Description                       | 
|--------------|---------|-----------------------------------|
| `count`      | integer | total settings found              |
| `id`         | integer | setting id, use it to create rule | 
| `notify_url` | string  | notify url                        | 
| `created_dt` | string  | '%d/%m/%Y, %H:%M:%S GMT' format   | 
| `email`      | string  | email                             |


```json
{
  "count": 2,
  "notify_settings": [
    {
      "id": 13,
      "notify_url": "https://example.com/v1/receive",
      "email": "example@mail.com",
      "created_dt": "2025-01-21T11:38:11.296878+00:00"
    },
    {
      "id": 14,
      "notify_url": "https://example.com/v1/receive2",
      "email": "example@mail.com",
      "created_dt": "2025-01-21T12:59:02.630147+00:00"
    }
  ]
}
```

**Error codes** see full specification [here ](../errors.md)


***

### [POST]/v1/monitoring/user_rule

Set up alerting configurations

**Content-Type** `application/json`

**Example**
```
https://my.tonguard.org//v1/monitoring/user_rule?notify_url=URL&email=EMAIL,EMAIL1
```

**Request body**

| Parameter                      | Type    | Description                                                                                                                                                                                                                 | Required |
|--------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| `monitoring_notify_setting_id` | integer | id from [POST/v1/monitoring/user_rule](#postv1monitoringnotify_setting) or [GET/v1/monitoring/user_rule](#getv1monitoringuser_rule)                                                                                         | yes      |
| `monitoring_rule_info_key`     | string  | choose rule type: <br/> `rescreening`: re-screening addresses, <br/> `risk_category`: tracking increases in risk score, <br/> `risk_threshold`:tracking changes in risk categories                                          | yes      |
| `custom_parameter`             | string  | depend on `monitoring_rule_info_key`: <br/> `rescreening`: {"interval": hours}, <br/> `risk_category`: {"risk_categories": [[risk category ](../dictionary.md) ]}, <br/> `risk_threshold`:{"risk_threshold": integer <=100} | yes      |
| `rule_name_custom`             | string  | name of alert configuration                                                                                                                                                                                                 | yes      |
| `comment`                      | string  | comment                                                                                                                                                                                                                     | no       |

```json
{
  "monitoring_notify_setting_id": 13,
  "monitoring_rule_info_key": "risk_threshold",
  "custom_parameter": {
    "risk_threshold": 67
  },
  "rule_name_custom": "my rule",
  "comment": "string"
}
```

**Responses**

`201` **Successful Response**

**Content-Type** `application/json`

```
{}
```

**Error codes** see full specification [here ](../errors.md)


***
### [GET]/v1/monitoring/user_rule
Get user rules

```
https://my.tonguard.org/api/v1/monitoring/user_rule?limit=INTEGER&offset=INTEGER
```

**Parameters(Query)**

| Parameter | Type    | Description                                     | Required |
|-----------|---------|-------------------------------------------------|----------|
| `limit`   | string  | limit of records to return, default: 10         | no       |
| `offset`  | integer | offset of records to return, Default value is 0 | no       |

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter                      | Type    | Description                     | 
|--------------------------------|---------|---------------------------------|
| `count`                        | integer | total rules found               |
| `id`                           | integer | rule id                         | 
| `monitoring_notify_setting_id` | integer | notify id                       | 
| `monitoring_rule_info_key`     | string  | rule type                       | 
| `custom_parameter`             | string  | rule configuration              |
| `addresses_count`              | integer | number of addresses using rule  |
| `comment`                      | string  | comment                         |
| `rule_name`                    | string  | rule name                       |
| `created_dt`                   | string  | '%d/%m/%Y, %H:%M:%S GMT' format |
| `is_enabled`                   | boolean | active or not                   |

```json
{
  "count": integer,
  "user_rules": {
    "id": integer
    "monitoring_notify_setting_id": integer,
    "monitoring_rule_info_key": "string",
    "custom_parameter": {
    }
    "addresses_count": integer,
    "rule_name": "string",
    "comment": "string",
    "created_dt": "string",
    "is_enabled": boolean
  }
}
```
**Error codes** see full specification [here ](../errors.md)

***

### [DELETE]/v1/monitoring/user_rule
Delete user rule

**Content-Type** `application/json`

**Request body JSON**

| Parameter                 | Type    | Description                | Required |
|---------------------------|---------|----------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id ypu want to delete | yes      |

```json
{
  "monitoring_user_rule_id": integer
}
```

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

```
{}
```

**Error codes** see full specification [here ](../errors.md)

***

### [POST]/v1/monitoring/address_under_rule
Attach a user rule to a wallet

**Content-Type** `application/json`

**Request body JSON**

| Parameter                 | Type    | Description                          | Required |
|---------------------------|---------|--------------------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id you want to attach to wallet | yes      |
| `address`                 | string  | TON wallet address                   | yes      |
| `comment`                 | string  | comment                              | no       |

```json
{
  "monitoring_user_rule_id": integer,
  "address": "string",
  "comment": "string"
}
```
**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

```
{}
```

**Error codes** see full specification [here ](../errors.md)

***

### [GET]/v1/monitoring/address_under_rule
Get addresses under monitoring

**Parameters(Query)**

| Parameter       | Type    | Description                                            | Required |
|-----------------|---------|--------------------------------------------------------|----------|
| `address`       | string  | TON wallet address in any base64 form (urlsafe or not) | no       |
| `user_rules`    | integer | user rule ids                                          | no       |
| `date_from`     | string  | date from for filter, "DD.MM.YYYY" format              | no       |
| `date_to`       | string  | date to for filter, "DD.MM.YYYY" format                | no       |
| `limit`         | string  | limit of records to return                             | no       |
| `offset`        | integer | offset of records to return                            | no       |

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter                | Type    | Description                                     | 
|--------------------------|---------|-------------------------------------------------|
| `count`                  | integer | total addresses found                           |          
| `address_under_rule_ids` | integer | rule id                                         |          
| `address_non_bounce`     | string  | TON wallet address                              |          
| `rule_names`             | string  | rule name                                       |         
| `first_added_dt`         | string  | date added,'%d/%m/%Y, %H:%M:%S GMT' format      |          
| `risk_score`             | integer | risk score                                      |          
| `fraud_level`            | string  | fraud level                                     |          
| `last_alert_dt`          | string  | last alert date,'%d/%m/%Y, %H:%M:%S GMT' format |          


```json
{
  "count": integer,
  "addresses": {
    "address_under_rule_ids": integer,
    "address_non_bounce": "string",
    "rule_names": "string",
    "first_added_dt": "string",
    "risk_score": integer,
    "fraud_level": "string",
    "last_alert_dt": "string"
  }
}
```

**Error codes** see full specification [here ](../errors.md)


***
### [DELETE]/v1/monitoring/address_under_rule

Delete address from monitoring

**Content-Type** `application/json`

**Request body JSON**

| Parameter                 | Type    | Description                | Required |
|---------------------------|---------|----------------------------|----------|
| `monitoring_user_rule_id` | integer | rule id you want to delete | yes      |


```json
{
  "monitoring_address_under_rule_id": integer
}
```

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

```
{}
```

**Error codes** see full specification [here ](../errors.md)

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
