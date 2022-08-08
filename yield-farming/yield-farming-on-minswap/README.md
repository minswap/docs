# Yield Farming on Minswap

### **How does Yield Farming work on Minswap?**

**1)** Firstly, anyone who Provides Liquidity in any pair on the DEX will receive **LP Tokens (LPTs)**.&#x20;

**2)** If the pair you have provided has a **farm** (a list of starting eligible farms is in the subsection _Farms Allocation & Governance_), these LPTs can then be staked and start earning MIN tokens from that moment on.&#x20;

**3)** Once you have staked your LPTs in a farm, you can withdraw your accrued MIN rewards **at any time**. Rewards will be calculated based on the second unit (so, **every second**), which means you **won’t need to wait a fixed period of time** to collect the MIN tokens you have earned. So, you can harvest any time that you have accrued rewards! But, we do advise **against harvesting rewards too often**, as you will incur _Cardano network fees_ (from ≈0.6 to ≈1.2 ADA) every time you do it!

**4)** If you add **additional LPTs** to a farm, the rewards accumulated since your last action (deposit or withdrawal) will be automatically calculated and sent to you. Then, you will start earning new rewards based on the new LP Token amount.

**5)** If you want to **withdraw a partial amount of LPTs** from a farm, the rewards accumulated since your last deposit or withdrawal action will be automatically calculated and sent to you. Then, you will start earning new rewards based on the new LPTs amount. If you **withdraw all the LPTs** staked in a farm, you will also automatically withdraw and receive all the MIN accrued until that point.

Any deposit or withdrawal transaction will automatically create a pending Harvest UTxO which attaches a **2 ADA fee and approximately 1.5 ADA will be returned** along with the harvested MIN rewards. It looks like receiving an airdrop on DripDropz, where you send 3 ADA or 5 ADA to redeem rewards and get about 1.5 ADA back.

Please note, when we refer to _“staking”_ it refers to **sending the LPTs to the Yield Farming Smart Contract** to accrue MIN rewards, it is completely different to the staking of ADA. It is _non-custodial_ as the LPTs are sent to and locked in the Staking Contract and only their owner can withdraw them.Yield Farming
