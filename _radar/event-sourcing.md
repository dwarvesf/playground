---
tags: null
title: Event Sourcing
date: null
description: null
authors: null
menu: radar
type: null
hide_frontmatter: false
confidence: Low
assign: Tom X Nguyen
priority: null
status: Hold
quadrant: Techniques
tag: Database, Backend
---

<!-- table_of_contents 2d7c73db-9777-4311-ba52-65704e503860 -->

### Description
Simply put, event sourcing is focused on the persistence of events as a recording of a change of state of an entity. 

Event sourcing is an approach for maintaining the state of business entities by recording each change of state as an event. This allows businesses to have a complete and accurate history of their data, which can be used for auditing, debugging, analytics, and replaying scenarios.

Event sourcing also enables businesses to implement the CQRS pattern, which separates the read and write models of data and improves scalability and performance. Event sourcing is an alternative way to persist data that offers many benefits for businesses.

### What’s better about this method or library
Event sourcing has several benefits for composition of entity states and data collection. Any business event can be converted into a data record. A collection of those data records, as well as the guarantee that replaying those data records in order will recreate business entities or states, gives the business a durability guarantee for their data. Other benefits includes, but is not limited to:

* Loosely coupled business entities that exchange events make it easier to migrate from a monolithic architecture to microservices.
* Event-sourced systems are easy to test and debug, as commands and events can be simulated for testing purposes, and the event log provides a good record for debugging.
* Event sourcing gives you a complete, consistent model of the slice of the world modeled by your software, which is attractive for auditing purposes.
* Observability is one of the most significant advantages of event sourcing. Each action in the system triggers an event, which gathers business intelligence and provides insight into how users interact with your application[4].

### What can we do with it
Along with auditing our current business entities, states, or table records, we can also derive new states with temporal queries.

Temporal queries are queries that determine the state of an entity at any point in time. They work with event sourcing by using the events stored in the event log to reconstruct the state of an entity at any given point in time. Event sourcing is a pattern where all changes to an application's state are stored as a sequence of events, which can be used to build up the current state of the application. This makes it possible to implement temporal queries that determine the state of an entity at any point in time. 

### How should we adopt it
We can observe any table in our systems or projects that establishes a state of an entity and persist any events that lead up to the composition of those states. With respect to SQL databases, this means any table can be broken down into events and have them persisted in another table. For instance, a hierarchical organization (graph) of employees can be broken down to events regarding hiring, dismissals, changes in leadership, etc. Event sourcing concerns only with persisting events in such a way that the current state of a system can be reconstructed.

<!-- child_database 91cbf2a6-ff37-4707-9d6d-dcb053b8e225 -->
