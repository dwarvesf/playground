---
tags: engineering, state, diagram, machines
author: Nguyen Xuan Anh
---

# What are finite state automata?
A **finite state automaton (FSM)** (**FSA**, plural: automata), or better known as a state machine, is a mathematical model of with a constraint such that the abstract machine can be only and exactly be one of a finite number of states at any point in time. Finite state here is typically represented as a string or equivalent enumeration.

# Mathematical Model
A _deterministic finite-state machine_ or _deterministic finite-state acceptor_ is a [quintuple](https://en.wikipedia.org/wiki/Tuple "Tuple")
$(\sum, S, s_0, \delta, F)$
- $\sum$ is the input alphabet (a finite non-empty set of symbols) -> our events
- $S$ is a finite non-empty set of states
- $s_0$ is an initial state, an element of $S$
- $\delta$ is the state-transition function: $\delta: S \times \sum \rightarrow S$
	- in a [nondeterministic finite automaton](https://en.wikipedia.org/wiki/Nondeterministic_finite_automaton "Nondeterministic finite automaton") it would be $\delta: S \times \sum \rightarrow P(S)$
-  $F$ is the set of final states, a (possibly empty) subset of $S$

# Coming from Algebraic Data Types
State machines are definitely a step up from [[Algebraic data types]] as it solves type/event explosion with nested [[Sum types]], however, it still has some limitations given that they can only solve a very flat domain problem. This is because the more nested states you want to represent in a finite state machine, the more combinatorially complex it becomes, causing a [[State explosion]].

Luckily, we can solve this with Harel [[Statecharts]]; you may know and refer to them as [UML state machines](https://en.wikipedia.org/wiki/UML_state_machine) In essence, statecharts are a combination of [Mealy machines](https://en.wikipedia.org/wiki/Mealy_machine) and [Moore machines](https://en.wikipedia.org/wiki/Moore_machine).

Although it is conventional to think $\delta$ as a [partial function](https://en.wikipedia.org/wiki/Partial_function), i.e: $\delta(s,x)$, the operator precedence relative to the data is, almost in all cases, left associative. This means asynchronously *parallel* application of the partial function will result in broken logic, that is unless all events are completely valid and it is possible combine partial and illegal transitions of states into a proper finite state (theory to apply for [[TimescaleDB]] [continuous aggregates](https://docs.timescale.com/timescaledb/latest/how-to-guides/continuous-aggregates/)) c

# References
- https://en.wikipedia.org/wiki/Finite-state_machine
- https://blog.honosoft.com/2019/10/31/partial-state-machine/
