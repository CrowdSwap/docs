# Protocol

###Fees/Estimation calculation
  
Source token & Destination token prices in USDT are estimated from coingecko or Binance APIs (refer to [Developer](../developers/guides.md)).

After estimating source token price in USDT, dex fee and network cost are estimated from each DEXes. Crowdswap fee is calculated as 0.1% of amountInUSDT. All fees are deducted from Destination amount.
###

![](../.gitbook/assets/calculation-fees-table.png)
###
For example by select ETH as source token and AUC as destination token you can see all calculated fees which come from estimation.
Keep in mind that by clicking swap button, a new estimation will be performed based on the best price DEX. 

![](../.gitbook/assets/estimate.png)


###Supported Networks and DEXes

* ####Ethereum Network
    * Uniswap V2
    * Uniswap V3
    * Sushiswap
    * Bancor
    * Balancer
    * Kyber
####  
* ####BSC Network
    * Pancake
    * Sushiswap
    * Apeswap
####
* ####Polygon Network
    * Quickswap
    * Sushiswap
  
###Contracts

* Token: [0x483dd3425278C1f79F377f1034d9d2CaE55648B6](https://polygonscan.com/token/0x483dd3425278C1f79F377f1034d9d2CaE55648B6)
* Distribution: [0xBeDf619c69f5C1655E58463B85A4EE67629dE409](https://polygonscan.com/address/0xBeDf619c69f5C1655E58463B85A4EE67629dE409)
* Swap
  * Ethereum: [0x467eC2d26Bb7DE784A4584c6762B43eb69e65636](https://etherscan.io/address/0x467eC2d26Bb7DE784A4584c6762B43eb69e65636)
  * BSC: [0x467eC2d26Bb7DE784A4584c6762B43eb69e65636](https://bscscan.com/address/0x467eC2d26Bb7DE784A4584c6762B43eb69e65636)
  * Polygon: [0x467eC2d26Bb7DE784A4584c6762B43eb69e65636](https://polygonscan.com/address/0x467eC2d26Bb7DE784A4584c6762B43eb69e65636)