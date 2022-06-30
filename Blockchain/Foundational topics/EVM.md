---
tags: blockchain, foundational-topics, evm, blocks, smart-contract
author: Pham Ngoc Thanh
---

## Ethereum virtual machine
The physical initialization of the EVM but it can be thought of as existing as a single machine maintained by thousands of connected computers running an Ethereum client (See also [[Distributed systems]]. the Ethereum protocol exists solely for the purpose of keeping the continuity, uninterrupted operation and immutability of this particular state machine; It is the environment for all Ethereum [[Accounts]] and [[Blockchain/Foundational topics/Smart Contract]] smart contracts that exist. At any given block in the chain, there is one and only one 'standard' state, and the EVM is what defines the rules for computing a new valid state from block to block. Simply put, it is a piece of software that handles deployment and execution on a smart contract. EVM is deployed on all network clients.
![](https://i.imgur.com/j7n3TLw.png)

Some basic familiarity with common computer science terms such as bytes, memory, and stack is necessary to understand EVM. It also helps if you are comfortable with cryptography/blockchain concepts like hash functions, proof of work, and Merkle trees. The EVM is a Turing-complete state machine, because all execution steps are limited to a finite number of computational steps. This is different from Bitcoin when on bitcoin the Stack Machine is just an incomplete Turing machine.

### 1. FROM LEDGER TO STATUS MACHINE
The analogy of 'distributed ledger' is often used to describe blockchains such as Bitcoin, which enables a decentralized currency using the underlying tools of cryptography. Cryptocurrencies behave like a 'normal' currency due to the rules that govern what one can and cannot do to modify the ledger. For example, a Bitcoin address cannot spend more Bitcoins than previously received Bitcoins. These rules underlie all transactions on Bitcoin and many other blockchains.

While Ethereum has its own cryptocurrency (Ether) that follows almost exactly the same visual rules, it also allows for a much more powerful function: smart contracts. For this more complex feature, a more complex analogy is required. Instead of a distributed ledger, Ethereum is a distributed state machine. The state of Ethereum is a big data structure that not only holds all accounts and balances, but also a state machine, which can change from block to block according to a predefined set of rules. and can execute arbitrary machine code. The specific rules of changing state from one block to another are determined by the EVM.

Ethereum EVM simulation diagram illustrated
![](https://i.imgur.com/dF8KYvZ.png)

#### ETHEREUM STATUS MACHINE TRANSFORM FUNCTION
EVM acts like a mathematical function: Given an input, it produces a definite output. Therefore, it would be helpful to describe Ethereum more formally as having a state transition function:
```Y(S, T)= S'```

Given the old valid state (S) and a new set of valid transactions (T), the Ethereum state transition function Y (S, T) produces a new valid output state S'
#### State
In the context of Ethereum, state is a giant data structure called the modified Merkle Patricia Trie that keeps all accounts linked using hash functions and can be reduced to a single hash. The unique root is stored on the blockchain.
#### Transactions
Transactions are cryptographically signed instructions from accounts. There are two types of transactions: transactions that lead to message calls and transactions that lead to contract creation.
Contract creation results in the creation of a new contract account containing the compiled smart contract bytecode. Whenever another account makes a notification call to that contract, it executes its bytecode.

#### EVM INSTRUCTION
The EVM executes as a stacker with a depth of 1024 entries. Each entry is a 256-bit word, chosen for ease of use with a 256-bit cipher (such as a Keccak-256 hash or a secp256k1 signature). During execution, the EVM maintains a temporary memory (like a word-addressed byte array) that does not persist between transactions. However, the contract does contain the Merkle Patricia trio (as a word-addressable word array), associated with the account in question and part of the global state.

The compiled smart contract bytecode executes as some EVM opcode, performing standard stack operations like XOR, AND, ADD, SUB, etc. v. EVM also implements several blockchain-specific stack operations, such as ADDRESS, BALANCE, BLOCKHASH, etc. v. EVM is designed in stack-based architecture, all is stored in stack, word size is 256-bit. The components that store information on the EVM are divided into 3 parts:
- A fixed ROM code, cannot be changed. Loaded with the byte code of the smart contract when processing the contract.
- A short-term memory. When you want to save on Solidity, use the keyword memory
- A long-term memory. When you want to save on Solidity, use the keyword storage

Diagrams adapted from Ethereum EVM illustrated
![](https://i.imgur.com/kAORYa2.png)


### 2. What is EVM Blockchain?
EVM blockchains are Ethereum virtual machine compatible blockchains, which means that Ethereum smart contracts can be run on those blockchains. In other words, with just a little tweaking, Dapps (decentralized applications) on Ethereum can be run on the EVM blockchain. Some examples of EVM blockchain are Fantom, Celo, Avax C-Chain, BSC,...
At the present time there are many EVM blockchains. The most mentioned are layer 2 solutions for the Ethereum network, simply because they are built on the foundation of Ethereum, so it is easy to inherit the advantages and overcome the disadvantages. Unlike layer 2 projects on Ethereum, layer 1 blockchains build their own blockchain platform and design, so there will definitely be differences. Examples of other blockchain EVMs such as Binance Smart Chain, Fantom, Avalanche, Harmony, Near Protocol,...
Non-EVM Blockchain

#### What is Non-EVM Blockchain?
As the name implies, Non-EVM Blockchain has a completely opposite definition compared to EVM- Blockchain. Non-EVM blockchains are Blockchains that are not compatible with EVM. These can be mentioned non-EVM blockchains such as Cardano, Solana, Algorand, Terra, Avalanche X-Chain, etc. The main feature of non-EVM blockchains is that they use a different smart contracts programming language than Solidity on Ethereum:
- Cardano uses Haskell/Plutus.
- Solana uses Rust/C/C++.
- Terra uses Rust.
- Algorand uses TEAL (Transaction Execution Approval Language).

### 3. Scripts
EVM's instruction set is divided into the following types
#### 1. Math processing
- ADD: Plus
- MUL: Multiply
- SUB: Minus
- DIV: Divide integers
- SDIV: Divide positive integers
- MOD: Module
- SMOD: Calculate the modulo of positive integers
- ADDMOD: Addition in the radix system
- MULMOD: Multiply in the radix system
- EXP: Exponential
- SIGNEXTEND: Increase the bit representation space of a positive integer
- SHA3: Calculate the hash value keccak256
#### 2. Command to interact with the stack
- POP: Remove the element on the top of the stack
- MLOAD: Load 1 word (16 bits) from memory
- MSTORE: Save 1 word in memory
- MSTORE8: Store 1 byte in memory
- SLOAD: Load 1 word from storage
- SSTORE: Save 1 word from storage
- MSIZE: Check the amount of free memory memory
- PUSHx: Change the value of x bytes on the stack (x from 1-32)
- DUPx: Duplicate the xth stack (x from 1 to 16)
- SWAPx: Change the position of the 1st stack and the stack (x+1) (x from 1-16)
#### 3. Interaction with registers
- STOP: Stop order
- JUMP: Set the value of the PC register to any value
- JUMPI: Condition change of value on register PC
- PC: Get the value of the PC . register
- JUMPDEST: Mark
#### 4. System commands
- LOGx: Add log with x parameters, (x from 0 to 4)
- CREATE: Create a new account
- CALL: Call to another account
- CALLCODE: Call to the account that is executing the transaction
- RETURN: Pause execution and return output data
- DELEGATECALL: Delegating the memory manipulation of the contract to another address
- STATICCALL: The call does not change the state
- REVERT: Revert transaction
- INVALID: Invalid order, stop execution
- SELFDESTRUCT: Cancel the contract and transfer the entire balance to another account
#### 5. Logic
- LT: Less than comparison (less than)
- GT: Greater than comparison (greater than)
- SLT: Compare less than positive number
- SGT: Compare greater than positive number
- EQ: Compare with
- ISZERO: NOT . operator
- AND: AND operator
- OR: OR . operator
- XOR: XOR . operator
- NOT: NOT operator
- BYTE: Get 1 byte from 256 bytes
#### 6. Environment
- [[Gas]]: Query the remaining amount of Gas during transaction execution
- ADDRESS: Get the value of the address that is executing the transaction
- BALANCE: Get account balance
- ORIGIN: Returns the value of the user's address that initiated the transaction
- CALLER: Returns the address calling this transaction (including the contract address)
- CALLVALUE: Returns the amount of eth used in the transaction
- CALLDATALOAD: Returns the input data of the transaction
- CALLDATASIZE: Returns the size of input data
- CALLDATACOPY: Copy the input data to memory
- CODESIZE: Returns the size of code in the current environment (EOA will have a size of code of 0)
- CODECOPY: Copy the code into memory
- GASPRICE: Returns the price of Gas
- EXTCODESIZE: Returns the size of the code of any account
- EXTCODECOPY: Copy the code into memory
- RETURNDATASIZE: Returns output data
- RETURNDATACOPY: Copy output data to memory
#### 7.Command to interact with block
- BLOCKHASH: Get the hash value of 1 of the last 256 blocks
- COINBASE //Get the block's beneficiary address for the block reward
- TIMESTAMP: Get the timestamp value of the block
- NUMBER: Get the value of block number
- DIFFICULTY: Get the difficulty value
- GASLIMIT: Get the value of gas limit

#### Reference
- https://ethereum.org/vi/developers/docs/evm/
- https://coinmarketcap.com/alexandria/glossary/ethereum-virtual-machine-evm
- https://www.alchemy.com/overviews/what-is-the-ethereum-virtual-machine-evm