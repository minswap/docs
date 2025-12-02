# Minswap APIs

## Pools APIs
Base URL: `https://api-mainnet-prod.minswap.org`

### 1. Get pools metrics:

#### API Description:
This API for get the list pool metrics data.

POST: `/v1/pools/metrics`

#### Request Body
| Name | Type | Mandatory | Description |
|------|------|-----------|-------------|
| tern | string | No | |
| limit|number | No | Minimum value 1, maximum value 100, default: 20 |
| only_verified | boolean | No | Dedault value `false` |
| search_after | string[] | No ||
| sort_direction | SortDirection | No | |
| sort_field | string | No | Values: `volume_usd_24h`, `volume_usd_7d`, `liquidity_usd`|
| protocols | Protocol[] | No | |


#### Request Response
```ts
  type Token = {
    currency_symbol: string,
    token_name: string,
    is_verified: boolean,
    metadata: TokenMedata,
    social_links: TokenSocialLinks
  }

  type TokenMedata = {
    name: string,
    decimals: number,
    ticker: string,
    url: string,
    logo: string,
    description: string,
  }

  type TokenSocialLinks = {
    website: string,
    discord: string,
    telegram: string,
    twitter: string,
    coingecko: string,
    coin_market_cap: string,
  }

  enum Protocol {
    Minswap = "Minswap",
    MinswapV2 = "MinswapV2",
    MinswapStable = "MinswapStable",
  }

  enum SortDirection {
    Asc = "asc",
    Desc = "desc",
  }

  type PoolMetricsRespone = {
    search_after: string[],
    pool_metrics: {
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
      trading_fee_tier: number[],
      trading_fee_apr: number[],
    }
  }
```
#### Example
```bash
curl --location 'http://localhost/v1/pools/metrics' \
--header 'Content-Type: application/json' \
--data '{}'
```

```json
{
	"search_after": [
		504648.73646031605,
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



  
