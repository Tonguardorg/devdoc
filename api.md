# API Documentation

## Overview

This API provides risk score and risk level estimation for TON blockchain addresses and etc 🚀

## Base URL

```
https://api.tonguard.org/
```

## Authentication

All API requests require authentication using JWT tokens. First you retrieve a new JWT token using login/password authentication. After that you can use it to access other resources.

## Status Codes

This API uses HTTP status codes to communicate with the API consumer:

- `200 OK` - Response to a successful GET, PUT, PATCH or DELETE
- `201 Created` - Response to a POST that results in a creation
- `400 Bad Request` - Malformed request; request body validation errors
- `401 Unauthorized` - When no or invalid authentication details are provided
- `403 Forbidden` - When authentication succeeded but authenticated user doesn't have access to the resource
- `428 Requests Limit Reached` - When user reached his predefined maximum amount of requests
- `429 Rate Limit Exceeded` - When calls to certain endpoint for user are higher than predefined limits
- `500 Server Error` - Something went wrong on the API end
- `501 Not Implemented` - The server either does not recognize the request method, or it lacks the ability to fulfill the request

## Endpoints

### Reports

- [GET] `/v2/reports/wallet_risk_score` - Get wallet risk score (including USDT information)
- [POST] `/v2/reports/bulk_wallet_fraud_score` - Get risk scores for multiple addresses
- [GET] `/v1/reports/risk_scoring_history` - Get risk scoring history
- [GET] `/v1/reports/risk_scoring_report` - Get risk scoring report
- [GET] `/v1/reports/risk_scoring_report_{uuid}.pdf` - Download report as PDF
- [GET] `/v1/reports/risk_history.csv` - Get risk scoring history as CSV

### Claims

- [POST] `/v1/claims/report_wallets` - Create wallet claim
- [PUT] `/v1/claims/update_wallet_claim/{uuid}` - Update wallet claim
- [GET] `/v1/claims/my` - Get claims
- [DELETE] `/v1/claims/delete` - Delete claims
- [GET] `/v1/claims/wallets_tags` - Get wallet tags
- [GET] `/v1/claims/claim_history.csv` - Get claims history as CSV

### Visualizer

- [GET] `/v1/visualizer/get_transactions_graph` - Get transactions graph
- [GET] `/v1/visualizer/get_last_transactions_graph` - Get last transactions graph
- [PUT] `/v1/visualizer/update_transactions_graph` - Update transactions graph
- [GET] `/v1/visualizer/get_visualizer_history` - Get visualizer history
- [GET] `/v1/visualizer/get_transactions_graph_by_uuid` - Get graph by UUID
- [DELETE] `/v1/visualizer/delete_transactions_graph` - Delete transactions graph

### Monitoring

- [GET] `/v1/monitoring/wallet_list` - Get user monitoring wallets
- [GET] `/v1/monitoring/notify_setting` - Get user notification URLs
- [POST] `/v1/monitoring/notify_setting` - Add user notification URL
- [GET] `/v1/monitoring/user_rule` - Get user rules
- [POST] `/v1/monitoring/user_rule` - Add user rule
- [DELETE] `/v1/monitoring/user_rule` - Delete user rule
- [GET] `/v1/monitoring/address_under_rule` - Get addresses under monitoring
- [POST] `/v1/monitoring/address_under_rule` - Attach a user rule to a wallet
- [DELETE] `/v1/monitoring/address_under_rule` - Delete address from monitoring
- [GET] `/v1/monitoring/user_rule_statistics` - Get user rule statistics

### Whitelists

- [GET] `/v1/whitelists/whitelist` - Get whitelist
- [DELETE] `/v1/whitelists/whitelist_entity` - Delete address from whitelist
- [GET] `/v1/whitelists/whitelist.csv` - Download whitelist as CSV
- [POST] `/v1/whitelists/whitelist.csv` - Upload whitelist data

### Users

- [GET] `/v1/users/me` - Get user info

### Top Holders

- [GET] `/v1/top_holders/top_usdt_holders` - Get top USDT holders

### Authentication

- [POST] `/v1/auth/login` - User authentication (JSON)
- [POST] `/v1/auth/token` - OAuth2 compatible token endpoint
- [POST] `/v2/reset-password/email` - Reset email
- [POST] `/v2/reset-password/check-token` - Check token
- [POST] `/v2/reset-password/change-password` - Change password

### Organizations

- [GET] `/api/v2/get_organizations` - Get organizations
- [POST] `/api/v2/upload_claims` - Upload claims

### Metrics

- [GET] `/metrics` - Get metrics 