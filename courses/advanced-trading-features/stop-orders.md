# Stop Orders

## What is a Stop Order?

{% embed url="https://www.youtube.com/watch?v=ptSCZR1zUic" %}

A stop order is a type of trade order that becomes a market order once a specified price is reached, known as the **stop price**. Unlike limit orders, which execute only at a predetermined price or better, stop orders trigger a trade when the market reaches the stop price, at which point the order becomes a regular market order that executes at the best available price. This feature allows traders to automate their trades based on market movements.

There are two main types of stop orders:

* **Stop-Loss Orders**: Used to limit potential losses by selling an asset once it falls to a certain price.
* **Stop-Buy Orders**: Used to enter a position or buy an asset once it rises to a specific price.

***

### How Stop Orders Work

#### Stop-Loss Order (For Selling)

A stop-loss order is designed to minimise losses by automatically selling an asset once its price falls to a specified level.\
&#xNAN;_&#x45;xample_: If a trader owns Token A and wants to prevent a significant loss, they might set a stop-loss order at **$50**. If Token A’s price drops to $50, the stop order is triggered, converting it into a market order, and the asset is sold at the best available price.

#### Stop-Buy Order (For Buying)

A stop-buy order purchases an asset once its price reaches a certain level. This order type is often used when traders want to capitalise on upward momentum.\
&#xNAN;_&#x45;xample_: If Token B is trading at **$40** but a trader believes it will continue rising once it hits **$45**, they can set a stop-buy order at $45. The stop order triggers when the price reaches $45, and Token B is bought at the market price.

***

### Key Benefits of Stop Orders

* **Automated Trading**: Traders don’t need to monitor the market constantly—once the stop price is reached, the trade is triggered automatically.
* **Risk Management**: Stop-loss orders protect traders from large losses by selling when prices fall below a set threshold.
* **Capitalising on Price Trends**: Stop-buy orders enable entry during upward momentum without constant monitoring.
* **Execution Speed**: Once triggered, the order executes at the best available price, ideal for fast-moving markets.

***

### Example of Stop Orders in Action

* **Stop-Loss Example**: A trader owns 100 tokens of Token C, currently priced at $30. They set a stop-loss order at **$25**. If the price falls to $25, the tokens are sold at the next available market price, limiting further losses.
* **Stop-Buy Example**: A trader watches Token D at $20 and believes it will rally once it breaks $25. They set a stop-buy order at **$25**. If the price hits $25, the tokens are bought automatically, allowing them to ride the momentum.

***

### Stop Orders vs. Limit Orders

* **Stop Orders**: Trigger a market order once the stop price is reached. Useful for protecting against losses or entering during momentum, but **do not guarantee exact execution price**.
* **Limit Orders**: Execute only at a specified price or better. Guarantee execution price but may never fill if the market doesn’t reach the set price.

***

### Potential Risks of Stop Orders

* **Price Slippage**: The actual trade price may differ from the stop price in volatile or low-liquidity markets.
* **Gaps in Price**: In fast-moving markets, the price may jump beyond the stop level before the order executes, leading to worse-than-expected outcomes.

***

### How to Create a Stop-Loss Order

1. **Choose Stop**\
   From the trading screen, choose **"Stop"** to start creating a stop order.
2. **Specify the Sell Amount**\
   Enter the asset you want to sell and the amount.\
   &#xNAN;_&#x45;xample_: Sell **MIN tokens** if the price drops further.
3. **Set the Stop Price**\
   Define the price at which you want to sell.\
   You can use predefined percentage options (e.g., 5%, 10%, 25%).\
   &#xNAN;_&#x45;xample_: Sell if MIN drops **10% below the current price**.
4. **Set the Expiry Time**\
   Choose when the order should expire. If it doesn’t trigger in time, assets are returned to your wallet.
5. **Place Order**\
   Click **"Place order"** to proceed.
6. **Sign and Submit**\
   Sign the transaction in your wallet and submit it on-chain. The stop order will now execute automatically if conditions are met.

### How to Create a Stop-Buy Order

A stop-buy order is designed to help traders enter a position during upward momentum. Instead of buying an asset immediately, you set a trigger price above the current market price. Once the stop price is reached, the order converts into a market order and executes at the best available price.

This strategy is commonly used when traders believe an asset will continue to rise once it breaks through a certain resistance level. Unlike a take profit order—which is used to **sell** and lock in gains—a stop-buy order is used to **buy** into strength.

#### Example

Suppose MIN is trading at **0.0469 ADA**. You believe that if it breaks **0.0494 ADA**, the trend will continue upward. You set a stop-buy order at **0.0494 ADA**. Once the price reaches this level, the order executes, and you purchase MIN automatically at the best available market price.

#### Steps to Place a Stop-Buy Order

1. **Choose Stop**\
   From the trading screen, select **"Stop"** as your order type.
2. **Specify the Buy Amount**\
   Enter the asset you wish to purchase and the amount (e.g., buy MIN with ADA).
3. **Set the Stop Price**\
   Define the trigger price at which the buy should occur.\
   &#xNAN;_&#x45;xample_: Buy MIN when it reaches **0.0494 ADA**.
4. **Set Expiry**\
   Choose an expiry time for the order. If the price doesn’t hit your stop price before expiry, your ADA remains in your wallet.
5. **Place Order and Sign**\
   Confirm the trade, sign in your wallet, and submit it on-chain. The order will execute automatically when conditions are met.

***

#### Stop-Buy vs. Take Profit

* **Stop-Buy Order**: Enters a new position once the price rises to a chosen level.
* **Take Profit Order**: Exits an existing position by selling once the price reaches a desired profit target.

Both can be used together as part of a risk/reward strategy:

* **Stop-Loss** to protect downside
* **Take Profit** to lock in gains
* **Stop-Buy** to catch upward trends
