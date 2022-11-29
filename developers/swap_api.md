# API Documentation

## Estimate all

This endpoint finds a list of dexes, with which a selected pair can swap. The list is sorted by profit, so we recommend to choose the first dex in the list.

```
curl -X 'GET' 'https://app.crowdswap.org/api/v1/swap/estimate-all?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bname%5D=Matic%20Token&fromToken%5Bsymbol%5D=MATIC&fromToken%5Bprice%5D=0.94036&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bname%5D=Crowd%20Token&toToken%5Bsymbol%5D=CROWD&toToken%5Bprice%5D=0.10172&amount=1000000000000000000&networkCoinPrice=0.98&slippage=0.5&deadline=30' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

### Estimation Request

| Field               | Description                                                                                                                       | Example                                                          |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| fromToken[address]  | Address of source token                                                                                                           | e.g Matic's address = 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | source chain id                                                                                                                   | e.g Polygon = 137                                                |
| fromToken[decimals] | Decimals of source token                                                                                                          | e.g Matic's decimals = 18                                        |
| fromToken[name]     | Name of source token                                                                                                              | e.g Matic's name = Matic Token                                   |
| fromToken[symbol]   | Symbol of source token                                                                                                            | e.g Matic's symbol = MATIC                                       |
| fromToken[price]    | Price of source token                                                                                                             | e.g Matic's price = 0.94036                                      |
| toToken[address]    | Address of destination token                                                                                                      | e.g Crowd's address = 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | destination chain id                                                                                                              | e.g Polygon = 137                                                |
| toToken[decimals]   | Decimals of destination token                                                                                                     | e.g Crowd's decimals = 18                                        |
| toToken[name]       | Name of destination token                                                                                                         | e.g Crowd's name = Crowd Token                                   |
| toToken[symbol]     | Symbol of destination token                                                                                                       | e.g Crowd's symbol = CROWD                                       |
| toToken[price]      | Price of destination token                                                                                                        | e.g Crowd's price = 0.10172                                      |
| amount              | An amount of input tokens to swap (the entrance amount must be based on token's decimal)                                          | e.g 1 ETH (decimals = 18 ) => 1000000000000000000                |
| networkCoinPrice    | The price of selected network's coin based on USD                                                                                 | e.g price of BNB = 279.22                                        |
| slippage            | A slippage constraint (in %) is a safeguard during swaps. It is used to calculate the minimum possible outcome during estimation. | e.g we set 0.5 as default slippage                               |
| gasPrice            | Gas Price based on selected network and gwei as unit                                                                              |                                                                  |
| deadline            | swap estimatio will be expired after this deadline                                                                                | e.g we set 30 as default deadline                                |

### Estimation Response

```
{​
  "successfulEstimationsList": [​
    {​
      "swapName": "string",​
      "delegatedDex": "string",​
      "fromToken": "string",​
      "toToken": "string",​
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
      "pricePerToken": 0,​
      "cost": 0,​
      "totalPaidInUSDT": "string",​
      "totalIncomeInUSDT": "string",​
      "amountOutInUSDT": "string",​
      "amountInInUSDT": "string",​
      "amountOutPerAmountInRatio": "string",​
      "amountInPerAmountOutRatio": "string",​
      "approveAddress": "string",​
      "tradeType": 0,​
      "trade": {}​
    }​
  ]​
​}
```

## Swap

This endpoint returns from, to, data, value, and gasLimit, all of which needed for executing a swap

- A dex name must be added to the url. The dex name can be found in `Estimate all` response e.g Quickswap, Sushiswap

```
curl -X 'GET' \
  'https://app.crowdswap.org/api/v1/swap/{dex}?fromToken%5Baddress%5D=0x0000000000000000000000000000000000001010&fromToken%5BchainId%5D=137&fromToken%5Bdecimals%5D=18&fromToken%5Bname%5D=Matic%20Token&fromToken%5Bsymbol%5D=MATIC&fromToken%5Bprice%5D=0.94036&toToken%5Baddress%5D=0x483dd3425278C1f79F377f1034d9d2CaE55648B6&toToken%5BchainId%5D=137&toToken%5Bdecimals%5D=18&toToken%5Bname%5D=Crowd%20Token&toToken%5Bsymbol%5D=CROWD&toToken%5Bprice%5D=0.10172&amount=1000000000000000000&networkCoinPrice=1000&slippage=0.5&userAddress=0x000000000000000000000000000000000000000&amountOutMin=1000&deadline=30' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

### Estimation Request

| Field               | Description                                                                                                                                    | Example                                                          |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| fromToken[address]  | Address of source token                                                                                                                        | e.g Matic's address = 0x0000000000000000000000000000000000001010 |
| fromToken[chainId]  | source chain id                                                                                                                                | e.g Polygon = 137                                                |
| fromToken[decimals] | Decimals of source token                                                                                                                       | e.g Matic's decimals = 18                                        |
| fromToken[name]     | Name of source token                                                                                                                           | e.g Matic's name = Matic Token                                   |
| fromToken[symbol]   | Symbol of source token                                                                                                                         | e.g Matic's symbol = MATIC                                       |
| fromToken[price]    | Price of source token                                                                                                                          | e.g Matic's price = 0.94036                                      |
| toToken[address]    | Address of destination token                                                                                                                   | e.g Crowd's address = 0x483dd3425278C1f79F377f1034d9d2CaE55648B6 |
| toToken[chainId]    | destination chain id                                                                                                                           | e.g Polygon = 137                                                |
| toToken[decimals]   | Decimals of destination token                                                                                                                  | e.g Crowd's decimals = 18                                        |
| toToken[name]       | Name of destination token                                                                                                                      | e.g Crowd's name = Crowd Token                                   |
| toToken[symbol]     | Symbol of destination token                                                                                                                    | e.g Crowd's symbol = CROWD                                       |
| toToken[price]      | Price of destination token                                                                                                                     | e.g Crowd's price = 0.10172                                      |
| amount              | An amount of input tokens to swap (the entrance amount must be based on token's decimal)                                                       | e.g 1 ETH (decimals = 18 ) => 1000000000000000000                |
| networkCoinPrice    | The price of selected network's coin based on USD                                                                                              | e.g price of BNB = 279.22                                        |
| slippage            | A slippage constraint (in %) is a safeguard during swaps. It is used to calculate the minimum possible outcome during estimation.              | e.g we set 0.5 as default slippage                               |
| userAddress         | User address who submits input tokens for a swap                                                                                               |                                                                  |
| deadline            | swap estimatio will be expired after this deadline                                                                                             | e.g we set 30 as default deadline                                |
| amountOutMin        | The minimum amount out expected from a swap (We can get this amount from estimation.Also the entrance amount must be based on token's decimal) |                                                                  |

### Swap Response

```
{
  "from": "string",
  "to": "string",
  "data": "string",
  "value": "string",
  "gasLimit": "string"
}
```

## Cross chain

### Cross chain estimation

This endpoint finds a route with the potentially best possible outcome for the requested cross-chain swap and returns an estimation

```
curl -X 'GET' \
  'https://app.crowdswap.org/api/v1/crossChainSwap/estimate?srcChainId=1&srcChainTokenInAddress=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&srcChainTokenInAmount=1000000000000000000&slippage=3&dstChainId=56&dstChainTokenOutAddress=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&userAddress=0x000000000000000000000000000000000000000' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

### Cross chain estimation Request

| Field                   | Description                                                                                                                       | Example                                                                                                       |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| srcChainId              | Source Chain Id                                                                                                                   | e.g ETH = 1, BSC = 56, POLYGON = 137                                                                          |
| srcChainTokenInAddress  | Source Chain Token Address                                                                                                        | e.g Ethereum = 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE, MATIC = 0x0000000000000000000000000000000000001010 |
| srcChainTokenInAmount   | An amount of input tokens to cross-chain swap (the entrance amount must be based on token's decimal)                              | e.g 1 ETH = 1000000000000000000                                                                               |
| slippage                | A slippage constraint (in %) is a safeguard during swaps. It is used to calculate the minimum possible outcome during estimation. | e.g slippage = 3                                                                                              |
| dstChainId              | Destination Chain Id                                                                                                              | e.g ETH = 1, BSC = 56, POLYGON = 137                                                                          |
| dstChainTokenOutAddress | Destination Chain Token Address                                                                                                   | e.g Ethereum = 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE, MATIC = 0x0000000000000000000000000000000000001010 |
| userAddress             | User address who submits input tokens for a cross-chain swap                                                                      |                                                                                                               |

### Cross chain estimation Response

```
{
  "estimation": {
    "srcChainTokenIn": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string"
    },
    "srcChainTokenOut": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string",
      "minAmount": "string"
    },
    "dstChainTokenIn": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string",
      "minAmount": "string"
    },
    "dstChainTokenOut": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string",
      "minAmount": "string"
    },
    "executionFee": {
      "token": {
        "address": "string",
        "name": "string",
        "symbol": "string",
        "decimals": 0
      },
      "recommendedAmount": "string",
      "actualAmount": "string"
    }
  },
  "tx": {
    "to": "string",
    "data": "string",
    "value": "string"
  }
}
```

### Cross chain swap

This endpoint finds a route with the potentially best possible outcome for the requested cross-chain swap and returns:

- an estimation, which includes the details of the found route, the estimated outcome, and the execution cost;
- the data for a transaction to execute the cross-chain swap according to the selected route and given constraints (slippage, execution fee, recipient, etc).

The transaction must be signed by the sender and sent to the blockchain by the requester.

### Cross chain swap Request

```
curl -X 'GET' \
  'https://app.crowdswap.org/api/v1/crossChainSwap/transaction?srcChainId=1&srcChainTokenInAddress=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&srcChainTokenInAmount=1000000000000000000&slippage=3&dstChainId=56&dstChainTokenOutAddress=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE&userAddress=0xFD4f361269dCdE0bc1CB410b54c0c30331a4FC99' \
  -H 'accept: application/json'
  -H 'x-api-key: YOUR_API_KEY'
```

| Field                   | Description                                                                                                                       | Example                                                                                                       |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| srcChainId              | Source Chain Id                                                                                                                   | e.g ETH = 1, BSC = 56, POLYGON = 137                                                                          |
| srcChainTokenInAddress  | Source Chain Token Address                                                                                                        | e.g Ethereum = 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE, MATIC = 0x0000000000000000000000000000000000001010 |
| srcChainTokenInAmount   | An amount of input tokens to cross-chain swap (the entrance amount must be based on token's decimal)                              | e.g 1 ETH = 1000000000000000000                                                                               |
| slippage                | A slippage constraint (in %) is a safeguard during swaps. It is used to calculate the minimum possible outcome during estimation. | e.g slippage = 3                                                                                              |
| dstChainId              | Destination Chain Id                                                                                                              | e.g ETH = 1, BSC = 56, POLYGON = 137                                                                          |
| dstChainTokenOutAddress | Destination Chain Token Address                                                                                                   | e.g Ethereum = 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE, MATIC = 0x0000000000000000000000000000000000001010 |
| userAddress             | User address who submits input tokens for a cross-chain swap                                                                      |                                                                                                               |

### Cross chain swap Response

```
{
  "estimation": {
    "srcChainTokenIn": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string"
    },
    "srcChainTokenOut": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string",
      "minAmount": "string"
    },
    "dstChainTokenIn": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string",
      "minAmount": "string"
    },
    "dstChainTokenOut": {
      "address": "string",
      "name": "string",
      "symbol": "string",
      "decimals": 0,
      "amount": "string",
      "minAmount": "string"
    },
    "executionFee": {
      "token": {
        "address": "string",
        "name": "string",
        "symbol": "string",
        "decimals": 0
      },
      "recommendedAmount": "string",
      "actualAmount": "string"
    }
  },
  "tx": {
    "to": "string",
    "data": "string",
    "value": "string"
  }
}
```

## How to send a transaction

Both `Swap` and `Cross chain swap` API return the data needed for executing a transaction. The data, which named `tx` in below code, contains `from (user address)`, `to (contract address)`, `data (populated data)`, `value (coin value if needed)`, `gasLimit`. You can use below code to run your transaction.

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
