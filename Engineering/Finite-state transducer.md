---
tags: engineering, state, diagram, machines, transducers
author: Nguyen Xuan Anh
---

## What is finite-state transducer?

It is essentially a [[Finite-state automata]] that has both inputs and outputs. In [Turing machines](https://en.wikipedia.org/wiki/Turing_machine), these inputs and outputs are referred to as 2 separate tapes:

- **input tape**: a set of strings or related data.
- **output tape**: a set of relations generated from the input tape.

This differs from a finite-state automaton which only has 1 (input) tape.

## Mathematical Model
As per the general classification noted on [UC Davis outline on transducers](https://www.cs.ucdavis.edu/~rogaway/classes/120/spring13/eric-transducers) (formatted with similar variables to [[Finite-state automata]]s), a deterministic finite-state machine has 7 main variables associated with its definition (a septuple): ($\Sigma$, $S$, $\Gamma$, $\delta$, $\omega$, $s_0$, _$F$).
- $\Sigma$ is the *input alphabet* (a finite non-empty set of symbols) -> our events;
- $S$ is a finite non-empty set of states;
- $\Gamma$ is the _output alphabet_;
- $\delta$ is the state-transition function: $\delta: S \times \Sigma \rightarrow S$
- $\omega$ is the output-transition function: $\omega: S \times \Sigma \rightarrow \Gamma$
- $s_0$ is an *initial state*, an element of $S$;
- $F$ is the set of _final states_ and is a subset of $S$; and
- $\delta \subseteq S \times (\Sigma \cup \{\epsilon\}) \times (\Gamma \cup \{\epsilon\}) \times S$ (where ε is the [empty string](https://en.wikipedia.org/wiki/Empty_string "Empty string")) is the _transition relation_.

Given any initial state in $s_0$, to transition our state to the next state with our output alphabet, our transition would be:
$$
\delta: s_0 \times \Sigma \rightarrow S
$$
$$
\omega: s_0 \times \Sigma \rightarrow \Gamma
$$
$$
\delta \subseteq s_0 \times (\Sigma \cup \{\epsilon\}) \times (\Gamma \cup \{\epsilon\}) \times S
$$
If we were to reach a final state starting from a known set of states, our transition would look pretty similar:
$$
\delta: S \times \Sigma \rightarrow F
$$
$$
\omega: S \times \Sigma \rightarrow \Gamma
$$
$$
\delta \subseteq S \times (\Sigma \cup \{\epsilon\}) \times (\Gamma \cup \{\epsilon\}) \times F
$$

Transducers that have a final state are used to recognize languages and have their use cases in [[Natural-Language Processing]].

### Simplified meaning
There's actually quite a few ways to write up a transducer, at it is not always simply a beefed-up state machine. To oversimplify, we'll model it closer to a regular state machine:

```typescript
type State = string
type Input = string
type Output = {...} //

const transition = (state: State, input: Input): Output => ...
```

Outputs that are product types of itself and the next state of a transition is referred to as a [[Mealy machine]].

## Examples of basic transducers
Although we've mentioned before that [[Reducers]] are single state machines, the canonical method of creating one mentioned in [Redux](https://redux.js.org/) and [React](https://reactjs.org/docs/hooks-reference.html#usereducer) are pretty much transducers as they can return state or objects (as **notions** of outputs).

```typescript
// https://reactjs.org/docs/hooks-reference.html#usereducer
// our outputs here is the { count: number } object
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

## Reference
- https://en.wikipedia.org/wiki/Turing_machine
- https://t-pl.io/ddd-aggregates-processes-state-machines-and-transducers
- https://en.wikipedia.org/wiki/Finite-state_transducer
- https://reactjs.org/docs/hooks-reference.html#usereducer
- https://www.cs.ucdavis.edu/~rogaway/classes/120/spring13/eric-transducers
- https://dl.acm.org/doi/10.5555/972695.972698
- https://web.stanford.edu/~laurik/publications/ciaa-2000/fst-in-nlp/fst-in-nlp.html
