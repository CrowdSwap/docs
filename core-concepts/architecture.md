# Architecture

The products described above combine to form an overall architecture, which we outline in this chapter. It serves as an overview, and we refer you to the individual chapters on the different\
architecture areas. The figure shows the composition of the various components, as they are described in the individual chapters.

For example, the Search App is based on the BPR layer, which is also responsible for best price determination. The Wallet Manager provides essential information for finding the best price for the user's initial situation using BPR. If the user does not own any cryptocurrencies yet, we will guide him through the onboarding process with the ramp-on provider's support. For the swap itself, it may be necessary to transfer tokens from one network to another.\
CrowdSwap uses the atomic token bridge to achieve this. We implement different solutions of bridged and atomic swaps here to prepare for future scenarios. The architecture describes the components that are currently in the scope of the project. We add additional features successively, which have already been touched upon in the chapters, such as simplified trading models or the consideration of on-chain data analysis to enhance swapping optimization, usability, and user experience. The following diagram illustrate the main components of the current version of the application: 


![Crowdswap-Architecture](https://user-images.githubusercontent.com/94463487/145383633-3eae4231-68ad-4794-ab69-4c9b71615b1b.png)
