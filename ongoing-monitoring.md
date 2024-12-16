# Setting up ongoing monitoring of TON addresses' risk score via API

## Purpose

The ongoing monitoring feature allows Tonguard users to receive API notifications when some condition regarding a specific address is met 
(e.g. its risk score exceeded a certain threshold)

## Endpoints list

https://api.tonguard.org/

## Integration

To configure the monitoring follow these steps:

1. Get access token via login

```
POST /v1/auth/login
{
  "username": "johnsmith@tonguard.org",
  "password": "ToNloveR2000"
}
```

2. Using the access token add the desired URL and emai to receive notifications

```
POST /v1/monitoring/notify_setting?notify_url=https%3A%2F%2Fexample.com%2Fv1%2Freceive
&email=example%40mail.com
```

3. Using the access token get the list of your available notification settings

```
GET /v1/monitoring/notify_setting
```

You will receive the list like this

```
{
  "count": 1,
  "notify_settings": [
    {
      "id": 8,
      "notify_url": "https://example.com/v1/receive",
      "email": "example@mail.com",
      "created_dt": "2024-12-16T11:27:02.242056+00:00"
    }
  ]
}
```

Remember the `id` of the notify_url you want to use

4. Using the access token create your monitoring rule. For key `monitoring_notify_setting_id` use the id received in 3.
Yet only risk score value is available as a base rule, so specify key `monitoring_rule_info_key` to be `risk_threshold`.
`rule_name_custom` and `comment` are optional and can be skipped (not added to JSON body)

```
POST /v1/monitoring/user_rule
{
  "monitoring_notify_setting_id": 8,
  "monitoring_rule_info_key": risk_threshold,
  "custom_parameter": {},
  "rule_name_custom": "Your custom name",
  "comment": "Your comment"
}
```

The default trigger risk score value is `80`. If you want to have it different, specify `custom_parameter` from 0 to 100 like so

```"custom_parameter": {"risk_threshold": 100}```

Note that you can add several rules with the same notify URL, but different parameters - or vice versa.

5. Using the access token get the list of your available rules

```
GET /v1/monitoring/user_rule
```

You will receive the list like this

```
{
  "count": 1,
  "user_rules": [
    {
      "id": 4,
      "monitoring_notify_setting_id": 8,
      "monitoring_rule_info_key": "risk_threshold",
      "custom_parameter": null,
      "rule_name": "string",
      "comment": "string",
      "created_dt": "2024-12-16T11:45:49.142165+00:00"
    }
  ]
}
```

Remember the `id` of the rule you want to use

6. Finally, add the desired address under monitoring. Yet you can add only 1 address per request. 
Using the access token triggers the endpoint below. You can pass `address` in EQ or UQ format. 
`comment` is optional and can be skipped. For `monitoring_user_rule_id` use the id received in 5.

```
POST /v1/monitoring/address_under_rule
{
  "monitoring_user_rule_id": 4,
  "address": "UQB879Q7IRXY-uLWBX9FomGCR0uxmyNjqqNgeqWYdk1Yx9d6",
  "comment": "string"
}
```

7. You can see the list of your monitored addresses via the endpoint below. 
It also allows for filtration using parameters `address, date_from, date_to, user_rules`

```
GET /v1/monitoring/address_under_rule
```

You will receive the list like this

```
{
  "count": 1,
  "addresses": [
    {
      "created_dt": "2024-05-22T12:35:11.058433+00:00",
      "monitoring_user_rule_name": "Risk threshold",
      "monitoring_address_under_rule_id": 1,
      "address": "UQB879Q7IRXY-uLWBX9FomGCR0uxmyNjqqNgeqWYdk1Yx9d6"
    }
  ]
}
```
```{
  "count": 1,
  "addresses": [
    {
      "address_under_rule_ids": [
        1
      ],
      "address_non_bounce": "UQDrLq-X6jKZNHAScgghh0h1iog3StK71zn8dcmrOj8jPTmF",
      "rule_names": [
        "string"
      ],
      "first_added_dt": "2024-12-16T11:48:31.368888+00:00",
      "risk_score": null,
      "fraud_level": null,
      "last_alert_dt": null
    }
  ]
}
```

8. You may want to exclude some address from monitoring. 
To do so, trigger the following endpoint passing `address_under_rule_ids` from 7.

```
DELETE /v1/monitoring/address_under_rule
{
  "monitoring_address_under_rule_id": 1
}
```
