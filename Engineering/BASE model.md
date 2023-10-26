---
tags: engineering, database, transaction
author: Nguyen Xuan Anh
github_id: monotykamary
date: 2022-04-18
---

## What is the BASE model?

BASE is an acronym for describing a flexible way to manipulate data. With requirements for NoSQL databases, the BASE model came to be as a less pessimistic approach of the [[ACID model]] when handling data. The acronym stands for:

- **Basic Availability:** The database is available and should work most of the time.
- **Soft-state:** Data stores don't have to be completely write-consistent or require mutual consistency between replicas.
- **Eventual consistency**: The database is lazily consistent, meaning it ensures data consistency at a later point.

![base model diagram](_assets/base_model_diagram.png)

BASE properties are significantly looser than ACID, but the tradeoff allows for scalability. Although BASE has loose consistency, it doesn't mean data will be completely inconsistent. However, it does require assistance from the developer when ensuring what the data should focus on being consistent in (e.g: consistent in time of activity or order of processing).

The BASE model loosely refers to distributed data stores, which means these databases require different approaches when handling transactions and events asynchronously. This will also mean a tradeoff of availability for consistency in the presence of a network partition or power outage; this is more deeply covered in [[CAP theorem]].

#### Reference

- https://phoenixnap.com/kb/acid-vs-base
- https://neo4j.com/blog/acid-vs-base-consistency-models-explained/

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