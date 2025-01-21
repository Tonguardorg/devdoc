## Top holders
Returns list of 100 top USDT holders

### [GET]/v1/top_holders/top_usdt_holders

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
**Example**
```
https://my.tonguard.org/top-accounts
```

**Responses**

`200` **Successful Response**

**Content-Type** `application/json`

| Parameter      | Type   | Description                               | 
|----------------|--------|-------------------------------------------|
| `address`      | string | TON wallet address                        | 
| `owner`        | string | owner's public name <br/>default: unknown | 
| `usdt_balance` | number | USDT jettons balance                      | 

**Error codes** see full specification [here ](../errors.md)

***