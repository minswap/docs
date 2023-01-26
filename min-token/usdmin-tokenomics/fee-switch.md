# Fee Switch

**Fee Switch** was activated following a [DAO vote on the activation of the "Fee Switch"](https://app.minswap.org/gov/4c00218a32ede4de1991f869aeb878cb51829c2c87732aff797ec962422370f2) which ended on _2022-12-29._

The **Fee Switch** refers to redirecting 0.05% of the 0.3% Fee that swappers pay. The aim for the Fees accumulated from the Fee Switch is to utilize them in order to increase the DAO Treasury's Protocol Owned Liquidity (meaning the assets it owns). An Overview of the Assets owned by the Minswap DAO can be found in [DAO Treasury POL](../../governance/dao-treasury-pol/).

1. Every time a user swaps on Minswap, 0.05% of the 0.3% of the Variable Fee is accumulated from the Fee Switch in the form of LP Tokens.&#x20;
2. Any LP Tokens accumulated through the Fee Switch that aren’t $MIN/$ADA LP Tokens and that are worth more than 100 $ADA are sold in the open market for $ADA. For example, if 100 $ADA worth in $XZY/$ADA LP Tokens was accumulated, the 50 $ADA worth of $XZY would be sold for $ADA.&#x20;
3. The rest of LP Tokens worth less than 100 $ADA are kept and accumulate until they reach the value of 100 $ADA.&#x20;
4. Any $ADA generated are zapped into $MIN/$ADA LP Tokens.
5. $MIN/$ADA LP Tokens are farmed.

Fee Sharing on the Minswap DEX **** revolves around using Fees to strengthen the Liquidity in the MIN/ADA Pool. Having a strong MIN/ADA Pool, especially in earlier stages of the project, is incredibly important as we highlighted in our [LBE article](https://minswap-labs.medium.com/meteor-lbe-mainnet-launch-yield-farming-more-f73c6c2a8b37).

### Fee Sharing API

An **API** for the Fee Switch is available to monitor:&#x20;

1. Total ADA worth of Accumulated Fee in liquidity pool + withdrawn Fee in Fee Sharing wallet + zapped ADA-MIN LP (_totalFeeADAWorth_).
2. Total converted ADA-MIN LP staying in the Fee Sharing wallet (_totalADAMINLP_).
3. Top 10 pools which having most Accumulated Fee Sharing LP still staying in liquidity pool and their Accumulated Fee Sharing information (_topPendingFeeSharingPools_).

The API is available at: [https://api-mainnet-prod.minswap.org/landing-page/fee-sharing-analysis](https://api-mainnet-prod.minswap.org/landing-page/fee-sharing-analysis)







