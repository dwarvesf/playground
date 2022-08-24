---
tags: engineering, finance, accounting, technique, design
author: Nguyen Xuan Anh
date: 2022-08-24
---

## Introduction

Double-entry accounting states that every financial transaction has equal and opposite effects in at least two different accounts. There are 5 main accounting types associated with this: *assets*, *liabilities*, and *equity*, *revenues*, and *expenses*.

Accountants have an **accounting equation** and it is used to check whether the bookkeeper has made a mistake if it is ever out of balance. The equation is:

$$
\text{Assets} = \text{Liabilities} + \text{Equity}
$$

We can derive a person's net worth to be the total equity they have:

$$
\text{Equity (Net Worth)} = \text{Assets} - \text{Liabilities}
$$

### How is it different from single-entry?

Single-entry accounting involves writing down all entity transactions (revenues, expenses, payroll, etc.) in a single ledger. The database equivalent to this is updating a single table with the accounts of every user. This makes it **difficult** to track assets and liabilities, and it is prone to mistakes.

### Reasons and proponents for accounting in double-entry

In a double-entry accounting system, a debit in one account offsets a credit in another, the sum of **all debits** must equal the sum of **all credits**. The system standardizes the accounting process and improves the accuracy of prepared financial statements, and enables us to detect errors in cases of fraud or laundering.

Double-entry systems, regardless of whether we keep track of journal entries, allow us to create reports on income statements, balance sheets, statements of cash flows, and statements of retained earnings.

## Terminology

| Basis for comparison | Debit                                                 | Credit                                                  |
| -------------------- | ----------------------------------------------------- | ------------------------------------------------------- |
| Meaning              | Refers to a record of money flowing *into* an account | Refers to a record of money flowing *out of* an account |

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
- https://bench.co/blog/accounting/double-entry-accounting/
