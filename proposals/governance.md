---
description: >-
  The governance structure outlined is a draft - subject and likely to change
  before mainnet launch
---

# Governance

## Initial Governance Overview

From the beginning, Minswap will have an online user interface and simple voting procedure for MIPs. MIP stands for Minswap Improvement Proposal, similar to BIP and EIP. As a community-oriented project from the start, new changes will be proposed and discussed with our community via the MIP process.

While Minswap governance will be live from day one, decentralized control of the treasury and protocol changes via MIP implementations will be rolled out on a vesting schedule.  An overview of this schedule will be published prior to launch. Essentially, the rights and power accorded to MIN token holders will steadily increase with time. The reason for vesting governance is to provide the community enough time to familiarize itself with the governance system, bring in high-quality protocol delegates, build and test our technical governance tools, and allow discussions and communications to develop.

To mitigate concerns about the use of the Minswap community treasury before governance fully vests we have implemented a number of measures. These include multi-sig wallet lockup of funds, public and audited smart contracts that hold treasury funds, a transparent process when key protocol changes are made, and a clear and fair vesting

## MIP Rollout

The first phase of MIP implementation will be informal due to technical and practical constraints. From a technical standpoint, a verifiable snapshot of Min token holder allocations must be taken at the point of proposal submission. This snapshot, indicating the voting rights accorded to each address, must be transferred off-chain to enable gasless voting that encourages broad participation. From a practical standpoint, there won’t be a broad distribution of Min tokens, i.e voting rights, in the very beginning. Our fair token launch means it will take some time for users to accumulate Min tokens based on protocol use. However, due to the high initial mint rate, we don’t anticipate this being a constraint for more than one or two months.

Snapshot voting ensures voters don’t have the opportunity to accumulate tokens/voting rights in response to a specific MIP and attempt to manipulate its outcome. A vote delegation system will likely be implemented a while after the first snapshot-based governance is live. This will encourage greater direct participation in the beginning and allow community members to identify high-quality delegates. Minswap is looking into possible tools for discovering delegates and mapping on-chain addresses to digital identities to maintain a delegate list.

## Informal MIP Governance

The initial informal governance system will consist of a forum for community members to submit MIPs and participate in voting. Proposal voting will be based on forum accounts with one account equal to one vote. Given the lack of Sybil resistance in this process, proposals that pass a predetermined vote threshold will not be binding. Rather, they will move into a proposal repository and be the first binding proposals voted on when Sybil resistant snapshot voting goes into effect. The voting order of informal MIPS from the repository will be determined by the total number of votes received.

The informal governance phase will allow community members to make suggestions for the team or foundation to implement. This will help the Minswap team get a better idea of the direction the community desires for the protocol. It also lowers the technical barriers some might encounter in submitting proposals during formal governance. Future MIPs, when formal governance vests, must be executable code, not suggestions for the team or foundation to implement.

## Formal MIP Governance

Formal governance will occur off-chain with our snapshot voting system and Sybil-like delegate list. In the beginning, only proposals posted to the snapshot voting system by the core team can be considered binding if passed with a quorum. Six months into formal governance this changes and any proposal is binding if passed with a quorum. At this point, proposals from the informal MIP repository that passed during the first six months, but were not implemented, will be up for a vote again.

Major structural changes and use of the dev fund wallet are voted on by the community, whereas smaller changes affecting operations, as well as Min emission changes to Minswap farming pairs, are decided on by the core team. Smaller operational changes can be voted on and implemented, though they will only be binding for 90 days before being subject to change without a vote.

## Formal MIP Governance Proposals

The MIP should provide a concise technical specification of the feature and a rationale for the feature.

The code for a proposal must be written before it comes to a vote. All proposed code should be audited by a professional auditor. This auditing process may be paid or reimbursed by the community treasury. Audits may be made after voting but before implementation. A MIP must go through two phases. A “Discourse” proposal must be elevated to a formal “Proposal” in order to be voted on as a binding MIP. This helps prevent too many proposals from clogging the system and ensures community members are aware when a binding MIP is up for vote, as fewer will make it to this step.

For a MIP to move from “Discourse” to “Proposal” it must gain at least X million MINC\(0.25 % total supply\)

For a MIP “Proposal” to pass and become binding it must gain a quorum of at least X million MINC            \(X = 3% of total supply\)

MINC is our voting metric, and is decided as follows: 

Each MIN in the MIN-ADA pool = 2 MINC 

Each MIN held via stakeMIN tokens = 1 MINC

Each MIN not deployed in protocol = .5 MINC

The duration of voting periods are:  Discourse Period - 14 days / "Proposal" Voting Period  - 7 days

