# Liquidity Pool Fee Governance

## Overview

The LP Fee Management System allows LP token holders to delegate the management of Liquidity Pool fees to a trusted individual, such as the Token Project Owner or a financial expert. The process involves proposing a candidate for this role, voting on the proposal, and, if approved, granting the selected individual the authority to adjust the pool fees based on market conditions. A deposit is required to submit a proposal, and delegation is controlled via an NFT.

### Proposal Types

* **Delegation:** Proposal for Delegate of Authority Fee Manager to an Address. Available when the pool doesn't have a Fee Manager.
* **Revoke:** Proposal for Revocation of Delegated Authority Fee Manager. Only available when the pool has a Fee Manager.
* **Transfer Ownership:** Proposal for Transferring Delegated Authority Fee Management to a New Manager. Only available when the pool has a Fee Manager.

### Proposal Rules

#### Proposing Rules:

* The proposer must be an LP holder.
* A 100 ADA deposit is required as a Proposal Fee. This deposit is refundable if the proposal passes; otherwise, it is donated to the ADA-MIN Pool v2.

#### Voting Rules:

* **Voting Period:** The voting period is open for a specified duration (e.g., 7 days) as determined by the proposer.
* **Participation:** Any LP token holders in the snapshot can join the Active proposal of the pool.
* **Snapshot Mechanism:** A snapshot is taken 1 hour before the start time of the proposal. For example, if the snapshot at 0h:0m:0s is used for any proposals that have a start time between 1h:0m:0s and 1h:59m:59s.
* **Pass Condition:** The proposal must receive more than 50% of total LP tokens votes in favor to pass and take effect **immediately** without waiting until the end of the voting period.
* **Fail Condition:** If at the end of the proposal period, the proposal receives less than 50% of total LP tokens votes in favor, it will fail. The deposit fund will be donated to the ADA-MIN Pool v2.
* **Changing Votes:** Once a vote is cast, it cannot be undone.

