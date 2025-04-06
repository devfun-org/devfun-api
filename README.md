# dev.fun Stats API

<div align="center">
  <img src="https://img.shields.io/badge/Status-Live-brightgreen" alt="Status: Live">
  <img src="https://img.shields.io/badge/Version-1.0.0-blue" alt="Version: 1.0.0">
</div>

## Overview

The dev.fun Stats API provides comprehensive statistics about the dev.fun platform, including developers, apps, tokens, and activity metrics. This API is publicly available for all users.

## Base URL

```
https://app.dev.fun/api/stats/
```

## Endpoints

- [Developers](#developers)
- [Apps](#apps)
- [Coins/Tokens](#coinstokens)
- [Other Stats](#other-stats)

---

### Developers

#### Get Overall Developer Stats
> Returns aggregated statistics about developers on the platform

```http
https://app.dev.fun/api/stats/devs
```

**Response**
```json
{
  "total_devs": 1000,
  "daily_new_devs": 50,
  "daily_active_devs": 200
}
```

#### Get Developer Profile
> Returns detailed information about a specific developer

```http
https://app.dev.fun/api/stats/devs/:uniqueId
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `uniqueId` | string | Developer's unique identifier (can be username, wallet, or ID) |

**Response**
```json
{
  "wallet": "solana_wallet_address",
  "username": "johndoe",
  "apps_created": 10,
  "commits": 150,
  "runs": 1000,
  "likes": 50,
  "joined_at": "2024-01-01T00:00:00Z",
  "id": "user_id",
  "privy_user_id": "privy_id",
  "name": "John Doe",
  "bio": "Developer bio...",
  "avatar": "https://avatar-url.com/img.png",
  "is_whitelist": true,
  "created_at": "2024-01-01T00:00:00Z",
  "updated_at": "2024-01-01T00:00:00Z",
  "following": 20,
  "followers": 30,
  "top_apps": [
    {
      "id": "app_id",
      "name": "App Name",
      "runs": 50,
      "created_at": "2024-01-01T00:00:00Z"
    }
  ]
}
```

#### List Developers
> Returns a paginated list of developers on the platform

```http
https://b-app.dev.fun/api/stats/devs/list?page=1?limit=20
```

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `page` | number | 1 | Page number |
| `limit` | number | 20 | Number of items per page |

**Response**
```json
{
  "developers": [
    {
      "wallet": "solana_wallet_address",
      "username": "johndoe",
      "apps_created": 5,
      "commits": 20,
      "runs": 50,
      "likes": 10,
      "id": "user_id", 
      "avatar": "https://avatar-url.com/img.png",
      "joined_at": "2024-01-01T00:00:00Z"
    }
  ],
  "page": 1,
  "limit": 20,
  "total": 100
}
```

---

### Apps

#### Get Overall App Stats
> Returns aggregated statistics about apps on the platform

```http
https://app.dev.fun/api/stats/apps
```

**Response**
```json
{
  "total_apps": 5000,
  "daily_created_apps": 100,
  "daily_live_apps": 80,
  "total_app_runs": 100000,
  "daily_app_runs": 5000,
  "total_forks": 1000,
  "daily_forks": 50
}
```

#### Get Apps List
> Returns a paginated list of apps

```http
https://app.dev.fun/api/stats/apps/list
```

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `page` | number | 1 | Page number |
| `limit` | number | 20 | Number of items per page |

**Response**
```json
{
  "apps": [
    {
      "app_id": "app_id",
      "app_name": "Amazing App",
      "dev_wallet": "solana_wallet_address",
      "runs": 100,
      "forks": 20,
      "commits": 50,
      "likes": 30,
      "linked_coin": "coin_contract_address",
      "created_at": "2024-01-01T00:00:00Z",
      "description": "App description...",
      "dev_username": "johndoe",
      "dev_avatar": "https://avatar-url.com/img.png",
      "token_symbol": "TOKEN"
    }
  ],
  "page": 1,
  "limit": 20,
  "total": 500
}
```

#### Get App Details
> Returns details about a specific app

```http
https://app.dev.fun/api/stats/apps/:appId
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | string | Unique app identifier |

**Response**
```json
{
  "app_id": "app123",
  "name": "Amazing App",
  "created_on": "2024-01-01T00:00:00Z",
  "dev": "johndoe",
  "runs": 1000,
  "commits": 50,
  "forks": 20,
  "likes": 100
}
```

#### Get Apps by Creation Date
> Returns apps created on a specific date

```http
https://app.dev.fun/api/stats/apps/by-date/:creationDate
```

| Parameter | Type | Format | Description |
|-----------|------|--------|-------------|
| `creationDate` | string | YYYY-MM-DD | Date when apps were created |

**Response**
```json
{
  "date": "2024-01-01",
  "apps": [
    {
      "app_id": "app_id",
      "app_name": "App Name",
      "dev_wallet": "solana_wallet_address",
      "runs": 100,
      "forks": 20,
      "commits": 50,
      "likes": 30,
      "linked_coin": "coin_contract_address",
      "created_at": "2024-01-01T00:00:00Z",
      "description": "App description...",
      "dev_username": "johndoe",
      "dev_avatar": "https://avatar-url.com/img.png",
      "token_symbol": "TOKEN"
    }
  ],
  "total": 10
}
```

#### Get Apps by Developer
> Returns apps created by a specific developer

```http
https://app.dev.fun/api/stats/apps/by-dev/:walletAddress
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `walletAddress` | string | Developer's Solana wallet address |

**Response**
```json
{
  "developer": {
    "wallet": "solana_wallet_address",
    "username": "johndoe",
    "avatar": "https://avatar-url.com/img.png"
  },
  "apps": [
    {
      "app_id": "app_id",
      "app_name": "App Name",
      "dev_wallet": "solana_wallet_address",
      "runs": 100,
      "forks": 20,
      "commits": 50,
      "likes": 30,
      "linked_coin": "coin_contract_address",
      "created_at": "2024-01-01T00:00:00Z",
      "description": "App description...",
      "dev_username": "johndoe",
      "dev_avatar": "https://avatar-url.com/img.png",
      "token_symbol": "TOKEN"
    }
  ],
  "total": 5
}
```

---

### Coins/Tokens

#### Get Coin Stats
> Returns overall statistics about coins/tokens on the platform

```http
https://app.dev.fun/api/stats/coins
```

**Response**
```json
{
  "native_coins": 100,
  "total_coins": 1000
}
```

#### Get Coins List
> Returns a paginated list of coins/tokens

```http
https://app.dev.fun/api/stats/coins/list
```

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `page` | number | 1 | Page number |
| `limit` | number | 20 | Number of items per page |

**Response**
```json
{
  "coins": [
    {
      "contract_address": "coin_contract_address",
      "is_devfun_native": true,
      "total_runs": 1000,
      "apps_count": 20,
      "devs_count": 10,
      "symbol": "TOKEN",
      "name": "Token Name",
      "description": "Token description...",
      "image": "https://token-image-url.com/img.png",
      "price": 1.23,
      "marketcap": 1000000,
      "volume_24h": 50000,
      "created_at": "2024-01-01T00:00:00Z"
    }
  ],
  "page": 1,
  "limit": 20,
  "total": 500
}
```

#### Get Coin Details
> Returns details about a specific coin/token

```http
https://app.dev.fun/api/stats/coin/:contractAddress
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `contractAddress` | string | Coin's contract address |

**Response**
```json
{
  "contract_address": "coin_contract_address",
  "is_devfun_native": true,
  "total_runs": 1000,
  "apps_count": 20,
  "devs_count": 10,
  "symbol": "TOKEN",
  "name": "Token Name",
  "description": "Token description...",
  "image": "https://token-image-url.com/img.png",
  "price": 1.23,
  "marketcap": 1000000,
  "volume_24h": 50000,
  "created_at": "2024-01-01T00:00:00Z"
}
```

#### Get Apps by Coin
> Returns apps associated with a specific coin/token

```http
https://app.dev.fun/api/stats/apps/by-coin/:contractAddress
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `contractAddress` | string | Coin's contract address |

**Response**
```json
{
  "coin": {
    "contract_address": "coin_contract_address",
    "symbol": "TOKEN",
    "name": "Token Name"
  },
  "apps": [
    {
      "app_id": "app_id",
      "app_name": "App Name",
      "dev_wallet": "solana_wallet_address",
      "runs": 100,
      "forks": 20,
      "commits": 50,
      "likes": 30,
      "linked_coin": "coin_contract_address",
      "created_at": "2024-01-01T00:00:00Z",
      "description": "App description...",
      "dev_username": "johndoe",
      "dev_avatar": "https://avatar-url.com/img.png",
      "token_symbol": "TOKEN"
    }
  ],
  "total": 20
}
```

---

### Other Stats

#### Get Commit Stats
> Returns statistics about commits on the platform

```http
https://app.dev.fun/api/stats/commits
```

**Response**
```json
{
  "total_commits": 10000,
  "daily_commits": 500
}
```

#### Get Trending Coins
> Returns a list of trending coins based on recent activity

```http
https://app.dev.fun/api/stats/trending-coins
```

**Response**
```json
[
  {
    "contract_address": "coin_contract_address",
    "symbol": "TOKEN",
    "name": "Token Name",
    "recent_live_app_count": 5,
    "recent_total_runs": 1000,
    "token_score": 10.5
  }
]
```

#### Get Lord of Dev Apps
> Returns a list of crowned apps and their developers

```http
https://app.dev.fun/api/stats/lord-of-dev
```

**Response**
```json
[
  {
    "app_id": "app123",
    "app_name": "Crowned App",
    "dev_wallet": "solana123",
    "created_on": "2024-01-01T00:00:00Z"
  }
]
```

---

## Error Handling

All endpoints return standard HTTP status codes:

| Status Code | Description |
|-------------|-------------|
| 200 | Success |
| 400 | Bad Request - Invalid parameters |
| 404 | Not Found - Resource not found |
| 500 | Server Error - Something went wrong |

**Error Response Format**

```json
{
  "error": "Error message description"
}
```

## Example Usage

```javascript
// Example using fetch
fetch('https://app.dev.fun/api/stats/apps')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

```bash
# Example using curl
curl -X GET https://app.dev.fun/api/stats/devs
```

---

<div align="center">
  <p>© 2024 dev.fun Organization. All rights reserved.</p>
  <p>
    <a href="https://dev.fun">Website</a> •
    <a href="https://api.dev.fun/docs">API Documentation</a> •
    <a href="https://github.com/devfun-org">GitHub</a>
  </p>
</div>