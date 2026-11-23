# $MIN Point System

If you have been long enough around Minswap, you likely will have seen one of our Posts about changes in the bi-weekly [$MIN Emissions Points (MEPs)](https://twitter.com/MinswapDEX/status/1556769599177342976?s=20\&t=l\_1oJqX6YUGsiSde6PUqBQ).&#x20;

The $MIN Point System is a simple structure to determine how many $MIN Farming rewards are allocated to which Liquidity Pools. Simply put, a quantitative formula takes on-chain data which is used every 2 weeks to determine the next allocation of rewards. The idea is to use $MIN in the most "cost-effective" manner as possible, maximizing TVL and Volume and hence directing $MIN rewards to the pools with the highest metrics.

For an overview of the current Allocation Points for Farms, and the History of Farm Rebalances, see the subsection: [Historical MIN Farm Reblances](https://app.gitbook.com/s/-Mb6kABTQvTeYDjx9qXI-887967055/\~/changes/FYA2xR9CSsN8KYtkqJmg/yield-farming/farms-allocation-and-governance/historical-min-farm-reblances). For a clloser look on how MEPs are determined, read on!

## How are Farm Points decided on?&#x20;

Farms are rebalanced bi-weekly according to the Forumula laid out in the following [Medium Article](https://marco112358.medium.com/a-formula-driven-model-for-minswap-min-emissions-a73f3f6794dc).

In short, the formula looks at these 2 metrics:

**30-Day Average Daily Volume:** a smoothed measure of the volume transacted in a LP over the past 30 days. The long term success of a DEX is driven by deep liquidity and volume. Token emissions cannot last forever, so eventually LP rewards will come down to volume only. A DEX that has strong volume after emissions end will continue to incentivize users to provide liquidity to the LPs. Therefore, we should be rewarding pools with high volume.

**30-Day Average Total Value Locked:** a smoothed measure of the Total Value Locked inside of a LP over the past 30 days. TVL shows how deep the liquidity of a pool is. Deeper liquidity means less slippage for anyone who wants to transact in that pair of tokens. So, deeper liquidity incentivizers users to use Minswap DEX to swap this specific pair of tokens. If a token pair has deeper liquidity on a competing DEX, it is highly likely that the competing DEX will have better pricing. Thus, we should be rewarding pools with lower TVL in order to incentivize users to deposit liquidity in those pools, and drive volume to Minswap.

Currently, the Volume Metric is **9x** more important, as the aim is to reward pools that have high Volume and low TVL.

In addition, it is extremely important we constantly gather feedback from community members and integrate it adjusting the Points of our farms. That is precisely the intention of our **“Kitty Farmer Committee”**. Kitty Farmers (also known as “OGs” in our Discord) are some of the most passionate Minswap Community Members, who have been supporting the team from the beginning, providing invaluable feedback and helping other less experienced community members get acquainted with Minswap and DeFi in general. Kitty Farmers play a significant role in adjusting the parameters of the forumla as well as deciding on the additon and removal of Farms.
