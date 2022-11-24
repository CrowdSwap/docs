# Overview

### Introduction

Crowdswap provides a dezen APIs that helps DeFi apps being more tangeble for end users.

- Finding the best route and dex for swapping is one of these APIs. We've been trying to create and keep update a list of the most profitable dexes and offer the to our users.

- Cross-chain is another service that let users to swap they asset between different chains. Similar to swap, we tried to provide an API that simplifies the process of swapping in away that end user do not to worry about a cross-chain steps.

Before explaining more about the details of the API, here is the link of endpoints in the swagger format: [Swagger UI](./api.md)

### API Key

In order to use CrowdSwap's API, you should send a request via this link: [Request API Key](https://docs.google.com/forms/d/e/1FAIpQLScnLpbly_9_4FoiOmS4VHFpWFQzQXSLZa-Eenb-wl15-mehJg/viewform?usp=sf_link)

### Connect wallet

You can connect your dApp to a wallet like this:

```node
npm install web3

npm install --save web3modal
```

```javascript
import { Injectable } from '@angular/core';
import Web3 from "web3";
import Web3Modal from "web3modal";
import WalletConnectProvider from "@walletconnect/web3-provider";
import { Subject } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class ContractService {
  private web3js: any;
  private provider: any;
  private accounts: any;
  web3Modal

  private accountStatusSource = new Subject<any>();
  accountStatus$ = this.accountStatusSource.asObservable();

  constructor() {
    const providerOptions = {
      walletconnect: {
        package: WalletConnectProvider, // required
        options: {
          infuraId: "INFURA_ID" // required
        }
      }
    };

    this.web3Modal = new Web3Modal({
      network: "mainnet", // optional
      cacheProvider: true, // optional
      providerOptions, // required
      theme: {
        background: "rgb(39, 49, 56)",
        main: "rgb(199, 199, 199)",
        secondary: "rgb(136, 136, 136)",
        border: "rgba(195, 195, 195, 0.14)",
        hover: "rgb(16, 26, 32)"
      }
    });
  }

  async connectAccount() {
    this.web3Modal.clearCachedProvider();

    this.provider = await this.web3Modal.connect(); // set provider
    this.web3js = new Web3(this.provider); // create web3 instance
    this.accounts = await this.web3js.eth.getAccounts();
    this.accountStatusSource.next(this.accounts)
  }

}
```

Then you can see a modal like this:

![](../.gitbook/assets/connect-wallet-modal.png)