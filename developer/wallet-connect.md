# Wallet Connect on Minswap DEX

Wallet Connect simplifies dApp connections. With your mobile wallet in hand, scan the website's QR code, and you're connected instantly.

## Modes

Minswap offers two distinct modes for Wallet Connect:

### Default Mode

**TLDR:** Default mode is widely supported by popular wallets like Eternl and Flint.

In Default mode, the account format is `<namespace>:<network>:<stake_address_in_cbor>`. However, it does not support network/account change events.

### Custom Mode

**TLDR:** Custom mode is Minswap's unique approach, designed to enhance the user experience. Currently, it's supported by NuFi.

Custom mode uses the account format `<namespace>:<network>:<stake_address_in_cbor>-<base_address_in_cbor>`. It supports network/account change events.

Under custom mode, there are 2 modes have their advantages and trade-offs, which are summarized in the table below:

| Field     | DApp RPC                                       | Wallet RPC                                  |
|-----------|------------------------------------------------|---------------------------------------------|
| UTxOs     | Fetches UTxOs using the base address (similar to nami) | Utilizes wallet UTxOs (includes support for locked and pending UTxOs) |
| Balance   | Displays the balance of the base address only | Shows the balance from the wallet (aggregates balances across all addresses) |
| UX        | Enhances the user experience with faster responses | Responses are relatively slower and necessitate the wallet to be connected in the background whenever the dApp is in use |
| Submit Tx | Submits transactions through minswap's node | Submits transactions using the wallet's submit endpoint |


`DApp RPC` mode was designed so that wallet need not be online all the time you access the DEX. When DEX request for a signature from wallet, mobile wallets should show push notification to sign the transaction.

User can toggle between `DApp RPC` and `Wallet RPC` modes upon selecting the dropdown where the address is displayed on the DEX as shown in image below.

<figure><img src="../../.gitbook/assets/wc-rpc-mode.png" alt=""><figcaption></figcaption></figure>

## Development

If you're a wallet developer interested in integrating Wallet Connect with Minswap DEX, check out our Wallet Connect repository on GitHub: [github.com/minswap/wallet-connect](https://github.com/minswap/wallet-connect) for more info.
