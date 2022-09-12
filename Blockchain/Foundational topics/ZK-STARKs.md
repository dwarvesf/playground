---
tags: blockchain, evm, zk, zk-starks
author: Pham Ngoc Thanh
---

## What is ZK-STARKs?

Like ZK-SNARKs, ZK-STARKs demonstrate the validity of off-chain computation without revealing the input. However, ZK-STARK is considered an improvement on ZK-SNARK because of their scalability and transparency.
- Scalable: ZK-STARK is faster than ZK-SNARK in generating and verifying evidence when witness size is larger. With STARK proofs, verification and proverb times only increase slightly as the witness grows (the times of the proverb and SNARK verifier increase linearly with witness size).
- Transparency: ZK-STARK relies on public verifiable randomness to generate public parameters for proof and verification instead of establishing trust. Therefore, they are more transparent than ZK-SNARK.
- ZK-STARKs also offer more scalability because the time required to prove and verify valid proofs increases with the complexity of the underlying computation. With ZK-SNARK, the proof and verification times expand linearly with respect to the size of the underlying computation. This means that ZK-STARK requires less time than ZK-SNARK to prove and verify as far as large data sets are concerned, making them useful for high volume applications.
- ZK-STARK is also secure against quantum computers, while Elliptic Curve Cryptography (ECC) used in ZK-SNARK is considered by many to be vulnerable to quantum computing attacks. The downside of ZK-STARKs is that they produce a larger proof size, which is more expensive to verify on Ethereum. Also, they don't support recursion, which is key to extending off-chain computation with zero-knowledge proofs.
