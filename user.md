## User
Get user info

### [GET]/v1/users/me

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
**Example**
```
https://api.tonguard.org/v1/users/me
```

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`


| Parameter            | Type    | Description                                      | 
|----------------------|---------|--------------------------------------------------|
| `tariff_start_date`  | string  | tariff start day                                 | 
| `tariff_end_date`    | string  | tariff end day                                   | 
| `request_limit`      | integer | total number of risk scoring requests for user   | 
| `executed_requests`  | integer | number of risk scoring requests made by the user |
| `remaining_requests` | integer | remaining number of risk scoring requests        |
| `number_of_claims`   | integer | claims count                                     |


**Error codes** see full specification [here ](../errors.md)

***