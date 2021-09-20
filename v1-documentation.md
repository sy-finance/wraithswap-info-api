# Documentation

All WraithSwap pairs consist of two different tokens. FTM is not a native currency in WraithSwap, and is represented only by WFTM in the pairs. 

The canonical WFTM address used by the WraithSwap interface is `0x21be370d5312f44cb42ce377bc9b8a0cef1a4c83`.

Results are cached for 5 minutes (or 300 seconds).

## [`/summary`](https://api.wraithswap.finance/api/summary)

Returns data for the top ~1000 WraithSwap pairs, sorted by reserves. 

### Request

`GET https://api.wraithswap.finance/api/summary`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "0x..._0x...": {                  // ERC20 token addresses, joined by an underscore
      "price": "...",                 // price denominated in token1/token0
      "base_volume": "...",           // last 24h volume denominated in token0
      "quote_volume": "...",          // last 24h volume denominated in token1
      "liquidity": "...",             // liquidity denominated in USD
      "liquidity_FTM": "..."          // liquidity denominated in FTM
    },
    // ...
  }
}
```

## [`/tokens`](https://api.wraithswap.finance/api/tokens)

Returns the tokens in the top ~1000 pairs on WraithSwap, sorted by reserves.

### Request

`GET https://api.wraithswap.finance/api/tokens`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "0x...": {                        // the address of the ERC20 token
      "name": "...",                  // not necessarily included for ERC20 tokens
      "symbol": "...",                // not necessarily included for ERC20 tokens
      "price": "...",                 // price denominated in USD
      "price_FTM": "...",             // price denominated in FTM
    },
    // ...
  }
}
```

## [`/tokens/0x...`](https://api.wraithswap.finance/api/tokens/0x4cf098d3775bd78a4508a13e126798da5911b6cd)

Returns the token information, based on address.

### Request

`GET https://api.wraithswap.finance/api/tokens/0x4cf098d3775bd78a4508a13e126798da5911b6cd`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "name": "...",                    // not necessarily included for ERC20 tokens
    "symbol": "...",                  // not necessarily included for ERC20 tokens
    "price": "...",                   // price denominated in USD
    "price_FTM": "...",               // price denominated in FTM
  }
}
```

## [`/pairs`](https://api.wraithswap.finance/api/pairs)

Returns data for the top ~1000 WraithSwap pairs, sorted by reserves.

### Request

`GET https://api.wraithswap.finance/api/pairs`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "0x..._0x...": {                  // the asset ids of FTM and ERC20 tokens, joined by an underscore
      "pair_address": "0x...",        // pair address
      "base_name": "...",             // token0 name
      "base_symbol": "...",           // token0 symbol
      "base_address": "0x...",        // token0 address
      "quote_name": "...",            // token1 name
      "quote_symbol": "...",          // token1 symbol
      "quote_address": "0x...",       // token1 address
      "price": "...",                 // price denominated in token1/token0
      "base_volume": "...",           // volume denominated in token0
      "quote_volume": "...",          // volume denominated in token1
      "liquidity": "...",             // liquidity denominated in USD
      "liquidity_FTM": "..."          // liquidity denominated in FTM
    },
    // ...
  }
}
```
