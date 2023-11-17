# API Documentation

## Swap

### Estimation

This endpoint retrieves a list of decentralized exchanges (dexes) where the selected pair can be swapped. The list is sorted by profit, so we recommend choosing the first dex in the list.

```
curl -X 'GET' 'https://api.crowdswap.org/api/v1/swap/estimate-all?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bname%5D=Matic%20Token&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bname%5D=Crowd%20Token&toToken%5Bsymbol%5D=CROWD&amount=1000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

#### Request

| Field               | Description                                                                                         | Example                                    |
| ------------------- | ----------------------------------------------------------------------------------------------------| -------------------------------------------|
| fromToken[address]  | Address of source token                                                                             | 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | Chain id of source token                                                                            | 137                                        |
| fromToken[decimals] | Decimals of source token                                                                            | 18                                         |
| fromToken[name]     | Name of source token                                                                                | Matic Token                                |
| fromToken[symbol]   | Symbol of source token                                                                              | MATIC                                      |
| toToken[address]    | Address of destination token                                                                        | 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | Chain id of destination token                                                                       | 137                                        |
| toToken[decimals]   | Decimals of destination token                                                                       | 18                                         |
| toToken[name]       | Name of destination token                                                                           | Crowd Token                                |
| toToken[symbol]     | Symbol of destination token                                                                         | CROWD                                      |
| amount              | An amount of the source token to be swapped (The decimal of token must be considered in the amount) | 1000000000000000000                        |

#### Response

```
{​
  "successfulEstimationsList": [​
    {​
      "swapName": "string",​
      "delegatedDex": "string",​
      "fromToken": "string",​
      "fromTokenPrice": "string",​
      "toToken": "string",​
      "toTokenPrice": "string",​
      "amountIn": "string",​
      "amountOut": "string",​
      "minAmountOut": "string",​
      "route": "string",​
      "reserves": [​
        "string"​
      ],​
      "priceImpact": "string",​
      "poolInfo": "string",​
      "swapFee": "string",​
      "networkFee": "string",​
      "gasPrice": "string",​
      "currentDexFeePercentage": "string",​
      "crowdswapFeePercentage": "string",​
      "swapFeeInUSDT": "string",​
      "networkFeeInUSDT": "string",​
      "crowdswapFeeInUSDT": "string",​
      "totalFeeInUSDT": "string",​
      "pricePerToken": "number",​
      "cost": "number",​
      "totalPaidInUSDT": "string",​
      "totalIncomeInUSDT": "string",​
      "amountOutInUSDT": "string",​
      "amountInInUSDT": "string",​
      "amountOutPerAmountInRatio": "string",​
      "amountInPerAmountOutRatio": "string",​
      "approveAddress": "string",​
      "tradeType": "number",​
      "trade": {}​
    }​
  ]​
​}
```

### Transaction

This endpoint returns ```from```, ```to```, ```data```, ```value```, and ```gasLimit```, all of which needed for executing a swap.

- A dex name must be added to the url. The dex name can be found in estimation response e.g., CrowdSwapV2, Quickswap

```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/swap/{dex}?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bname%5D=Matic%20Token&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bname%5D=Crowd%20Token&toToken%5Bsymbol%5D=CROWD&amount=1000000000000000000&userAddress=0x000000000000000000000000000000000000000&receiverAddress=0x000000000000000000000000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

#### Request

| Field               | Description                                                                               | Example                                    |
| ------------------- | ------------------------------------------------------------------------------------------| ------------------------------------------ |
| fromToken[address]  | Address of source token                                                                   | 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | Chain id of source token                                                                  | 137                                        |
| fromToken[decimals] | Decimals of source token                                                                  | 18                                         |
| fromToken[name]     | Name of source token                                                                      | Matic Token                                |
| fromToken[symbol]   | Symbol of source token                                                                    | MATIC                                      |
| toToken[address]    | Address of destination token                                                              | 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | Chain id of destination token                                                             | 137                                        |
| toToken[decimals]   | Decimals of destination token                                                             | 18                                         |
| toToken[name]       | Name of destination token                                                                 | Crowd Token                                |
| toToken[symbol]     | Symbol of destination token                                                               | CROWD                                      |
| amount              | An amount of input tokens to swap (the entrance amount must be based on token's decimal)  | 1000000000000000000                        |
| userAddress         | Address of the user who initiates the swap transaction                                    | any arbitrary address                                           |
| userAddress         | Address of the recipient                                                                  | any arbitrary address                                           |

#### Response

```
{
  "from": "string",
  "to": "string",
  "data": "string",
  "value": "string",
  "gasLimit": "string"
}
```

## Cross-Chain

### Estimation and Transaction

This endpoint finds a route with potentially the best possible outcome for the requested cross-chain pair and returns an estimation.

```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/crossChainSwap/estimate-all?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bname%5D=Matic%20Token&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&toToken%5BchainId%5D=56&toToken%5Bdecimals%5D=18&toToken%5Bname%5D=Binance%20Coin&toToken%5Bsymbol%5D=BNB&amountIn=1000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

#### Request

| Field               | Description                                                                                          | Example                                       |
| --------------------| -----------------------------------------------------------------------------------------------------| ----------------------------------------------|
| fromToken[address]  | Address of source token                                                                              | 0x0000000000000000000000000000000000001010    |
| fromToken[chainId]  | Chain id of source token                                                                             | 137                                           |
| fromToken[decimals] | Decimals of source token                                                                             | 18                                            | 
| fromToken[name]     | Name of source token                                                                                 | Matic Token                                   |
| fromToken[symbol]   | Symbol of source token                                                                               | MATIC                                         |
| toToken[address]    | Address of destination token                                                                         | 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE    |
| toToken[chainId]    | Chain id of destination token                                                                        | 56                                            |
| toToken[decimals]   | Decimals of destination token                                                                        | 18                                            |
| toToken[name]       | Name of destination token                                                                            | Binance Coin                                  |
| toToken[symbol]     | Symbol of destination token                                                                          | BNB                                           |
| amountIn            | An amount of ```fromToken``` to be swapped (The decimal of token must be considered in the amount)   | 1000000000000000000                           |
| userAddress         | Address of the user who initiates the cross-chain swap transaction                                   | any arbitrary address                         |

#### Response

```
{
  "crossChainName": "string",
  "tokenIn": {
    "address": "string",
    "chainId": "number",
    "decimals": "number",
    "amount": "string",
    "symbol": "string"
  },
  "tokenOut": {
    "address": "string",
    "chainId": "number",
    "decimals": "number",
    "amount": "string",
    "symbol": "string"
  },
  "amountIn": "string",
  "amountOut": "string",
  "minAmountOut": "string",
  "approveAddress": "string",
  "status": "number",
  "msg": "string",
  "swapTx": {
    "to": "string",
    "data": "number",
    "value": "number",
    "gasLimit": "string"
  },
  "fees": {
    "token": {
      "address": "string",
      "chainId": "number",
      "decimals": "number",
      "name": "string",
      "symbol": "string"
    },
    "amount": "string",
    "type": "number"
  },
  "includedInOutputFees": {
    "token": {
      "address": "string",
      "chainId": "number",
      "decimals": "number",
      "name": "string",
      "symbol": "string"
    },
    "amount": "string",
    "type": "number"
  },
  "swapSpecData": {}
}
```

## How to send a transaction

Both `Swap` and `Cross-Chain` APIs return the data needed for executing a transaction. The data, which named `tx` in below code, contains `from (user address)`, `to (contract address)`, `data (populated data)`, `value (coin value if needed)`, `gasLimit`. You can use below code to run your transaction.

To send a transaction, you can get `tx` from the response of Swap and Cross-Chain end-points.

```javascript
import { ExternalProvider, Web3Provider } from '@ethersproject/providers';

export class TransactionService{
  private provider?: Web3Provider;

  constructor(){
    this.provider = new Web3Provider(provider as ExternalProvider, 'any');
  }

  function sendTransaction(tx){
    this.provider?.getSigner().sendTransaction(tx);
  }
}
```
