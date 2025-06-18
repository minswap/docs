# Minswap Aggregator API

The Minswap Aggregator API provides direct access to Minswap's aggregation functionality for partners who want to implement their own interface and control the trading logic.

## Base URL

All API endpoints are accessible at:
```
https://monorepo-mainnet-prod.minswap.org/aggregator
```

## Supported DEX Protocols

The aggregator supports the following DEX protocols:

```typescript
type Protocol =
    | "MinswapV2"        
    | "Minswap"          
    | "MinswapStable"    
    | "MuesliSwap"       
    | "Splash"           
    | "SundaeSwapV3"     
    | "SundaeSwap"       
    | "VyFinance"        
    | "WingRidersV2"     
    | "WingRiders"       
    | "WingRidersStableV2" 
    | "Spectrum"         
    | "SplashStable";    
```

This protocol enum is used in various endpoints.

## Endpoints

<details>
<summary><strong>GET /ada-price - Get current ADA price in multiple currencies</strong></summary>

Retrieve the current ADA price and 24-hour price change in a specified currency.

```http
GET /ada-price
```

#### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `currency` | `string` | Yes | The currency code to get the ADA price in. Must be one of the supported currencies (see below). |

#### Supported Currencies

The following currency codes are supported:

| Code | Currency | | Code | Currency | | Code | Currency |
|------|----------|-|------|----------|-|------|----------|
| `aed` | UAE Dirham | | `hkd` | Hong Kong Dollar | | `php` | Philippine Peso |
| `ars` | Argentine Peso | | `huf` | Hungarian Forint | | `pkr` | Pakistani Rupee |
| `aud` | Australian Dollar | | `idr` | Indonesian Rupiah | | `pln` | Polish Złoty |
| `bdt` | Bangladeshi Taka | | `ils` | Israeli New Shekel | | `rub` | Russian Ruble |
| `bhd` | Bahraini Dinar | | `inr` | Indian Rupee | | `sar` | Saudi Riyal |
| `bmd` | Bermudian Dollar | | `jpy` | Japanese Yen | | `sek` | Swedish Krona |
| `brl` | Brazilian Real | | `krw` | South Korean Won | | `sgd` | Singapore Dollar |
| `cad` | Canadian Dollar | | `kwd` | Kuwaiti Dinar | | `thb` | Thai Baht |
| `chf` | Swiss Franc | | `lkr` | Sri Lankan Rupee | | `try` | Turkish Lira |
| `clp` | Chilean Peso | | `mmk` | Myanmar Kyat | | `twd` | New Taiwan Dollar |
| `cny` | Chinese Yuan | | `mxn` | Mexican Peso | | `uah` | Ukrainian Hryvnia |
| `czk` | Czech Koruna | | `myr` | Malaysian Ringgit | | `usd` | US Dollar |
| `dkk` | Danish Krone | | `ngn` | Nigerian Naira | | `vef` | Venezuelan Bolívar |
| `eur` | Euro | | `nok` | Norwegian Krone | | `vnd` | Vietnamese Đồng |
| `gbp` | British Pound | | `nzd` | New Zealand Dollar | | `xdr` | Special Drawing Rights |
| | | | | | | `zar` | South African Rand |

#### Response

```typescript
{
  currency: string;  // The requested currency code
  value: {
    change_24h: number;  // 24-hour price change
    price: number;     // Current price in the requested currency
  } | null;           // null if price data is unavailable
}
```

#### Example Request

```bash
curl "${BASE_URL}/adaPrice?currency=usd"
```

#### Example Response

```json
{
  "currency": "usd",
  "value": {
    "change_24h": -2.34,  // -2.34% change in last 24 hours
    "price": 0.75        // Current price: $0.75 per ADA
  }
}
```

</details>

<details>
<summary><strong>GET /wallet - Query wallet balances and token information</strong></summary>

Retrieve wallet balance information including ADA and native tokens.

```http
GET /wallet
```

#### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `address` | `string` | Yes | The Cardano wallet address to query, support both Cbor and Hex format |

#### Response

```typescript
{
  wallet: string;              // The wallet address in cbor format
  ada: string;                 // ADA balance in lovelace (1 ADA = 1,000,000 lovelace)
  minimum_lovelace: string;    // Minimum required ADA for the wallet
  balance: Array<{            // Array of token balances
    asset: {
      token_id: string;       // Token identifier in format <policyId><tokenName>, or "lovelace" for ADA
      ticker?: string;        // Token ticker symbol (if available)
      is_verified?: boolean;  // Token verification status
      price_by_ada?: number;  // Token price in ADA
      project_name?: string;  // Project name (if available)
      decimals?: number;      // Token decimals (6 for ADA)
    };
    amount: string;           // Token balance amount
  }>;
}
```

#### Example Request

```bash
curl "${BASE_URL}/wallet?address=addr1..."
```

#### Example Response

```json
{
  "wallet": "addr1...",
  "ada": "5000000",
  "minimum_lovelace": "1000000",
  "balance": [
    {
      "asset": {
        "token_id": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e",
        "ticker": "MIN",
        "is_verified": true,
        "price_by_ada": 1.5,
        "project_name": "Minswap",
        "decimals": 6
      },
      "amount": "1000000000"
    }
  ]
}
```

</details>

<details>
<summary><strong>POST /tokens - Search and filter token information</strong></summary>

Search for tokens with optional filtering and pagination support.

```http
POST /tokens
```

#### Request Body

```typescript
{
  query: string;            // Search query string (e.g., token name, ticker)
  only_verified: boolean;   // If true, returns only verified tokens those are verified by Minswap
  assets?: string[];       // Optional list of specific token_ids to fetch
  search_after?: string[]; // Optional pagination cursor from previous response
}
```

#### Response

```typescript
{
  tokens?: Array<{
    token_id: string;       // Token identifier in format <policyId><tokenName>, or "lovelace" for ADA
    ticker?: string;        // Token ticker symbol (if available)
    is_verified?: boolean;  // Token verification status
    price_by_ada?: number;  // Token price in ADA
    project_name?: string;  // Project name (if available)
    decimals?: number;      // Token decimals
  }>;
  search_after: string[];   // Pagination cursor for next page
}
```

#### Example Request

```bash
curl "${BASE_URL}/tokens" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "query": "min",
    "only_verified": true,
  }'
```

#### Example Response

```json
{
  "tokens": [
    {
      "token_id": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e",
      "ticker": "MIN",
      "is_verified": true,
      "price_by_ada": 1.5,
      "project_name": "Minswap",
      "decimals": 6
    },
    ...
  ],
  "search_after": [...]
}
```

</details>

<details>
<summary><strong>POST /estimate - Get optimal swap route and price estimation</strong></summary>

Get the best possible swap route and price estimation across multiple DEX protocols.

```http
POST /estimate
```

#### Request Body

```typescript
{
  amount: string;             // Amount of input token (in smallest unit)
  token_in: string;          // Token identifier for input token (<policyId><tokenName> or "lovelace")
  token_out: string;         // Token identifier for output token (<policyId><tokenName> or "lovelace")
  slippage: number;          // Slippage tolerance (e.g., 0.5 for 0.5%)
  exclude_protocols?: string[]; // Optional protocols to exclude from routing
  allow_multi_hops?: boolean;   // Optional, allow routes through MinswapV2 - Multi Route (default: true)
  partner?: string;          // Optional partner code for tracking and fee sharing
}
```

#### Response

```typescript
{
  token_in: string;          // Input token identifier
  token_out: string;         // Output token identifier
  amount_in: string;         // Input amount (in smallest unit)
  amount_out: string;        // Expected output amount without slippage (in smallest unit)
  min_amount_out: string;    // Minimum output amount considering slippage
  total_lp_fee: string;      // Total LP fees for the route (amount of token_in)
  total_dex_fee: string;     // Total DEX fees for the route (amount of ADA)
  deposits: string;          // Required deposits for the swap (amount of ADA)
  avg_price_impact: number;  // Average price impact percentage
  paths: Array<Array<{      // Array of possible swap paths
    pool_id: string;        // Pool identifier
    protocol: string;       // DEX protocol used (e.g., "MinswapV2", "Minswap")
    lp_token: string;       // LP token identifier
    token_in: string;       // Input token for this hop
    token_out: string;      // Output token for this hop
    amount_in: string;      // Input amount for this hop
    amount_out: string;     // Output amount for this hop
    min_amount_out: string; // Minimum output with slippage
    lp_fee: string;        // LP fee for this hop
    dex_fee: string;       // DEX fee for this hop
    deposits: string;      // Required deposits for this hop
    price_impact: number;  // Price impact for this hop
  }>>;
  aggregator_fee?: string;   // Optional aggregator fee amount (amount of ADA)
  aggregator_fee_percent_num?: number;  // Numerator of fee percentage
  aggregator_fee_percent_den?: number;  // Denominator of fee percentage
}
```

#### Example Request

```bash
curl "${BASE_URL}/estimate" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "amount": "10000000",
    "token_in": "lovelace",
    "token_out": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e",
    "slippage": 0.5,
    "allow_multi_hops": true
  }'
```

#### Example Response

```json
{
  "token_in": "lovelace",
  "token_out": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e",
  "amount_in": "10000000",
  "amount_out": "15000000",
  "min_amount_out": "14850000",
  "total_lp_fee": "30000",
  "total_dex_fee": "10000",
  "deposits": "2000000",
  "avg_price_impact": 0.25,
  "paths": [
    [
      {
        "pool_id": "pool1...",
        "protocol": "MinswapV2",
        "lp_token": "asset1...",
        "token_in": "lovelace",
        "token_out": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e",
        "amount_in": "10000000",
        "amount_out": "15000000",
        "min_amount_out": "14850000",
        "lp_fee": "30000",
        "dex_fee": "10000",
        "deposits": "2000000",
        "price_impact": 0.25
      }
    ]
  ],
  "aggregator_fee": "5000",
  "aggregator_fee_percent_num": 3,
  "aggregator_fee_percent_den": 1000
}
```

#### Notes

- Amounts are always in the smallest unit (lovelace for ADA, considering token decimals for others)
- `min_amount_out` is calculated based on the provided slippage tolerance
- The `paths` array has two dimensions:
  1. First dimension: Splits the trade into separate orders for optimal execution (e.g., splitting a large trade into smaller ones across multiple DEXs)
  2. Second dimension: For each split order, contains possible execution routes through different pools
- `allow_multi_hops` enables/disables indirect routes that swap through intermediate tokens (e.g., Token A → ADA → Token B)

</details>

<details>
<summary><strong>POST /build-tx - Build a swap transaction</strong></summary>

Build an unsigned swap transaction based on the estimated swap route. This endpoint generates a transaction CBOR that needs to be signed by the user's wallet.

```http
POST /build-tx
```

#### Request Body

```typescript
{
  sender: string;           // The sender's Cardano wallet address
  min_amount_out: string;  // Minimum amount to receive (from /estimate response)
  estimate: {              // The swap parameters (same as /estimate request)
    amount: string;        // Amount of input token (in smallest unit)
    token_in: string;      // Input token identifier
    token_out: string;     // Output token identifier
    slippage: number;      // Slippage tolerance (e.g., 0.5 for 0.5%)
    exclude_protocols?: string[];  // Optional protocols to exclude
    allow_multi_hops?: boolean;   // Optional, allow multi-hop routes
    partner?: string;      // Optional partner code for tracking and fee sharing
  }
}
```

#### Response

```typescript
{
  cbor: string;  // The unsigned transaction in CBOR format
}
```

#### Example Request

```bash
curl "${BASE_URL}/build-tx" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "sender": "addr1...",
    "min_amount_out": "14850000",
    "estimate": {
      "amount": "10000000",
      "token_in": "lovelace",
      "token_out": "29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e",
      "slippage": 0.5,
      "allow_multi_hops": true
    }
  }'
```

#### Example Response

```json
{
  "cbor": "84a500818258..."  // Abbreviated for readability
}
```

#### Notes

- After receiving the transaction CBOR, it needs to be:
  1. Signed by the user's wallet
  2. Submitted using the /finalize-and-submit-tx endpoint
- Use the `min_amount_out` value from the /estimate response to ensure consistent slippage protection
- The transaction will fail if submitted after the route becomes invalid (e.g., due to price changes)
</details>

<details>
<summary><strong>POST /finalize-and-submit-tx - Submit a signed transaction</strong></summary>

Submit a signed transaction to the Cardano network. This endpoint is used to submit transactions after they have been signed by the user's wallet.

```http
POST /finalize-and-submit-tx
```

#### Request Body

```typescript
{
  cbor: string;         // The original transaction CBOR from /build-tx
  witness_set: string;  // The signature witness set from the wallet
}
```

#### Response

```typescript
{
  tx_id: string;  // The transaction ID (hash) of the submitted transaction
}
```

#### Example Request

```bash
curl "${BASE_URL}/finalize-and-submit-tx" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "cbor": "84a500818258...",
    "witness_set": "a100818258..."
  }'
```

#### Example Response

```json
{
  "tx_id": "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef"
}
```

#### Notes

- The `cbor` should be the exact transaction CBOR received from /build-tx
- The `witness_set` is generated by the wallet when signing the transaction
- The transaction will be validated before submission to ensure:
  1. The signature is valid
  2. The transaction meets all Cardano network requirements
- If submission fails, you may need to:
  1. Get a new quote from /estimate
  2. Build a new transaction with /build-tx
  3. Get it signed again by the wallet
  4. Retry submission
</details>

<details>
<summary><strong>POST /cancel-tx - Build a transaction to cancel pending orders</strong></summary>

Build an unsigned transaction that cancels one or more pending orders on various DEX protocols.

```http
POST /cancel-tx
```

#### Request Body

```typescript
{
  sender: string;           // The sender's Cardano wallet address
  orders: Array<{          // Array of orders to cancel (1-6 orders)
    tx_in: string;         // Transaction input containing the order to cancel. <tx_id>#<tx_index> format.
    protocol: string;      // The DEX protocol where the order exists
  }>;
}
```

#### Response

```typescript
{
  cbor: string;  // The unsigned cancel transaction in CBOR format
}
```

#### Example Request

```bash
curl "${BASE_URL}/cancel-tx" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "sender": "addr1...",
    "orders": [
      {
        "tx_in": "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef#1",
        "protocol": "MinswapV2"
      }
    ]
  }'
```

#### Example Response

```json
{
  "cbor": "84a500818258..."  // Abbreviated for readability
}
```

#### Notes

- You can cancel up to 6 orders in a single transaction
- Each `tx_in` should be in the format: `<tx_id>#<tx_index>`
- Supported protocols can be found in the /estimate endpoint documentation
- After receiving the transaction CBOR:
  1. Get it signed by the user's wallet
  2. Submit using the `/finalize-and-submit-tx` endpoint
- Orders can only be cancelled by the address that created them
- The transaction will fail if any of the orders have already been fulfilled or cancelled
</details>

