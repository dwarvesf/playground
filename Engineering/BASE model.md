---
tags: engineering, database, transaction
author: Nguyen Xuan Anh
---

## What is the BASE model?

BASE is an acronym for describing a flexible way to manipulate data. With requirements for NoSQL databases, the BASE model came to be as a less pessimistic approach of the [[ACID model]] when handling data. The acronym stands for:

- **Basic Availability:** The database is available and should work most of the time.
- **Soft-state:** Data stores don't have to be completely write-consistent or require mutual consistency between replicas.
- **Eventual consistency**: The database is lazily consistent, meaning it ensures data consistency at a later point.

![base model diagram](https://phoenixnap.com/kb/wp-content/uploads/2021/04/base-acronym.png)

BASE properties are significantly looser than ACID, but the tradeoff allows for scalability. Although BASE has loose consistency, it doesn't mean data will be completely inconsistent. However, it does require assistance from the developer when ensuring what the data should focus on being consistent in (e.g: consistent in time of activity or order of processing).

The BASE model loosely refers to distributed data stores, which means these databases require different approaches when handling transactions and events asynchronously. This will also mean a tradeoff of availability for consistency in the presence of a network partition or power outage; this is more deeply covered in [[CAP theorem]].

#### Reference

- https://phoenixnap.com/kb/acid-vs-base
- https://neo4j.com/blog/acid-vs-base-consistency-models-explained/
