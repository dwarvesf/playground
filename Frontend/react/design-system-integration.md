---
authors:
  - 'thanh'
date: '2024-10-29'
description: 'Learn how to integrate design systems in React applications with comprehensive coverage of design tokens, atomic components, and accessibility standards.'
tags:
  - 'react'
  - 'design-system'
  - 'storybook'
title: 'Design System Integration in React'
short_title: 'Design System Integration'
---

Design system integration in React involves creating a set of reusable, consistent, and easily maintainable components that reflect your app’s design guidelines. Integrating a design system helps ensure visual and functional consistency across your application while allowing for scalability as new components and features are added. Design systems often include UI components, design tokens, typography, colors, icons, spacing guidelines, and accessibility standards.

**Key Steps and Concepts for Design System Integration in React**

1. Define the Core Design Tokens (colors, typography, spacing, etc.)
2. Build Atomic Components (buttons, inputs, typography)
3. Create Composable, Flexible Components
4. Establish and Use a Component Library Framework (Storybook)
5. Implement Accessibility Standards
6. Use Context and Theming for Adaptable Designs

### 1. Define Core Design Tokens

**Design tokens** are the fundamental building blocks of your design system. They represent design decisions like colors, typography, and spacing in a consistent, reusable format. By defining tokens, you create a single source of truth that makes updates and adjustments easy across the app.

**Example: Design Tokens in a JSON Format**

```json
{
  "colors": {
    "primary": "#007bff",
    "secondary": "#6c757d",
    "background": "#f8f9fa",
    "text": "#212529"
  },
  "typography": {
    "fontFamily": "Arial, sans-serif",
    "fontSize": {
      "small": "12px",
      "medium": "16px",
      "large": "24px"
    }
  },
  "spacing": {
    "small": "4px",
    "medium": "8px",
    "large": "16px"
  }
}
```

You can then access and apply these tokens in your components, ensuring they follow consistent visual guidelines.

**In a React Component:**

```js
import tokens from './tokens.json'

const Button = ({ children }) => (
  <button
    style={{
      backgroundColor: tokens.colors.primary,
      color: tokens.colors.background,
      padding: tokens.spacing.medium,
      fontSize: tokens.typography.fontSize.medium,
      fontFamily: tokens.typography.fontFamily,
    }}
  >
    {children}
  </button>
)
```

### 2. Build Atomic Components

Atomic design breaks down UI elements into **atoms**, **molecules**, **organisms**, **templates**, and **pages**. This approach helps in building reusable, low-level components that can be combined and customized to create more complex components and layouts.

**Atomic Design Hierarchy:**

- **Atoms**: Smallest, single-purpose components like buttons, inputs, or labels.
- **Molecules**: Combinations of atoms, such as an input field with a label.
- **Organisms**: Groups of molecules that form distinct sections, like a header or a form.
- **Templates and Pages**: Higher-level layouts or complete screens that use organisms and molecules.

**Example: Button Component (Atom)**

```jsx
const Button = ({ label, onClick, variant = 'primary' }) => {
  const styles = {
    primary: {
      backgroundColor: tokens.colors.primary,
      color: tokens.colors.background,
    },
    secondary: {
      backgroundColor: tokens.colors.secondary,
      color: tokens.colors.background,
    },
  }

  return (
    <button style={styles[variant]} onClick={onClick}>
      {label}
    </button>
  )
}
```

**Example: Form Component (Molecule)**

```jsx
const FormField = ({ label, type = 'text', value, onChange }) => (
  <div>
    <label>{label}</label>
    <input type={type} value={value} onChange={onChange} />
  </div>
)
```

### 3. Create Composable, Flexible Components

Design systems benefit from **flexible components** that can adapt to different use cases without being overly rigid. Use **props** and **styled-system** libraries (e.g., styled-components or emotion) to make your components customizable.

```jsx
import styled from 'styled-components'
import tokens from './tokens.json'

const Button = styled.button`
  padding: ${tokens.spacing.medium};
  font-size: ${tokens.typography.fontSize.medium};
  color: ${({ variant }) => tokens.colors[variant]};
  background-color: ${({ bg }) => bg || tokens.colors.background};
`
```

This approach allows the Button component to be reusable, enabling different colors and backgrounds with minimal code.

### 4. Establish and Use a Component Library Framework (Storybook)

[Storybook](https://storybook.js.org/) is a popular tool for creating isolated component libraries, documenting components, and allowing team members to interact with components outside of the application environment.

**Set up Storybook**

Install Storybook in your React project.

```sh
npx sb init
```

**Write Stories for Components**

Each component should have its own story, describing its appearance with various props and states.

```jsx
// Example: Button.stories.js
import React from 'react'
import { Button } from './Button'

export default {
  title: 'Design System/Button',
  component: Button,
}

export const Primary = () => <Button variant="primary" label="Primary Button" />
export const Secondary = () => <Button variant="secondary" label="Secondary Button" />
```

**Benefits:**

- Provides a single source of truth for UI components, where designers and developers can collaborate.
- Enables interactive testing of each component’s variations, ensuring they meet design requirements.
- Encourages consistency across components, as each component variation is clearly documented.

### 5. Implement Accessibility Standards

Design systems must prioritize accessibility to create inclusive applications. Follow **WCAG guidelines** and use accessible components, ensuring that all users can interact with your app.

- **Color Contrast**: Use tokens that meet accessibility standards for contrast. Tools like axe can test for color contrast and other accessibility issues.

- **Aria Roles and Attributes**: Use ARIA attributes for interactive components like buttons, modals, and dialogs to improve screen reader support.

```jsx
// Example: Accessible Button with ARIA
const Button = ({ label, onClick, ariaLabel, variant = 'primary' }) => (
  <button onClick={onClick} style={{ backgroundColor: tokens.colors[variant] }} aria-label={ariaLabel}>
    {label}
  </button>
)
```

- **Keyboard Navigation**: Ensure that all components can be navigated via keyboard. Focus management is crucial, especially for modal dialogs or dynamic components like carousels.

```jsx
// Example: Focus Management in a Modal
import { useEffect, useRef } from 'react'

const Modal = ({ isOpen, onClose, children }) => {
  const closeButtonRef = useRef()

  useEffect(() => {
    if (isOpen) {
      closeButtonRef.current.focus()
    }
  }, [isOpen])

  return isOpen ? (
    <div role="dialog" aria-modal="true" tabIndex={-1}>
      <button ref={closeButtonRef} onClick={onClose}>
        Close
      </button>
      {children}
    </div>
  ) : null
}
```

Tools:

- `axe-core` and `eslint-plugin-jsx-a11y` for testing accessibility issues.
- `Storybook accessibility addon` to validate and fix issues while developing components.

### 6. Use Context and Theming for Adaptable Designs

To support **themes** (e.g., dark and light modes), use **context providers** to pass theme values down to components. This enables consistent theming and allows the user to switch themes easily.

**Example: Theming with Context**

1. Create Theme Context:

```jsx
import React, { createContext, useContext, useState } from 'react'
import tokens from './tokens.json'

const ThemeContext = createContext()

export const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light')

  const toggleTheme = () => setTheme((prev) => (prev === 'light' ? 'dark' : 'light'))

  const themeStyles = theme === 'light' ? tokens.light : tokens.dark

  return <ThemeContext.Provider value={{ theme, themeStyles, toggleTheme }}>{children}</ThemeContext.Provider>
}

export const useTheme = () => useContext(ThemeContext)
```

2. Consume Theme Context in Components:

```jsx
const ThemedButton = ({ label }) => {
  const { themeStyles } = useTheme()
  return (
    <button
      style={{
        backgroundColor: themeStyles.colors.primary,
        color: themeStyles.colors.background,
      }}
    >
      {label}
    </button>
  )
}
```

3. Switch Themes in App:

```jsx
function App() {
  const { toggleTheme } = useTheme()
  return (
    <div>
      <ThemedButton label="Click me" />
      <button onClick={toggleTheme}>Toggle Theme</button>
    </div>
  )
}
```

### Summary

| Technique                           | Purpose                                                                                  |
| ----------------------------------- | ---------------------------------------------------------------------------------------- |
| **Design Tokens**                   | Centralize colors, typography, and spacing for consistent styling                        |
| **Atomic Components**               | Build scalable, reusable components from basic building blocks                           |
| **Composable, Flexible Components** | Ensure flexibility for various use cases using props and dynamic styling                 |
| **Storybook**                       | Document, test, and showcase all components, ensuring design and functionality alignment |
| **Accessibility Standards**         | Improve usability for all users, following WCAG and ARIA best practices                  |
| **Context and Theming**             | Support adaptable designs, allowing for light and dark themes or other custom themes     |

By integrating these techniques, you can build a design system that is robust, adaptable, and consistent, making it easier to scale and maintain the UI over time.
