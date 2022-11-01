# Trading Fee Discount

The motive behind this initiative is the one of rewarding and incentivising those avid Minswap users who trade on the DEX on a frequent basis. Read below for how the Batcher Fee Discount works!

### How it Works

Currently, everyone who swaps on the Minswap DEX pays a **2 $ADA fee** in addition to the 0.3% fee that is paid to LPs. As part of the initiative to increase the utility of the $MIN token within the platform, the $MIN token will entitle traders on Minswap to a **Discount on this 2 $ADA Batcher Fee** as long as:

1. They **hold $MIN** in their wallet the moment they make the trade.&#x20;
2. Or they have provided $MIN as liquidity providers and they **hold $MIN/$ADA LP Tokens** in their wallet the moment they make the trade.

For now, the discount **will not apply to those who are staking** $MIN/$ADA LP Tokens in Yield Farming or have $MIN/$ADA LP Tokens in the MINt conversion process.

The moment you want to make a trade on Minswap, the backend will identify how many $MIN tokens you hold (whether $MIN in your wallet, or $MIN in $MIN/$ADA LP Tokens) and will apply a Discount on the 2 $ADA Batcher Fee depending on the Fee Structure underscored below.

### Fee Structure

<figure><img src="../../.gitbook/assets/image (3) (2).png" alt=""><figcaption></figcaption></figure>

The maximum amount for the Fee Discount on the Batcher Fee is **50,000 $MIN** and the equivalent LP Tokens (at the time of writing 25,000 $MIN and the equivalent $ADA are _5,000,000,000 $MIN-ADA LP Tokens_). The **maximum Discount** will be **25%**, meaning users with more than 50,000 $MIN or 5,000,000,000 $MIN-ADA LP Tokens will pay **1.5 $ADA instead of 2 $ADA**. Users with less than 50,000 $MIN will also receive a Discount on their Batcher fees as long as they have 1 $MIN worth in their wallet. This **Discount** is determined by the following formula:

#### Assumptions

* (_X_) is the amount of MIN in the wallet
* (_Y_) is the amount of ADA-MIN LP in the wallet
* (_MX_) is the amount of MIN which can get 25% reduction (currently 50,000 $MIN)&#x20;
* (_MY_) is the amount of ADA-MIN LP which can get 25% reduction (currently 5,000,000,000 $MIN-ADA LP Tokens)

<figure><img src="../../.gitbook/assets/Screenshot 2022-09-15 221602.jpg" alt=""><figcaption></figcaption></figure>

As such, Batcher Fee Discount is linearly increased based on the amount of $MIN and $MIN-ADA LP. ou can see a table representative of the different discounts and the $ADA fee to be paid and the amount of $MIN needed above. Bear in mind, even a wallet with 1 $MIN will be eligible for a Discount in the Batcher Fee!
