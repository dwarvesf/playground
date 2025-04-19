---
tags: 
  - engineering
  - modeling
title: Finite State Machine
date: 2018-08-29
description: null
---

A Finite State Machine is a model of computation based on a hypothetical machine made of one or more states. Only one single state of this machine can be active at the same time. It means the machine has to transition from one state to another in to perform different actions

![](assets/finite-state-machine_db5600646453d67b0df29dfa3c9dc5b0_md5.webp)

Above image is a simple FSM, each circle is a `state` and arrow is an `event` or `action`.

### Pros and Cons

**Pros**

* State machines are good firewalls
* Let say, bugs in our software are the results of actions dispatched in the wrong state. They leave our app in the state that we don't know about, and this breaks our program or lead to incorrect behavior.
* Straightforward

**Cons**

* Scalability is a nightmare
* FSM works well when we have a well-organized set of states and transitions, when we add some additional states we have to re-define a logic between themConcurrency
* When running multiple state machines in parallel, you either end up with deadlocks or you have edit them all in a way they are compatible.

### Thinking in term of states (instead of transitions)

(Okay, tbh the concept of FSM is eye-opening for me :kappa:)

We will try to solve a very simple problem that we face everyday. We want to fetch data from a back-end API and display to the user

Before get into state machines, my workflow for building such a feature is something like this:

* We display a fetch-data button.
* The user clicks the fetch-data button.
* Fire the request to the back end.
* Retrieve the data and parse it.
* Show it to the user.
* Or, if there is an error, display the error message and show the fetch-data button so that we can trigger the process again.

![](assets/finite-state-machine_93ba1268646d3675466aa8887079d580_md5.webp)

It seems pretty right for me, until there are a bunch of bugs coming because user dispatched an unexpected action

* User hit button so many times
* So many requests will be sent to backend ?
* The request is succeed but data is being corrupted
* Will we render it anyway ?

We will need to spend more effort to cover all these things that make our software much more complexity with a lot of business logic code also have to widen our testing cases

What if we think in the `states` way:

* **idle:** In this state, we display the fetch-data button, sit and wait. The possible action is:
* **click**

```plain_text
    When the user clicks the button, we are firing the request to the back end and then transition the machine to a “fetching” state.
```

* **fetching:** The request is in flight, and we sit and wait. The actions are:
* **success**

```plain_text
    The data arrives successfully and is not corrupted. We use the data in some way and transition back to the “idle” state.

- failure

    If there is an error while making the request or parsing the data, we transition to an “error” state.
```

error: We show an error message and display the fetch-data button. This state accepts one action:
retry: When the user clicks the retry button, we fire the request again and transition the machine to the “fetching” state.

![](assets/finite-state-machine_b5d7d35ae8b3b4cbd6c0c9d8589d4dae_md5.webp)

This simplifies the logic and makes it more predictable. It also solves some of the problems mentioned above. Notice that, while we are in “fetching” state, we are not accepting any clicks. So, even if the user clicks the button, nothing will happen because the machine is not configured to respond to that action while in that state. This approach automatically eliminates the unpredictable branching of our code logic

### Example

* Traffic light
* Order management
* Network protocol based on state like TCP
