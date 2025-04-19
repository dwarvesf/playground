---
tags: 
 - blockchain
 - network 
 - ethereum
authors: 
 - bienvh
github_id: vhbien000
title: 'Layer 2: Scaling Solutions for Ethereum'
date: 2022-12-06
description: Explore Layer 2 solutions for Ethereum scaling, including rollups and their benefits. Learn how Layer 2 extends Ethereum's capabilities, reduces gas fees, and maintains security while improving transaction throughput and efficiency.
---

## What?

- [Ethereum scaling solutions](#ethereum-scaling-solutions)
- Separate [blockchain](#blockchain)
  - Extends [Ethereum](#ethereum)
  - Inherits the security guarantees of [Ethereum](#ethereum)
- All user transactions on the Layer 2 can ultimately settle back to [Layer 1](#layer-1)
- [Ethereum](#ethereum) also functions as a data availability layer for Layer 2s
  - Layer 2 will post their transactions data onto [Ethereum](#ethereum)
  - Rely on [Ethereum](#ethereum) for data availability
    - Used to get the state of Layer 2
    - Dispute transaction of Layer 2

## Why?

Blockchain has 3 desirable properties

- Decentralized
- Secure
- Scalable

"can only achieve 2 out of 3" - [Blockchain trilemma](#blockchain-trilemma)

High demand -> Need to scale without sacrificing decentralization and security => Need Layer 2 to scale Blockchain that takes advantage of robust decentralized security of [Layer 1](#layer-1)

## How?

- Communicate with [Layer 1](#layer-1) by submitting bundles of transactions
- [Layer 1](#layer-1) handles security, data availability, and decentralization
- Layer 2 handles scaling by computing and sending finalized proofs to [Layer 1](#layer-1) -> Remove transaction loading.

### Rollup

- Preferred layer 2 scaling solution in Ethereum
- Reduce gas fees by up to 100x compared to [Layer 1](#layer-1)
- Rollup bundle ("roll up") hundreds of transactions into a [Layer 1](#layer-1) transaction => Fee will be dived/distributed to all users (owners of these hundreds of transactions) -> Cheaper
  - For example:
    - 1 [Layer 1](#layer-1) transaction is paid for 1eth as fees
    - 100 Layer 2 transactions rolled up in 1 [Layer 1](#layer-1) transaction are also paid for 1eth. So 1 Layer 2 transaction is just only needed 0.01 eth to execute.
- Rollup is executed outside [Layer 1](#layer-1) (in Layer 2), but finalized result (proof) is submitted to [Layer 1](#layer-1) => and can be secured by [Layer 1](#layer-1) security mechanisms.
- Have 2 approaches (different on posting transaction data to L1):
  - [Optimistic](#optimistic-rollups)
  - [ZK Rollups](#zk-rollups) aka Zero-knowledge Rollups

## Example

- Arbitrum One
- Optimism
- Boba Network

## References

- https://ethereum.org/en/layer-2
