# API

> Version 2.0.0

Provides risk score and risk level estimation for TON blockchain addresses and etc  🚀

## Endpoints list

https://api.tonguard.org/

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
| GET | [/v1/reports/risk_scoring_report_{uuid}.pdf](#getv1reportsrisk_scoring_report_uuidpdf) | Download report as a pdf file. |
| GET | [/v1/reports/risk_history.csv](#getv1reportsrisk_historycsv) | Returns risk scoring history in a csv file. |
| POST | [/v1/claims/report_wallets](#postv1claimsreport_wallets) | Create Wallet Claim |
| PUT | [/v1/claims/update_wallet_claim/{uuid}](#putv1claimsupdate_wallet_claimuuid) | Update Wallet Claim |
| GET | [/v1/claims/my](#getv1claimsmy) | Get Claims |
| DELETE | [/v1/claims/delete](#deletev1claimsdelete) | Delete Claims |
| GET | [/v1/claims/wallets_tags](#getv1claimswallets_tags) | Wallets Tags |
| GET | [/v1/claims/claim_history.csv](#getv1claimsclaim_historycsv) | Returns claims history in a csv file. |
| GET | [/v1/visualizer/get_transactions_graph](#getv1visualizerget_transactions_graph) | Visualizer |
| GET | [/v1/visualizer/get_last_transactions_graph](#getv1visualizerget_last_transactions_graph) | Last Transactions Graph |
| PUT | [/v1/visualizer/update_transactions_graph](#putv1visualizerupdate_transactions_graph) | Update Transactions Graph |
| GET | [/v1/monitoring/wallet_list](#getv1monitoringwallet_list) | Get user monitoring wallets |
| GET | [/v1/monitoring/notify_setting](#getv1monitoringnotify_setting) | Get user notification urls |
| POST | [/v1/monitoring/notify_setting](#postv1monitoringnotify_setting) | Add user notification url |
| GET | [/v1/monitoring/user_rule](#getv1monitoringuser_rule) | Get user rules |
| POST | [/v1/monitoring/user_rule](#postv1monitoringuser_rule) | Add user rule |
| GET | [/v1/monitoring/address_under_rule](#getv1monitoringaddress_under_rule) | Get addresses under monitoring |
| POST | [/v1/monitoring/address_under_rule](#postv1monitoringaddress_under_rule) | Attach a user rule to a wallet |
| DELETE | [/v1/monitoring/address_under_rule](#deletev1monitoringaddress_under_rule) | Delete address from monitoring |
| GET | [/v1/monitoring/user_rule_statistic](#getv1monitoringuser_rule_statistic) | Get User Rule Statistic |
| GET | [/v1/whitelists/whitelist.csv](#getv1whitelistswhitelistcsv) | Download whitelist as a file. |
| POST | [/v1/whitelists/whitelist.csv](#postv1whitelistswhitelistcsv) | Upload whitelist data |
| GET | [/v1/users/me](#getv1usersme) | Get user info |
| GET | [/v1/top_holders/top_usdt_holders](#getv1top_holderstop_usdt_holders) | Returns a list of 100 top USDT holders. |
| GET | [/v2/reports/wallet_risk_score](#getv2reportswallet_risk_score) | Returns address risk score, risk level and query related info,including the usdt information.Each query exceeds remaining number of queries for the user. |

## Reference Table

| Name | Path | Description |
| --- | --- | --- |
| AddressUnderRule | [#/components/schemas/AddressUnderRule](#componentsschemasaddressunderrule) |  |
| AddressesUnderRule | [#/components/schemas/AddressesUnderRule](#componentsschemasaddressesunderrule) |  |
| ApiError | [#/components/schemas/ApiError](#componentsschemasapierror) |  |
| AuthRequest | [#/components/schemas/AuthRequest](#componentsschemasauthrequest) |  |
| Body_update_transactions_graph_v1_visualizer_update_transactions_graph_put | [#/components/schemas/Body_update_transactions_graph_v1_visualizer_update_transactions_graph_put](#componentsschemasbody_update_transactions_graph_v1_visualizer_update_transactions_graph_put) |  |
| Body_upload | [#/components/schemas/Body_upload](#componentsschemasbody_upload) |  |
| ClaimWalletTag | [#/components/schemas/ClaimWalletTag](#componentsschemasclaimwallettag) |  |
| ClaimedWallet | [#/components/schemas/ClaimedWallet](#componentsschemasclaimedwallet) |  |
| CreateAddressUnderRule | [#/components/schemas/CreateAddressUnderRule](#componentsschemascreateaddressunderrule) |  |
| CreateUserRule | [#/components/schemas/CreateUserRule](#componentsschemascreateuserrule) |  |
| DeleteAddressUnderRule | [#/components/schemas/DeleteAddressUnderRule](#componentsschemasdeleteaddressunderrule) |  |
| Edge | [#/components/schemas/Edge](#componentsschemasedge) |  |
| HTTPValidationError | [#/components/schemas/HTTPValidationError](#componentsschemashttpvalidationerror) |  |
| MonitoringWallet | [#/components/schemas/MonitoringWallet](#componentsschemasmonitoringwallet) |  |
| MonitoringWallets | [#/components/schemas/MonitoringWallets](#componentsschemasmonitoringwallets) |  |
| Node | [#/components/schemas/Node](#componentsschemasnode) |  |
| NodeAdditionalData | [#/components/schemas/NodeAdditionalData](#componentsschemasnodeadditionaldata) |  |
| NodeRiskScore | [#/components/schemas/NodeRiskScore](#componentsschemasnoderiskscore) |  |
| NodeWithPosition | [#/components/schemas/NodeWithPosition](#componentsschemasnodewithposition) |  |
| NotifySetting | [#/components/schemas/NotifySetting](#componentsschemasnotifysetting) |  |
| NotifySettings | [#/components/schemas/NotifySettings](#componentsschemasnotifysettings) |  |
| RiskScoreHistoryResponse | [#/components/schemas/RiskScoreHistoryResponse](#componentsschemasriskscorehistoryresponse) |  |
| RiskScoringMixin | [#/components/schemas/RiskScoringMixin](#componentsschemasriskscoringmixin) |  |
| RiskScoringReportResponse | [#/components/schemas/RiskScoringReportResponse](#componentsschemasriskscoringreportresponse) |  |
| RiskyConnection | [#/components/schemas/RiskyConnection](#componentsschemasriskyconnection) |  |
| SourceOfFunds | [#/components/schemas/SourceOfFunds](#componentsschemassourceoffunds) |  |
| TokenPayload | [#/components/schemas/TokenPayload](#componentsschemastokenpayload) |  |
| TopUsdtHolder | [#/components/schemas/TopUsdtHolder](#componentsschemastopusdtholder) |  |
| UserClaim | [#/components/schemas/UserClaim](#componentsschemasuserclaim) |  |
| UserClaims | [#/components/schemas/UserClaims](#componentsschemasuserclaims) |  |
| UserInfo | [#/components/schemas/UserInfo](#componentsschemasuserinfo) |  |
| UserRule | [#/components/schemas/UserRule](#componentsschemasuserrule) |  |
| UserRuleStatistic | [#/components/schemas/UserRuleStatistic](#componentsschemasuserrulestatistic) |  |
| UserRuleStatistics | [#/components/schemas/UserRuleStatistics](#componentsschemasuserrulestatistics) |  |
| UserRules | [#/components/schemas/UserRules](#componentsschemasuserrules) |  |
| ValidationError | [#/components/schemas/ValidationError](#componentsschemasvalidationerror) |  |
| VisualizerResponse | [#/components/schemas/VisualizerResponse](#componentsschemasvisualizerresponse) |  |
| VisualizerWithPosition | [#/components/schemas/VisualizerWithPosition](#componentsschemasvisualizerwithposition) |  |
| WalletInfo | [#/components/schemas/WalletInfo](#componentsschemaswalletinfo) |  |
| WalletRiskScoreWithUsdtAndExchangeInfo | [#/components/schemas/WalletRiskScoreWithUsdtAndExchangeInfo](#componentsschemaswalletriskscorewithusdtandexchangeinfo) |  |
| WalletUpdateInfo | [#/components/schemas/WalletUpdateInfo](#componentsschemaswalletupdateinfo) |  |
| ton_aml__platform__api__v1__aml__reports__serializers__WalletRiskScore | [#/components/schemas/ton_aml__platform__api__v1__aml__reports__serializers__WalletRiskScore](#componentsschemaston_aml__platform__api__v1__aml__reports__serializers__walletriskscore) |  |
| ton_aml__platform__api__v2__aml__reports__serializers__WalletRiskScore | [#/components/schemas/ton_aml__platform__api__v2__aml__reports__serializers__WalletRiskScore](#componentsschemaston_aml__platform__api__v2__aml__reports__serializers__walletriskscore) |  |
| ton_aml__platform__core__command__scoring__data_models__WalletRiskScore | [#/components/schemas/ton_aml__platform__core__command__scoring__data_models__WalletRiskScore](#componentsschemaston_aml__platform__core__command__scoring__data_models__walletriskscore) |  |
| ton_aml__platform__core__command__scoring__data_models__WalletTag | [#/components/schemas/ton_aml__platform__core__command__scoring__data_models__WalletTag](#componentsschemaston_aml__platform__core__command__scoring__data_models__wallettag) |  |
| ton_aml__platform__core__repository__postgre_connector__data_models__WalletTag | [#/components/schemas/ton_aml__platform__core__repository__postgre_connector__data_models__WalletTag](#componentsschemaston_aml__platform__core__repository__postgre_connector__data_models__wallettag) |  |

***





### [GET]/v1/reports/wallet_risk_score

- Summary  
Returns address risk score, risk level and query related info. Each query exceeds remaining number of queries for the user.

#### Parameters(Query)

```ts
// Source of the request.
source: string //default: api
```

```ts
// TON wallet address in any base64 form (urlsafe or not).
address: string
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
  whitelist: boolean
  blacklist: boolean
  address: string
  address_raw: string //default: unknown
  address_non_bounceable: string //default: unknown
  address_type: string //default: unknown
  owner: string //default: unknown
  risk_score: integer
  fraud_level: enum[high, medium, low, lowest, unknown] //default: lowest
  risk_category: string[]
  total_days: integer
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_transactions_amount: number
  total_transactions_count: integer
  total_counterparts_count: integer
  total_sent_transactions_amount: number
  total_sent_transactions_count: integer
  total_sent_counterparts_count: integer
  total_received_transactions_amount: number
  total_received_transactions_count: integer
  total_received_counterparts_count: integer
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
  miner_wallet_status: string[]
  nft_wallet_status: string[]
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
    loc: Partial(string) & Partial(integer)[]
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
address: string
```

```ts
// Limit of records to return.
limit: integer //default: 10
```

```ts
// Offset of records to return.
offset: integer
```

```ts
// Limit of risk for filter.
risk_limit: integer
```

```ts
// Offset of risk for filter.
risk_offset: integer
```

```ts
// List of info tags for filter.
info_category: string
```

```ts
// List of risk tags for filter.
risk_category: string
```

```ts
// List of risk levels for filter.
risk: string
```

```ts
// Source of the request
source: string
```

```ts
// Date from for filter
date_from: string
```

```ts
// Date to for filter
date_to: string
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
    created_dt: string
    endpoint_used: string
    source: string //default: api
    whitelist: boolean
    blacklist: boolean
    address: string
    address_type: string //default: unknown
    address_raw: string
    address_non_bounceable: string
    owner: string //default: unknown
    fraud_level: string
    risk_score: integer
    info_category: integer[]
    risk_category: integer[]
    risky_connections: {
    }[]
    source_of_funds: {
    }[]
    first_transaction_time: string
    last_transaction_time: string
    total_balance: number
    total_balance_in_usd: number
    total_days: number
    total_transactions_amount: number
    total_transactions_amount_in_usd: number
    total_sent_transactions_amount: number
    total_sent_transactions_amount_in_usd: number
    total_received_transactions_amount: number
    total_received_transactions_amount_in_usd: number
    total_counterparts_count: integer
    total_sent_counterparts_count: integer
    total_received_counterparts_count: integer
    total_transactions_count: integer
    total_sent_transactions_count: integer
    total_received_transactions_count: integer
    bridge_wallet_status: string[]
    exchange_wallet_status: string[]
    stacking_wallet_status: string[]
    miner_wallet_status: string[]
    nft_wallet_status: string[]
    gambling_message_count: integer
    spam_message_count: integer
    scam_message_count: integer
    usdt_balance: number
    total_usdt_transactions_amount: number
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
    loc: Partial(string) & Partial(integer)[]
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
    created_dt: string
    endpoint_used: string
    source: string //default: api
    whitelist: boolean
    blacklist: boolean
    address: string
    address_type: string //default: unknown
    address_raw: string
    address_non_bounceable: string
    owner: string //default: unknown
    fraud_level: string
    risk_score: integer
    info_category: integer[]
    risk_category: integer[]
    risky_connections: {
    }[]
    source_of_funds: {
    }[]
    first_transaction_time: string
    last_transaction_time: string
    total_balance: number
    total_balance_in_usd: number
    total_days: number
    total_transactions_amount: number
    total_transactions_amount_in_usd: number
    total_sent_transactions_amount: number
    total_sent_transactions_amount_in_usd: number
    total_received_transactions_amount: number
    total_received_transactions_amount_in_usd: number
    total_counterparts_count: integer
    total_sent_counterparts_count: integer
    total_received_counterparts_count: integer
    total_transactions_count: integer
    total_sent_transactions_count: integer
    total_received_transactions_count: integer
    bridge_wallet_status: string[]
    exchange_wallet_status: string[]
    stacking_wallet_status: string[]
    miner_wallet_status: string[]
    nft_wallet_status: string[]
    gambling_message_count: integer
    spam_message_count: integer
    scam_message_count: integer
    usdt_balance: number
    total_usdt_transactions_amount: number
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/reports/risk_scoring_report_{uuid}.pdf

- Summary  
Download report as a pdf file.

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Data successfully downloaded.

`application/json`

```ts
{}
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/reports/risk_history.csv

- Summary  
Returns risk scoring history in a csv file.

#### Parameters(Query)

```ts
// TON wallet address in any base64 form (urlsafe or not).
address: string
```

```ts
// Limit of risk for filter.
risk_limit: integer
```

```ts
// Offset of risk for filter.
risk_offset: integer
```

```ts
// List of info tags for filter.
info_category: string
```

```ts
// List of risk tags for filter.
risk_category: string
```

```ts
// List of risk levels for filter.
risk: string
```

```ts
// Source of the request
source: string
```

```ts
// Date from for filter
date_from: string
```

```ts
// Date to for filter
date_to: string
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
  "title": "Response Download"
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
    loc: Partial(string) & Partial(integer)[]
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
  tags: integer[]
  comment: string
  transaction_link: string
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [PUT]/v1/claims/update_wallet_claim/{uuid}

- Summary  
Update Wallet Claim

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
{
  tags: integer[]
  comment: string
  transaction_link: string
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
    loc: Partial(string) & Partial(integer)[]
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
address: string
```

```ts
// Date from
date_from: string
```

```ts
// Date to
date_to: string
```

```ts
// tags to filter
tags: string
```

```ts
// Limit to paginate created wallets claims. Default value is 300.
limit: integer //default: 300
```

```ts
// Offset to paginate over created wallets claims. Default value is 0.
offset: integer
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
    transaction_link: string
    comment: string
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
    loc: Partial(string) & Partial(integer)[]
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/claims/wallets_tags

- Summary  
Wallets Tags

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
  code: integer
  name: string
  type: enum[INFO, RISK]
  description: string
}[]
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/claims/claim_history.csv

- Summary  
Returns claims history in a csv file.

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### Responses

- 200 Claim history successfully retrieved.

`application/json`

```ts
{
  "title": "Response Download"
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/visualizer/get_transactions_graph

- Summary  
Visualizer

#### Parameters(Query)

```ts
// TON wallet address in any base64 form (urlsafe or not). Accepts both address types - bounceable and non-bounceable.
address: string
```

```ts
// Limit of records to return.
limit: integer //default: 10
```

```ts
// User action
action: string
```

```ts
// List of risk levels to return.
risk: string
```

```ts
// Date from for filter
date_from: string
```

```ts
// Date to for filter
date_to: string
```

```ts
// Depth of records to return.
depth: integer //default: 10
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
  address: string
  nodes: {
    id: string
    alias: string
    name: string
    type: enum[input, output, custom]
    label: string
    data: {
      owner: string
      incoming_transactions: integer
      outgoing_transactions: integer
      balance: number
      turnover: number
      report: {
        fraud_level: string
        risk_score: integer
      }
    }
  }[]
  edges: {
    id: Partial(integer) & Partial(string)
    created_dt: string
    source: string
    target: string
    label: Partial(number) & Partial(number)
    value: Partial(number) & Partial(number)
    logical_time: integer
    transaction_hash: string
    forward_fee: integer
  }[]
  action: string
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/visualizer/get_last_transactions_graph

- Summary  
Last Transactions Graph

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
  address: string
  nodes: {
    data: {
      id: string
      alias: string
      name: string
      type: enum[input, output, custom]
      label: string
      data: {
        owner: string
        incoming_transactions: integer
        outgoing_transactions: integer
        balance: number
        turnover: number
        report: {
          fraud_level: string
          risk_score: integer
        }
      }
    }
    position: {
    }
  }[]
  edges: {
    id: Partial(integer) & Partial(string)
    created_dt: string
    source: string
    target: string
    label: Partial(number) & Partial(number)
    value: Partial(number) & Partial(number)
    logical_time: integer
    transaction_hash: string
    forward_fee: integer
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [PUT]/v1/visualizer/update_transactions_graph

- Summary  
Update Transactions Graph

#### Parameters(Query)

```ts
address: string
```

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- application/json

```ts
{
  nodes: {
  }[]
  edges: {
  }[]
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
    loc: Partial(string) & Partial(integer)[]
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
limit: integer //default: 10
```

```ts
// Offset to paginate over. Default value is 0.
offset: integer
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
    loc: Partial(string) & Partial(integer)[]
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
    id: integer
    notify_url: string
    email: string
    created_dt: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
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

```ts
// Email to send notifications to
email: string
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
    loc: Partial(string) & Partial(integer)[]
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
    monitoring_rule_info_key: string
    custom_parameter: {
    }
    rule_name: string
    comment: string
    created_dt: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
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
  monitoring_rule_info_key: string
  custom_parameter: {
  }
  rule_name_custom: string
  comment: string
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
    loc: Partial(string) & Partial(integer)[]
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
address: string
```

```ts
// Date from
date_from: string
```

```ts
// Date to
date_to: string
```

```ts
// user rules to filter
user_rules: string
```

```ts
// Limit to paginate. Default value is 10.
limit: integer //default: 10
```

```ts
// Offset to paginate over. Default value is 0.
offset: integer
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
    loc: Partial(string) & Partial(integer)[]
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
  comment: string
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
    loc: Partial(string) & Partial(integer)[]
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/monitoring/user_rule_statistic

- Summary  
Get User Rule Statistic

#### Parameters(Query)

```ts
// Limit to paginate. Default value is 10.
limit: integer //default: 10
```

```ts
// Offset to paginate over. Default value is 0.
offset: integer
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
  user_rule_statistics: {
    created_dt: string
    rule_name: string
    alert_count: integer
    delivered_count: integer
    comment: string
  }[]
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/whitelists/whitelist.csv

- Summary  
Download whitelist as a file.

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
  "title": "Response Download"
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [POST]/v1/whitelists/whitelist.csv

- Summary  
Upload whitelist data

#### Headers

```ts
// JWT token of authorised user
token: string
```

#### RequestBody

- multipart/form-data

```ts
{
  // CSV file containing whitelist data.
  file: string
}
```

#### Responses

- 200 Data successfully uploaded.

`application/json`

```ts
{
  "title": "Response Upload"
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
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/users/me

- Summary  
Get user info

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
  tariff_start_date: string
  tariff_end_date: string
  request_limit: integer
  executed_requests: integer
  remaining_requests: integer
  number_of_claims: integer
}
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***

### [GET]/v1/top_holders/top_usdt_holders

- Summary  
Returns a list of 100 top USDT holders.

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
  address: string
  owner: string
  usdt_balance: number
}[]
```

- 422 Validation Error

`application/json`

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
    msg: string
    type: string
  }[]
}
```

***


### [GET]/v2/reports/wallet_risk_score

- Summary  
Returns address risk score, risk level and query related info,including the usdt information.Each query exceeds remaining number of queries for the user.

#### Parameters(Query)

```ts
// Source of the request.
source: string //default: api
```

```ts
// TON wallet address in any base64 form (urlsafe or not).
address: string
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
  whitelist: boolean
  blacklist: boolean
  address: string
  address_raw: string //default: unknown
  address_non_bounceable: string //default: unknown
  address_type: string //default: unknown
  owner: string //default: unknown
  risk_score: integer
  fraud_level: enum[high, medium, low, lowest, unknown] //default: lowest
  risk_category: string[]
  total_days: integer
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_transactions_amount: number
  total_transactions_count: integer
  total_counterparts_count: integer
  total_sent_transactions_amount: number
  total_sent_transactions_count: integer
  total_sent_counterparts_count: integer
  total_received_transactions_amount: number
  total_received_transactions_count: integer
  total_received_counterparts_count: integer
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
  miner_wallet_status: string[]
  nft_wallet_status: string[]
  total_usdt_transactions_amount: number
  usdt_balance: number
  total_balance_in_usd: number
  total_transactions_amount_in_usd: number
  total_received_transactions_amount_in_usd: number
  total_sent_transactions_amount_in_usd: number
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
    loc: Partial(string) & Partial(integer)[]
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
  password: string //default: ToNloveR2000
}
```

### #/components/schemas/Body_update_transactions_graph_v1_visualizer_update_transactions_graph_put

```ts
{
  nodes: {
  }[]
  edges: {
  }[]
}
```

### #/components/schemas/Body_upload

```ts
{
  // CSV file containing whitelist data.
  file: string
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
  comment: string
}
```

### #/components/schemas/CreateUserRule

```ts
{
  monitoring_notify_setting_id: integer
  monitoring_rule_info_key: string
  custom_parameter: {
  }
  rule_name_custom: string
  comment: string
}
```

### #/components/schemas/DeleteAddressUnderRule

```ts
{
  monitoring_address_under_rule_id: integer
}
```

### #/components/schemas/Edge

```ts
{
  id: Partial(integer) & Partial(string)
  created_dt: string
  source: string
  target: string
  label: Partial(number) & Partial(number)
  value: Partial(number) & Partial(number)
  logical_time: integer
  transaction_hash: string
  forward_fee: integer
}
```

### #/components/schemas/HTTPValidationError

```ts
{
  detail: {
    loc: Partial(string) & Partial(integer)[]
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

### #/components/schemas/Node

```ts
{
  id: string
  alias: string
  name: string
  type: enum[input, output, custom]
  label: string
  data: {
    owner: string
    incoming_transactions: integer
    outgoing_transactions: integer
    balance: number
    turnover: number
    report: {
      fraud_level: string
      risk_score: integer
    }
  }
}
```

### #/components/schemas/NodeAdditionalData

```ts
{
  owner: string
  incoming_transactions: integer
  outgoing_transactions: integer
  balance: number
  turnover: number
  report: {
    fraud_level: string
    risk_score: integer
  }
}
```

### #/components/schemas/NodeRiskScore

```ts
{
  fraud_level: string
  risk_score: integer
}
```

### #/components/schemas/NodeWithPosition

```ts
{
  data: {
    id: string
    alias: string
    name: string
    type: enum[input, output, custom]
    label: string
    data: {
      owner: string
      incoming_transactions: integer
      outgoing_transactions: integer
      balance: number
      turnover: number
      report: {
        fraud_level: string
        risk_score: integer
      }
    }
  }
  position: {
  }
}
```

### #/components/schemas/NotifySetting

```ts
{
  id: integer
  notify_url: string
  email: string
  created_dt: string
}
```

### #/components/schemas/NotifySettings

```ts
{
  count: integer
  notify_settings: {
    id: integer
    notify_url: string
    email: string
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
    created_dt: string
    endpoint_used: string
    source: string //default: api
    whitelist: boolean
    blacklist: boolean
    address: string
    address_type: string //default: unknown
    address_raw: string
    address_non_bounceable: string
    owner: string //default: unknown
    fraud_level: string
    risk_score: integer
    info_category: integer[]
    risk_category: integer[]
    risky_connections: {
    }[]
    source_of_funds: {
    }[]
    first_transaction_time: string
    last_transaction_time: string
    total_balance: number
    total_balance_in_usd: number
    total_days: number
    total_transactions_amount: number
    total_transactions_amount_in_usd: number
    total_sent_transactions_amount: number
    total_sent_transactions_amount_in_usd: number
    total_received_transactions_amount: number
    total_received_transactions_amount_in_usd: number
    total_counterparts_count: integer
    total_sent_counterparts_count: integer
    total_received_counterparts_count: integer
    total_transactions_count: integer
    total_sent_transactions_count: integer
    total_received_transactions_count: integer
    bridge_wallet_status: string[]
    exchange_wallet_status: string[]
    stacking_wallet_status: string[]
    miner_wallet_status: string[]
    nft_wallet_status: string[]
    gambling_message_count: integer
    spam_message_count: integer
    scam_message_count: integer
    usdt_balance: number
    total_usdt_transactions_amount: number
  }[]
  count: integer
}
```

### #/components/schemas/RiskScoringMixin

```ts
{
  version: string
  uuid: string
  created_dt: string
  endpoint_used: string
  source: string //default: api
  whitelist: boolean
  blacklist: boolean
  address: string
  address_type: string //default: unknown
  address_raw: string
  address_non_bounceable: string
  owner: string //default: unknown
  fraud_level: string
  risk_score: integer
  info_category: integer[]
  risk_category: integer[]
  risky_connections: {
  }[]
  source_of_funds: {
  }[]
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_balance_in_usd: number
  total_days: number
  total_transactions_amount: number
  total_transactions_amount_in_usd: number
  total_sent_transactions_amount: number
  total_sent_transactions_amount_in_usd: number
  total_received_transactions_amount: number
  total_received_transactions_amount_in_usd: number
  total_counterparts_count: integer
  total_sent_counterparts_count: integer
  total_received_counterparts_count: integer
  total_transactions_count: integer
  total_sent_transactions_count: integer
  total_received_transactions_count: integer
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
  miner_wallet_status: string[]
  nft_wallet_status: string[]
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  usdt_balance: number
  total_usdt_transactions_amount: number
}
```

### #/components/schemas/RiskScoringReportResponse

```ts
{
  report: {
    version: string
    uuid: string
    created_dt: string
    endpoint_used: string
    source: string //default: api
    whitelist: boolean
    blacklist: boolean
    address: string
    address_type: string //default: unknown
    address_raw: string
    address_non_bounceable: string
    owner: string //default: unknown
    fraud_level: string
    risk_score: integer
    info_category: integer[]
    risk_category: integer[]
    risky_connections: {
    }[]
    source_of_funds: {
    }[]
    first_transaction_time: string
    last_transaction_time: string
    total_balance: number
    total_balance_in_usd: number
    total_days: number
    total_transactions_amount: number
    total_transactions_amount_in_usd: number
    total_sent_transactions_amount: number
    total_sent_transactions_amount_in_usd: number
    total_received_transactions_amount: number
    total_received_transactions_amount_in_usd: number
    total_counterparts_count: integer
    total_sent_counterparts_count: integer
    total_received_counterparts_count: integer
    total_transactions_count: integer
    total_sent_transactions_count: integer
    total_received_transactions_count: integer
    bridge_wallet_status: string[]
    exchange_wallet_status: string[]
    stacking_wallet_status: string[]
    miner_wallet_status: string[]
    nft_wallet_status: string[]
    gambling_message_count: integer
    spam_message_count: integer
    scam_message_count: integer
    usdt_balance: number
    total_usdt_transactions_amount: number
  }
}
```

### #/components/schemas/RiskyConnection

```ts
{
  last_transaction_time: string
  wallet_address: string
  neighbor_wallet_address: string
  total_income: integer
  total_outcome: integer
  risk_score: integer
  fraud_level: string
  total_transactions_count: integer
  total_transactions_amount: string
  tags: {
    code: integer
    name: string
    type: string
    description: string
  }[]
}
```

### #/components/schemas/SourceOfFunds

```ts
{
  category: string
  percentage: number
  total_input_ton: number
  total_input_usdt: number
}
```

### #/components/schemas/TokenPayload

```ts
{
  token: string
  token_type: string //default: JWT
  expiry: string
  queries_count_left: integer
}
```

### #/components/schemas/TopUsdtHolder

```ts
{
  address: string
  owner: string
  usdt_balance: number
}
```

### #/components/schemas/UserClaim

```ts
{
  uuid: string
  address: string
  created_dt: string
  transaction_link: string
  comment: string
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
    transaction_link: string
    comment: string
    tags: Partial({
       code: integer
       name: string
       type: enum[INFO, RISK]
       description: string
     }[]) & Partial(integer[])
  }[]
}
```

### #/components/schemas/UserInfo

```ts
{
  tariff_start_date: string
  tariff_end_date: string
  request_limit: integer
  executed_requests: integer
  remaining_requests: integer
  number_of_claims: integer
}
```

### #/components/schemas/UserRule

```ts
{
  id: integer
  monitoring_notify_setting_id: integer
  monitoring_rule_info_key: string
  custom_parameter: {
  }
  rule_name: string
  comment: string
  created_dt: string
}
```

### #/components/schemas/UserRuleStatistic

```ts
{
  created_dt: string
  rule_name: string
  alert_count: integer
  delivered_count: integer
  comment: string
}
```

### #/components/schemas/UserRuleStatistics

```ts
{
  count: integer
  user_rule_statistics: {
    created_dt: string
    rule_name: string
    alert_count: integer
    delivered_count: integer
    comment: string
  }[]
}
```

### #/components/schemas/UserRules

```ts
{
  count: integer
  user_rules: {
    id: integer
    monitoring_notify_setting_id: integer
    monitoring_rule_info_key: string
    custom_parameter: {
    }
    rule_name: string
    comment: string
    created_dt: string
  }[]
}
```

### #/components/schemas/ValidationError

```ts
{
  loc: Partial(string) & Partial(integer)[]
  msg: string
  type: string
}
```

### #/components/schemas/VisualizerResponse

```ts
{
  address: string
  nodes: {
    id: string
    alias: string
    name: string
    type: enum[input, output, custom]
    label: string
    data: {
      owner: string
      incoming_transactions: integer
      outgoing_transactions: integer
      balance: number
      turnover: number
      report: {
        fraud_level: string
        risk_score: integer
      }
    }
  }[]
  edges: {
    id: Partial(integer) & Partial(string)
    created_dt: string
    source: string
    target: string
    label: Partial(number) & Partial(number)
    value: Partial(number) & Partial(number)
    logical_time: integer
    transaction_hash: string
    forward_fee: integer
  }[]
  action: string
}
```

### #/components/schemas/VisualizerWithPosition

```ts
{
  address: string
  nodes: {
    data: {
      id: string
      alias: string
      name: string
      type: enum[input, output, custom]
      label: string
      data: {
        owner: string
        incoming_transactions: integer
        outgoing_transactions: integer
        balance: number
        turnover: number
        report: {
          fraud_level: string
          risk_score: integer
        }
      }
    }
    position: {
    }
  }[]
  edges: {
    id: Partial(integer) & Partial(string)
    created_dt: string
    source: string
    target: string
    label: Partial(number) & Partial(number)
    value: Partial(number) & Partial(number)
    logical_time: integer
    transaction_hash: string
    forward_fee: integer
  }[]
}
```

### #/components/schemas/WalletInfo

```ts
{
  wallet_address: string
  tags: integer[]
  comment: string
  transaction_link: string
}
```

### #/components/schemas/WalletRiskScoreWithUsdtAndExchangeInfo

```ts
{
  uuid: string
  version: string
  whitelist: boolean
  blacklist: boolean
  address: string
  address_type: string //default: unknown
  address_raw: string //default: unknown
  address_non_bounceable: string //default: unknown
  owner: string //default: unknown
  fraud_level: string
  risk_score: integer
  risk_category: {
    code: integer
    name: string
    type: string
    description: string
  }[]
  info_category:#/components/schemas/ton_aml__platform__core__command__scoring__data_models__WalletTag[]
  risky_connections: {
    last_transaction_time: string
    wallet_address: string
    neighbor_wallet_address: string
    total_income: integer
    total_outcome: integer
    risk_score: integer
    fraud_level: string
    total_transactions_count: integer
    total_transactions_amount: string
    tags: {
      code: integer
      name: string
      type: string
      description: string
    }[]
  }[]
  source_of_funds: {
    category: string
    percentage: number
    total_input_ton: number
    total_input_usdt: number
  }[]
  total_days: integer
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_transactions_amount: number
  total_transactions_count: integer
  total_counterparts_count: integer
  total_sent_transactions_amount: number
  total_sent_transactions_count: number
  total_sent_counterparts_count: number
  total_received_transactions_amount: number
  total_received_transactions_count: number
  total_received_counterparts_count: number
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  nft_wallet_status: string[]
  miner_wallet_status: string[]
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
  total_usdt_transactions_amount: number
  usdt_balance: number
  total_balance_in_usd: number
  total_transactions_amount_in_usd: number
  total_received_transactions_amount_in_usd: number
  total_sent_transactions_amount_in_usd: number
}
```

### #/components/schemas/WalletUpdateInfo

```ts
{
  tags: integer[]
  comment: string
  transaction_link: string
}
```

### #/components/schemas/ton_aml__platform__api__v1__aml__reports__serializers__WalletRiskScore

```ts
{
  version: string
  whitelist: boolean
  blacklist: boolean
  address: string
  address_raw: string //default: unknown
  address_non_bounceable: string //default: unknown
  address_type: string //default: unknown
  owner: string //default: unknown
  risk_score: integer
  fraud_level: enum[high, medium, low, lowest, unknown] //default: lowest
  risk_category: string[]
  total_days: integer
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_transactions_amount: number
  total_transactions_count: integer
  total_counterparts_count: integer
  total_sent_transactions_amount: number
  total_sent_transactions_count: integer
  total_sent_counterparts_count: integer
  total_received_transactions_amount: number
  total_received_transactions_count: integer
  total_received_counterparts_count: integer
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
  miner_wallet_status: string[]
  nft_wallet_status: string[]
}
```

### #/components/schemas/ton_aml__platform__api__v2__aml__reports__serializers__WalletRiskScore

```ts
{
  version: string
  whitelist: boolean
  blacklist: boolean
  address: string
  address_raw: string //default: unknown
  address_non_bounceable: string //default: unknown
  address_type: string //default: unknown
  owner: string //default: unknown
  risk_score: integer
  fraud_level: enum[high, medium, low, lowest, unknown] //default: lowest
  risk_category: string[]
  total_days: integer
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_transactions_amount: number
  total_transactions_count: integer
  total_counterparts_count: integer
  total_sent_transactions_amount: number
  total_sent_transactions_count: integer
  total_sent_counterparts_count: integer
  total_received_transactions_amount: number
  total_received_transactions_count: integer
  total_received_counterparts_count: integer
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
  miner_wallet_status: string[]
  nft_wallet_status: string[]
  total_usdt_transactions_amount: number
  usdt_balance: number
  total_balance_in_usd: number
  total_transactions_amount_in_usd: number
  total_received_transactions_amount_in_usd: number
  total_sent_transactions_amount_in_usd: number
}
```

### #/components/schemas/ton_aml__platform__core__command__scoring__data_models__WalletRiskScore

```ts
{
  uuid: string
  version: string
  whitelist: boolean
  blacklist: boolean
  address: string
  address_type: string //default: unknown
  address_raw: string //default: unknown
  address_non_bounceable: string //default: unknown
  owner: string //default: unknown
  fraud_level: string
  risk_score: integer
  risk_category: {
    code: integer
    name: string
    type: string
    description: string
  }[]
  info_category:#/components/schemas/ton_aml__platform__core__command__scoring__data_models__WalletTag[]
  risky_connections: {
    last_transaction_time: string
    wallet_address: string
    neighbor_wallet_address: string
    total_income: integer
    total_outcome: integer
    risk_score: integer
    fraud_level: string
    total_transactions_count: integer
    total_transactions_amount: string
    tags: {
      code: integer
      name: string
      type: string
      description: string
    }[]
  }[]
  source_of_funds: {
    category: string
    percentage: number
    total_input_ton: number
    total_input_usdt: number
  }[]
  total_days: integer
  first_transaction_time: string
  last_transaction_time: string
  total_balance: number
  total_transactions_amount: number
  total_transactions_count: integer
  total_counterparts_count: integer
  total_sent_transactions_amount: number
  total_sent_transactions_count: number
  total_sent_counterparts_count: number
  total_received_transactions_amount: number
  total_received_transactions_count: number
  total_received_counterparts_count: number
  gambling_message_count: integer
  spam_message_count: integer
  scam_message_count: integer
  nft_wallet_status: string[]
  miner_wallet_status: string[]
  bridge_wallet_status: string[]
  exchange_wallet_status: string[]
  stacking_wallet_status: string[]
}
```

### #/components/schemas/ton_aml__platform__core__command__scoring__data_models__WalletTag

```ts
{
  code: integer
  name: string
  type: string
  description: string
}
```

### #/components/schemas/ton_aml__platform__core__repository__postgre_connector__data_models__WalletTag

```ts
{
  code: integer
  name: string
  type: string
  description: string
}
```
