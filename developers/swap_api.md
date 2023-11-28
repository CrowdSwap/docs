## API Documentation

### Swap

#### Quote

This endpoint finds a route with potentially the best possible outcome for the requested pair. If ```userAddress``` is provided, it also returns the necessary details — ```from```, ```to```, ```data```, ```value```, and ```gasLimit``` — required for executing a swap transaction.

```
curl -X 'GET' 'https://api.crowdswap.org/api/v1/swap/quote?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bsymbol%5D=CROWD&amount=1000000000000000000&userAddress=0x000000000000000000000000000000000000000&receiverAddress=0x000000000000000000000000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

###### Request

| Field               | Description                                                                                         | Example                                    |
| ------------------- | ----------------------------------------------------------------------------------------------------| -------------------------------------------|
| fromToken[address]  | Address of source token                                                                             | 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | Chain id of source token                                                                            | 137                                        |
| fromToken[decimals] | Decimals of source token                                                                            | 18                                         |
| fromToken[symbol]   | Symbol of source token                                                                              | MATIC                                      |
| toToken[address]    | Address of destination token                                                                        | 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | Chain id of destination token                                                                       | 137                                        |
| toToken[decimals]   | Decimals of destination token                                                                       | 18                                         |
| toToken[symbol]     | Symbol of destination token                                                                         | CROWD                                      |
| amount              | An amount of ```fromToken``` to be swapped (The decimal of token must be considered in the amount)  | 1000000000000000000                        |
| userAddress         | If provided, the API returns the swapTx as well as the estimation. The "from" address of the transaction will be the ```userAddress```. The "to" address will be the ```receiverAddress``` specified in the request, if provided; otherwise, it will default to the ```userAddress```. | any arbitrary address  |
| receiverAddress     | Address of the recipient. Provide this value only if it differs from the ```userAddress``` property | any arbitrary address                      |


###### Response

```json
{
    "swapName": "string",
    "delegatedDex": "string",
    "fromToken": "string",
    "fromTokenPrice": "string",
    "toToken": "string",
    "toTokenPrice": "string",
    "amountIn": "string",
    "amountOut": "string",
    "minAmountOut": "string",
    "route": "string",
    "reserves": [
        "string"
    ],
    "priceImpact": "string",
    "poolInfo": "string",
    "swapFee": "string",
    "networkFee": "string",
    "gasPrice": "string",
    "currentDexFeePercentage": "string",
    "crowdswapFeePercentage": "string",
    "swapFeeInUSDT": "string",
    "networkFeeInUSDT": "string",
    "crowdswapFeeInUSDT": "string",
    "totalFeeInUSDT": "string",
    "pricePerToken": "number",
    "cost": "number",
    "totalPaidInUSDT": "string",
    "totalIncomeInUSDT": "string",
    "amountOutInUSDT": "string",
    "amountInInUSDT": "string",
    "amountOutPerAmountInRatio": "string",
    "amountInPerAmountOutRatio": "string",
    "approveAddress": "string",
    "tradeType": "number",
    "trade": {},
    "swapTx": {
        "from": "string",
        "to": "string",
        "data": "string",
        "value": "string",
        "gasLimit": "string"
    }
}
```

#### Estimation

This endpoint retrieves a list of decentralized exchanges (dexes) where the selected pair can be swapped. The list is sorted by profit, so we recommend choosing the first dex in the list.

```
curl -X 'GET' 'https://api.crowdswap.org/api/v1/swap/estimate-all?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bsymbol%5D=CROWD&amount=1000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

###### Request

| Field               | Description                                                                                         | Example                                    |
| ------------------- | ----------------------------------------------------------------------------------------------------| -------------------------------------------|
| fromToken[address]  | Address of source token                                                                             | 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | Chain id of source token                                                                            | 137                                        |
| fromToken[decimals] | Decimals of source token                                                                            | 18                                         |
| fromToken[symbol]   | Symbol of source token                                                                              | MATIC                                      |
| toToken[address]    | Address of destination token                                                                        | 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | Chain id of destination token                                                                       | 137                                        |
| toToken[decimals]   | Decimals of destination token                                                                       | 18                                         |
| toToken[symbol]     | Symbol of destination token                                                                         | CROWD                                      |
| amount              | An amount of the source token to be swapped (The decimal of token must be considered in the amount) | 1000000000000000000                        |

###### Response

```json
{
  "successfulEstimationsList":
    {
      "swapName": "string",
      "delegatedDex": "string",
      "fromToken": "string",
      "fromTokenPrice": "string",
      "toToken": "string",
      "toTokenPrice": "string",
      "amountIn": "string",
      "amountOut": "string",
      "minAmountOut": "string",
      "route": "string",
      "reserves": [
        "string"
      ],
      "priceImpact": "string",
      "poolInfo": "string",
      "swapFee": "string",
      "networkFee": "string",
      "gasPrice": "string",
      "currentDexFeePercentage": "string",
      "crowdswapFeePercentage": "string",
      "swapFeeInUSDT": "string",
      "networkFeeInUSDT": "string",
      "crowdswapFeeInUSDT": "string",
      "totalFeeInUSDT": "string",
      "pricePerToken": "number",
      "cost": "number",
      "totalPaidInUSDT": "string",
      "totalIncomeInUSDT": "string",
      "amountOutInUSDT": "string",
      "amountInInUSDT": "string",
      "amountOutPerAmountInRatio": "string",
      "amountInPerAmountOutRatio": "string",
      "approveAddress": "string",
      "tradeType": "number",
      "trade": {}
    }
  ]
}
```

#### Transaction

This endpoint returns the necessary details — ```from```, ```to```, ```data```, ```value```, and ```gasLimit``` — required for executing a swap transaction.

- A dex name must be added to the url. The dex name can be found in estimation result, e.g., ```CrowdswapV2```, ```Quickswap```

```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/swap/{dex}?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bsymbol%5D=CROWD&amount=1000000000000000000&userAddress=0x000000000000000000000000000000000000000&receiverAddress=0x000000000000000000000000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

##### Request

| Field               | Description                                                                                         | Example                                    |
| ------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| fromToken[address]  | Address of source token                                                                             | 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | Chain id of source token                                                                            | 137                                        |
| fromToken[decimals] | Decimals of source token                                                                            | 18                                         |
| fromToken[symbol]   | Symbol of source token                                                                              | MATIC                                      |
| toToken[address]    | Address of destination token                                                                        | 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | Chain id of destination token                                                                       | 137                                        |
| toToken[decimals]   | Decimals of destination token                                                                       | 18                                         |
| toToken[symbol]     | Symbol of destination token                                                                         | CROWD                                      |
| amount              | An amount of input tokens to swap (the entrance amount must be based on token's decimal)            | 1000000000000000000                        |
| userAddress         | If provided, the API returns the swapTx as well as the estimation. The "from" address of the transaction will be the ```userAddress```. The "to" address will be the ```receiverAddress``` specified in the request, if provided; otherwise, it will default to the ```userAddress```. | any arbitrary address  |
| receiverAddress     | Address of the recipient. Provide this value only if it differs from the ```userAddress``` property | any arbitrary address                      |

##### Response

```json
{
  "from": "string",
  "to": "string",
  "data": "string",
  "value": "string",
  "gasLimit": "string"
}
```

#### Cross-Dex Transaction

This endpoint must be called if the ```estimate-all``` endpoint returns a cross-dex estimation. If the estimation, typically the first index in the ```successfulEstimationsList``` list, includes ```firstDex``` and ```secondDex``` properties, it means that a potential connection between two dexes is available for creating an optimal route. The endpoint returns the necessary details — ```from```, ```to```, ```data```, ```value```, and ```gasLimit``` — required for executing a cross-dex swap transaction.
```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/swap/cross-dex?fromToken%5Baddress%5D=0x55d398326f99059fF775485246999027B3197955&fromToken%5BchainId%5D=56&fromToken%5Bdecimals%5D=18&fromToken%5Bsymbol%5D=USDT&middleToken%5Baddress%5D=0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c&middleToken%5BchainId%5D=56&middleToken%5Bdecimals%5D=18&middleToken%5Bsymbol%5D=WBNB&toToken%5Baddress%5D=0xA5d4B64a639d93b660cdA04D331374dA1108F8f5&toToken%5BchainId%5D=56&toToken%5Bdecimals%5D=18&toToken%5Bsymbol%5D=CROWD&amount=1000000000000000000&amountInFirstSwap=1000000000000000000&amountInSecondSwap=4253431943203308&userAddress=0x000000000000000000000000000000000000000&receiverAddress=0x000000000000000000000000000000000000000&firstSwapName=Kyber&secondSwapName=CrowdswapV2' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

##### Request

| Field                 | Description                                                                                         | Example                                    |
| -------------------   | --------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| fromToken[address]    | Address of source token                                                                             | 0x55d398326f99059fF775485246999027B3197955 |
| fromToken[chainId]    | Chain id of source token                                                                            | 56                                         |
| fromToken[decimals]   | Decimals of source token                                                                            | 18                                         |
| fromToken[symbol]     | Symbol of source token                                                                              | USDT                                       |
| middleToken[address]  | Address of middle token                                                                             | 0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c |
| middleToken[chainId]  | Chain id of middle token                                                                            | 56                                         |
| middleToken[decimals] | Decimals of middle token                                                                            | 18                                         |
| middleToken[symbol]   | Symbol of middle token                                                                              | WBNB                                       |
| toToken[address]      | Address of destination token                                                                        | 0xA5d4B64a639d93b660cdA04D331374dA1108F8f5 |
| toToken[chainId]      | Chain id of destination token                                                                       | 56                                         |
| toToken[decimals]     | Decimals of destination token                                                                       | 18                                         |
| toToken[symbol]       | Symbol of destination token                                                                         | CROWD                                      |
| amount                | An amount of ```fromToken``` to be swapped (The decimal of token must be considered in the amount)                                               | 1000000000000000000  |
| amountInFirstSwap     | An amount of ```fromToken``` to be swapped (The decimal of token must be considered in the amount). It is available in the estimation result.    | 1000000000000000000  |
| amountInSecondSwap    | An amount of ```middleToken``` to be swapped (The decimal of token must be considered in the amount). It is available in the estimation result.  | 4253431943203308     |
| userAddress           | If provided, the API returns the swapTx as well as the estimation. The "from" address of the transaction will be the ```userAddress```. The "to" address will be the ```receiverAddress``` specified in the request, if provided; otherwise, it will default to the ```userAddress```. | any arbitrary address  |
| receiverAddress       | Address of the recipient. Provide this value only if it differs from the ```userAddress``` property | any arbitrary address                      |
| firstSwapName         | The name of the first dex. It is available in the estimation result.                                | Kyber                                      |
| secondSwapName        | The name of the second dex. It is available in the estimation result.                               | CrowdswapV2                                |

##### Response

```json
{
  "from": "string",
  "to": "string",
  "data": "string",
  "value": "string",
  "gasLimit": "string"
}
```

### Cross-Chain

#### Estimation and Transaction

This endpoint identifies the optimal route for the requested cross-chain pair, potentially offering the best outcome. If the ```userAddress``` is provided, it additionally returns the transaction details to be sent to the blockchain.

```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/crossChainSwap/estimate-all?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bname%5D=Matic%20Token&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&toToken%5BchainId%5D=56&toToken%5Bdecimals%5D=18&toToken%5Bname%5D=Binance%20Coin&toToken%5Bsymbol%5D=BNB&amountIn=1000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

##### Request

| Field               | Description                                                                                          | Example                                       |
| --------------------| -----------------------------------------------------------------------------------------------------| ----------------------------------------------|
| fromToken[address]  | Address of source token                                                                              | 0x0000000000000000000000000000000000001010    |
| fromToken[chainId]  | Chain id of source token                                                                             | 137                                           |
| fromToken[decimals] | Decimals of source token                                                                             | 18                                            | 
| fromToken[symbol]   | Symbol of source token                                                                               | MATIC                                         |
| toToken[address]    | Address of destination token                                                                         | 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE    |
| toToken[chainId]    | Chain id of destination token                                                                        | 56                                            |
| toToken[decimals]   | Decimals of destination token                                                                        | 18                                            |
| toToken[symbol]     | Symbol of destination token                                                                          | BNB                                           |
| amountIn            | An amount of ```fromToken``` to be swapped (The decimal of token must be considered in the amount)   | 1000000000000000000                           |
| userAddress         | Address of the user who initiates the cross-chain transaction                                        | any arbitrary address                         |

##### Response

```json
{
  "crossChain": "number",
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
  }
}
```

#### Status

This endpoint returns the status of a cross-chain.

- A number must be added to the url. The number represents the cross-chain service used to initiate the cross-chain. This value, denoted as ```crossChain```, is accessible in the estimation result. 

```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/crosschainswap/status/1?transactionHash=0x8c08234a2cf142b51bc3fa3d2673bda3bcfda0ac561c458542229f878126b877' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

##### Request

| Field               | Description                                  | Example                                                            |
| --------------------| ---------------------------------------------| -------------------------------------------------------------------|
| transactionHash     | The transaction hash on the source network   | 0x8c08234a2cf142b51bc3fa3d2673bda3bcfda0ac561c458542229f878126b877 |

##### Response

```json
{
  "status": "string",
  "destTxHash": "string",
  "cancelTxHash": "string"
}
```

#### Cancel

This endpoint returns the transaction needed to cancel a cross-chain. The transaction must be sent to the destination blockchain. The user funds, including all associated fees, will then be refunded on the source blockchain.

- A number must be added to the url. The number represents the cross-chain service used to initiate the cross-chain. This value, denoted as ```crossChain```, is accessible in the estimation result.

```
curl -X 'GET' \
  'https://api.crowdswap.org/api/v1/crosschainswap/cancel/1?transactionHash=0x8c08234a2cf142b51bc3fa3d2673bda3bcfda0ac561c458542229f878126b877' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

##### Request

| Field               | Description                                  | Example                                                            |
| --------------------| ---------------------------------------------| -------------------------------------------------------------------|
| transactionHash     | The transaction hash on the source network   | 0x8c08234a2cf142b51bc3fa3d2673bda3bcfda0ac561c458542229f878126b877 |

##### Response

```json
{
  "chainId": "number",
  "from": "string",
  "to": "string",
  "data": "string",
  "value": "string",
  "gasLimit": "string",
  "cancelBeneficiary": "string"
}
```

#### Operating Expenses

This endpoint provides an estimate of the operating expenses (execution cost) for a cross-chain. It is particularly useful when implementing max balance functionality. Deduct the ```operatingExpenses``` from the user balance before calling the ```estimate-all``` endpoint. If the source token is the coin of the source network, also deduct the ```fixFee```.

```
curl -X 'GET' \
  'http://localhost:3002/api/v1/crossChainSwap/operating-expenses?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bsymbol%5D=MATIC&toToken%5Baddress%5D=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&toToken%5BchainId%5D=56&toToken%5Bdecimals%5D=18&toToken%5Bsymbol%5D=BNB' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

##### Request

| Field               | Description                     | Example                                       |
| --------------------| --------------------------------| ----------------------------------------------|
| fromToken[address]  | Address of source token         | 0x0000000000000000000000000000000000001010    |
| fromToken[chainId]  | Chain id of source token        | 137                                           |
| fromToken[decimals] | Decimals of source token        | 18                                            | 
| fromToken[symbol]   | Symbol of source token          | MATIC                                         |
| toToken[address]    | Address of destination token    | 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE    |
| toToken[chainId]    | Chain id of destination token   | 56                                            |
| toToken[decimals]   | Decimals of destination token   | 18                                            |
| toToken[symbol]     | Symbol of destination token     | BNB                                           |


##### Response

```json
{
  "operatingExpenses": "1401190173991438405",
  "fixFee": "500000000000000000"
}
```

### How to send a transaction

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
