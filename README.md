# tap.exchange api

This repo provides an overview of the available API endpoints for tap.exchange and their responses.

## Get All Deployed Tokens

**Endpoint**

``` GET tap.exchange/api/renderAllTokens/ ```

**Description**

Returns a JSON array of all tokens deployed till date.

**Response**

```
[
  {
    "tick": "string",
    "max": "string", //bigint string
    "lim": "string", //bigint string
    "dec": 0,
    "blck": 0,
    "tx": "string",
    "ins": "string",
    "num": 0,
    "ts": 0,
    "addr": "string",
    "crsd": true
  }
]
```
## Get Token Details by Address

**Endpoint**

``` GET tap.exchange/api/accounts/{address} ```

**Description**

Returns a JSON array of token details held by the specified address where the balance of tokens is not equal to 0.

**Request Parameters**

* address (string): The address for which token details are requested.

**Response**

```
[
  {
    "ticker": "string",
    "balance": 0,
    "transferable": 0,
    "dec": 0,
    "available": 0
  }
]

```
## Get Transaction History by Address and Ticker

**Endpoint**

``` GET tap.exchange/api/accounts/{address}/{ticker} ```

**Description**

Returns a JSON array containing the transaction history for the specified ticker and address, ordered from the latest to the earliest transactions.

**Request Parameters**

* **address** (string): The address for which token details are requested.
* **ticker** (string): The specific token ticker.

**Response**

```
[
  {
    "id": "string",
    "number": "string",
    "method": "string",
    "quantity": 0,
    "balance": 0,
    "from": "string",
    "to": "string",
    "datetime": "string"
  }
]

```

## Get Token Details

**Endpoint**

``` GET tap.exchange/api/tokens/{ticker} ```

**Description**

Returns a JSON object containing deployment details, mint tokens left, holders count, and addresses with balances and transferable tokens for the specified token.

**Request Parameters**

* **ticker** (string): The specified token ticker.

**Response**

```
{
  "deployment": {
    "tick": "string",
    "max": "string",
    "lim": "string",
    "dec": 0,
    "blck": 0,
    "tx": "string",
    "ins": "string",
    "num": 0,
    "ts": 0,
    "addr": "string",
    "crsd": true
  },
  "mintTokensLeft": "string",
  "holdersCount": 0,
  "holders": [
    {
      "address": "string",
      "balance": "string",
      "transferable": "string"
    }
  ]
}
```
## Get Transaction History for a Token

**Endpoint**

``` GET tap.exchange/api/tokens/{ticker}/history ```

**Description**

Returns a JSON array containing the transaction history for the specified token.

**Request Parameters**

* **ticker** (string): The specified token ticker.

**Response**

```
[
  {
    "id": "string",
    "number": 0,
    "method": "string",
    "quantity": 0,
    "balance": 0,
    "from": "string",
    "to": "string",
    "datetime": "string"
  }
]
```
