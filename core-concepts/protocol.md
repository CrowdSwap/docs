# Protocol

### Cross-Chain Fees

At CrowdSwap, we believe in transparency and fairness, which extends to our fee structure for the Cross-Chain feature. CrowdSwap charges a nominal fee for each trade to facilitate the transaction and maintain the platform. The fee is a small percentage of the transaction amount, ensuring it remains affordable for all users.
The transaction fee consists of:
1. Flat Protocol Fee
2. Variable Protocol Fee
3. CrowdSwap Fee

| Chain      | Flat Protocol Fee | Variable Protocol Fee       | CrowdSwap Fee          |
| ---------- | ----------------- |  -------------------------- | ---------------------- |
| Ethereum   | 0.001 ETH         | 0.04% - 0.08% of the amount | 0.2%- 1% of the amount |
| BSC        | 0.005 BNB         | 0.04% - 0.08% of the amount | 0.2%- 1% of the amount |
| Polygon    | 0.5 MATIC         | 0.04% - 0.08% of the amount | 0.2%- 1% of the amount |
| Avalanche  | 0.01 AVAX         | 0.04% - 0.08% of the amount | 0.2%- 1% of the amount |
| Arbitrum   | 0.001 ETH         | 0.04% - 0.08% of the amount | 0.2%- 1% of the amount |
| Optimism   | 0.001 ETH         | 0.04% - 0.08% of the amount | 0.2%- 1% of the amount |

### Swap Fees/Estimation calculation
  
The price of source and destination tokens in USD is inquired from coingecko or Binance APIs.
The fee of each DEX and network cost are inquired from that DEX. Crowdswap fee is calculated as 0.1% of source price in USD.
All fees are deducted from destination amount except liquidity provider fee which is deducted from source token amount.

###

![](../.gitbook/assets/calculation-fees-table.png)

* Gas Price: [https://ethgasstation.info/](https://ethgasstation.info/)
* Gas Cost: Historical gas usage of functions in the target DEX
* Amount In USD: source token amount * source token price in USD
###
For example, by selecting ETH as source token and AUC as destination token, you can see fees are calculated based on data from estimation.
Keep in mind that by clicking swap button, a new estimation will be performed based on the best price DEX. 

![](../.gitbook/assets/estimate.png)


### Supported Networks and DEXes (current state)

* #### Ethereum Network
    * Uniswap V2
    * Uniswap V3
    * Sushiswap
    * Bancor
    * Balancer
    * Kyber
    * Crypto.com
    * Curve v1
    * Radioshack
    * Dodo
####  
* #### BSC Network
    * Pancake
    * Sushiswap
    * Apeswap
    * Biswap
    * Curve v1
    * Radioshack
    * Dodo
####
* #### Polygon Network
    * Quickswap
    * Sushiswap
    * Uniswap V3
    * Apeswap
    * Curve v1
    * Radioshack
####
* #### Avalanche Network
    * Trader Joe
    * Sushiswap
    * Curve v1
    * Radioshack
    * Pangolin
    * Dodo
  
### Contracts

* Token: [0x483dd3425278C1f79F377f1034d9d2CaE55648B6](https://polygonscan.com/token/0x483dd3425278C1f79F377f1034d9d2CaE55648B6)
* Distribution: [0xBeDf619c69f5C1655E58463B85A4EE67629dE409](https://polygonscan.com/address/0xBeDf619c69f5C1655E58463B85A4EE67629dE409)
* Staking: [0x3C868fe859eF46a133e032f22B443e6Efd617449](https://polygonscan.com/address/0x3C868fe859eF46a133e032f22B443e6Efd617449)
* Swap
  * Ethereum: [0x467eC2d26Bb7DE784A4584c6762B43eb69e65636](https://etherscan.io/address/0x467eC2d26Bb7DE784A4584c6762B43eb69e65636)
  * BSC: [0xd4560c06db2bAe0b06E9243896aD48e4bD14cdb2](https://bscscan.com/address/0xd4560c06db2bAe0b06E9243896aD48e4bD14cdb2)
  * Polygon: [0xBBc607D84eE5836C802B8b98392C8EAd8B9cDa5D](https://polygonscan.com/address/0xBBc607D84eE5836C802B8b98392C8EAd8B9cDa5D)
  * Avalanche: [0x467eC2d26Bb7DE784A4584c6762B43eb69e65636](https://snowtrace.io/address/0x467eC2d26Bb7DE784A4584c6762B43eb69e65636)
