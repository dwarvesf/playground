---
tags: engineering, state, diagram, machines
author: Nguyen Xuan Anh
---

# Moore machine

## What is a Moore machine?
A Moore machine is a [[Finite-state automata]] where the output values are determined by only its current state. Moore machines are a restricted type of a [[Finite-state transducer]].

![Moore Machine](https://d8it4huxumps7.cloudfront.net/uploads/images/61d43f4652280_block_diagram_of_moore_machine.jpg)

## Mathematical Model
As per the general classification noted on [UC Davis outline on transducers](https://www.cs.ucdavis.edu/~rogaway/classes/120/spring13/eric-transducers) (formatted with similar variables to [[Finite-state automata]]s), a deterministic Moore machine has 6 main variables associated with its definition (a sextuple): ($\Sigma$, $S$, $\Gamma$, $\delta$, $\omega$, $s_0$).
- $\Sigma$ is the *input alphabet* (a finite non-empty set of symbols) -> our events;
- $S$ is a finite non-empty set of states;
- $\Gamma$ is the _output alphabet_;
- $\delta$ is the state-transition function: $\delta: S \times \Sigma \rightarrow S$
- $\omega$ is the output-transition function: $\omega: S \rightarrow \Gamma$
- $s_0$ is an *initial state*, an element of $S$; and
- $\delta \subseteq S \times (\Sigma \cup \{\epsilon\}) \times (\Gamma \cup \{\epsilon\}) \times S$ (where ε is the [empty string](https://en.wikipedia.org/wiki/Empty_string "Empty string")) is the _transition relation_.

Given any initial state in $s_0$, to transition our state to the next state with our output alphabet, our transition would be:
$$
\delta: s_0 \times \Sigma \rightarrow S
$$
$$
\omega: s_0 \rightarrow \Gamma
$$

## Differences between

### With formal [[Finite-state transducer]]s

Moore machines are a type of generator and are not used in processing natural language. As such, they do not have a concept of a final state.

### With [[Mealy Machine]]s

Both Mealy and Moore machines are generator-type state machines and can be used to parse [regular language](https://en.wikipedia.org/wiki/Regular_language). The outputs on a Mealy machine depend on **both the state and inputs**, whereas a Moore machine have their outputs **synchronously change with the state.**

> Every Moore machine can be converted to a Mealy machine and every Mealy machine can be converted to a Moore machine. Moore machine and Mealy machine are equivalent.

## Reference
- https://en.wikipedia.org/wiki/Mealy_machine
- https://www.cs.ucdavis.edu/~rogaway/classes/120/spring13/eric-transducers
- https://unstop.com/blog/difference-between-mealy-and-moore-machine
