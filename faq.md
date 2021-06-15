---
description: Frequently Asked Questions
---

# FAQ

## 1. Token Launch & General Information

### 1.1 Can you do an elevator pitch of MinSwap?

We aim to bring an innovative multi-model asset pool decentralized exchange to the Cardano blockchain. MinSwap aims to be the best liquidity provider on the market by integrating the best asset pool models from across the DEX ecosystem into one protocol. The combination of stable pools, multi-asset pools, and concentrated liquidity will benefit both traders and liquidity providers. We are fair launch with no pre-sales. This ensures our community of users are maximally rewarded, not speculators and insiders.

### 1.2 How do you buy MIN token?

MIN tokens do not have any pre-sale or ICO, ISO or IDO. The only way to acquire MIN tokens is by participating in the protocol or trading it directly on MinSwap. However, there will be an airdrop to reward participants of our incentivized test-net.

1. We anticipate our incentivized test-net \(open to everybody\) with an airdrop will occur in mid-July \(exact date could change based on IOHK onboarding to Alonzo test-net\). You will be able to open the web interface, use the DEX \(trade, farm, and provide liquidity with test tokens\) as normal but in a test environment, and receive airdrop tokens for it. As far as airdrop participation goes, we are going to logarithmically limit rewards, so whales are more on an even playing field with regular stakers. This mechanism, as well as a detailed test-net guide, will be released prior to the test-net launch. Participation will be straightforward and accessible to the non-technical user.
2. Upon DEX main-net launch, stake LP tokens gained from providing an equal amount of ADA and MIN tokens as liquidity to farm more MIN tokens. This should be sometime in late August/early September. Initial MIN tokens are obtained from the test-net, once main-net goes live you can buy MIN tokens after 24 hours.

### 1.3 Will the airdropped tokens on test-net need to be converted to main-net when the main-net launches?

Even though you will be using a test wallet, you will receive your MIN tokens on the main-net wallet. We put a small logic at the monetary policy that allows a transaction sending MINv0 token to burn address \(0x0\) and forge corresponding MINv1 tokens. Also, we airdrop to the main-net address based on your public key in test-net since your private key can work the same way, you’ll be able to access your funds on main-net. We have tools to scan the blockchain and see which wallets interact with which contracts.

### 1.4 How is MinSwap different from upcoming DEXs in Cardano such as Sundae Swap, Cardex or ErgoDEX?

MinSwap offers a different approach, for instance see the features highlighted in our [Whitepaper](https://docs.minswap.org/whitepaper) such as: multi-function liquidity pools, multi-pool routing, functioning as an on-chain price oracle or automatic babel fees redemption. We also focus more on building instead of fundraising. However, since no DEXs have launched or provided test-environments comparisons are difficult.

1. MinSwap will focus on developing multiple kinds of AMM liquidity pools and allow a user's trade to route through the most efficient pools \(this multi-pool routing feature could later be turned into a DEX aggregator\).
2. We will also roll out features that help to develop the Cardano ecosystem, like an IFO launchpad that allows other projects to launch their tokens safely without fearing IDO sniping bots. We will also have an SPO-friendly delegation policy that helps the decentralization of the network. We aim to be the best platform for new projects to list their token, and for their community to buy and support them.

### 1.5 How can I support MinSwap?

Follow our [Twitter](https://twitter.com/minswapdex) and join our [Discord ](https://discord.gg/amg2AFrPMJ)for the latest news. Go to [Ideascale](https://cardano.ideascale.com/a/dtd/MinSwap-Multi-pool-DEX/352679-48088) to support our proposal by clapping and vote for us in the upcoming Catalyst Fund 5, and future ones when voting comes. Catalyst voting is important as this is how the MinSwap project will obtain funds for future development.

### 1.6 Are you developing your own wallet? Or will there be a MetaMask-like wallet for Cardano by the time you launch?

We hope [Yoroi](https://yoroi-wallet.com/) and [Daedelus](https://daedaluswallet.io/) will be functional by then, but otherwise we will create a minimal interface for the wallet.

### 1.7 Is the team part of [Plutus Pioneers Program](https://developers.cardano.org/en/plutus-pioneer-program/)?

Yes, and the team also learnt Plutus by watching Lars´ videos, reading Plutus source code and grinding every day.

### 1.8 What will be the price of MIN token to ADA or to USD?

MIN is not pegged. No specific formula has been decided upon yet. Once the first LP is created, you can stake to earn it. So, market forces will determine the price.

### 1.9 Is there any restriction on the development funds?

Yes, there will be multi-sig and withdrawal limit. So it will take most of the dev team and a long period of time to fully drain the funds.

### 1.10 Is there an official Telegram group for MinSwap?

No, there isn't. Our community discussion is held in [Discord](https://discord.gg/amg2AFrPMJ) only.

### 1.11 What does MIP-1 in the Whitepaper mean?

MIP stands for MinSwap Improvement Proposal, similar to BIP and EIP. MinSwap is a community oriented project from the start and new changes will be proposed and discussed with our community via MIP process.

### 1.12 Could you share some details about the team’s experience and how the project came about?

Our team consists of 4 engineers with experience in FAANG companies and large open-source projects, one marketing manager and 2 designers. You can check our profiles \(Linkedin, Github, etc\) on MinSwap.org. The project started around Feb/Mar 2021 when we were researching cryptocurrencies and Cardano, we found that there wasn't any DEX built on Cardano yet and decided to conceive one. There are many L1 platforms but we found that Cardano has a good community that really cares about its ecosystem and decentralization, good technology and researching approach and we thought that if we choose Cardano as L1 platform to build a DEX it will definitely last.

## 2. Implementation, Attracting LPs and Marketing.

### 2.1 What model/mathematical formula will your first available pools follow?

First one will be like [Uniswap v2](https://uniswap.org/blog/uniswap-v2/). Uniswap v3 \(concentrated LP\) is probably the next if it proves itself well in Ethereum and we can translate it nicely into Cardano eUTxO model as it keeps all AMM´s good parts while being close to an order-book model in terms of capital efficiency. Later on, we'll expand to other liquidity pools such as StableSwap pool or DMM pool and the trading interface will become like a pool aggregator that routes the trade through the most efficient pools.

### 2.2 Regarding DEXs, will you focus more on gamification/UX/marketing \(like PancakeSwap\) or like others more on liquidity \(like Uniswap\). Do we know what the initial focus of MinSwap will be?

Uniswap v3 is focusing on capital efficiency because they've gathered enough liquidity, the users consist more of professionals and institutions, and they have a team highly experienced in Solidity and Ethereum to pull that off. Pancake is based on Uniswap v2 and they took some good ideas from Ethereum to implement on BSC, along with good UI/UX and marketing to make it a well rounded product. MinSwap will most likely follow Pancake in the beginning then go our own path \(multi-pool, capital efficiency\) afterwards.

### 2.3 Did you overcome the MIN value ADA problem? At the moment, to transfer native tokens on Cardano blockchain you need to send around 1.45 ADA along for the transaction fee. Is this still the case?

The official ADA fee to transact with native tokens is not known yet, we will know once Alonzo test-net is out. In the blockchain simulator, where we show our Proof of Concept \([see video](https://youtu.be/NxZBj8e_Yic)\) it charges a flat transaction of 10 ADA or 10 Lovelace.

### 2.4 Regarding the video of the Demo, once swapping on the pool, is there somewhere where we can see the “pool stats” \(e.g. total liquidity in the LP, the fees taken…\)?

We will add more helpful text in the interface, we'll also create a dedicated info site like the one for [Uniswap.](https://info.uniswap.org/)

### 2.5 How do you market to people who have substantial liquidity to provide to the protocol?

We are considering making the mint rate much higher \(like x5-x10\) in the beginning \(2-4 weeks\) to attract more LPs, this is similar to how a traditional business discounts when just opening. Early announcement + large incentives for a short duration will suffice in the beginning. To keep LPs from withdrawing their liquidity after the high initial rewards end we are considering a number of options. MIN multipliers for long-term early providers, NFTs, leaderboards, and other methods are being explored.

### 2.6 What's your plan for the NFT campaign?

Our plan is to release our NFTs which we'll be able to share on NFT related forums and servers. It appeals to global markets, as we're big on multilingual international reach. Our first target is Japan. Second is Spain. Then South America, Brazil, then maybe Italy and so on. There will be some time between each giveaway as the team will also be focused on limited merch and other promotional items.

### 2.7 How will you do marketing?

We plan to promote MinSwap and attract users in a number of ways. Twitter will be the platform for big giveaways, community engagement, and most announcements can be found there first. Keep an eye on our [Twitter page](https://twitter.com/minswapdex). Interviews on different Youtube channels, engagement with the [Reddit community](https://www.reddit.com/r/MinSwap/), and promotion in places where the crypto community gathers are all underway.

## 3. DEX Features

### 3.1 How will you gradually implement different pools?

In the beginning, because of low liquidity, LPs can only provide liquidity to ADA/X pool \(X is a token\) and every trade of X to Y will go like X -&gt; ADA -&gt; Y. After we get enough users, we'll allow people to create X/Y pools and our frontend interface will find the best trade routes, but that's for constant-product pools, after that we'll go multi-pool which you can find in the [WhitePaper](https://docs.minswap.org/whitepaper).

### 3.2 Will MinSwap have Limit Orders for swapping?

DEXs normally don't have limit orders for a reason, it's hard to implement on smart contracts of a CFMM \(Constant Function Market Makers\) though Uniswap v3 with their new concentrated liquidity pool has a "sort of" limit order.

### 3.3 Any plans for smart contract audit?

Yes, we'll contact audit firms and apply for Catalyst Fund 6. The audit firms and completion dates will be announced in the next few months before the main-net launch.

### 3.4 Will there be light mode/dark mode?

It is on our roadmap but not a priority.

### 3.5 Will MinSwap only be able to trade tokens built on Cardano? Will there be an ETH/ADA pool?

There'll be the ERC20-Converter that helps bridge tokens from Ethereum, and [WrapAssets](https://www.wrapassets.io) to bring wrapped Bitcoin and other cryptocurrencies, so we will be able to have ETH/ADA pool.

### 3.6 Is it a cross-chain DEX?

We originally had an idea of a cross-chain DEX based on Cardano when writing the WhitePaper. But then figured that other projects are probably developing bridges in parallel while we develop the DEX \(e.g. ERC-20 converter, WrapAsset, ThorChain\) so we set that idea aside. When MinSwap comes out, we'll use whatever bridge is available to trade assets from other chains.

### 3.7 Is the code open-sourced?

Yes, most of the code is open sourced on Github. The smart contract code is private and will be open sourced once it is fully audited before main-net launch. But to understand how people are building Dapps for Cardano the Plutus Pioneer Program has great example code: [Found Here.](https://github.com/input-output-hk/plutus-pioneer-program)

### 3.8 According to your [Youtube Demo](https://youtu.be/NxZBj8e_Yic), performing a transaction seems kind of slow from a User Experience perspective, how will you improve this?

Through User Interface, we're going to show a popup of "Transaction submitted, view on Cardano explorer" and then show the transaction confirmed notification later.

## 4. DEX for eUTXO Model, security and tokenomics.

### 4.1 Regarding eUTXO model, isn’t it annoying for farming on a DEX?

Smart contracts don’t keep any addresses, they only keep the funds and the total supply of LP tokens corresponding to the pool. So, when you redeem LP tokens, the smart contract gives you the funds according to the ratio of your LP tokens. In the worst case, we have to store the people's addresses in the farm, it's easy enough as Plutus allows us to get the “true” PubKeyHash of a wallet, as opposed to the “smoke” addresses of Yoroi/Daedelus.

### 4.2 Is MinSwap going to have protection against flash loan attacks?

This refers to an attack on Pancake Bunny using Pancake Swap, it is difficult something like this can happen in Cardano. In addition, we will have a TWAP \(Time Weighted Average Price\) price oracle and fair LP token pricing in our roadmap to help other projects shield against flash loan attacks if they're interested in using MinSwap as price oracle.

### 4.3 Are you afraid of front-running attacks?

No, Cardano doesn't even have to care about front-running or MEV \(“miner-extractable value” refers to the amount of value that miners can suck out of the system by front-running\), because of the eUTXO model. In the eUTXO model the input and output of a transaction is predetermined before it's submitted to the chain, so if a relayer/staker node saw it and decided to front-run you, they'll use the input and your transaction is no longer valid, and you don't have to pay any fee. Since front-running a transaction makes that transaction invalid, the front-runner doesn't make any profit, and a sandwich attack is impossible.

### 4.4 What is the tokenomics of MIN?

The tokenomics is under research. It will be published in the next MIP \(will be shared in the Discord server\). Some rough ideas include a huge mint rate in the beginning to offset for Impermanent Loss, MIN tokens will be used for governance and for staking xMIN to get a percentage of trading fees and other economic activities such as dividends. Every protocol begins with a highly inflationary scheme to reward early participants, because it's extremely risky in the beginning. Thus, providing liquidity in the first month \(“harvest season”\) after main-net launch will lead to x5-x10 more rewards than in later months. We'll have a detailed tokenomics draft, then send it to the community for feedback and input, then finalize it and make it official.

### 4.5 Do you have the APYs for different pools, emission schedules and other numbers figured out yet? Will rewards be locked for any amount of time?

APY: it depends on supply and demand, the supply is controlled by our team and later by community via a DAO, the demand is control by market participants.

Emission schedule: The first month is the "harvest season", emission is huge there, it will be reduced as time goes on and trading volume increases allowing LPs to earn more from trading fees.

### 4.6 How does MinSwap delegate locked ADA?

20% of locked ADA is delegated to stake pools that haven't produced any block to help the SPOs mint their first block. The rest is delegated to small-to-medium community pools to encourage decentralization and make sure LPs earn stake rewards on top of trade fees. The delegation policy parameters can later be voted to change by the DAO.

## 5. Advanced Technicals

### 5.1 In your Youtube Interview with [MUSE Pool](https://youtu.be/yL9RXSqVHDs), you mention you can “stake” your ADA, 3 times, which would give you 3 ways to generate passive income at the same time, how does this work?

You provide your ADA tokens to MinSwap to earn LP tokens and trade fees, MinSwap delegates your ADA to stake pools so you earn staking rewards, later on you lend your LP tokens at [Liqwid](https://www.liqwid.finance/) and earn interest. So that's 3 times.

### 5.2 How do you design around the issue that Cardano only lets you touch a eUTXO once per block? Without designing around that, only one person could trade against each pool every block.

There's a myth that the eUTXO model only allows one UTXO to be consumed per block, but when we tested it, we found no problem so far. Our hypothesis is that if the transactions are being submitted sequentially through a centralized PAB \(Plutus Application Backend\), the PAB will execute each transaction with UTXO ref of the previous transaction and once all transactions are included in a block it will naturally succeed.

**There are 2 scenarios that could go wrong though:**

1. Somebody submitted an invalid transaction that fails, thus failing subsequent dependent transactions. However, this somebody will suffer a transaction fee because they fail as onchain validator but the subsequent dependent transaction doesn't have to pay a fee because they just refer to the wrong UTXO ref.
2. Transactions are being submitted from different PAB that takes time to sync their blockchain state with each other, they both refer to the same UTXO and fail. This is unavoidable but we think it's better than letting nodes deciding transaction order based on gas bidding which would lead to nasty problems like transaction took forever to confirm and MEV**.**

Additional info found on Reddit: A single dApp like a DEX could enable simultaneity by having multiple transaction outputs that users can access. Although each output can only be used by one person, there are multiple of them. If someone submits an invalid transaction nothing will happen. There will be no failed transaction or charged transaction fee, unless a malicious actor tries to breach the rules then they will suffer fees.This is a complicated topic, the team is waiting for an official answer from IOHK and the Plutus team.

### 5.3 How does writing Smart Contracts in Cardano with Plutus compare to Solidity on Ethereum?

Plutus is written in Haskell, which means that we benefit from using a language that has been developed for decades to write safe and correct programs, instead of inventing a new one. Haskell is one of the few languages supporting big integers natively, so we can write normal arithmetic like a + b - c instead of weird code like a.add\(b\).sub\(c\). Building on Haskell also means we can use a lot of stable tooling and libraries from day 1, including QuickCheck. Normally in Solidity devs only write tests for a few scenarios, but QuickCheck is like a test monkey that randomly plays with our smart contract a few thousand times to see if it breaks.

Solidity, there are many kinds of tokens: Ether, ERC-20, ERC-721,... which lead to ugly wrap and unwrap in many cases. In Plutus all tokens are the same thing: native token, so operations on them are much easier. eUTXO is amazing because it can predict transaction fees accurately and users pay no fee for failed transactions. It also prevents a whole class of problems Ethereum is fighting now like front-running, never-confirmed transactions and MEV. There are some concerns with concurrency in eUTXO but it stems from the Ethereum mindset that a smart contract is one giant state machine serving the richest gas bidders first, which again leads to so many problems like the ones above.

The blockchain only stores the hash of a script, which means a script takes the same space no matter how complicated it is. This is long-term thinking about decentralization, considering Ethereum is more than 300GB now. Of course, there's always 2 sides of the same coin - one thing we found difficult with Plutus is on-chain debugging, but we believe the Plutus team is working hard to improve this. In conclusion, the long years of researching and building from scratch has yielded results. What we have now is a better, faster and safer smart contract platform.

## Disclaimer

**The content of the FAQ is for informational purposes only, you should not construe any such information or any material on the MinSwap site as legal, investment, financial, or other advice. Your use of the MinSwap protocol upon launch involves various risks, including, but not limited to, losses while digital assets are being supplied to the MinSwap protocol and losses due to the fluctuation of prices of tokens in a trading pair or liquidity pool. Before using the MinSwap protocol, you should review the relevant documentation to make sure you understand how the MinSwap protocol works. Although MinSwap Labs developed much of the initial code for the MinSwap protocol, it does not provide, own, or control the MinSwap protocol, which is run by smart contracts deployed on the Cardano blockchain. After launch, upgrades and modifications to the protocol will be managed in a community-driven way by holders of the MIN governance token . No developer or entity involved in creating the MinSwap protocol will be liable for any claims or damages whatsoever associated with your use.**

