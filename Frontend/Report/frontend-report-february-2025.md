---
tags:
  - frontend
  - market-report
title: Frontend Report February 2025
short_title: "February 2025"
description: This February 2025 report explores key frontend insights, including React's evolution beyond CRA, Next.js performance innovations, essential browser interoperability developments, and emerging tools like React Scan and Standard Schema. Discover practical strategies for authentication, performance optimization, and accessibility in today's rapidly evolving web development landscape.
date: 2025-02-28
authors:
  - hthai2201
---

## React

### [Create React App deprecated: What's next for React developers?](https://syntackle.com/blog/create-react-app-deprecated)

The React team has officially deprecated Create React App (CRA), Discover the limitations of CRA, including its lack of control over the build process and outdated bundling with Webpack. Explore the best alternatives, such as Vite for speed and simplicity, Next.js for server-side rendering and React Server Components.

### [React Context: Performance pitfalls and practical solutions](https://tigerabrodi.blog/was-react-context-a-mistake)

React Context simplifies data sharing but can cause performance issues due to unnecessary re-renders. Mitigate this by splitting large contexts into smaller ones or using state management libraries like Jotai or Zustand for finer control over re-renders.



### [Understanding React Server Components: Under the hood](https://tonyalicea.dev/blog/understanding-react-server-components/)

Uncover how React Server Components(RSCs) work under the hood. This guide explores the key differences from traditional rendering, the Virtual DOM, streaming with the `Flight` format, and the `double data problem`. Learn about the role of bundlers, component imports, and the limitations of hooks in RSCs.

### [React Query - The bad parts](https://tkdodo.eu/blog/react-query-the-bad-parts)

A slide deck on the tradeoffs made when choosing React Query, such as it having a large bundle size, declarative data fetching, normalized cache.

### Quick links

- [Server-side renaissance: A year without React](https://kellysutton.com/2025/01/18/moving-on-from-react-a-year-later.html)
- [17 tips from a senior React developer](https://www.frontendjoy.com/p/17-tips-from-a-senior-react-developer)
- [We replaced our React frontend with Go and WebAssembly](https://dagger.io/blog/replaced-react-with-go)
- [React UI component libraries in 2025](https://www.builder.io/blog/react-component-library)

## Next.js

### [Vercel Functions: Introducing Fluid Compute for AI applications](https://www.youtube.com/watch?v=itSu3T1zJew)

Vercel's Fluid Compute combines the benefits of servers and serverless architectures into a unified model. This new feature aims to improve speed and cost-efficiency, especially for AI applications and those with concurrent network requests. Fluid Compute allows multiple requests to be packed into a single function, reducing overall function usage and costs. This feature offers improved performance and can lead to significant savings on Vercel function bills, sometimes up to 85%. Fluid Compute replaces previous `Edge` functions, offering better performance and developer experience by utilizing full Node.js support for middleware and other workloads.

### [Build a Next.js login page with session-based authentication](https://clerk.com/blog/building-a-nextjs-login-page-template)

Learn how to implement session-based authentication in a Next.js application, including essential aspects such as database schema design (users and sessions tables), backend security measures (password hashing and session ID verification), and frontend user interface considerations (sign-up/sign-in forms). The article also introduces Clerk, a user management platform that simplifies the authentication process.

### [Next.js 15: Master error handling best practices](https://devanddeliver.com/blog/frontend/next-js-15-error-handling-best-practices-for-code-and-routes)

This article covers error handling in Next.js 15, focusing on anticipating, detecting, and addressing errors using error.tsx, global-error.tsx, and not-found.tsx. Use error.tsx for unexpected errors, global-error.tsx for unhandled global errors, and not-found.tsx for 404 errors. Employ ErrorBoundary to isolate errors and improve user experience. For server-side errors, use the useActionState hook.

### Quick links

- [Make your Next.JS Docker images microscopic!](https://xeiaso.net/notes/2024/small-nextjs-images/)
- [Revolutionizing performance with Next.js composable caching](https://nextjs.org/blog/composable-caching)

## Others

### [Double-keyed caching: How browser cache partitioning changed the web](https://addyosmani.com/blog/double-keyed-caching)

Run AI tasks right in the browser! Transformers.js leverages a pipeline API that is easy to use and can perform tasks like sentiment analysis and object detection. All processing occurs client-side, no server needed.

### [Accessibility essentials every front-end developer should know](https://martijnhols.nl/blog/accessibility-essentials-every-front-end-developer-should-know)

This post covers styling considerations like focus indicators and how to use ARIA attributes. Following accessibility best practices improves the user experience for everyone, not just those with disabilities. Some key principles include using semantic HTML, correctly structuring forms with labels (avoiding placeholders), writing descriptive alt text for images, and having smooth keyboard navigation with focus management in modals.

## [Easy performance wins: Speed up your web apps now!](https://syntax.fm/show/874/fast-apps-easy-perf-wins)

To boost web app performance, focus on: reducing data by optimizing images, minifying JavaScript, and using Gzip. Employ caching using client and server-side methods for efficient content delivery. A CDN can distribute content globally to cut latency. Identify and fix bottlenecks using browser developer tools, focusing on LCP, INP, CLS, FCP, and TTFB. Optimize CSS by inlining critical CSS and using preload/prefetch tags. Use system fonts over custom ones when possible.

### Quick links

- [A poor Lighthouse result doesn't mean poor performance](https://www.debugbear.com/blog/poor-performance-score-good-performance)
- [Mistakes in the design of CSS](https://wiki.csswg.org/ideas/mistakes)

## Trending

### [5 technical JavaScript trends you need to know about in 2025](https://risingstars.js.org/2024/en)

JavaScript trends in 2025 include serverless architectures, WebAssembly integration, and localized state management. Serverless frameworks, especially with edge functions, will improve performance and developer experience, while WebAssembly will optimize performance-intensive tasks. The rise of microfrontends using tools like Webpack Module Federation will enable more scalable development.

### [State of React 2024](https://2024.stateofreact.com/)

The 2024 State of React survey gathered 7,870 responses to identify trends in the React ecosystem, such as the fact that forwardREf and memo were pain points among common APIs that React 19 aims to address. While React stabilizes, its ecosystem continues to innovate rapidly. TanStack Start emerges as a potential competitor to Next.js.

### [Launching Interop 2025](https://web.dev/blog/interop-2025)

Interop continues to push browser vendors toward a unified web experience. With a 95% pass rate in 2024, Interop 2025 introduces 19 focus areas, tackling key challenges like CSS Zoom standardization, WebRTC security, and mobile testing parity. By refining interoperability, we empower developers with a more consistent, reliable, and future-proof web platform.

### Quick links

- [The success of Interop 2024!](https://webkit.org/blog/16413/the-success-of-interop-2024/)
- [Which rich text editor framework should you choose in 2025?](https://liveblocks.io/blog/which-rich-text-editor-framework-should-you-choose-in-2025)

## Tools

### [React Scan: Simplifying React performance detection](https://react-scan.com/)

React Scan automatically detects performance issues in your React app. Existing tools require code changes and lack visual cues and a simple API, but React Scan requires no code changes and highlights exactly the components you need to optimize.

### [Nue: A standards first web framework](https://nuejs.org/blog/standards-first-web-framework)

Nue is a new web framework that hopes to address the complexities of modern frontend development. The framework tackles two key issues: an over-reliance on JavaScript frameworks, which creates unnecessary complexity and technical debt, and the disconnect between design and engineering, which hinders creative design systems. Nue promotes a standards-first approach using HTML, Markdown, and modern CSS for cleaner, faster, and more maintainable code.

### [Standard Schema: Zod's biggest competitor?](https://www.youtube.com/watch?v=V1vMaNVwTaI)

While Zod has gained popularity, it has drawbacks including slower speed, Typescript performance issues, and incomplete adherence to validation standards. The standard schema aims to address these limitations and enhance the validation ecosystem for Typescript developers by enabling developers to use any validator they prefer without needing to install multiple validators.

### Quick links

- [Learn Yjs: Interactive tutorials](https://learn.yjs.dev/)
- [Thoughts on state management libraries in the React compiler era](https://blog.axlight.com/posts/thoughts-on-state-management-libraries-in-the-react-compiler-era/)
- [bippy: Hack into react internals](https://www.bippy.dev/)
- [CSS Variables editor](https://www.cssvariables.com/)

## Commentary

- [Why developers hate linters?](https://www.coderabbit.ai/blog/why-developers-hate-linters)
- [Will AI eat the browser?](https://crazystupidtech.com/archive/will-ai-eat-the-browser/)
- [HTML is actually a programming language. Fight me](https://www.wired.com/story/html-is-actually-a-programming-language-fight-me/)
