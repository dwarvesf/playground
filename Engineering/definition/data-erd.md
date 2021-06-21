---
tag: data model, ERD
---

### What
ERD stands for Entity Relationship Diagram, a structural diagram that contains symbols nad connectors that visualizes 2 types of information
- The major Entities
- The Relationship between those entities


When we talk bout Entities, we are referring to the business objects within the system: people/role, tangile object (product).

When we talk about Relationship, we are referring how those entities relate with each other. 

### Primary key & Foreign key
- Primary key: Use to uniquely define a record in database table
- Foreign key: a foreign key of a table is used aas a navigation to a primary key of another table

### When 
ERDs are mostly developed during concept visualization, database design, database debugging, requirement information system.

###  How-to
- Answer the purpose: What is this ERD for
- Clarify the model scope. This prevents the model from having too many redundant entities. Onyl select the entities that is critical and relevant to the business model. 
- Define the models/ major entities
- Define the attribute of that entities (related information)
- Decide the relationship between those entities (which one might affect one another)
- Decide the kind of relationship
	- 1:1
	- 1:many
	- many:1
	- many:many

#### Example
![[Screen Shot 2021-06-15 at 16.10.23.png]]

-> [the diagram]([Homework-04 - dbdiagram.io](https://dbdiagram.io/d/5f994c163a78976d7b798240))

![[Screen Shot 2021-06-15 at 16.11.14.png]]


#### Citation
- [Explaning the ERD](https://www.visual-paradigm.com/guide/data-modeling/what-is-entity-relationship-diagram/#erd-data-models-conceptual)
- [Difference of the relationship](https://stackoverflow.com/questions/3113885/difference-between-one-to-many-many-to-one-and-many-to-many)
- [Example of ERD](https://www.guru99.com/er-diagram-tutorial-dbms.html)