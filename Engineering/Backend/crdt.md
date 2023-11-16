---
tag:
    - engineering
    - engineering/backend
    - distributed-system
author: Nguyen Tan Phat
github_id: fuatto
date: 2023-11-5
icy: 10
---

## What is CRDT?

- Conflict-free Replicated Data Types (CRDTs) (aka convergent replicated data type or commutative replicated data type)
are data structures that can be replicated across multiple computers in a network, where the replicas can be updated independently and concurrently without coordination between them, and enable operations to always converge to a final state consistent among all replicas.

## Why CRDT?

**Addressing Data Modification Dilemma**

- Two approaches to handling concurrent modifications:
    - *Strongly Consistent Replication*: Replicas coordinate for modifications but sacrifice performance. Limited by the [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem).
    - *Optimistic Replication*: Users can independently modify data for enhanced performance. May lead to conflicts, resolved during replica communication.

**Role of CRDTs**

- CRDTs perform replication as commutative operations:
    - Used in optimistic replication systems.
    - Automatic conflict resolution ensures seamless merging of data modifications.
    - Eliminates the need for special conflict resolution code or user intervention

## How to use CRDT?

**Applications of CRDTs**

- *Mobile Apps*:
Ensures seamless synchronization of data across user devices.
- *Distributed Databases*:
Maintains data integrity across replicas, even in different locations.
- *Collaboration Software*:
Manages concurrent changes by multiple users to the same file or data.
- *Large-scale Data Storage Systems*:
Facilitates global scalability by replicating data.

**Decentralized Operation**

- CRDTs support decentralized operation.
- Unlike systems like Google Docs, Trello, and Figma, CRDTs don't rely on a single server.
- Thrives in peer-to-peer networks and other decentralized settings.

## Conclusion

In short, Conflict-free Replicated Data Types (CRDTs) play a pivotal role in managing conflict resolution. It guarantees the seamless merging of data into a coherent state, irrespective of the modifications made on distinct replicas. Importantly, CRDTs automate this merging process, eliminating the necessity for specialized conflict resolution code or user intervention.

Furthermore, a noteworthy attribute of CRDTs lies in their support for decentralized operation. Unlike systems relying on algorithms utilized by platforms such as Google Docs, Trello, and Figma, CRDTs don't presuppose the reliance on a single server. This distinctive quality allows CRDTs to seamlessly integrate into peer-to-peer networks and various decentralized settings, setting them apart in the landscape of distributed data management.

## References

- https://crdt.tech/
- https://redis.com/blog/diving-into-crdts/
- https://jakelazaroff.com/words/an-interactive-intro-to-crdts/#user-content-fn-cvrdt