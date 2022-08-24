---
tags: engineering, finance, accounting, technique, design
author: Nguyen Xuan Anh
date: 2022-08-24
---

## Introduction

Double-entry accounting states that every financial transaction has equal and opposite effects in at least two different accounts. There are 5 main accounting types associated with this: *assets*, *liabilities*, *equity*, *revenues*, and *expenses*.

## Terminology

In accounting, every financial transaction of an entity is kept inside a ***journal***. The entries inside the journal are used to create a general ***ledger***. The differences between them are listed in the table below:

| Basis for comparison               | Journal                                                        | Ledger                                                                           |
| ---------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Meaning                            | The book which records all financial transactions of an entity | The book that contains financial information needed to make                      |
| Known as                           | Book of original entry                                         | Book of secondary entry                                                          |
| Purpose                            | Used in preparation of a ledger                                | Used for labelling balances for final accounts                                   |
| Transactions Recorded              | All entries are made in chronological order                    | Entries are organized by account                                                 |
| Debit and credit                   | Can be separated by columns or by entries                      | The left side of a ledger is often the debit side while the right side is credit |
| Narration (comment or description) | Required                                                       | Not required                                                                     |
| Balancing                          | Balancing is not done                                          | All accounts are balanced based on the 5 main accounting types                                                                               |

## Using `hledger` to help us understand labelling

[`hledger`](https://hledger.org/) is a multi-commodity double-entry accounting software that is accessible through the command-line/terminal. It is mostly inspired by [ledger-cli](https://www.ledger-cli.org/), but rewritten in Haskell with build support for M1 Mac machines. `hledger` will help us orient how we compose and label transactions to understand the perspective of our journal entries.

### Assets

### Liabilities

### Equity

### Revenues

### Expenses

## Database Design

For database design, refer to [[Database design for double-entry accounting | database design for double-entry accounting]].

## Reference
- https://www.freshbooks.com/hub/accounting/an-accounting-journal
