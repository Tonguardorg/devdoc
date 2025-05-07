# API Documentation

## Overview

This API provides risk score and risk level estimation for TON blockchain addresses.

## Base URL

```
https://api.tonguard.org/
```

## Authentication

All API requests require authentication using JWT tokens.

## Endpoints

### Reports

- [GET] `/v2/reports/wallet_risk_score` - Get wallet risk score
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
- [GET] `/v1/visualizer/get_visualizer_history` - Get addresses history
- [GET] `/v1/visualizer/get_transactions_graph_by_id` - Get graph by ID

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

- [GET] `/v1/whitelists/whitelist.csv` - Download whitelist as CSV
- [POST] `/v1/whitelists/whitelist.csv` - Upload whitelist data

### Users

- [GET] `/v1/users/me` - Get user info

### Top Holders

- [GET] `/v1/top_holders/top_usdt_holders` - Get top USDT holders

### Authentication

- [POST] `/v1/auth/login` - User authentication
- [POST] `/v2/reset-password/email` - Reset email
- [POST] `/v2/reset-password/check-token` - Check token
- [POST] `/v2/reset-password/change-password` - Change password 