# Stable Pools

Stable Pools on Minswap allows you to trade stable pairs with a lower slippage based on an invariant curve slippage function. It is designed to swap specific assets that are priced closely – such as USD stablecoins. Such pools requires accurate token decimals to work in an optimal way. While some of the recent tokens in Cardano have decimal information through CIP-68, not all tokens provide such data, hence the need to exercise vigilance to maintain pool health and ensure user safety.

### The constraints of creating permissionless Stable Pools

For user protection, operational integrity, and functionality, Minswap currently opts for manually creating stable pools due to:

1. **Safety Risks**: Wrongly set or unmatched parameters will break the pool's logic and, therefore, could contribute to huge losses to liquidity providers and traders. These parameters hence require manual check and validation by the Minswap team to avoid such incidences.
2. **Smart Contract Complexity**: Each Stable Pool uses the same base smart contract but requires different hard-coded parameters tailored to the tokens involved.

### How to set up a Stable Pool

Follow these steps to begin setting up a new stable pool:

1. **Review the Stableswap Contract**: Before proceeding, it is beneficial to familiarize yourself with the [Stableswap contract on GitHub](https://github.com/minswap/minswap-stableswap) to understand the operational requirements of Stable Pools.
2. **Open a Ticket on Minswap Discord**: To initiate the setup of a new stable pool, contact the Minswap team directly by opening a support ticket in the [Minswap Discord server](https://discord.gg/minswap). Provide comprehensive information about the tokens you wish to include in the pool and any other relevant details.
3. **Collaboration and Verification**: After your submission, the Minswap team will assess your tokens, review the necessary parameters, and collaborate with you to meet all technical and safety standards.
