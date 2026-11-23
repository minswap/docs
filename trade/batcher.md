# Batcher

Cardano’s unique Extended UTXO (eUTxO) model means decentralised exchanges (DEXs) like Minswap must handle transactions differently than Ethereum-based platforms.

Instead of each user transaction directly interacting with smart contracts, Minswap uses batchers — off-chain services that collect multiple swap requests, bundle them, and submit a single transaction to the Cardano blockchain.

#### What Are Batchers?&#xD;

Batchers play a crucial role in the Cardano DEX ecosystem by:

#### Collecting swap requests from users&#xD;

Efficiently batching multiple trades into a single transaction
\
Submitting that transaction to the blockchain on the users’ behalf
\
This system improves throughput, reduces congestion, and optimises transaction efficiency on-chain.

#### Why Are Batcher Fees Charged?


\
Batchers charge a small fee (2 ADA per order on Minswap) to:

* Cover the cost of transaction fees on the Cardano network
*
  Incentivise operators who maintain and run the batching infrastructure
