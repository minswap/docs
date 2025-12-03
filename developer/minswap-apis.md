# Minswap APIs

This documentation provides comprehensive information about Minswap's public APIs for accessing pool metrics, asset data, and price information.

## Table of Contents

- [Getting Started](#getting-started)
- [HTTP Status Codes](#http-status-codes)
- [Common Types](#common-types)
- [Assets APIs](#assets-apis)
  - [Get List Assets](#1-get-list-assets)
- [Pools APIs](#pools-apis)
  - [Get Pools Metrics](#1-get-pools-metrics)
  - [Get Pool Metrics by ID](#2-get-pool-metrics-by-id)
  - [Get Pool Price Candlestick](#3-get-pool-price-candlestick)
  - [Get Pool Price Timeseries](#4-get-pool-price-timeseries)

## Getting Started

**Base URL:** `https://api-mainnet-prod.minswap.org`

### Rate Limiting

The API implements rate limiting to ensure fair usage. If you exceed the rate limit, you'll receive a `429 Too Many Requests` response. Please implement appropriate retry logic with exponential backoff.

## HTTP Status Codes

| Status | Description | Notes |
|--------|-------------|-------|
| 200 | Success | Request completed successfully |
| 400 | Bad Request | Invalid parameters or request format |
| 401 | Unauthorized | Authentication failed (if required) |
| 404 | Not Found | Resource not found |
| 429 | Too Many Requests | Rate limit exceeded, please retry later |
| 500 | Internal Server Error | Server error, please contact support if persists |

### Error Response Format

```json
{
  "statusCode": 400,
  "code": "FST_ERR_VALIDATION",
  "error": "Error message description",
  "message": "querystring/period must be equal to constant"
}
```

## Common Types

The following type definitions are used across multiple endpoints:

```typescript
type Token = {
  currency_symbol: string,
  token_name: string,
  is_verified: boolean,
  metadata?: AssetMetadata,
  social_links?: SocialLinks
}

type AssetMetadata = {
  name?: string,
  decimals: number,
  ticker?: string,
  url?: string,
  logo?: string,
  description?: string,
}

type SocialLinks = {
  website?: string,
  discord?: string,
  telegram?: string,
  twitter?: string,
  coingecko?: string,
  coin_market_cap?: string,
}

enum Protocol {
  MinswapV1 = "Minswap",
  MinswapV2 = "MinswapV2",
  MinswapStable = "MinswapStable",
}

enum SortDirection {
  Ascending = "asc",
  Descending = "desc"
}
```

## Assets APIs

Assets APIs allow you to retrieve information about tokens available on Minswap, including their metadata, verification status, and social links.

### 1. Get List Assets

**GET:** `/v1/assets`

**Description:** Retrieve a paginated list of assets available on Minswap with their metadata and verification status. Use this endpoint to populate token selection interfaces or search for specific assets.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| term | string | No | - | Search by asset name, currency symbol, token name, or ticker |
| limit | number | No | `20` | Number of results per page (min: `1`, max: `100`) |
| only_verified | boolean | No | `false` | Filter to show only verified tokens |
| search_after | string[] | No | `[]` | Pagination cursor from previous response |

**Note:** For pagination, use the `search_after` value from the previous response to get the next page of results.

#### Request Response

```typescript
type Response = {
  search_after: string[],
  assets: Asset[]        
}

type Asset = {
  currency_symbol: string,  
  token_name: string,       
  is_verified: boolean,     
  metadata?: AssetMetadata, 
  social_links?: SocialLinks
}
```
#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/assets?term=&limit=20&only_verified=false'
```

```json
{
  "search_after": [
    "1",
    "14110",
    "f66d78b4a3cb3d37afa0ec36461e51ecbde00f26c8f0a68f94b69880.69425443"
  ],
  "assets": [
    {
      "currency_symbol": "",
      "token_name": "",
      "is_verified": true,
      "metadata": {
        "decimals": 6,
        "name": "Cardano",
        "ticker": "ADA"
      }
    },
    {
      "currency_symbol": "c48cbb3d5e57ed56e276bc45f99ab39abe94e6cd7ac39fb402da47ad",
      "token_name": "0014df105553444d",
      "is_verified": true,
      "metadata": {
        "name": "USDM",
        "url": "https://moneta.global/",
        "ticker": "USDM",
        "decimals": 6,
        "description": "Fiat-backed stablecoin native to the Cardano blockchain"
      }
    },
  ]
}
```

## Pools APIs

Pools APIs provide comprehensive data about liquidity pools, including metrics, price history, and performance indicators.

### 1. Get Pools Metrics

**POST:** `/v1/pools/metrics`

**Description:** Retrieve a list of liquidity pools with their metrics including trading volume, liquidity, and trading fee APR. Use this endpoint to display pool statistics, compare pool performance, or filter pools by specific criteria.

#### Request Body

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| term | string | No | - | Search by asset name, currency symbol, ticker, or LP asset |
| limit | number | No | `20` | Number of results per page (min: `1`, max: `100`) |
| only_verified | boolean | No | `false` | Filter to show only pools with verified tokens |
| search_after | string[] | No | `[]` | Pagination cursor from previous response |
| sort_direction | string | No | - | Sort order: `asc` or `desc` |
| sort_field | string | No | - | Sort by: `volume_usd_24h`, `volume_usd_7d`, or `liquidity_usd` |
| protocols | string[] | No | All | Filter by protocol: `Minswap`, `MinswapV2`, `MinswapStable` |


#### Request Response

```typescript
type Response = {
  search_after: string[],
  pool_metrics: PoolMetric[]
}

type PoolMetric = {
  lp_asset: Token,             
  asset_a: Token,              
  asset_b: Token,              
  type: Protocol,              
  volume_usd_24h: number,      
  volume_usd_7d: number,       
  liquidity_usd: number,       
  liquidity_a_usd: number,     
  liquidity_b_usd: number,     
  liquidity: number,           
  liquidity_a: number,         
  liquidity_b: number,         
  trading_fee_usd_24h: number, 
  trading_fee_usd_7d: number,  
  trading_fee_tier: number[], // Fee tiers [asset_a_fee, asset_b_fee]
  trading_fee_apr: number 
}
```
#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/metrics' \
--header 'Content-Type: application/json' \
--data '{}'
```

```json
{
	"search_after": [
		"504648.73646031605",
		"f5808c2c990d86da54bfc97d89cee6efa20cd8461616359478d96b4c.a449f98fa06fff1d6c17b95c65ca609660049dc683cc3e94d3846b05419fc20d"
	],
	"pool_metrics": [
		{
			"lp_asset": {
				"currency_symbol": "5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd6",
				"token_name": "5553444d2d555344412d534c50",
				"is_verified": false
			},
			"type": "MinswapStable",
			"asset_a": {
				"currency_symbol": "c48cbb3d5e57ed56e276bc45f99ab39abe94e6cd7ac39fb402da47ad",
				"token_name": "0014df105553444d",
				"is_verified": true,
				"metadata": {
					"name": "USDM",
					"url": "https://moneta.global/",
					"ticker": "USDM",
					"decimals": 6,
					"description": "Fiat-backed stablecoin native to the Cardano blockchain"
				}
			},
			"asset_b": {
				"currency_symbol": "fe7c786ab321f41c654ef6c1af7b3250a613c24e4213e0425a7ae456",
				"token_name": "55534441",
				"is_verified": true,
				"metadata": {
					"name": "USDA",
					"url": "https://www.anzens.com",
					"ticker": "USDA",
					"decimals": 6,
					"description": "Anzens USDA Stablecoin"
				}
			},
			"volume_usd_24h": 275887.6115451449,
			"volume_usd_7d": 1096418.146131719,
			"liquidity_usd": 11894141.900263073,
			"liquidity_a_usd": 6371591.613676783,
			"liquidity_b_usd": 5522550.286586288,
			"liquidity": 11424797740483,
			"liquidity_a": 6146880,
			"liquidity_b": 5301950,
			"trading_fee_usd_24h": 69.15013892473809,
			"trading_fee_usd_7d": 274.5034984422627,
			"trading_fee_tier": [
				0.05,
				0.05
			],
			"trading_fee_apr": 0.5588071063497281
		}
	]
}
```

### 2. Get Pool Metrics by ID

**GET:** `/v1/pools/:id/metrics`

**Description:** Retrieve detailed metrics for a specific liquidity pool using its unique identifier (LP asset). Use this endpoint to display detailed pool information on pool detail pages.

#### Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | Pool identifier (LP asset in format: `{policy_id}.{token_name}` or `{policy_id}{token_name}`) |

#### Request Response
```ts
type Response = {
  lp_asset: Token,
  asset_a: Token,
  asset_b: Token,
  type: Protocol,
  volume_usd_24h: number,
  volume_usd_7d: number,
  liquidity_usd: number,
  liquidity_a_usd: number,
  liquidity_b_usd: number,
  liquidity: number,
  liquidity_a: number,
  liquidity_b: number,
  trading_fee_usd_24h: number,
  trading_fee_usd_7d: number,
  trading_fee_tier: number[], // [trading_fee_tier_a, trading_fee_tier_b]
  trading_fee_apr: number
}
```

### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/f5808c2c990d86da54bfc97d89cee6efa20cd8461616359478d96b4c.82e2b1fd27a7712a1a9cf750dfbea1a5778611b20e06dd6a611df7a643f8cb75/metrics'
```

```json
{
  "lp_asset": {
    "currency_symbol": "f5808c2c990d86da54bfc97d89cee6efa20cd8461616359478d96b4c",
    "token_name": "82e2b1fd27a7712a1a9cf750dfbea1a5778611b20e06dd6a611df7a643f8cb75",
    "is_verified": false
  },
  "type": "MinswapV2",
  "asset_a": {
    "currency_symbol": "",
    "token_name": "",
    "is_verified": true,
    "metadata": {
      "decimals": 6,
      "name": "Cardano",
      "ticker": "ADA"
    }
  },
  "asset_b": {
    "currency_symbol": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c6",
    "token_name": "4d494e",
    "is_verified": true,
    "metadata": {
      "name": "Minswap",
      "url": "https://minswap.org/",
      "ticker": "MIN",
      "decimals": 6,
      "description": "Minswap is a multi-pool decentralize exchange protocol on Cardano"
    }
  },
  "volume_usd_24h": 33450.56473381408,
  "volume_usd_7d": 414577.06098515296,
  "liquidity_usd": 4014574.127954561,
  "liquidity_a_usd": 2007287.0639772804,
  "liquidity_b_usd": 2007287.0639772804,
  "liquidity": 31904344470140,
  "liquidity_a": 4959938,
  "liquidity_b": 214384918,
  "trading_fee_usd_24h": 146.6456692739724,
  "trading_fee_usd_7d": 1275.4345738452926,
  "trading_fee_tier": [
    0.3,
    1
  ],
  "trading_fee_apr": 2.714538755500508
}
```

### 3. Get Pool Price Candlestick

**GET:** `/v1/pools/:id/price/candlestick`

**Description:** Retrieve OHLCV (Open, High, Low, Close, Volume) candlestick data for a specific pool's price history. Use this endpoint to display price charts and historical trading data.

#### Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | Pool identifier (LP asset) |

#### Request Query

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| interval | string | **Yes** | - | Candlestick interval (see supported intervals below) |
| start_time | number | No | 1 year ago | Start timestamp in milliseconds |
| end_time | number | No | Current time | End timestamp in milliseconds |
| limit | number | No | `500` | Max results (min: `1`, max: `1000`) |

**Supported Intervals:**
- Minutes: `1m`, `5m`, `15m`, `30m`
- Hours: `1h`, `2h`, `4h`, `6h`, `12h`
- Days/Weeks/Months: `1d`, `1w`, `1M`

#### Request Response

```typescript
type Response = Candlestick[]

type Candlestick = {
  open: number,      
  high: number,      
  low: number,       
  close: number,     
  volume: number,    
  timestamp: number  
}
```
**Note:** Results are sorted by timestamp in ascending order.

### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd6.5553444d2d555344412d534c50/price/candlestick?interval=1w'
```

```json
[
  {
    "open": 1,
    "high": 1.0006422551006466,
    "low": 0.982164538002603,
    "close": 0.9985817609540729,
    "volume": 1162928.645893875,
    "timestamp": 1740960000000
  },
  {
    "open": 0.9991815087622149,
    "high": 1.003046739205926,
    "low": 0.9884252565466588,
    "close": 1.0004556637397555,
    "volume": 1983393.985634902,
    "timestamp": 1741564800000
  },
  {
    "open": 1.0005697563181883,
    "high": 1.0032710788557815,
    "low": 0.9938494885491757,
    "close": 0.994448078550209,
    "volume": 1197875.7042322678,
    "timestamp": 1742169600000
  }
]
```

### 4. Get Pool Price Timeseries

**GET:** `/v1/pools/:id/price/timeseries`

**Description:** Retrieve simplified timeseries price data for a specific pool over a given period. Use this endpoint for displaying price trends and historical price movements.

#### Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | string | Yes | Pool identifier (LP asset) |

#### Request Query

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| period | string | **Yes** | Time period to retrieve data for |

**Supported Periods:**
- `1d` - Last 24 hours
- `1w` - Last 7 days
- `1M` - Last 30 days
- `6M` - Last 6 months
- `1y` - Last 12 months
- `all` - All available data

#### Request Response

```typescript
// Array of price data points, sorted by timestamp in ascending order
type Response = PricePoint[]

type PricePoint = {
  value: number,
  timestamp: number 
}
```
**Note:** Results are sorted by timestamp in ascending order (oldest first).

### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd6.5553444d2d555344412d534c50/price/timeseries?period=1w'
```

```json
[
  {
    "value": 1.0094032988713695,
    "timestamp": 1764072000000
  },
  {
    "value": 1.009669208304249,
    "timestamp": 1764086400000
  },
  {
    "value": 1.0097130824357143,
    "timestamp": 1764100800000
  }
]
```



  
