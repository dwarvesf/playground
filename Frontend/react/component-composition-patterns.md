---
authors:
  - 'thanh'
date: '2024-10-29'
description: 'Learn React composition patterns with coverage of HOCs, render props, compound components, and custom hook'
tags:
  - 'react'
title: 'Component Composition Patterns in React'
short_title: 'Component Composition Patterns'
---

Component composition patterns are foundational for creating scalable, flexible, and reusable React components. They allow us to build UIs by combining smaller, single-purpose components in various ways.

## Key Composition Patterns in React

### Higher-Order Components (HOCs)

HOCs are functions that take a component and return a new component, adding additional functionality. They’re particularly useful for cross-cutting concerns like logging, analytics, or authentication.

**Example Use Case**: Suppose you need to add logging functionality to multiple components. Instead of embedding logging code in each component, you create an HOC that wraps each component and handles the logging logic.

```js
function withLogging(WrappedComponent) {
  return function EnhancedComponent(props) {
    useEffect(() => {
      console.log(`Component ${WrappedComponent.name} mounted`)
    }, [])
    return <WrappedComponent {...props} />
  }
}
```

**When to Use HOCs**:

- For injecting props or shared behavior across multiple components.
- To handle cross-cutting concerns that aren’t tightly coupled with the component’s core logic.
- When you want to avoid prop drilling by creating an abstraction layer.

**Trade-offs**:

- Can lead to “wrapper hell” if overused.
- Less popular with modern hooks as custom hooks can sometimes achieve similar results in a more straightforward way.

### Render Props

With render props, a component uses a prop as a function to control its output, allowing you to pass dynamic rendering logic.

**Example Use Case**: If you have a `<DataFetcher />` component that retrieves data, you could use render props to define how that data should be rendered by the consuming component.

```js
function DataFetcher({ render }) {
  const [data, setData] = useState(null)
  useEffect(() => {
    fetchData().then(setData)
  }, [])
  return render(data)
}

// Usage:
<DataFetcher render={(data) => <DisplayData data={data} />} />
```

**When to Use Render Props**:

- For providing control over how the child component renders data.
- When the consuming component needs flexibility in rendering but also needs the data or logic encapsulated in the parent.

**Trade-offs**:

- Can lead to deeply nested code if not structured thoughtfully.
- Not as widely used with hooks and context, which often simplify sharing functionality across components.

### Compound Components

Compound components are components that work together as a single unit but allow for great customization of individual parts.

**Example Use Case**: A `<Dropdown />` component that lets you use `<Dropdown.Toggle />` and `<Dropdown.Menu />` as children, giving flexibility to control each part while keeping the structure consistent.

```js
function Dropdown({ children }) {
  const [isOpen, setIsOpen] = useState(false)
  return (
    <DropdownContext.Provider value={{ isOpen, setIsOpen }}>
      <div className="dropdown">{children}</div>
    </DropdownContext.Provider>
  )
}

Dropdown.Toggle = function Toggle() {
  const { setIsOpen } = useContext(DropdownContext)
  return <button onClick={() => setIsOpen((open) => !open)}>Toggle</button>
}

Dropdown.Menu = function Menu({ children }) {
  const { isOpen } = useContext(DropdownContext)
  return isOpen ? <div className="menu">{children}</div> : null
}
```

**When to Use Compound Components**:

- When you have related components that need to work together in a coordinated way but require customization for each part.
- Especially effective for components like modals, tabs, or dropdowns.

**Trade-offs**:

- Requires careful management of context to avoid coupling.
- If the API isn’t intuitive, can be confusing for developers unfamiliar with the compound pattern.

### Controlled and Uncontrolled Components

Controlled components let the parent manage the state, whereas uncontrolled components manage their own state internally. Combining them allows more flexibility in form components.

**Example Use Case**: A `<TextInput />` component that can work either as a controlled component (with value and onChange passed from the parent) or an uncontrolled component (handling its own state).

```js
function TextInput({ value, defaultValue, onChange }) {
    const [internalValue, setInternalValue] = useState(defaultValue);
    const isControlled = value !== undefined;

    const handleChange = (e) => {
        const newValue = e.target.value;
        if (isControlled) {
            onChange(newValue);
        } else {
            setInternalValue(newValue);
        }
    };

    return (
        <input
            value={isControlled ? value : internalValue}
            onChange={handleChange}
        />
    );
}

// Usage:
<TextInput defaultValue="Uncontrolled" />
<TextInput value={controlledValue} onChange={setControlledValue} />
```

**When to Use Controlled and Uncontrolled Components**:

- Controlled components are essential for forms or any element that requires data validation.
- Uncontrolled components are more performant and simpler for elements without validation needs.

**Trade-offs**:

- Controlled components can lead to performance issues in large forms.
- Uncontrolled components lack flexibility for handling validation or dynamic data flow.

### Custom Hooks

Custom hooks provide a way to abstract and encapsulate complex logic, making components more modular and readable. They can be used in place of certain HOCs and render props for handling things like async data, complex state, or side effects.

**Example Use Case**: If you frequently need to fetch data in multiple components, a `useFetch` custom hook encapsulates this logic, making the components cleaner and more testable.

```js
function useFetch(url) {
  const [data, setData] = useState(null)
  useEffect(() => {
    fetch(url)
      .then((response) => response.json())
      .then(setData)
  }, [url])
  return data
}
```

**When to Use Custom Hooks**:

- When encapsulating side effects, data fetching, or complex state logic.
- As a more readable and flexible alternative to HOCs and render props.

**Trade-offs**:

- Dependency management in hooks can be tricky, especially with complex dependencies.
- Not ideal for injecting UI-related functionality that might be easier to handle with HOCs or render props.

## Choosing the Right Pattern

Selecting the right pattern often depends on:

- **Complexity of data flow**: If your data flow is complex, consider compound components or render props.
- **Component reusability**: HOCs are ideal for reusable logic across unrelated components.
- **Level of control**: Controlled/uncontrolled patterns are great for balancing simplicity and flexibility in form handling.
