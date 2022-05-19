---
description: General Frequently Asked Questions
---

# General

## 1. Token Launch & General Information

### 1.1 Can you do an elevator pitch of Minswap?

We aim to bring an innovative multi-model asset pool decentralized exchange to the Cardano blockchain. Minswap aims to be the best liquidity provider on the market by integrating the best asset pool models from across the DEX ecosystem into one protocol. The combination of stable pools, multi-asset pools, and concentrated liquidity will benefit both traders and liquidity providers. Our tokens are fairly distributed without any private or VC investment. This ensures our community of users are maximally rewarded, not speculators and insiders.

### 1.2 How do you buy MIN token?

Swap on DEXs where Minswap tokens are currently traded such as [Minswap](https://app.minswap.org/swap).

### 1.3 Will the airdropped tokens on test-net need to be converted to main-net when the main-net launches?

Even though you will be using a test wallet, you will receive your MIN tokens on the mainnet wallet. We put a small logic at the monetary policy that allows a transaction sending MINv0 token to burn address (0x0) and forge corresponding MINv1 tokens. Also, we airdrop to the mainnet address based on your public key in test-net since your private key can work the same way, you’ll be able to access your funds on main-net. We have tools to scan the blockchain and see which wallets interact with which contracts.

### 1.4 How is Minswap different from upcoming DEXs in Cardano such as SundaeSwap, Cardax or ErgoDEX?

Minswap offers a different approach, for instance see the features highlighted in our [Whitepaper](https://docs.minswap.org/whitepaper) such as: multi-function liquidity pools, multi-pool routing, functioning as an on-chain price oracle or automatic babel fees redemption. In addition:

1. Minswap will focus on developing **multiple kinds of AMM liquidity pools** and allow a user's trade to route through the most efficient pools (this multi-pool routing feature could later be turned into a DEX aggregator).
2. Minswap aims to be at the **cutting edge of Cardano DeFi**, we pioneered ideas such as the [FISO](https://medium.com/minswap/minswap-fair-launch-tokenomics-and-fiso-airdrop-start-date-a75f3e75a546) model, the [MINt](https://forum.minswap.org/t/mint-token-expose-mint-liquidity-providers-to-other-pairs/40) token an our [LBE](https://minswap-labs.medium.com/meteor-lbe-mainnet-launch-yield-farming-more-f73c6c2a8b37), and plan to continue doing so with further novel initiatives, like an IFO launchpad that allows other projects to launch their tokens safely without fearing IDO sniping bots. We will also have an SPO-friendly delegation policy that helps the decentralization of the network. We aim to be the best platform for new projects to list their token, and for their community to buy and support them.

### 1.5 How can I support Minswap?

Follow our [Twitter](https://twitter.com/minswapdex), join our [Discord ](https://discord.gg/amg2AFrPMJ)for the latest news and participate in our [Forum ](https://forum.minswap.org/)to dicuss ideas that help improve Minswap as a whole.

### 1.6 Are you developing your own wallet? Or will there be a MetaMask-like wallet for Cardano by the time you launch?

Currently, Minswap DEX supports CCVault, Nami, Flint, Typhon and GeroWallet. Support for Yoroi will be added later.

### 1.7 Is the team part of [Plutus Pioneers Program](https://developers.cardano.org/en/plutus-pioneer-program/)?

Yes, and the team also learnt Plutus by watching Lars videos, reading Plutus source code and grinding every day.

### 1.8 What will be the price of MIN token to ADA or to USD?

MIN is not pegged. No specific formula has been decided upon yet. Once the first LP is created, you can stake to earn it. So, market forces will determine the price.

### 1.9 Is there any restriction on the development funds?

Yes, there will be multi-sig and withdrawal limit. So it will take most of the dev team and a long period of time to fully drain the funds.

### 1.10 Is there an official Telegram group for Minswap?

Our community discussion is held in [Discord](https://discord.gg/amg2AFrPMJ) mostly, but we have a [Telegram Channel](https://t.me/MinswapMafia) for announcements.

### 1.11 What does MIP-1 in the Whitepaper mean?

MIP stands for Minswap Improvement Proposal, similar to BIP and EIP. Minswap is a community oriented project from the start and new changes will be proposed and discussed with our community via MIP process.

### 1.12 Could you share some details about the team’s experience and how the project came about?

Our team consists of 4 engineers with experience in big companies like Amazon, GHTK and large open-source projects, one marketing manager and 2 designers. You can check our profiles (Linkedin, Github, etc) on Minswap.org. The project started around Feb/Mar 2021 when we were researching cryptocurrencies and Cardano, we found that there wasn't any DEX built on Cardano yet and decided to conceive one. There are many L1 platforms but we found that Cardano has a good community that really cares about its ecosystem and decentralization, good technology and researching approach and we thought that if we choose Cardano as L1 platform to build a DEX it will definitely last.

## 2. Implementation, Attracting LPs and Marketing.

### 2.1 What model/mathematical formula will your first available pools follow?

First one will be like [Uniswap v2](https://uniswap.org/blog/uniswap-v2/). Uniswap v3 (concentrated LP) is probably the next if it proves itself well in Ethereum and we can translate it nicely into Cardano eUTxO model as it keeps all the good parts of AMMs while being close to an order-book model in terms of capital efficiency. Later on, we'll expand to other liquidity pools such as StableSwap pool or DMM pool and the trading interface will become like a pool aggregator that routes the trade through the most efficient pools.

### 2.2 Regarding DEXs, will you focus more on gamification/UX/marketing (like PancakeSwap) or like others more on liquidity (like Uniswap). Do we know what the initial focus of Minswap will be?

Uniswap v3 is focusing on capital efficiency because they've gathered enough liquidity, the users consist more of professionals and institutions, and they have a team highly experienced in Solidity and Ethereum to pull that off. Pancake is based on Uniswap v2 and they took some good ideas from Ethereum to implement on BSC, along with good UI/UX and marketing to make it a well rounded product. Minswap will most likely follow Pancake in the beginning then go our own path (multi-pool, capital efficiency) afterwards.

### 2.3 How do you market to people who have substantial liquidity to provide to the protocol?

We are considering making the mint rate much higher (like x5-x10) in the beginning (2-4 weeks) to attract more LPs, this is similar to how a traditional business discounts when just opening. Early announcement + large incentives for a short duration will suffice in the beginning. To keep LPs from withdrawing their liquidity after the high initial rewards end we are considering a number of options. MIN multipliers for long-term early providers, NFTs, leaderboards, and other methods are being explored.

### 2.4 How will you do marketing?

We plan to promote Minswap and attract users in a number of ways. Twitter will be the platform for big giveaways, community engagement, and most announcements can be found there first. Keep an eye on our [Twitter page](https://twitter.com/minswapdex). Interviews on different Youtube channels, engagement with the [Reddit community](https://www.reddit.com/r/Minswap/), and promotion in places where the crypto community gathers are all underway.

## 3. DEX Features

### 3.1 Any plans for smart contract audit?

Yes, we have been audited by [Tweag](https://minswap-labs.medium.com/minswap-announces-audit-completion-by-tweag-79a2910b98a).&#x20;

### 3.2 Will Minswap only be able to trade tokens built on Cardano? Will there be an ETH/ADA pool?

Once it is ready, there'll be the ERC20-Converter that helps bridge tokens from Ethereum, and [WrapAssets](https://www.wrapassets.io) to bring wrapped Bitcoin and other cryptocurrencies, so we will be able to have ETH/ADA pool.

### 3.3 Is it a cross-chain DEX?

We originally had an idea of a cross-chain DEX based on Cardano when writing the WhitePaper. But then figured that other projects are probably developing bridges in parallel while we develop the DEX (e.g. ERC-20 converter, WrapAsset, ThorChain) so we set that idea aside. When Minswap comes out, we'll use whatever bridge is available to trade assets from other chains.

### 3.4 Is the code open-sourced?

Yes, most of the code is open sourced on Github. The smart contract code is private and will be open sourced once it is fully audited after main-net launch. But to understand how people are building Dapps for Cardano the Plutus Pioneer Program has great example code: [Found Here.](https://github.com/input-output-hk/plutus-pioneer-program)

## 4. DEX for eUTXO Model, security and tokenomics.

### 4.1 Regarding eUTXO model, isn’t it annoying for farming on a DEX?

Smart contracts don’t keep any addresses, they only keep the funds and the total supply of LP tokens corresponding to the pool. So, when you redeem LP tokens, the smart contract gives you the funds according to the ratio of your LP tokens. In the worst case, we have to store the people's addresses in the farm, it's easy enough as Plutus allows us to get the “true” PubKeyHash of a wallet, as opposed to the “smoke” addresses of Yoroi/Daedelus.

### 4.2 Is Minswap going to have protection against flash loan attacks?

This refers to an attack on Pancake Bunny using Pancake Swap, it is difficult something like this can happen on Cardano. In addition, we will have a TWAP (Time Weighted Average Price) price oracle and fair LP token pricing in our roadmap to help other projects shield against flash loan attacks if they're interested in using Minswap as price oracle.

### 4.3 Are you afraid of front-running attacks?

No, Cardano doesn't even have to care about front-running or MEV (“miner-extractable value” refers to the amount of value that miners can suck out of the system by front-running), because of the eUTXO model. In the eUTXO model the input and output of a transaction is predetermined before it's submitted to the chain, so if a relayer/staker node saw it and decided to front-run you, they'll use the input and your transaction is no longer valid, and you don't have to pay any fee. Since front-running a transaction makes that transaction invalid, the front-runner doesn't make any profit, and a sandwich attack is impossible.

### 4.4 What is the tokenomics of MIN?

You can read about our tokenomics here: [Tokenomics](https://docs.minswap.org/tokenomics).

### 4.5 Do you have the APYs for different pools, emission schedules and other numbers figured out yet? Will rewards be locked for any amount of time?

You can see our Yield Farming schedule on our [Tokenomics page](../tokenomics.md). APYs vary according to factors such as TVL of the Pool and Volume. To see how MIN rewards are allocated to each Pool, please read our [Yield Farming page](../yield-farming/).

## 5. Advanced Technicals

### 5.1 In your Youtube Interview with [MUSE Pool](https://youtu.be/yL9RXSqVHDs), you mention you can “stake” your ADA, 3 times, which would give you 3 ways to generate passive income at the same time, how does this work?

You provide your ADA tokens to Minswap to earn LP tokens and trade fees, Minswap delegates your ADA to stake pools so you earn staking rewards, later on you lend your LP tokens at [Liqwid](https://www.liqwid.finance/) and earn interest. So that's 3 times.

### 5.2 How do you design around the issue that Cardano only lets you touch a eUTXO once per block? Without designing around that, only one person could trade against each pool every block.

[Introducing Laminar — An eUTxO scaling protocol for accounting-style smart contract](https://medium.com/minswap/introducing-laminar-an-eutxo-scaling-protocol-for-accounting-style-smart-contract-d1ac8847dde8)

### 5.3 How does writing Smart Contracts in Cardano with Plutus compare to Solidity on Ethereum?

Plutus is written in Haskell, which means that we benefit from using a language that has been developed for decades to write safe and correct programs, instead of inventing a new one. Haskell is one of the few languages supporting big integers natively, so we can write normal arithmetic like a + b - c instead of weird code like a.add(b).sub(c). Building on Haskell also means we can use a lot of stable tooling and libraries from day 1, including QuickCheck. Normally in Solidity devs only write tests for a few scenarios, but QuickCheck is like a test monkey that randomly plays with our smart contract a few thousand times to see if it breaks.

Solidity, there are many kinds of tokens: Ether, ERC-20, ERC-721,... which lead to ugly wrap and unwrap in many cases. In Plutus all tokens are the same thing: native token, so operations on them are much easier. eUTXO is amazing because it can predict transaction fees accurately and users pay no fee for failed transactions. It also prevents a whole class of problems Ethereum is fighting now like front-running, never-confirmed transactions and MEV. There are some concerns with concurrency in eUTXO but it stems from the Ethereum mindset that a smart contract is one giant state machine serving the richest gas bidders first, which again leads to so many problems like the ones above.

The blockchain only stores the hash of a script, which means a script takes the same space no matter how complicated it is. This is long-term thinking about decentralization, considering Ethereum is more than 300GB now. Of course, there's always 2 sides of the same coin - one thing we found difficult with Plutus is on-chain debugging, but we believe the Plutus team is working hard to improve this. In conclusion, the long years of researching and building from scratch has yielded results. What we have now is a better, faster and safer smart contract platform.

## Disclaimer

**The content of the FAQ is for informational purposes only, you should not construe any such information or any material on the Minswap site as legal, investment, financial, or other advice. Your use of the Minswap protocol upon launch involves various risks, including, but not limited to, losses while digital assets are being supplied to the Minswap protocol and losses due to the fluctuation of prices of tokens in a trading pair or liquidity pool. Before using the Minswap protocol, you should review the relevant documentation to make sure you understand how the Minswap protocol works. Although Minswap Labs developed much of the initial code for the Minswap protocol, it does not provide, own, or control the Minswap protocol, which is run by smart contracts deployed on the Cardano blockchain. After launch, upgrades and modifications to the protocol will be managed in a community-driven way by holders of the MIN governance token. No developer or entity involved in creating the Minswap protocol will be liable for any claims or damages whatsoever associated with your use.**
