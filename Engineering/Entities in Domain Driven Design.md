---
tags: engineering, domain-driven-design, DDD
author: M.Vu Cuong(Jim)
---

### What is domain-driven-design
A software design focusing on the **Domain**, one of the keys to a program success, by removing *communication lag* between **Developers** and **Domain Experts**, *separate important Domain-specific components* for maintenance and scalability.

### What is an Entity

- **An Object with ID or Identity**, identify it with another objects with the same attributes. Examples:
	- A banknote(paper money) will have an **ID** that identifies it on the digital systems or a physical log book even if all of its attributes are the same as another banknote(value, printing date, printing batch, etc..).
	-  **Combination of attributes** that make an object unique, a batch of newspapers identify by *name, city, and publish date*.
	
- **An Object has a set of fingerprints or traces**  when going through multiple systems. Examples:
	- An online shopping service with an external payment and shipping system. You can see and identify the order in each step(checkout, payment, shipping) on the shopping site or external service.
	- To send an anonymous donation, the flow includes: *Sender -> API_1 -> API_2 -> API_3 -> Receiver*. There is no way to indentify the donation so each API will log the request ID for debugging purposes or when they need to make a refund. 

### Entities's role in DDD
**Domain** includes Entities performing business-related actions or interacting with each other so They _must be clear and predictable_. We need to focus on how the system revolves around that entity and decide the identifier, not the reverse. Example:

- **A online shopping site for Furniture**, the user only check brand name, model number, maybe design, and color for comparison between chairs or tables. Having a separate ID for each item might impact the decision on how to implement checkout(that item with ID is sold out so the user will need to find a similar item with a different ID).

### References

- https://herbertograca.com/category/development/book-notes/domain-driven-design-by-eric-evans/

- Domain-driven design by Eric Evans
