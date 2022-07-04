# Get your Token Price on CoinMarketCap with Minswap price feeds

[As was announced in the beginning of July on our Twitter](https://twitter.com/MinswapDEX/status/1542850619152662529?s=20\&t=Jia\_fXbexrqo5N5Hgbtj\_g), Cardano Native Tokens no longer need to list on a CEX to get tracked on [CoinMarketCap](https://coinmarketcap.com/), projects can list their tokens on Minswap DEX to get tracked automatically on CMC.

## How does it work?

1\. First, go to [**Submit a request on CMC**](https://support.coinmarketcap.com/hc/en-us/requests/new?ticket\_form\_id=360000493112) **** and submit your token for listing. The process should be pretty quick if you provide all information correctly.

2\. Second, when you apply, on the **Contract Address field**, you need to fill in the concatenation of your policy ID and asset name in _hex format_. This is important to correctly map your token and Minswap price feeds data.\
\
You can see the below snippet for an example:

![](https://lh6.googleusercontent.com/L1h\_Q6JaF9hvModwZYHzQERVmnmmGS70qmf9e78RxivbbJ-KPGIsrBJ2SAXMbCwz3l-xygM8gDYqX2oGKXtSZuBW7d4YN9XqX\_dA065tF8\_4A3TkQBumuCNE86OZcoF-JLAt8g0\_levR)

![](https://lh3.googleusercontent.com/WCFnDx-aTVU1AEB-UVzHQyqz824YlqcXR9oMC6BMvqjfIf3\_0Vbx\_XV9-7LiqvofkfoU0R40NtOLufmbC22lkmR-K2jRIaScXqLtqnD23mCSUARdt3-K4NMFTcHhtcO6xsc1YozGcRwi)

## Example with MIN Token

Lets have a look at the Minswap Token for an example. \
\
Minswap token (MIN): https://cardanoscan.io/token/29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e \
\
Policy ID: 29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c6 \
\
Asset name (hex): 4d494e \
\
\=>  Contract address: 29d222ce763455e3d7a09a665ce554f00ac89d2e99a1a83d267170c64d494e

_An easy way to get the contract address is to look at the Cardanoscan URL of your token._
