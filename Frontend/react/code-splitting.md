---
authors:
  - 'thanh'
date: '2024-10-29'
description: 'Optimize JavaScript performance with code splitting techniques like route-based splitting, lazy loading, and dynamic imports'
tags:
  - 'react'
  - 'performance'
title: 'Code Splitting in React'
short_title: 'Code Splitting'
---

Code splitting is a technique used to optimize JavaScript bundles by breaking them into smaller chunks, loading only the necessary parts when they’re needed. This reduces the initial loading time for users, as they only download the essential code to render the initial view. Code splitting is particularly valuable in large applications where bundling everything together can lead to slow load times and performance issues.

We will explore various code splitting techniques, including their use cases and practical implementation examples.

## Code Splitting Techniques

### Entry Point Splitting

Entry point splitting involves separating the main application entry points. In Webpack, you can specify multiple entry points, each generating a separate bundle. This technique is helpful in multi-page applications (MPAs) or if you have clearly separate sections within a single-page app (SPA) that can load independently.

```js
// webpack.config.js
module.exports = {
  entry: {
    home: './src/home.js',
    dashboard: './src/dashboard.js',
  },
  output: {
    filename: '[name].bundle.js',
    path: __dirname + '/dist',
  },
}
```

Here, Webpack creates `home.bundle.js` and `dashboard.bundle.js`, loading only the necessary code when the user navigates to either the home page or dashboard.

**Use Case:**

- Ideal for MPAs or complex SPAs where different parts of the app can load independently.

### Route-Based Code Splitting

Route-based code splitting is common in SPAs. Instead of loading the entire app at once, only the components needed for the current route are loaded initially. Additional routes are loaded only when the user navigates to them.

**Example with React Router and React.lazy:**

```jsx
import React, { lazy, Suspense } from 'react'
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom'

const Home = lazy(() => import('./Home'))
const About = lazy(() => import('./About'))
const Contact = lazy(() => import('./Contact'))

function App() {
  return (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route path="/" exact component={Home} />
          <Route path="/about" component={About} />
          <Route path="/contact" component={Contact} />
        </Switch>
      </Suspense>
    </Router>
  )
}
```

**Explanation:**

- `React.lazy` dynamically imports each component.
- `Suspense` shows a fallback (loading spinner) while the component loads.

**Benefits:**

- Reduces initial load time, as only the code for the first route is loaded.
- Each route loads on demand, improving perceived performance for users.

### Component-Level Code Splitting with React.lazy and Suspense

If you have a large component that doesn’t need to load right away (e.g., a modal or sidebar), you can split it out and load it only when it’s needed. This helps reduce the initial bundle size, as non-essential components load asynchronously.

**Example: Lazy Loading a Component**

```jsx
import React, { lazy, Suspense, useState } from 'react'

const UserProfile = lazy(() => import('./UserProfile'))

function App() {
  const [showProfile, setShowProfile] = useState(false)

  return (
    <div>
      <button onClick={() => setShowProfile((prev) => !prev)}>Toggle User Profile</button>
      <Suspense fallback={<div>Loading...</div>}>{showProfile && <UserProfile />}</Suspense>
    </div>
  )
}
```

**Explanation:**

- The `UserProfile` component only loads when showProfile is true.
- `Suspense` ensures that a fallback UI (loading spinner) is displayed while `UserProfile` is being loaded.

**Use Cases:**

- Large, non-essential components such as modals, drawers, or other sections that users may not access right away.

### Splitting Large Dependencies or Utilities

Sometimes a single library or utility can significantly increase your bundle size. Instead of loading the entire library, use dynamic `import()` to load only the necessary part of the code when needed. This is particularly useful for utilities like date formatting or image processing libraries that may not be required on every page.

**Example: Lazy Loading a Utility Library**

```jsx
function DateFormatter({ date }) {
  const [formattedDate, setFormattedDate] = useState('')

  useEffect(() => {
    async function loadDateLibrary() {
      const { format } = await import('date-fns')
      setFormattedDate(format(new Date(date), 'yyyy-MM-dd'))
    }
    loadDateLibrary()
  }, [date])

  return <div>{formattedDate}</div>
}
```

**Explanation:**

- The date-fns library only loads when DateFormatter is rendered.
- This avoids including the entire library in the initial bundle, saving on bundle size.

**Benefits:**

- Reduces initial load time by avoiding unnecessary libraries in the main bundle.
- Load dependencies only when needed, improving performance and responsiveness.

### Library-Based Code Splitting with `react-loadable`

For more complex loading scenarios, `react-loadable` offers additional features such as delayed loading, error boundaries, and preloading. It’s especially helpful if you want to provide a custom loading experience or handle loading errors gracefully.

**Example Using react-loadable**

```jsx
import Loadable from 'react-loadable'

const LoadableComponent = Loadable({
  loader: () => import('./HeavyComponent'),
  loading: ({ isLoading, pastDelay, error }) => {
    if (isLoading && pastDelay) return <div>Loading...</div>
    if (error) return <div>Error loading component!</div>
    return null
  },
  delay: 300, // Shows loading only if loading takes longer than 300ms
})

function App() {
  return <LoadableComponent />
}
```

**Explanation:**

- `react-loadable` provides a loading component that displays based on certain conditions, such as past delay time or error occurrence.
- This allows you to handle cases where loading might take a long time or fail altogether, providing a better user experience.

**Use Cases:**

- Components that may take longer to load due to their size or network conditions.
- Error-prone components that need error handling.

## Advanced Code Splitting Techniques

### Preloading and Prefetching Components

Preloading and prefetching are useful when you want to load components in advance, either to improve performance or to anticipate user interactions.

- **Preload**: Load code for a component in the background, without delaying the initial page load.
- **Prefetch**: Load code when the user is likely to need it soon, based on user interaction patterns (e.g., hovering over a link).

```jsx
const UserProfile = lazy(() => import(/* webpackPrefetch: true */ './UserProfile'))
```

**Use Case:**

- Preload the next route’s component in the background while the user is interacting with the current route.

### Bundle Splitting

Bundling tools, such as Webpack, that have the `SplitChunksPlugin` component can be configured to automatically separate common dependencies (like react or lodash) into distinct bundles. This avoids redundant code in each chunk and reduces the total bundle size.

**Example Configuration in Webpack:**

```js
module.exports = {
  optimization: {
    splitChunks: {
      chunks: 'all',
      minSize: 30000,
      maxSize: 50000,
      cacheGroups: {
        vendor: {
          test: /[\\/]node_modules[\\/]/,
          name: 'vendors',
          chunks: 'all',
        },
      },
    },
  },
}
```

**Explanation**:

- SplitChunksPlugin creates a vendors chunk with common dependencies, reducing redundancy and improving caching.

**Use Case:**

- In large applications with many shared dependencies.

### Lazy Loading Images and Assets

For non-JavaScript assets like images and fonts, you can also improve performance by loading them only when they’re in the viewport.

**Example: Lazy Loading Images with `loading="lazy"`**

```jsx
function ImageComponent() {
  return <img src="path/to/image.jpg" loading="lazy" alt="Lazy loaded image" />
}
```

**Explanation:**

- The loading="lazy" attribute ensures the image loads only when it’s about to enter the viewport.

**Benefits:**

- Reduces initial data transfer, helping pages load faster, especially when there are many images.

### Summary

| Technique                      | Best For                                                 | Examples                                               |
| ------------------------------ | -------------------------------------------------------- | ------------------------------------------------------ |
| **Entry Point Splitting**      | Multi-page apps with separate entry points               | Home, Admin, Dashboard entry points                    |
| **Route-Based Splitting**      | Single-page apps, lazy loading route components          | Lazy loading routes with React Router                  |
| **Component-Level Splitting**  | Large components like modals, settings panels            | Lazy loading non-essential components                  |
| **Large Dependency Splitting** | Libraries used infrequently                              | Date formatting utilities, large image processing libs |
| **Library-Based Splitting**    | Components that need advanced loading/error handling     | `react-loadable` for complex loading states            |
| **Preloading and Prefetching** | Anticipating user actions to improve UX                  | Preloading next route or component                     |
| **Bundle Splitting**           | Avoiding redundancy by splitting common dependencies     | Splitting `vendors` bundle                             |
| **Lazy Loading Images**        | Reducing initial page weight for media-rich applications | `loading="lazy"` attribute on images                   |

Each of these techniques targets a specific aspect of load management and bundle optimization, providing flexibility to load only what’s necessary. Applying them strategically improves both the initial load time and the user experience throughout the app, especially as users navigate or interact more deeply with various parts of the application.
