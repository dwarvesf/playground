---
tags: 
  - event-sourcing
title: Sdk Event Sourcing
date: 2020-05-21
description: null
---

## Software Development Kit (SDK)

SDK stands for Software Development Kit: the tools and software to develop application through a specific platform. SDK provides libraries, document, templates, code sample, debugging, supportive documentation or additional document for developers to integrate into their software/ application. SDK can also be a combination of many APIs under the form of libraries to interact with the operating system.

Let's take a cellphone for an example. Every cellphone has an operating system with programmed API, and many underlying connected libraries. A kit of APIs that can be used for different hardwares with the same operating system.

## Function of SDK

* Interact with hardware
* Interact with files
* Manage cookies

## Event Sourcing

Event Sourcing is a term for an architecture that is designed for interaction/ communication between app A and app B. Event Sourcing acts as a message-oriented middleware where data is stored and sorted on prioritized order, and ready to be called out for communication purpose between parties.

Consider Event Sourcing as a mailbox to store the data for communication.

* event: stands for data
* sourcing: where the data comes from

### Example: TIKI

Tiki is a marketplace for good tradings. Let's say TIKI has 3 types of parties

**Marketplace**

* Time of order
* Time of invoice

**Warehouse**

* Stock status
* Time of import/ export

**Support**

* Delivery status
* Goods returning

The data between parties has a connection with each other, and it needs interaction to smooth the process of goods handling and delivery. Different types of data (events) from different parties (source) will need a system to filter and organize it with prioritized order to make sure the communication goes smoothly, that's what Event Sourcing is all about. __

## React Hook

Hooks are functions that let you “hook into” React state and lifecycle features from function.
