---
tags: engineering, domain-driven-design, DDD
author: M.Vu Cuong(Jim)
---

### Recap on Domain Driven Design

A software design approach to create a rich and meaningful **Domain model** which enforces the conversation around the domain. As result, removes _the communication lag_ between **Developers** and **Domain/Business experts**.

[Here is the full overview](obsidian://open?vault=brain&file=Engineering%2FOverview%20of%20Domain%20Driven%20Design)

### Domain model is
Your organized and structured **knowledge of the business problem**. Represents as a diagram, code examples, or written documentation, and **must** be accessible and understandable by **everyone** involved with the project.
### Domain model consists of
The vocabulary and key concepts of the domain, and the relationships among all of the entities.
These are mainly divided into: **Domain events**, **Commands**, **Aggregates**, and **Bounded context**.
### Domain events
They are factual statements about the **things that happened** in a business system. It is important to phrase these statements in the past tense so one can frame this as a ‘what happened’ statement.
Exp: Order submitted, Shopping cart updated
### Commands
Is the identifier to why the **domain events** occurred. Commands express our intent for something to happen in the future as used in present tense. Commands may be documented as both user and system actions.
Exp: **Add product(Command)** -> Shopping cart updated(Domain event)
### Aggregrates
It is represented by a cluster of events with corresponding commands and the responsible actor.
Exp: Checkout process
User(Actor) ->  Checkout -> Checkout completed -> Shipping address validated -> Payment completed -> Inventory updated
### Bounded context
This is a high-level structure that consists of categorizations of functionality that group related entities together.
Exp: In an aggregate for the shopping process,  we draw the bounded contexts for **Shopping cart**, and **Offers**.
**Shopping cart**(User -> Add product to cart -> Cart updated) -> **Offers**(Promotiational Offers Identified -> Offers added)
### A whole picture with domain model
- "Bite-size" pieces of the system, through **bounded context**, help for system introduction, dividing team responsibility, or pin-pointing critical process.
- Refined and accurate workflow through **aggregates**
- Understanding the relationship between components with **domain events**, and **commands**.
### References
- https://herbertograca.com/category/development/book-notes/domain-driven-design-by-eric-evans/
- Domain-driven design by Eric Evans
- https://creately.com/blog/diagrams/event-storming/