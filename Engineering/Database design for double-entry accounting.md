---
tags: engineering, finance, accounting, technique, design, database
author: Nguyen Xuan Anh
date: 2022-09-07
---

## Introduction

There are a few ways to design double-entry accounting in databases, where the design and performance nuances are dependent on business requirements and their tolerances. For our case, we essentially need to keep track of these 2 things:
- Journal entries – a journal containing single or double entry representing the transaction for two parties in both their credit and debit perspectives.
- Accounts (Books) – a ledger or a list of accounts and their balance totals derived from the journal entries.

## Modeling

Canonically, in [[Double-entry accounting|double-entry accounting]], for each transaction, there will be 2 journal entries: 1 debit entry and 1 credit entry. However, the tradeoff in implementing this in a database means there will be always **2 write operations** for every transaction to the table. In a relational database, this also means these entries will also be **indexed**, which compounds the IO issue with regard to disk space.

#WIP

## Example case studies

### Books, an immutable double-entry accounting database service at Square

#WIP

![[square-books-double-entry.png]]

### What about blockchain?

Although blockchain uses what is technically a journal to keep track of transactions, how it handles writes across a distributed system means it essentially uses [[Triple-entry accounting|triple-entry accounting]].

With the advent of financial cryptography, the blockchain essentially automates the role of an **auditor** between multple owners of a journal/ledger.

|                                          |                                          |
| ----------------------------------------- | ----------------------------------------- |
| ![[Pasted image 20220907162942.png\|250x250]] | ![[Pasted image 20220907163733.png\|330x250]] |

## Reference
- https://developer.squareup.com/blog/books-an-immutable-double-entry-accounting-database-service/
- https://rcoh.me/posts/postgres-indexes-under-the-hood/
- https://en.wikipedia.org/wiki/B-tree
- https://blog.gilded.finance/the-accounting-innovation-nobody-is-talking-about-triple-entry/
- https://onlinelibrary.wiley.com/doi/epdf/10.1111/acfi.12556
