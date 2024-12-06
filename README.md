# VPN Backend API Documentation

---

## Overview
This documentation provides a comprehensive guide to the API endpoints for the VPN application backend. \
It includes details on user authentication, session management, referral handling, subscription management, reporting, server connections, and app updates.

---

## Table of Contents
- [Authentication](#authentication)
- [User Management](#user-management)
- [Referrals](#referrals)
- [Subscription Management](#subscription-management)
- [Reporting](#reporting)
- [Server Management](#server-management)
- [App Updates](#app-updates)

---

## Authentication
### 1. Login User
- **Endpoint**: `POST /api/auth/login`
- **Payload**: `username`, `password`, `package`, `device_id`
- **Response**: `status`, `jwtToken`, `details`, `name`, `subscription`, `plan_name`, `devices`, `userID`

### 2. Init User Session
- **Endpoint**: `GET /api/auth/check`
- **Payload/Header**: `token`, `device_info`, `device_id`
- **Response**: `status`, `subscription`, `validity`, `valid`, `refer_code`

### 3. Register User
- **Endpoint**: `POST /api/auth/new`
- **Payload**: `email`, `username`, `password`, `token`, `ref_code`
- **Response**: `status`, `jwtToken`, `details`, `name`, `subscription`, `plan_name`, `devices`, `ref_code_used`, `ref_code`

---

## User Management
### 4. Redeem Promo Code
- **Endpoint**: `POST /api/account/redeem`
- **Payload**: `jwtToken`, `promo_code`
- **Response**: `status`, `redeem_status`, `message`, `validity`, `plan_name`

### 5. Referrals Get
- **Endpoint**: `GET /api/account/myRef`
- **Payload/Header**: `jwtToken`, `email`
- **Response**: `ref_code`, `users_referral_code`, `used`, `ref_valid`, `valid_referred_users`, `ref_total_time`, `ref_time_used`, `ref_time_remained`

### 6. Referrals New User
- **Endpoint**: `POST /api/account/ref_redeem`
- **Payload**: `jwtToken`, `device_id`, `ref_code`
- **Response**: `status`, `message`, `ref_total_time`, `ref_cron`

---

## Subscription Management
### 7. Subscription Purchase VIP
- **Endpoint**: `POST /api/account/purchase`
- **Payload**: Depends on in-app payment logic
- **Response**: `status`, `message`, `subscription_status`, `validity`, `auto_renew`, `store_region`

### 8. Subscription Refund
- **Endpoint**: `POST /api/account/purchase_refund`
- **Payload**: Logic to be added

### 9. Subscription Cancel
- **Endpoint**: `POST /api/account/purchase_cancel`
- **Payload**: Logic to be added

### 10. Subscription Get Trial
- **Endpoint**: `POST /api/account/purchase_free`

---

## Reporting
### 11. Report Send
- **Endpoint**: `POST /api/account/report_new`
- **Payload**: `jwtToken`, `email`, `message`, `userID`
- **Response**: `status`, `message`, `report_id`, `report_status`, `report_user`

### 12. Get Users Reports
- **Endpoint**: `POST /api/account/report_get`
- **Payload**: `jwtToken`, `userID`
- **Response**: `status`, `report_total`, `report_open`, `report_solved`, `reports`

### 13. Get Reports
- **Endpoint**: `GET /api/account/report_status`
- **Payload**: `jwtToken`, `report_id`, `userID`
- **Response**: `status`, `message`, `report_id`, `report_title`, `report_status`, `report_message`, `report_response`

---

## Server Management
### 14. Get Servers All
- **Endpoint**: `GET /api/v1/list`
- **Payload**: `jwtToken`, `userID`
- **Response**: `status`, `servers_count`, `servers_free`, `server_list`

### 15. Connect To Server
- **Endpoint**: `POST /api/v1/connect`
- **Payload**: `jwtToken`, `server_id`, `userID`, `device_id`, `plan_name`
- **Response**: `status`, `message`, `server_ip4`, `server_port4`, `server_ip6`, `server_port6`, `server_type`, `server_load`, `server_country`, `server_city`, `server_speed`, `server_flag`, `time_connect`

### 16. Disconnect
- **Endpoint**: `POST /api/v1/disconnect`
- **Payload**: `jwtToken`, `server_id`, `user_id`, `device_id`
- **Response**: `status`, `time_disconnect`, `time_consumed`, `time_remain`

---

## App Updates
### 17. App Update
- **Endpoint**: `GET /api/update`
- **Payload**: None

---

## Further Implementations
- **Idea**: These are all endpoints i was told to work on.
- **Multi User**: If we allow one account to use multiple devices per subscription, we can allow or restrict to x devices.
- **More**: Let me know what else we need in backend.

---

This documentation is concept based on new VPN app requirements based recent discussion we had. \
Further changes will be made here upon request.

