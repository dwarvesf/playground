---
tags: engineering, domain-driven-design, DDD
author: M.Vu Cuong(Jim)
---
### Domain model is
Your organized and structured **knowledge of the business problem**. Represents as a diagram, code examples, or written documentation, and **must** be accessible and understandable by **everyone** involved with the project.
[Overview of Domain Driven Design](https://github.com/dwarvesf/brain/blob/master/Engineering/Overview%20of%20Domain%20Driven%20Design.md)
### Domain model consists of
The vocabulary and key concepts of the domain, and the relationships among all of the entities.
These are mainly divided into: **Domain events**, **Commands**, **Aggregates**, and **Bounded context**.
### Domain events
*A statement in past tense* describes the **things that happened** in a business system that alternates the state of the entity.
Exp: Order submitted, Shopping cart updated
### Commands
*A verb in present tense* describes the action that triggers the corresponding **domain event**. It is either user or system actions.
- Exp: `Add product`(Command) -> `Shopping cart updated`(Domain event)
### Aggregrates
Represented by a *minimal cluster* of associated objects(domain events, commands, and actors) that we treat as a unit for data change. Each has a boundary and only exposes its root(**Aggregate Root**) which allows other objects to reference it.
- Exp: A team wants to update its member role according to each project: </n>
`Project, Update member role` (Aggregate Root) -> `Project's member role updated`</n>
### Bounded context
A high-level structure consists of categorizations of functionality, represents a circle or square, that groups related entities together. It can bound parts of an aggregate or multiple aggregates.
- Exp: In an aggregate for the shopping process,  we draw the bounded contexts for **Shopping cart**, and **Offers**: </n>
Shopping cart(`User` -> `Add product to cart` -> `Cart updated`) -> Offers(`Promotiational Offers Identified` -> `Offers added`)
### References
- https://herbertograca.com/category/development/book-notes/domain-driven-design-by-eric-evans/
- Domain-driven design by Eric Evans
- https://creately.com/blog/diagrams/event-storming/
- https://www.jamesmichaelhickey.com/domain-driven-design-aggregates/
- https://serialized.io/java/working-with-aggregates/