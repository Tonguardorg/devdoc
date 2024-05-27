# API

> Version 1.1.2

Provides risk score and risk level estimation for TON blockchain addresses and etc  🚀

##  Authentication

First you retrieve a new JWT token using login/password authentication. After that you can use it to access other resources.

**JWT token example**

`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoiYWNjZXNzX3Rva2VuIiwiZXhwIjoxNjY3ODEwMjI4LCJpYXQiOjE2Njc4MDY2MjgsInN1YiI6IjIiLCJzY29wZXMiOlsiMiJdfQ.dbPU2vVx48bZejzElrfQS-Pa5B5CmzhL2F19X0l4EAA`

**Decoded header**:

```
{
  "alg": "HS256",
  "typ": "JWT"
}
```

**Decoded payload**:

```
{
  "type": "access_token",
  "exp": 1667810228,
  "iat": 1667806628,
  "sub": "2",
  "scopes": [
    "2"
  ]
}
```

The URL examples throughout this documentation use token as a placeholder. For these examples to work, you **need** to substitute the value with your **own** access token.

## Status codes

This API uses HTTP status codes to communicate with the API consumer.

`200 OK` - Response to a successful GET, PUT, PATCH or DELETE.

`201 Created` - Response to a POST that results in a creation.

`400 Bad Request` - Malformed request; request body validation errors.

`401 Unauthorized` - When no or invalid authentication details are provided.

`403 Forbidden` - When authentication succeeded but authenticated user doesn't have access to the resource.

`428 Requests Limit Reached` - When user reached his predefined maximum amount of requests

`429 Rate Limit Exceeded` - When calls to certain endpoint for user are higher than predefined limits

`500 Server Error` - Something went wrong on the API end.

`501 Not Implemented` - The server either does not recognize the request method, or it lacks the ability to fulfill the request.

# List of available endpoints


## Path Table

| Method | Path | Description |
| --- | --- | --- |
| GET | [/v1/reports/wallet_risk_score](#getv1reportswallet_risk_score) | Returns address risk score, risk level and query related info. Each query exceeds remaining number of queries for the user. |
| GET | [/v1/reports/risk_scoring_history](#getv1reportsrisk_scoring_history) | Returns risk scoring history for a specific user and address. |
| GET | [/v1/reports/risk_scoring_report](#getv1reportsrisk_scoring_report) | Return risk scoring report for a specific uuid. |
| POST | [/v1/claims/report_wallets](#postv1claimsreport_wallets) | Create Wallet Claim |
| GET | [/v1/claims/my](#getv1claimsmy) | Get Claims |
| DELETE | [/v1/claims/delete](#deletev1claimsdelete) | Delete Claims |
| GET | [/v1/service/download/{data_name}.csv](#getv1servicedownloaddata_namecsv) | Download data as a file. |
| GET | [/v1/monitoring/wallet_list](#getv1monitoringwallet_list) | Get user monitoring wallets |
| GET | [/v1/monitoring/notify_setting](#getv1monitoringnotify_setting) | Get user notification urls |
| POST | [/v1/monitoring/notify_setting](#postv1monitoringnotify_setting) | Add user notification url |
| GET | [/v1/monitoring/user_rule](#getv1monitoringuser_rule) | Get user rules |
| POST | [/v1/monitoring/user_rule](#postv1monitoringuser_rule) | Add user rule |
| GET | [/v1/monitoring/address_under_rule](#getv1monitoringaddress_under_rule) | Get addresses under monitoring |
| POST | [/v1/monitoring/address_under_rule](#postv1monitoringaddress_under_rule) | Attach a user rule to a wallet |
| DELETE | [/v1/monitoring/address_under_rule](#deletev1monitoringaddress_under_rule) | Delete address from monitoring |
| POST | [/v1/auth/login](#postv1authlogin) | User authentication. Does not exceed remaining number of queries for the user |

## Reference Table

| Name | Path | Description |
| --- | --- | --- |
| AddressUnderRule | [#/components/schemas/AddressUnderRule](#componentsschemasaddressunderrule) |  |
| AddressesUnderRule | [#/components/schemas/AddressesUnderRule](#componentsschemasaddressesunderrule) |  |
| ApiError | [#/components/schemas/ApiError](#componentsschemasapierror) |  |
| AuthRequest | [#/components/schemas/AuthRequest](#componentsschemasauthrequest) |  |
| ClaimWalletTag | [#/components/schemas/ClaimWalletTag](#componentsschemasclaimwallettag) |  |
| ClaimedWallet | [#/components/schemas/ClaimedWallet](#componentsschemasclaimedwallet) |  |
| CreateAddressUnderRule | [#/components/schemas/CreateAddressUnderRule](#componentsschemascreateaddressunderrule) |  |
| CreateUserRule | [#/components/schemas/CreateUserRule](#componentsschemascreateuserrule) |  |
| DeleteAddressUnderRule | [#/components/schemas/DeleteAddressUnderRule](#componentsschemasdeleteaddressunderrule) |  |
| HTTPValidationError | [#/components/schemas/HTTPValidationError](#componentsschemashttpvalidationerror) |  |
| MonitoringWallet | [#/components/schemas/MonitoringWallet](#componentsschemasmonitoringwallet) |  |
| MonitoringWallets | [#/components/schemas/MonitoringWallets](#componentsschemasmonitoringwallets) |  |
| NotifySetting | [#/components/schemas/NotifySetting](#componentsschemasnotifysetting) |  |
| NotifySettings | [#/components/schemas/NotifySettings](#componentsschemasnotifysettings) |  |
| RiskScoreHistoryResponse | [#/components/schemas/RiskScoreHistoryResponse](#componentsschemasriskscorehistoryresponse) |  |
| RiskScoringMixin | [#/components/schemas/RiskScoringMixin](#componentsschemasriskscoringmixin) |  |
| RiskScoringReportResponse | [#/components/schemas/RiskScoringReportResponse](#componentsschemasriskscoringreportresponse) |  |
| RiskyConnection | [#/components/schemas/RiskyConnection](#componentsschemasriskyconnection) |  |
| TokenPayload | [#/components/schemas/TokenPayload](#componentsschemastokenpayload) |  |
| UserClaim | [#/components/schemas/UserClaim](#componentsschemasuserclaim) |  |
| UserClaims | [#/components/schemas/UserClaims](#componentsschemasuserclaims) |  |
| UserRule | [#/components/schemas/UserRule](#componentsschemasuserrule) |  |
| UserRules | [#/components/schemas/UserRules](#componentsschemasuserrules) |  |
| ValidationError | [#/components/schemas/ValidationError](#componentsschemasvalidationerror) |  |
| WalletInfo | [#/components/schemas/WalletInfo](#componentsschemaswalletinfo) |  |
| WalletRiskScore | [#/components/schemas/WalletRiskScore](#componentsschemaswalletriskscore) |  |
| WalletTag | [#/components/schemas/WalletTag](#componentsschemaswallettag) |  |

## Path Details

***

### [GET]/v1/reports/wallet_risk_score

- Summary  
Returns address risk score, risk level and query related info. Each query exceeds remaining number of queries for the user.

#### Parameters(Query)

```ts
// TON wallet address in any base64 form (urlsafe or not).
address?: string
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Risk score, risk level and query related info.

`application/json`

```ts
{
  version: string
  address: string
  address_raw?: string //default: unknown
  address_non_bounceable?: string //default: unknown
  address_type?: string //default: unknown
  risk_score?: integer
  fraud_level?: enum[high, medium, low, lowest, unknown] //default: lowest
  risk_category?: string[]
  total_days?: integer
  first_transaction_time?: string
  last_transaction_time?: string
  total_balance?: number
  total_transactions_amount?: number
  total_transactions_count?: integer
  total_counterparts_count?: integer
  total_sent_transactions_amount?: number
  total_sent_transactions_count?: integer
  total_sent_counterparts_count?: integer
  total_received_transactions_amount?: number
  total_received_transactions_count?: integer
  total_received_counterparts_count?: integer
  gambling_message_count?: integer
  spam_message_count?: integer
  scam_message_count?: integer
  bridge_wallet_status?: string[]
  exchange_wallet_status?: string[]
  stacking_wallet_status?: string[]
  miner_wallet_status?: string[]
  nft_wallet_status?: string[]
}
```

- 400 Bad Request

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 401 Unauthorized

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 402 Payment Required

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 403 Forbidden

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

- 429 Too Many Requests

`application/json`

```ts
{
  code: integer
  detail: string
}
```

***

### [GET]/v1/reports/risk_scoring_history

- Summary  
Returns risk scoring history for a specific user and address.

#### Parameters(Query)

```ts
// TON wallet address in any base64 form (urlsafe or not).
address?: string
```

```ts
// Limit of records to return.
limit?: integer //default: 10
```

```ts
// Offset of records to return.
offset?: integer
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Risk scoring history successfully retrieved.

`application/json`

```ts
{
  history: {
    version: string
    uuid: string
    created_dt?: string
    address: string
    address_type?: string //default: unknown
    address_raw?: string
    address_non_bounceable?: string
    fraud_level?: string
    risk_score?: integer
    info_category?: integer[]
    risk_category?: integer[]
    risky_connections: {
    }[]
    first_transaction_time?: string
    last_transaction_time?: string
    total_balance?: number
    total_days?: number
    total_transactions_amount?: number
    total_sent_transactions_amount?: number
    total_received_transactions_amount?: number
    total_counterparts_count?: integer
    total_sent_counterparts_count?: integer
    total_received_counterparts_count?: integer
    total_transactions_count?: integer
    total_sent_transactions_count?: integer
    total_received_transactions_count?: integer
    bridge_wallet_status?: string[]
    exchange_wallet_status?: string[]
    stacking_wallet_status?: string[]
    miner_wallet_status?: string[]
    nft_wallet_status?: string[]
    gambling_message_count?: integer
    spam_message_count?: integer
    scam_message_count?: integer
  }[]
  count: integer
}
```

- 400 Bad Request

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 404 Not Found

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/reports/risk_scoring_report

- Summary  
Return risk scoring report for a specific uuid.

#### Parameters(Query)

```ts
// UUID of scoring report.
uuid: string
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Risk scoring report succesfully retrieved.

`application/json`

```ts
{
  report: {
    version: string
    uuid: string
    created_dt?: string
    address: string
    address_type?: string //default: unknown
    address_raw?: string
    address_non_bounceable?: string
    fraud_level?: string
    risk_score?: integer
    info_category?: integer[]
    risk_category?: integer[]
    risky_connections: {
    }[]
    first_transaction_time?: string
    last_transaction_time?: string
    total_balance?: number
    total_days?: number
    total_transactions_amount?: number
    total_sent_transactions_amount?: number
    total_received_transactions_amount?: number
    total_counterparts_count?: integer
    total_sent_counterparts_count?: integer
    total_received_counterparts_count?: integer
    total_transactions_count?: integer
    total_sent_transactions_count?: integer
    total_received_transactions_count?: integer
    bridge_wallet_status?: string[]
    exchange_wallet_status?: string[]
    stacking_wallet_status?: string[]
    miner_wallet_status?: string[]
    nft_wallet_status?: string[]
    gambling_message_count?: integer
    spam_message_count?: integer
    scam_message_count?: integer
  }
}
```

- 400 Bad Request

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 404 Not Found

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [POST]/v1/claims/report_wallets

- Summary  
Create Wallet Claim

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
{
  wallet_address: string
  tags?: integer[]
  comment?: string
  transaction_link?: string
}[]
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{
  uuid: string
  address: string
  created_dt: string
}[]
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/claims/my

- Summary  
Get Claims

#### Parameters(Query)

```ts
// address
address?: string
```

```ts
// Date from
date_from?: string
```

```ts
// Date to
date_to?: string
```

```ts
// tags to filter
tags?: string
```

```ts
// Limit to paginate created wallets claims. Default value is 300.
limit?: integer //default: 300
```

```ts
// Offset to paginate over created wallets claims. Default value is 0.
offset?: integer
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{
  count: integer
  claims: {
    uuid: string
    address: string
    created_dt: string
    transaction_link?: string
    comment?: string
    tags: Partial({
       code: integer
       name: string
       type: enum[INFO, RISK]
       description: string
     }[]) & Partial(integer[])
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [DELETE]/v1/claims/delete

- Summary  
Delete Claims

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
string[]
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/service/download/{data_name}.csv

- Summary  
Download data as a file.

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Data successfully downloaded.

`application/json`

```ts
{
  "title": "Response Download Data"
}
```

- 400 Bad Request

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 404 Not Found

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/monitoring/wallet_list

- Summary  
Get user monitoring wallets

#### Parameters(Query)

```ts
// Limit to paginate. Default value is 10.
limit?: integer //default: 10
```

```ts
// Offset to paginate over. Default value is 0.
offset?: integer
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{
  count: integer
  wallets: {
    id: integer
    address: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/monitoring/notify_setting

- Summary  
Get user notification urls

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{
  count: integer
  notify_settings: {
    notify_url: string
    created_dt: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [POST]/v1/monitoring/notify_setting

- Summary  
Add user notification url

#### Parameters(Query)

```ts
// The URL to send notifications to.
notify_url: string
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/monitoring/user_rule

- Summary  
Get user rules

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{
  count: integer
  user_rules: {
    id: integer
    monitoring_notify_setting_id: integer
    monitoring_rule_info_id: integer
    custom_parameter: {
    }
    rule_name?: string
    comment?: string
    created_dt?: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [POST]/v1/monitoring/user_rule

- Summary  
Add user rule

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
{
  monitoring_notify_setting_id: integer
  monitoring_rule_info_id: integer
  custom_parameter: {
  }
  rule_name_custom?: string
  comment?: string
}
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/monitoring/address_under_rule

- Summary  
Get addresses under monitoring

#### Parameters(Query)

```ts
// address
address?: string
```

```ts
// Date from
date_from?: string
```

```ts
// Date to
date_to?: string
```

```ts
// user rules to filter
user_rules?: string
```

```ts
// Limit to paginate. Default value is 10.
limit?: integer //default: 10
```

```ts
// Offset to paginate over. Default value is 0.
offset?: integer
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{
  count: integer
  addresses: {
    created_dt: string
    monitoring_user_rule_name: string
    monitoring_address_under_rule_id: integer
    address: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [POST]/v1/monitoring/address_under_rule

- Summary  
Attach a user rule to a wallet

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
{
  monitoring_user_rule_id: integer
  address: string
  comment?: string
}
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [DELETE]/v1/monitoring/address_under_rule

- Summary  
Delete address from monitoring

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
{
  monitoring_address_under_rule_id: integer
}
```

#### Responses

- 200 Successful Response

`application/json`

```ts
{}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [POST]/v1/auth/login

- Summary  
User authentication. Does not exceed remaining number of queries for the user

- Description  
Get the JWT for a user with data from request form body.  
Returns next structure:  
   - **token**: string  
   - **token_type**: "JWT"  
   - **expiry**: string, token expiry time in '%d/%m/%Y, %H:%M:%S GMT' format  
   - **queries_count_left**: int, the remaining number of queries for the user

#### RequestBody

- application/json

```ts
{
  // E-mail address of user.
  username: string
  password?: string //default: ToNloveR2000
}
```

#### Responses

- 200 Returns JWT token related info and and remaining number of queries

`application/json`

```ts
{
  token?: string
  token_type?: string //default: JWT
  expiry: string
  queries_count_left: integer
}
```

- 401 Unauthorized

`application/json`

```ts
{
  code: integer
  detail: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

- 429 Too Many Requests

`application/json`

```ts
{
  code: integer
  detail: string
}
```

## References

### #/components/schemas/AddressUnderRule

```ts
{
  created_dt: string
  monitoring_user_rule_name: string
  monitoring_address_under_rule_id: integer
  address: string
}
```

### #/components/schemas/AddressesUnderRule

```ts
{
  count: integer
  addresses: {
    created_dt: string
    monitoring_user_rule_name: string
    monitoring_address_under_rule_id: integer
    address: string
  }[]
}
```

### #/components/schemas/ApiError

```ts
{
  code: integer
  detail: string
}
```

### #/components/schemas/AuthRequest

```ts
{
  // E-mail address of user.
  username: string
  password?: string //default: ToNloveR2000
}
```

### #/components/schemas/ClaimWalletTag

```ts
{
  code: integer
  name: string
  type: enum[INFO, RISK]
  description: string
}
```

### #/components/schemas/ClaimedWallet

```ts
{
  uuid: string
  address: string
  created_dt: string
}
```

### #/components/schemas/CreateAddressUnderRule

```ts
{
  monitoring_user_rule_id: integer
  address: string
  comment?: string
}
```

### #/components/schemas/CreateUserRule

```ts
{
  monitoring_notify_setting_id: integer
  monitoring_rule_info_id: integer
  custom_parameter: {
  }
  rule_name_custom?: string
  comment?: string
}
```

### #/components/schemas/DeleteAddressUnderRule

```ts
{
  monitoring_address_under_rule_id: integer
}
```

### #/components/schemas/HTTPValidationError

```ts
{
  detail: {
    loc?: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

### #/components/schemas/MonitoringWallet

```ts
{
  id: integer
  address: string
}
```

### #/components/schemas/MonitoringWallets

```ts
{
  count: integer
  wallets: {
    id: integer
    address: string
  }[]
}
```

### #/components/schemas/NotifySetting

```ts
{
  notify_url: string
  created_dt: string
}
```

### #/components/schemas/NotifySettings

```ts
{
  count: integer
  notify_settings: {
    notify_url: string
    created_dt: string
  }[]
}
```

### #/components/schemas/RiskScoreHistoryResponse

```ts
{
  history: {
    version: string
    uuid: string
    created_dt?: string
    address: string
    address_type?: string //default: unknown
    address_raw?: string
    address_non_bounceable?: string
    fraud_level?: string
    risk_score?: integer
    info_category?: integer[]
    risk_category?: integer[]
    risky_connections: {
    }[]
    first_transaction_time?: string
    last_transaction_time?: string
    total_balance?: number
    total_days?: number
    total_transactions_amount?: number
    total_sent_transactions_amount?: number
    total_received_transactions_amount?: number
    total_counterparts_count?: integer
    total_sent_counterparts_count?: integer
    total_received_counterparts_count?: integer
    total_transactions_count?: integer
    total_sent_transactions_count?: integer
    total_received_transactions_count?: integer
    bridge_wallet_status?: string[]
    exchange_wallet_status?: string[]
    stacking_wallet_status?: string[]
    miner_wallet_status?: string[]
    nft_wallet_status?: string[]
    gambling_message_count?: integer
    spam_message_count?: integer
    scam_message_count?: integer
  }[]
  count: integer
}
```

### #/components/schemas/RiskScoringMixin

```ts
{
  version: string
  uuid: string
  created_dt?: string
  address: string
  address_type?: string //default: unknown
  address_raw?: string
  address_non_bounceable?: string
  fraud_level?: string
  risk_score?: integer
  info_category?: integer[]
  risk_category?: integer[]
  risky_connections: {
  }[]
  first_transaction_time?: string
  last_transaction_time?: string
  total_balance?: number
  total_days?: number
  total_transactions_amount?: number
  total_sent_transactions_amount?: number
  total_received_transactions_amount?: number
  total_counterparts_count?: integer
  total_sent_counterparts_count?: integer
  total_received_counterparts_count?: integer
  total_transactions_count?: integer
  total_sent_transactions_count?: integer
  total_received_transactions_count?: integer
  bridge_wallet_status?: string[]
  exchange_wallet_status?: string[]
  stacking_wallet_status?: string[]
  miner_wallet_status?: string[]
  nft_wallet_status?: string[]
  gambling_message_count?: integer
  spam_message_count?: integer
  scam_message_count?: integer
}
```

### #/components/schemas/RiskScoringReportResponse

```ts
{
  report: {
    version: string
    uuid: string
    created_dt?: string
    address: string
    address_type?: string //default: unknown
    address_raw?: string
    address_non_bounceable?: string
    fraud_level?: string
    risk_score?: integer
    info_category?: integer[]
    risk_category?: integer[]
    risky_connections: {
    }[]
    first_transaction_time?: string
    last_transaction_time?: string
    total_balance?: number
    total_days?: number
    total_transactions_amount?: number
    total_sent_transactions_amount?: number
    total_received_transactions_amount?: number
    total_counterparts_count?: integer
    total_sent_counterparts_count?: integer
    total_received_counterparts_count?: integer
    total_transactions_count?: integer
    total_sent_transactions_count?: integer
    total_received_transactions_count?: integer
    bridge_wallet_status?: string[]
    exchange_wallet_status?: string[]
    stacking_wallet_status?: string[]
    miner_wallet_status?: string[]
    nft_wallet_status?: string[]
    gambling_message_count?: integer
    spam_message_count?: integer
    scam_message_count?: integer
  }
}
```

### #/components/schemas/RiskyConnection

```ts
{
  last_transaction_time?: string
  wallet_address?: string
  neighbor_wallet_address?: string
  total_income?: integer
  total_outcome?: integer
  risk_score?: integer
  fraud_level?: string
  total_transactions_count?: integer
  total_transactions_amount?: string
  tags: {
    code: integer
    name: string
    type: string
    description: string
  }[]
}
```

### #/components/schemas/TokenPayload

```ts
{
  token?: string
  token_type?: string //default: JWT
  expiry: string
  queries_count_left: integer
}
```

### #/components/schemas/UserClaim

```ts
{
  uuid: string
  address: string
  created_dt: string
  transaction_link?: string
  comment?: string
  tags: Partial({
     code: integer
     name: string
     type: enum[INFO, RISK]
     description: string
   }[]) & Partial(integer[])
}
```

### #/components/schemas/UserClaims

```ts
{
  count: integer
  claims: {
    uuid: string
    address: string
    created_dt: string
    transaction_link?: string
    comment?: string
    tags: Partial({
       code: integer
       name: string
       type: enum[INFO, RISK]
       description: string
     }[]) & Partial(integer[])
  }[]
}
```

### #/components/schemas/UserRule

```ts
{
  id: integer
  monitoring_notify_setting_id: integer
  monitoring_rule_info_id: integer
  custom_parameter: {
  }
  rule_name?: string
  comment?: string
  created_dt?: string
}
```

### #/components/schemas/UserRules

```ts
{
  count: integer
  user_rules: {
    id: integer
    monitoring_notify_setting_id: integer
    monitoring_rule_info_id: integer
    custom_parameter: {
    }
    rule_name?: string
    comment?: string
    created_dt?: string
  }[]
}
```

### #/components/schemas/ValidationError

```ts
{
  loc?: Partial(string) & Partial(integer)[]
  msg: string
  type: string
}
```

### #/components/schemas/WalletInfo

```ts
{
  wallet_address: string
  tags?: integer[]
  comment?: string
  transaction_link?: string
}
```

### #/components/schemas/WalletRiskScore

```ts
{
  version: string
  address: string
  address_type?: string //default: unknown
  address_raw?: string //default: unknown
  address_non_bounceable?: string //default: unknown
  fraud_level?: string
  risk_score?: integer
  risk_category: {
    code: integer
    name: string
    type: string
    description: string
  }[]
  info_category: {
    code: integer
    name: string
    type: string
    description: string
  }[]
  risky_connections: {
    last_transaction_time?: string
    wallet_address?: string
    neighbor_wallet_address?: string
    total_income?: integer
    total_outcome?: integer
    risk_score?: integer
    fraud_level?: string
    total_transactions_count?: integer
    total_transactions_amount?: string
    tags: {
      code: integer
      name: string
      type: string
      description: string
    }[]
  }[]
  total_days?: integer
  first_transaction_time?: string
  last_transaction_time?: string
  total_balance?: number
  total_transactions_amount?: number
  total_transactions_count?: integer
  total_counterparts_count?: integer
  total_sent_transactions_amount?: number
  total_sent_transactions_count?: number
  total_sent_counterparts_count?: number
  total_received_transactions_amount?: number
  total_received_transactions_count?: number
  total_received_counterparts_count?: number
  gambling_message_count?: integer
  spam_message_count?: integer
  scam_message_count?: integer
  nft_wallet_status?: string[]
  miner_wallet_status?: string[]
  bridge_wallet_status?: string[]
  exchange_wallet_status?: string[]
  stacking_wallet_status?: string[]
}
```

### #/components/schemas/WalletTag

```ts
{
  code: integer
  name: string
  type: string
  description: string
}
```
