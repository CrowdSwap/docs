# CrowdSwap’s Cross-Chain Protocol Overview

CrowdSwap's cross-chain protocol enables users to effortlessly move crypto assets across different blockchains, unlocking access to the best opportunities within the DeFi ecosystem. By leveraging advanced technology and secure protocols, CrowdSwap simplifies and streamlines token swaps, removing the usual complexities of cross-chain transactions. Built on a proof-of-stake security model that mirrors many of the blockchains it connects, the service ensures secure token bridging and swapping, regardless of the underlying consensus mechanisms. This innovation provides users with maximum value, flexibility, and security, all within a user-friendly platform.

## TL;DR

To utilize CrowdSwap's cross-chain protocol, start by invoking the callContract method of the CrowdSwapGateway on the source chain. At the same time, pay the fixed validator fee, the protocol’s variable fee, and the execution cost for the destination network to the CrowdSwapGasService contract on the source chain. Once your transaction is initiated, you can track its progress using the CrowdSwap Scanner, a dedicated blockchain explorer designed to monitor your transaction status in real time.

## Get started

Executing a cross-chain transaction with CrowdSwap involves key components, including Routers, Gateways, CrowdHub (built on the Cosmos SDK), Validators and Operators. Here’s an overview of the key steps:

1. Quote and Estimation: When requesting a cross-chain swap, CrowdSwap’s Swap service provides a quote by calculating the output based on the CROWD pair on the destination chain. It considers the incoming volume from the source chain and prepares a transaction payload optimized for execution on the destination network.

2. Initiate Source Transaction: Begin by executing the transaction on the source blockchain, where a cross-chain event is emitted. The CrowdSwap Operator System actively monitors the source chain for this event and ensures the transaction reaches finality (i.e., confirmed by the network). Once the transaction is confirmed, the Operator broadcasts an InitContractCall message to CrowdSwap's native blockchain, CrowdHub.

3. Create Poll: After receiving the InitContractCall, CrowdHub initiates a Poll. This Poll requests Validators to assess and verify the source transaction’s validity on the originating chain.

4. Voting Process: Validators then retrieve the transaction receipt from the source chain and verify key details, such as transaction finality and event logs. Once the transaction is validated, Validators broadcast a Vote message to confirm the authenticity and accuracy of the cross-chain event.

5. Listen for EVMEventCompleted: Once sufficient votes are received, CrowdHub processes tasks like distributing fees or penalties based on the voting results. After this, it emits an EVMEventCompleted event. The Operator listens for this event and uses it to trigger the start of signing-related operations for the destination chain.

6. Approve Command Execution: Once the signing process is complete, the Operator forwards the signed commands to the Gateway on the destination chain, verifying the execution of the fulfillment transaction.

7. Fulfillment of Destination Transaction: Finally, the Operator executes the original destination address and payload on the destination network. This step completes the cross-chain transaction, ensuring the token bridge or swap is successfully carried out on the destination blockchain.

8. CROWD Buyback mechanism: To maintain the value of CROWD and enhance liquidity, CrowdSwap employs a dynamic buyback mechanism. After the transaction is fulfilled on the destination network, a buyback service automatically repurchases the sold CROWD using funds from the source chain. This ensures continuous liquidity and preserves CROWD's value, creating a sustainable and efficient cross-chain ecosystem.

## Liquidity in Cross-Chain Transactions

One of the key challenges in cross-chain transactions is ensuring sufficient liquidity across networks. CrowdSwap addresses this by utilizing its native token, CROWD, as a core liquidity source for cross-chain fulfillment. This design ensures that users can execute trades with optimized pricing, benefiting from lower fees and better swap rates.

For more details, check out: [Token Use Cases](https://crowdswap.org/token-usecases/#cross_chain)
