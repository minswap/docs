# Minswap APIs

This documentation provides comprehensive information about Minswap's public APIs for accessing pool metrics, asset data, and price information.

## Table of Contents

- [Getting Started](#getting-started)
- [HTTP Status Codes](#http-status-codes)
- [Common Types](#common-types)
- [Assets APIs](#assets-apis)
  - [Get List Assets](#1-get-list-assets)
  - [Get Assets Metrics](#2-get-assets-metrics)
  - [Get Asset Metrics](#3-get-asset-metrics)
  - [Get Asset Price Candlestick](#4-get-asset-price-candlestick)
  - [Get Asset Price Timeseries](#5-get-asset-price-timeseries)
- [Pools APIs](#pools-apis)
  - [Get Pools Metrics](#1-get-pools-metrics)
  - [Get Pool Metrics by ID](#2-get-pool-metrics-by-id)
  - [Get Pool Price Candlestick](#3-get-pool-price-candlestick)
  - [Get Pool Price Timeseries](#4-get-pool-price-timeseries)
  - [Get Pool Volume Timeseries](#5-get-pool-volume-timeseries)
  - [Get Pool TVL Timeseries](#6-get-pool-tvl-timeseries)
  - [Get Pool Fee Timeseries](#7-get-pool-fee-timeseries)

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
type Asset = {
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

type SupportedCurrency = 'aed' | 'ars' | 'aud' | 'bdt' | 'bhd' | 'bmd' | 'brl' | 'cad' | 'chf' | 'clp' | 'cny' | 'czk' | 'dkk' | 'eur' | 'gbp' | 'hkd' | 'huf' | 'idr' | 'ils' | 'inr' | 'jpy' | 'krw' | 'kwd' | 'lkr' | 'mmk' | 'mxn' | 'myr' | 'ngn' | 'nok' | 'nzd' | 'php' | 'pkr' | 'pln' | 'rub' | 'sar' | 'sek' | 'sgd' | 'thb' | 'try' | 'twd' | 'uah' | 'usd' | 'vef' | 'vnd' | 'xdr' | 'zar';

type TimeSeriesPeriod = "1d" | "1w" | "1M" | "6M" | "1y" | "all";

/**
 * Minutes: `1m`, `5m`, `15m`, `30m`
 * Hours: `1h`, `2h`, `4h`, `6h`, `12h`
 * Days/Weeks/Months: `1d`, `1w`, `1M`
 */
type CandlestickInterval = "1m" | "5m" | "15m" | "30m" | "1h" | "2h" | "4h" | "6h" | "12h" | "1d" | "1w" | "1M"

type Ohlcv = {
  open: number;
  high: number;
  low: number;
  close: number;
  volume: number;
  timestamp: number;
}
```

## Assets APIs

### 1. Get List Assets

**GET:** `/v1/assets`

**Description:** Retrieve a paginated list of assets available on Minswap with their metadata and verification status. Use this endpoint to populate asset selection interfaces or search for specific assets.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| term | string | No | `""` | Search by asset name, currency symbol, token name, or ticker |
| limit | number | No | `20` | Number of results per page (min: `1`, max: `100`) |
| only_verified | boolean | No | `false` | Filter to show only verified tokens |
| search_after | string[] | No | `[]` | Pagination cursor from previous response |

**Note:** For pagination, use the `search_after` value from the previous response to get the next page of results.

#### Request Response

```typescript

type AssetsResponse = {
  search_after: string[] | undefined;
  assets: Asset[];
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

### 2. Get Assets Metrics

**POST:** `/v1/assets/metrics`

**Description:** Retrieve a paginated list of assets available on Minswap with their metadata and verification status. Use this endpoint to populate asset selection interfaces or search for specific assets.

#### Request Body

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| term | string | No | `""` | Search by asset name, currency symbol, token name, or ticker |
| limit | number | No | `20` | Number of results per page (min: `1`, max: `100`) |
| only_verified | boolean | No | `true` | Filter to show only verified tokens |
| search_after | string[] | No | `[]` | Pagination cursor from previous response |
| sort_direction | string | No | `desc` | Sort order: `asc` or `desc` |
| sort_field | string | No | `volume_24h` | Sort by: `price_change_1h`, `price_change_24h`, `price_change_7d`, `volume_1h`, `volume_24h`, `volume_7d`, `liquidity`, `market_cap`, `fully_diluted`, `total_supply`, `circulating_supply` |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

**Note:** For pagination, use the `search_after` value from the previous response to get the next page of results.

#### Request Response

```typescript
type Response = {
  search_after: string[] | undefined,
  asset_metrics: AssetMetric[];       
}

type AssetMetric = {
  asset: Asset;
  price_change_1h: number;
  price_change_24h: number;
  price_change_7d: number;
  volume_1h: number;
  volume_24h: number;
  volume_7d: number;
  total_supply: number;
  circulating_supply: number;
  created_at?: string;
  created_tx_id?: string;
  categories?: string[];
  price: number;
  liquidity: number;
  market_cap: number;
  fully_diluted: number;
}

```
#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/assets/metrics' \
--data '{
    "term": "",
    "limit": 1,
    "only_verified": true,
    "sort_direction": "desc",
    "sort_field": "liquidity",
    "currency": "usd"
}'
```

```json
{
    "search_after": [
        "9954917.19354675",
        "c48cbb3d5e57ed56e276bc45f99ab39abe94e6cd7ac39fb402da47ad.0014df105553444d"
    ],
    "asset_metrics": [
        {
            "asset": {
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
            "total_supply": 0,
            "circulating_supply": 0,
            "created_at": "2024-03-17T00:21:21.000Z",
            "created_tx_id": "ac1cb7d3bc2a6e1a356b16c959e222608005524fc0c35919b63574d6b0b20b5a",
            "categories": [
                "Stablecoin"
            ],
            "price": 0.9975544277153409,
            "price_change_1h": 0.02207271877209818,
            "price_change_24h": -2.350271288070098,
            "price_change_7d": -0.09023188511685103,
            "volume_1h": 15276.40548938064,
            "volume_24h": 1058967.9023246677,
            "volume_7d": 7092205.7164879,
            "liquidity": 9954917.19354675,
            "market_cap": 0,
            "fully_diluted": 0
        }
    ]
}
```
### 3. Get Asset Metrics

**GET:** `v1/assets/:id/metrics`

**Description:** Retrieves detailed metrics for a specific asset by its ID, optionally filtered by display currency. It returns comprehensive asset statistics such as volume, liquidity, and price data for use in analytics or UI display.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | The id parameter is a required string that uniquely identifies the asset for which metrics are being requested (ID asset in format: `{policy_id}{token_name}`) |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response

```typescript
type Response = {
  asset: RestAssetMetadata;
  price_change_1h: number;
  price_change_24h: number;
  price_change_7d: number;
  volume_1h: number;
  volume_24h: number;
  volume_7d: number;
  total_supply: number;
  circulating_supply: number;
  created_at?: string;
  created_tx_id?: string;
  categories?: string[];
  price: number;
  liquidity: number;
  market_cap: number;
  fully_diluted: number;
}

```
#### Example

```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/assets/016be5325fd988fea98ad422fcfd53e5352cacfced5c106a932a35a442544e/metrics?currency=usd'
```
```json
{
    "asset": {
        "currency_symbol": "016be5325fd988fea98ad422fcfd53e5352cacfced5c106a932a35a4",
        "token_name": "42544e",
        "is_verified": true,
        "metadata": {
            "name": "BTN",
            "url": "https://butane.dev",
            "ticker": "BTN",
            "decimals": 6,
            "description": "BTN is the native token of Butane, an advanced synthetics protocol."
        },
        "social_links": {
            "website": "https://butane.dev",
            "discord": "https://discord.gg/butane",
            "telegram": "https://t.me/butaneprotocol",
            "twitter": "https://twitter.com/butaneprotocol"
        }
    },
    "total_supply": 25000000,
    "circulating_supply": 12432701.092661,
    "created_at": "2024-02-22T14:03:08.000Z",
    "created_tx_id": "c2d43135e34981fcb9a5db3d9b189c81d278adadc9940967f93980f8ee2b7074",
    "categories": [
        "DeFi"
    ],
    "price": 0.05475648065168212,
    "price_change_1h": 0.25619128949616055,
    "price_change_24h": -3.539488320210792,
    "price_change_7d": -32.212313963662844,
    "volume_1h": 0,
    "volume_24h": 150.8735360716138,
    "volume_7d": 55897.59149512404,
    "liquidity": 182029.9901877545,
    "market_cap": 680770.9568284391,
    "fully_diluted": 1368912.016292053
}
```
### 4. Get Asset Price Candlestick

**GET:** `v1/assets/:id/price/candlestick`

**Description:** Returns historical candlestick (OHLCV) price data for a specific asset, supporting custom time ranges and resolutions

#### Request Parameters
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | The id parameter is a required string that uniquely identifies the asset for which metrics are being requested (ID asset in format: `{policy_id}{token_name}`) |
| start_time | number | No | - | The Unix timestamp (in milliseconds) marking the start of the time range for the candlestick data. |
| end_time | number | No | - | The Unix timestamp (in milliseconds) marking the end of the time range for the candlestick data. |
| limit | number | No | `500` | Max results (min: `1`, max: `1000`) |
| interval | `CandlestickInterval` | Yes | - | Candlestick interval. |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response
```typescript
type Response = Ohlcv[]

type Ohlcv = {
  open: number;
  high: number;
  low: number;
  close: number;
  volume: number;
  timestamp: number;
}
```
#### Example

```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/assets/0691b2fecca1ac4f53cb6dfb00b7013e561d1f34403b957cbb5af1fa4e49474854/price/candlestick?end_time=1766028002000&interval=15m&currency=usd'
```
```json
[
    {
        "open": 0.05150856356161587,
        "high": 0.05150856356161587,
        "low": 0.05047932810976648,
        "close": 0.050701693758410896,
        "volume": 50724.16443664555,
        "timestamp": 1765578600000
    },
    {
        "open": 0.05093382373126923,
        "high": 0.05093382373126923,
        "low": 0.05030821733861369,
        "close": 0.050525200451240655,
        "volume": 26361.171205892428,
        "timestamp": 1765579500000
    }
]
```
### 5. Get Asset Price Timeseries

**GET:** `v1/assets/:id/price/timeseries`

**Description:** Retrieve simplified timeseries price data for a specific asset over a given period. Use this endpoint to analyze price trends and historical price movements.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | The id parameter is a required string that uniquely identifies the asset for which metrics are being requested (ID asset in format: `{policy_id}{token_name}`) |
| period | `TimeSeriesPeriod` | Yes | - | Time interval for aggregating the timeseries data |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response

```typescript
// Array of price data points, sorted by timestamp in ascending order
type Response = {
  value: number,
  timestamp: number 
}[]
```
#### Example

```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/assets/016be5325fd988fea98ad422fcfd53e5352cacfced5c106a932a35a442544e/price/timeseries?period=1w&currency=usd'
```
```json
[
    {
        "value": 0.21675761701343657,
        "timestamp": 1766476800000
    },
    {
        "value": 0.21675761701343657,
        "timestamp": 1766491200000
    }
]
```


## Pools APIs

Pools APIs provide comprehensive data about liquidity pools, including metrics, price history, and performance indicators.

### 1. Get Pools Metrics

**POST:** `/v1/pools/metrics`

**Description:** Retrieve a list of liquidity pools with their metrics including trading volume, liquidity, and trading fee APR. Use this endpoint to display pool statistics, compare pool performance, or filter pools by specific criteria.

#### Request Body

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| term | string | No | `""` | Search by asset name, currency symbol, ticker, or LP asset |
| limit | number | No | `20` | Number of results per page (min: `1`, max: `100`) |
| only_verified | boolean | No | `false` | Filter to show only pools with verified tokens |
| search_after | string[] | No | `[]` | Pagination cursor from previous response |
| sort_direction | string | No | `desc` | Sort order: `asc` or `desc` |
| sort_field | string | Yes | `liquidity` | Sort by: `volume_24h`, `volume_7d`, or `liquidity` |
| protocols | string[] | No | All | Filter by protocol: `Minswap`, `MinswapV2`, `MinswapStable` |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response

```typescript
type Response = {
  search_after: string[] | undefined,
  pool_metrics: PoolMetrics[]
}

type PoolMetrics = {
  lp_asset: AssetMetadata;
  type: Protocol;
  asset_a: AssetMetadata;
  asset_b: AssetMetadata;
  liquidity_raw: number;
  liquidity_a_raw: number;
  liquidity_b_raw: number;
  trading_fee_tier: number[];
  trading_fee_apr?: number;
  volume_24h: number;
  volume_7d: number;
  trading_fee_24h: number;
  trading_fee_7d: number;
  liquidity: number;
  liquidity_a: number;
  liquidity_b: number;
}

```
#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/metrics' \
--data '{
    "term": "",
    "only_verified": true,
    "limit": 1,
    "sort_field": "liquidity",
    "sort_direction": "desc",
    "currency": "usd"
}'
```

```json
{
    "search_after": [
        "10183179.86675752",
        "5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd6.5553444d2d555344412d534c50"
    ],
    "pool_metrics": [
        {
            "lp_asset": {
                "currency_symbol": "5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd6",
                "token_name": "5553444d2d555344412d534c50",
                "is_verified": true
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
            "trading_fee_tier": [
                0.05,
                0.05
            ],
            "trading_fee_apr": 0.3437032224976275,
            "liquidity_raw": 10053890543674,
            "liquidity_a_raw": 5393732.846663,
            "liquidity_b_raw": 4683667.353299,
            "volume_24h": 294243.8992270554,
            "volume_7d": 2042834.6864464958,
            "liquidity": 10183179.86675752,
            "liquidity_a": 5409159.8695964,
            "liquidity_b": 4774019.997161119,
            "trading_fee_24h": 73.6453803607475,
            "trading_fee_7d": 511.1735333229008
        }
    ]
}
```

### 2. Get Pool Metrics by ID

**GET:** `/v1/pools/:id/metrics`

**Description:** Retrieve detailed metrics for a specific liquidity pool using its unique identifier (LP asset). Use this endpoint to display detailed pool information on pool detail pages.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | LP asset ID combining policy ID and token name: `{policy_id}{token_name}` |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |


#### Request Response
```typescript
type PoolMetrics = {
  lp_asset: AssetMetadata;
  type: Protocol;
  asset_a: AssetMetadata;
  asset_b: AssetMetadata;
  liquidity_raw: number;
  liquidity_a_raw: number;
  liquidity_b_raw: number;
  trading_fee_tier: number[];
  trading_fee_apr: number;
  volume_24h: number;
  volume_7d: number;
  trading_fee_24h: number;
  trading_fee_7d: number;
  liquidity: number;
  liquidity_a: number;
  liquidity_b: number;
}

```

#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd65553444d2d555344412d534c50/metrics?currency=usd'
```

```json
{
    "lp_asset": {
        "currency_symbol": "5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd6",
        "token_name": "5553444d2d555344412d534c50",
        "is_verified": true
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
    "trading_fee_tier": [
        0.05,
        0.05
    ],
    "trading_fee_apr": 0.3436275699948192,
    "liquidity_raw": 10053890543674,
    "liquidity_a_raw": 5393732.846663,
    "liquidity_b_raw": 4683667.353299,
    "volume_24h": 294243.8992270554,
    "volume_7d": 2020489.306139798,
    "liquidity": 10183179.86675752,
    "liquidity_a": 5409159.8695964,
    "liquidity_b": 4774019.997161119,
    "trading_fee_24h": 73.6453803607475,
    "trading_fee_7d": 505.84438543787957
}
```

### 3. Get Pool Price Candlestick

**GET:** `/v1/pools/:id/price/candlestick`

**Description:** Retrieve OHLCV (Open, High, Low, Close, Volume) candlestick data for a specific pool's price history. Use this endpoint to display price charts and historical trading data.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | LP asset ID combining policy ID and token name: `{policy_id}{token_name}` |
| start_time | number | No | - | The Unix timestamp (in milliseconds) marking the start of the time range for the candlestick data. |
| end_time | number | No | - | The Unix timestamp (in milliseconds) marking the end of the time range for the candlestick data. |
| limit | number | No | `500` | Limit the number of candlestick records returned (min: `1`, max: `1000`) |
| interval | `CandlestickInterval` | Yes | - | Candlestick interval. |

#### Request Response

```typescript
type Response = Ohlcv[]
```
**Note:** Results are sorted by timestamp in ascending order.

#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd65553444d2d555344412d534c50/price/candlestick?limit=20&interval=1d&start_time=1767259443000&end_time=1767864243000'
```

```json
[
    {
        "open": 1.0113540174376618,
        "high": 1.012268074014591,
        "low": 1.0108867111873354,
        "close": 1.0115087260420723,
        "volume": 571529.0232354626,
        "timestamp": 1767312000000
    },
    {
        "open": 1.0115018499993238,
        "high": 1.0115018499993238,
        "low": 1.0104833741322214,
        "close": 1.0113550182936037,
        "volume": 463985.1281049333,
        "timestamp": 1767398400000
    }
]
```

### 4. Get Pool Price Timeseries

**GET:** `/v1/pools/:id/price/timeseries`

**Description:** Retrieve simplified timeseries price data for a specific pool over a given period. Use this endpoint for displaying price trends and historical price movements.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | LP asset ID combining policy ID and token name: `{policy_id}{token_name}` |
| period | `TimeSeriesPeriod` | Yes | - | Time interval for aggregating the timeseries data |

#### Request Response

```typescript
// Array of price data points, sorted by timestamp in ascending order
type Response = {
  value: number,
  timestamp: number 
}[]
```
**Note:** Results are sorted by timestamp in ascending order (oldest first).

#### Example
```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd65553444d2d555344412d534c50/price/timeseries?period=1w'
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
### 5. Get Pool Volume Timeseries

**GET:** `v1/pools/:id/volume/timeseries`

**Description:** Retrieve trading volume timeseries data for a specific pool over a given period. Use this endpoint to analyze trading activity and volume trends over time.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | LP asset ID combining policy ID and token name: `{policy_id}{token_name}` |
| period | `TimeSeriesPeriod` | Yes | - | Time interval for aggregating the timeseries data |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response

```typescript
type Response = {
  value: number;
  timestamp: number;
}[]
```

#### Example

```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd65553444d2d555344412d534c50/volume/timeseries?period=1d'
```

```json
[
    {
        "value": 33236.80321708667,
        "timestamp": 1767340800000
    },
    {
        "value": 29202.326747222072,
        "timestamp": 1767355200000
    }
]
```
### 6. Get Pool TVL Timeseries

**GET:** `v1/pools/:id/tvl/timeseries`

**Description:** Retrieve total value locked (TVL) timeseries data for a specific pool over a given period. Use this endpoint to track liquidity changes and pool growth metrics over time.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | LP asset ID combining policy ID and token name: `{policy_id}{token_name}` |
| period | `TimeSeriesPeriod` | Yes | - | Time interval for aggregating the timeseries data |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response

```typescript
type Response = {
  value: number;
  timestamp: number;
}[]
```

#### Example

```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd65553444d2d555344412d534c50/tvl/timeseries?period=1w&currency=usd'
```

```json
[
    {
        "value": 27414288.316657227,
        "timestamp": 1766476800000
    },
    {
        "value": 28325724.627680056,
        "timestamp": 1766491200000
    }
]
```
### 7. Get Pool Fee Timeseries

**GET:** `v1/pools/:id/fees/timeseries`

**Description:** Retrieve accumulated trading fees timeseries data for a specific pool over a given period. Use this endpoint to analyze fee generation and revenue performance of liquidity pools.

#### Request Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|-------------|---------|
| id | string | Yes | - | LP asset ID combining policy ID and token name: `{policy_id}{token_name}` |
| period | `TimeSeriesPeriod` | Yes | - | Time interval for aggregating the timeseries data |
| currency | `SupportedCurrency` | No | - | Return values are in ADA if there is no value |

#### Request Response

```typescript
type Response = {
  value: number;
  timestamp: number;
}[]
```

#### Example

```bash
curl --location 'https://api-mainnet-prod.minswap.org/v1/pools/5f0d38b3eb8fea72cd3cbdaa9594a74d0db79b5a27e85be5e9015bd65553444d2d555344412d534c50/fees/timeseries?period=1d&currency=usd'
```

```json
[
    {
        "value": 0,
        "timestamp": 1767060000000
    },
    {
        "value": 0.9978481459422092,
        "timestamp": 1767061800000
    }
]
```



  
