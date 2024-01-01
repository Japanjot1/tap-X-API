
# tapX.app API documentation

This repository provides an overview of the available API endpoints for tapX and their responses.

## Get All Deployed Tokens

**Endpoint**

``` GET tapX.app/api/renderAllTokens/ ```

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
## Get Deployed Tokens ( Paginated ) from TRAC-API

**Endpoint**

``` GET tapX.app/api/v2/renderAllTokensPaged?offset={offset}&max={max}```

**Request Query Parameters**

* offset ( required ): The offset for the query.
* max ( required ): max to fetch.

**Description**

Returns a paginated JSON array  of all tokens deployed till date. 

**Response**

```
{
	deploymentsLength:0,
	deployments:[
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
}
```
## Get Deployed Tokens ( Paginated ) from TAPX-DB

**Endpoint**

``` GET tapX.app/api/v2/renderAllTokensDB?```

**Request Query Parameters**

* p ( required ): The offset for the query.
* sort ( optional ): Sort to be applied ("hc" : holdersCount || "dt" : date deployed || "tx":tx 		   	    Count || "prg" : Progress) 
* q ( optional ) : Search query string. 
* status ( optional ) : The current status of token , minting or completed ( 'all' || 'completed' || 'minting')
* tapart( optional ) : Filter tapart switch. To filter for tapart and tokens. ( 'true' || 'false' )

**Description**

Returns a paginated JSON array  of all tokens deployed till date from TAPX-DB. 

**Response**

```
{
	totalCount:0,
	deployments:[
	  {
		    "ticker": "string",
		    "Progress": 0, 
		    "holderscount": 0, 
		    "transactions": 0,
		    "deploytime": string,
	  }
	]
}
```
## Get Tickers by Address

**Endpoint**

``` GET tapX.app/api/accounts/{address} ```

**Description**

Returns a JSON array of tickers held by the specified address where the balance of tokens is not equal to 0.

**Request Parameters**

* address (string): The address for which token details are requested.

**Response**

```
[  
	"ticker 1",  
	"ticker 2",  
	"ticker 3",  
	// ... more tickers
]
```
## Get Ticker Details by Address and Ticker

**Endpoint**

``` GET tapX.app/api/accounts/{address}/{ticker}/getInfo ```

**Description**

Returns a JSON object containing the ticker details for the specified ticker and address.

**Request Parameters**

* **address** (string): The address for which token details are requested.
* **ticker** (string): The specific token ticker.

**Response**

```
[
  {
    "ticker": "string",
    "balance": "string", //BigInt
    "transferable": "string", //Bigint
    "dec": 0,
    "available": 0, //BigInt
  }
]

```
## Get Transaction History by Address and Ticker

**Endpoint**

``` GET tapX.app/api/accounts/{address}/{ticker} ```

**Description**

Returns a JSON array containing the transaction history for the specified ticker and address, ordered from the latest to the earliest transactions.

**Request Parameters**

* **address** (string): The address for which token transactions are requested.
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
## Get Transaction History by Address Paginated ( V2 )

**Endpoint**

``` GET tapX.app/api/v2/getAccountHistoryForTicker/{address}? ```

**Description**

Returns a JSON array containing the transaction history for the specified ticker and address, ordered from the latest to the earliest transactions.

**Request Parameters**

* **address** (string): The address for which token transactions are requested.

**Request Query Parameters**

* **ticker** ( required ): The specified token ticker.
* **tab** ( required ): The type of the transaction to fetch ( 'mint' || 'transfer' || 'sent' || 		'receive' )
* **p** ( required ): The page number to fetch. (pageSize = 10)

**Response**

```
{
	listLength : 0,
	data : [
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
}
```
## Get Token Details

**Endpoint**

``` GET tapX.app/api/tokens/{ticker} ```

**Description**

Returns a JSON object containing deployment details, mint tokens left, holders count for the specified token.

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
  ]
}
```
## Get Transaction History for a Ticker

**Endpoint**

``` GET tapX.app/api/tokens/{ticker}/history ```

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
## Get Holders for a Ticker ( v2 )

**Endpoint**

``` GET tapX.app/api/v2/getAllHolders/{ticker}```

**Description**

Returns a JSON array containing the Holders array for the specified token.

**Request Parameters**

* **ticker** (string): The specified token ticker.

**Response**

```
[
	{
		"address":"string",
		"balance":"0"//BigInt String,
		"transferable":"0" //BigInt String
	}
]
```

## Get Transfer inscriptions for a Address ( marketplace )

**Endpoint**

``` GET tapX.app/api/marketplace/getTransferINS/{address}```

**Description**

Returns a JSON array containing the array for the transfer inscriptions for the specified address.

**Request Parameters**

* **address** (string): The specified token ticker.

**Response**

```
[
	{
		"addr":"string",		
		"blck":0,
		"amt":"string",
		"trf":"0",
		"bal":"0",		
		"tx":"string",
		"ins":"string",
		"num":0,
		"ts":0,
		"fail":true,
		"int":false,
		"ticker":"string"
		"dec":0
	}
]
```
