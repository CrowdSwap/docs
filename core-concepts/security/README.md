# Security
Security is the first-class citizen in our architecture. We have used many effective methods to secure our platform. The following sections describe the main concepts of security in three essential parts of our architecture.

## Smart Contracts
We have developed smart contacts using Solidity deployed on the Ethereum based networks.
To secure smart contracts against attacks and vulnerabilities, we make these key points:
* Some well-known auditors audit this smart contract
* Write a more secure smart contract code with best practices followed by leading organizations
* Periodically perform smart contract security audits and penetration tests
* Follow a blockchain security checklist
* Run automated security scans on a smart contract
* Use the trusted blockchain tools for design, development, security, auditing and exploiting

## Back-end Services and APIs
CrowdSwap is a DeFi application. So, main features like Swap and wallet management are provided On-Chain. Only the best routing service is hosted as Off-Chain services.  We deploy some public APIs in our back-end servers to provide this feature. To secure this part, We use the following features:
* No sensitive data pass from a browser application to back-end services
* APIs are developed as public services, So, there are no vulnerabilities against them
* The hosted servers are protected with Firewalls
* We prevent our service from DOS attack by using a Rate limit service

## UI
We use a web3 provider to communicate with the user wallet and blockchain network. Users pass the final transactions by signing them with their private key using a secure wallet like Metamask.

The CrowdSwap app is developed as a SPA using the Angular framework. The production version is deployed on a CDN. This protects the app from some security attacks. As UI uses some back-end service, all data is passed using the SSL. Also, a couple of methods are used to protect the app against CORS, CSRF and Code Injection attacks.
