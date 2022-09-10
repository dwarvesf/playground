---
tags: blockchain, evm, zk-rollups, zk
author: Pham Ngoc Thanh
---

#### What is ZK-Rollups

Zero-knowledge Rollups (ZK-rollups) is a layer 2 scaling solution that increases throughput on the Ethereum Mainnet by moving computation and storing state off-chain. ZK-rollups can process thousands of transactions in a batch and then only post a minimal amount of summary data to the Mainnet. This summary data identifies changes that need to be made to the state of Ethereum and some cryptographic evidence that those changes are correct.

#### Features of ZK-rollups:

- Process multiple offchain transactions at the same time
- Massive processing throughput based on off-chain computing
- Save gas in transactions, fast transaction processing time
- Periodically save the processing data to the ZK-rollup chain
- The data is accessible on the Ethereum chain as calldata
- Anyone can censor data
- L2 transaction is completed only when L1 accepts valid proof.
- Transactions cannot be reversed once completed on L1.
- Increased risk of malicious operators censoring users by denying more transactions in batches.
- Users can actively submit transactions to the ZL-rollup contract on ethereum.

#### How [[ZK]] works?

Zero-knowledge rollups (ZK-rollups) bundle (or 'roll up') into batches that are executed off-chain. Off-chain computation reduces the amount of data that has to be posted to the blockchain. ZK-rollup operators send a summary of the changes needed to represent all transactions in a batch instead of sending each transaction individually. They also present valid evidence to prove the correctness of their changes. Valid proof that demonstrates cryptographic certainty that the proposed changes to the state of Ethereum are indeed the end result of executing all transactions in the batch.

The state of the ZK-rollup is maintained by a smart contract deployed on the Ethereum mainnet. To update this status, ZK scrolling buttons must submit a valid proof for verification. This means that ZK-rollups only need to provide valid proofs to complete transactions on Ethereum instead of posting all transaction data on-chain as optimistic aggregates would.

- On-chain contracts: the ZK-rollup protocol is controlled by smart contracts running on Ethereum such as: the main contract stores roll-up blocks, tracks deposits, and keeps track of state updates. Another online contract (verifier contract) verifies zero-knowledge proofs submitted by block producers.
- Off-chain virtual machine (VM): A separate virtual machine that processes off-chain transactions to store state, valid proofs of off-chain transactions are guaranteed by Ethereum mainnet.
- Transactions: Use POS validator to aggregate and create rollup batch, if operator performs malicious behavior will be punished.
- State commitments: The summary changes to a new state after executing a new set of transactions. The moderator that initiated the state transition is required to compute the new state root and submit the contract on-chain. If the valid proof associated with the batch is validated by the verifier contract, the new Merkle root becomes the ZK-rollup canonical state root.
- Validity proofs: The new state of the ZK-rollup root submitted to the L1 contract is an update of the rollup state.


#### How do validity proofs work in ZK-rollups?

In order to prove that the off-chain processing is correct, the operators also perform the same transaction checking as on ethereum such as: sender, receiver is part of the state tree, sender has enough funds to perform the transaction. translation, transaction is true and matches sender address, sender nonce is true... And when Zk-Rollup has enough transactions, it will aggregate them in 1 transaction, it includes: markle tree of all transactions in batch, mark proofs for transactions to proof in batch. Markle proofs for each sender-receiver pair to prove those accounts are part of the rollup state tree. An intermediate set of state roots, derived from updating the state root after applying a state update to each transaction (i.e. decreasing the sender account and increasing the receiver account).

##### Proof verification

After the proving circuit verifies the correctness of state updates, the L2 operator submits the computed validity proof to the verifier contract on L1. The contract's verification circuit verifies the proof's validity and also checks public inputs that form part of the proof:

- Pre-state root: The ZK-rollup's old state root (i.e., before the batched transactions were executed), reflecting the L2 chain's last known valid state.
- Post-state root: The ZK-rollup's new state root (i.e., after the execution of batched transactions), reflecting the L2 chain's newest state. The post-state root is the final root derived after applying state updates in the proving circuit.
- Batch root: The Merkle root of the batch, derived by merklizing transactions in the batch and hashing the tree's root.
- Transaction inputs: Data associated with the transactions executed as part of the submitted batch.

##### Entries and exits

- If you want to transfer assets from L1 to L2, you will deposit tokens into the ZK-rollup contract, the Operator will transfer your Eth to the Contract bridge when your tokens have been transferred to the rollup
- In contrast, transferring assets from L2 to L1, the user will deposit the token into an account for burning, if the operator adds that transaction in the next batch, the user can submit a withdrawal request to the L1 contract with the following parameters:
    - Merkle proof proving the inclusion of the user's transaction to the burn account in a transaction batch
    - Transaction data
    - Batch root
    - L1 address to receive funds

The rollup contract hashes the transaction data, checks if the batch root exists, and uses the Merkle proof to check if the transaction hash is part of the batch root. Afterward, the contract executes the exit transaction and sends funds to the user's chosen address on L1.

#### How does the gas charge work on ZK-ROLLUP

The amount users pay for transactions on ZK-rollups depends on gas fees, just like on the Ethereum Mainnet. However, gas charges work differently on L2 and are affected by the following costs:
1. State write: There is a fixed cost for writing to Ethereum’s state (i.e., submitting a transaction on the Ethereum blockchain). ZK-rollups reduce this cost by batching transactions and spreading fixed costs across multiple users.
2. Data publication: ZK-rollups publish state data for every transaction to Ethereum as calldata. calldata costs are currently maintained by EIP-1559, which stipulates a cost of 16 gas for non-zero bytes and 4 gas for zero of calldata, respectively. The cost paid on each transaction is derived by how much calldata needs to be posted on-chain for it.
3. L2 operator fees: This is the amount paid to the rollup operator as compensation for computational costs in processing transactions, much like miner fees on Ethereum.
4. Proof generation and verification: ZK-rollup operators must produce validity proofs for transaction batches, which is resource-intensive. Verifying zero-knowledge proofs on Mainnet also costs gas (~500,000 gas).

#### Future of ZK rollup and layer 2
- Data is compressed which maximizes the number of transactions processed per block.
- ZK-Rollup can compress transaction data better than Optimism rollups
- The advantage of ZK proof is proof that verifies other proofs. It's called proof-of-recursion, which dramatically increases throughput on ZK-rollups.
- Recursive proofs helps to finalize several blocks with one validity proof, so it will be very effective.

#### Popular ZK Algorithms

- [[ZK-SNARKs]]
- [[ZK-STARKs]]
 
#### Compare with Optimism Rollups:

- Optimism has OVM: the virtual machine can run most of the Smart contract code like EVM, but there is still a difference, so it cannot use the bytecode of EVM.
- Another challenge for implementations lies in the fact that proofs of fraud for large blocks may require more gas than allowed by the L1 block gas limit. These proofs of fraud must then be broken down into multiple ETH transactions.
- Optimistic Rollup can support any privacy solution available on L2 Ethereum (mixers, etc)

#### SNARKs vs STARKs

Below, we have a couple tables depicting some of the high-level differences between the two technologies.

![](https://i.imgur.com/zxUNEzT.png)
Source: Matter Labs
![](https://i.imgur.com/fdBKwXp.png)
Source: Beanstalk

SNARKs are estimated to require only 24% of that  gas that STARKs would require, meaning that transacting with SNARKs would be far cheaper for the end-user. Finally, the proof size for SNARKs is much smaller than STARKs, meaning it would take less on-chain storage. STARKs have far larger proof sizes than SNARKs, which means that verifying STARKs takes more time than SNARKs and also leads to STARKs requiring more gas.

#### Project working with ZK-Rollups:

- Polygon Zero
- Polygon Miden
- Poligon Hermez
- StarkEx
- ZKSync
- Zkyber
- Starknet
- Loopring

### Referral

- [ZK engine]()
- [An Incomplete Guide to Rollups](https://vitalik.ca/general/2021/01/05/rollup.html)
- [zkEVM Scroll](https://scroll.io/blog/zkEVM)
- [Optimistic vs. ZK Rollup: Deep Dive](https://blog.matter-labs.io/optimistic-vs-zk-rollup-deep-dive-ea141e71e075)
- [Polygon ZK: Deep Dive Into Polygon Hermez 2.0](https://blog.polygon.technology/zkverse-deep-dive-into-polygon-hermez-2-0/)
- [ZK-EVM resources](https://github.com/LuozhuZhang/awesome-zkevm)
- [Rollup under the hood](https://vitalik.ca/general/2021/01/05/rollup.html)