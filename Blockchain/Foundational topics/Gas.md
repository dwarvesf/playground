---
tags: blockchain, foundational-topics, gas, smart-contract, evm
author: Pham Ngoc Thanh
---

### 1. What is Gas? Why is it necessary?

The purpose of gas is to act as a fee to calculate the operations of a smart contract performed by each Ethereum node. A computational fee is required to prevent an attacker from shutting down the network by deploying a large number of complex contracts that require long computation times. This type of DDoDS attack is not recommended as it would be very expensive to run.
The gas fee is to pay the validator who is responsible for making sure the information in the transaction is valid, there are no errors/exceptions from the EVM, and the sender complies with the request for the required amount for payment. for the calculation. When the sender sets a high gas limit, it indicates that the complex operation should incentivize validators to make transactions for high rewards. When network activity is high, validators can simply choose from a pool of pending transactions with a higher gas limit. Therefore, gasoline fees are affected by supply and demand. The good news is that any gasoline not consumed is refunded to the sender. If the prepaid gas limit is reached, validators are still compensated for their work but the transaction is not completed. In this way, the EVM is almost Complete because the computations it can complete are limited to the amount the sender is willing to pay to be completed.

#### 2. What is gas limit

The gas limit is the maximum amount of gas that the payer is willing to pay for the transaction to be executed and validated. To calculate gas fees, you can multiply the total cost of gas (the base cost of the operations) by the gas price (the cost of completing those operations). Just like when filling your car with actual gas, there will be the cost of the gas itself and the amount of gas needed to get you to your destination.

#### How to calculate Gas for 1 transaction

Gas fee = Total used gas x Gas price

### 3. Hand on gas optimization for smart contract

Each opcode has a gas cost assigned to it with more complex opcodes having a higher cost. For example, simple add costs 3 gas and every transaction starts with a cost of 21,000 gas. Most of the complaints are not about the amount of gas but about the amount of gas to complete a successful transaction.

#### 3.1 Coding Techniques

- Use reasonable variables, variable order, fixed byte size, fixed length...
- Optimize source code when deploying using Solidity optimization run
- Use proxy to redeploy the same contract.
- Use assembly code.
- Use minimalist libraries. You can use only the necessary code.

#### 3.2 Logical data storage.

- Only save the necessary data.
- Avoid data duplication.
- Only write data at the end of processing, use temporary variables when possible.
- Avoid reading too much global state. logical data query.
- Using uint8 will cost more storage than uint256.
- Use Byte32 type instead of string if possible.

#### 3.3 Use proper data types

- Use external declaration for functions and calldata for data.
- Use memory variables for internal functions when possible, avoid using storage because of high storage costs.
- It is recommended to use variable types with as small as possible bytecode size
- For type struct, alway order small bytecode variable type on top with block of 256 bytes

#### 3.4 Using event

- Maximize processing logic off-chain, use events to minimize on-chain storage.
- Index the necessary topics in the event to optimize the query.
- Combine small events into one big event if possible.

#### 3.5 Remove unnecessary components.

- Remove unused codes.
- Remove unused libraries.
- Avoid calling back and forth between smart contracts

#### 3.6 Clear data after use.

- Delete data when the application is no longer in use.
- Optimized for querying with smart contracts with optimal data.


#### Reference

- https://ethereum.org/vi/developers/docs/smart-contracts/
- https://ethereum.org/en/developers/docs/gas/
- https://github.com/iskdrews/awesome-solidity-gas-optimization
- https://github.com/djrtwo/evm-opcode-gas-costs/blob/master/opcode-gas-costs_EIP-150_revision-1e18248_2017-04-12.csv
- https://medium.com/coinmonks/8-ways-of-reducing-the-gas-consumption-of-your-smart-contracts-9a506b339c0a
- https://ethereum.stackexchange.com/questions/11556/use-string-type-or-bytes32
- https://github.com/djrtwo/evm-opcode-gas-costs
- https://coinmarketcap.com/alexandria/article/3-minute-tips-what-are-gas-wars
- https://markets.businessinsider.com/news/currencies/crypto-exchange-bitfinex-ethereum-tether-transaction-fees-error-deversifi-2021-9
