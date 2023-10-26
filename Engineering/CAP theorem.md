---
tags: engineering, database, transaction, distributed
author: Nguyen Xuan Anh
github_id: monotykamary
date: 2022-04-18
---

## What is CAP theorem

CAP theorem, or also named Brewer's theorem (from scientist Eric Brewer), states that any distributed data store can provide only two of three guarantees:

- **Consistency:** Any read operations are up-to-date with the latest write operation, meaning that all clients see the same data at a given point of time.
- **Availability:** In a distributed data store, any and all working nodes in the system should return a valid response for any request, without exception.
- **Partition tolerance**: This refers to tolerance for an event that causes a network or power disturbance between 2 or more nodes. Tolerance here means that the cluster should continue to work despite drops in communication between nodes.

![cap theorem diagram](_assets/cap_theorem_diagram.png)

## CAP theorem database types

- **CP database:** A CP database sacrifices availability for consistency and partition tolerance. In a network partition, non-consistent nodes are shut down until the partition is resolved.
- **AP database:** An AP database delivers availability and partition tolerance at the cost of consistency. In a network partition, read consistencies occur between nodes, such that clients accessing one node may see different data than other clients. This inconsistency occurs until the partition is resolved, in which case the system will try to re-sync all nodes to repair all inconsistencies.
- **CA database:** A CA database achieves consistency and availability across all nodes. In a network partition, request for data will not return a valid response, as any partition will mean a loss of consistency. As such, such a database is not fault-tolerant.

## In reality

Eric Brewer makes it a point that you can only have 2 out of 3 guarantees in CAP theorem, which is not completely true. You can ensure at least a subset of guarantees between all three parts of the CAP theorem. There will always be nuanced tradeoffs in such a rounded approach to a distributed data store.

#### Reference

- https://en.wikipedia.org/wiki/CAP_theorem
- https://www.ibm.com/cloud/learn/cap-theorem

---
<!-- CTA -->
### Contributing

At Dwarves, we encourage our people to read, write, share what we learn with others, and [contributing to the Brainery](./CONTRIBUTING.md) is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?

- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)