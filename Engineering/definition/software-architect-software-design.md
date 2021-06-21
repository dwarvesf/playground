---
tag: software architecture, software design
---

## Software Architecture (SA)
**Sum up**
- structure the software
- Answer for: what we are building

**WHAT**
Software Architecture (SA) 
create a complete system architecture. 

The type of architecture will decide the constrains of software design. 

A software must have the charateristics (based on biz requirement). SA helps connects these characteristics into structural solution. 

SA prevents the accumulation of technical debts.

**EXAMPLE**
- Microservices 
- Monolith
- Event-Driven
- Serverless

**HOW**
The architecture descision must based on business requirement (scaling/ traffice volume, ...etc) 
Helps achieve biz goal and tech strategy

## Software Design (SD)
**Sum up**
- implement the software
- answer for: how we are building

**WHAT**
Software Design (SD) arranging the order of component is called software design. 

SD responsible for code-level design. 
- what each module is doing
- what problem does each module esolve

**EXAMPLE**
- Factory pattern
- Adapter pattern

**HOW**
- Decide the function of each component and how they interact with others.
- Create the specifications of software artifacts. How individual modules/ components are amde and interact with each other
- Follows the SOLID principle
	- each class have to serve one purpose
	- open for extension. add more function without breaking the existing codes
	- use inheritance and dont break the app's logic
	- catergorize the interfaces <> structure the code so that a class won't be forced to implement a redundant function
	- decoupling the code 


#### Citation
- https://codeburst.io/software-architecture-the-difference-between-architecture-and-design-7936abdd5830