---
tags:
  - frontend
  - market-report
title: Frontend Report August 2024
description: A comprehensive August 2024 update on key advancements in React 19, Next.js 15, and web development tools. Highlights include new async transitions, server components, SSR performance comparisons, and emerging technologies in the web development landscape
date: 2024-09-09
authors:
  - mashiro5951
---

A comprehensive August 2024 update on key advancements in React 19, Next.js 15, and web development tools. Highlights include new async transitions, server components, SSR performance comparisons, and emerging technologies in the web development landscape.

# Core Stack

## React

### [React 19 RC: Async Transitions, Server Components, and Optimistic Updates](https://react.dev/blog/2024/04/25/react-19#whats-new-in-react-19)

React 19 introduces async transitions through Actions, improved error handling for hydration, and new hooks like `useOptimistic` for managing state. It enhances support for Server Components, integrates async scripts and resource preloading, and offers better tools for managing form submissions.

### [An SSR Performance Showdown](https://blog.platformatic.dev/ssr-performance-showdown)

This article compares the Server-Side Rendering (SSR) performance of major frontend libraries, including React, Vue, Svelte, Solid, and Preact, using Fastify. Vue led in performance, closely followed by Svelte and Solid, with React and Preact falling behind.

### [Essential React Libraries for 2024](https://www.robinwieruch.de/react-libraries/)

A handy guide to the best React libraries you should consider in 2024. It covers everything from state management tools like Zustand, to UI components like Tailwind CSS, and data-fetching libraries like TanStack Query. It’s all about streamlining your development and optimize performance with the latest trends in React.

### Quick Links

- [Build your own React state management library in under 40 lines of code](https://paripsky.github.io/blog/build-your-own-react-state-management/)
- [Managing Effects in React](https://ui.dev/c/react/effects): Understanding `useEffect`
- [Interface Segregation Principle in React](https://alexkondov.com/interface-segregation-principle-in-react/)
- [Everything About Google Translate Crashing React](https://martijnhols.nl/gists/everything-about-google-translate-crashing-react)
- [Implementing React from Scratch](https://www.rob.directory/blog/react-from-scratch)

## Next.js

### [Next.js 15 RC - Now Supporting React 19 RC](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-15-rc/amp)

Next.js 15 brings support for React 19 RC, along with better hydration error handling, caching improvements, and experimental features like the React Compiler and Partial Prerendering, allowing for incremental static and dynamic rendering.

### [Build Anything with v0 (3D Games, Interactive Apps)](https://www.youtube.com/watch?v=zA-eCGFBXjM)

A quick introduction to the new version of V0, showcasing its ability to create interactive apps and games.

### Quick Links

- [Vercel AI SDK 3.3](https://vercel.com/blog/vercel-ai-sdk-3-3)
- [Next.js + Supabase App in Production: Lessons Learned](https://catjam.fi/articles/next-supabase-what-do-differently)

## Others

### [State of CSS 2024 Is Now Open!](https://survey.devographics.com/en-US/survey/state-of-css/2024)

Want to calculate a square root or cosine in your CSS? Use that to build scroll-triggered animations? And maybe scope all of it down so it doesn't have any unwanted effects? Now you can do all that, and much more! This is an interesting survey to share your experiences and thoughts on the current trends in CSS.

### [JS Dates Are About to Be Fixed](https://docs.timetime.in/blog/js-dates-finally-fixed)

The [Temporal proposal](https://github.com/tc39/proposal-temporal) promises to simplify time zone handling, fix issues with UTC and local times, and add features like daylight saving time management and easy date comparisons.

### [MUI v6 Is Out!](https://mui.com/blog/material-ui-v6-is-out/)

MUI v6 introduces CSS theme variables, container queries, and performance improvements. The update reduces package size, stabilizes Grid v2, and introduces experimental features like Pigment CSS and React Server Components, fully compatible with React 19.

### Quick Links

- [Common Causes of Memory Leaks in JavaScript](https://www.trevorlasn.com/blog/common-causes-of-memory-leaks-in-javascript)
- [CSS Grid Areas: A Fresh Look](https://ishadeed.com/article/css-grid-area/)
- [Front-End Security Checklist](https://www.trevorlasn.com/blog/frontend-security-checklist)
- [When Regex Goes Wrong](https://www.trevorlasn.com/blog/when-regex-goes-wrong)
- [Why CSS-in-JS Can Be Slow](https://playfulprogramming.com/posts/why-is-css-in-js-slow)
- [Announcing TypeScript 5.6 RC](https://devblogs.microsoft.com/typescript/announcing-typescript-5-6-rc/)

# Trending

### [Top Programming Languages 2024: Typescript and Rust on the Rise](https://spectrum.ieee.org/top-programming-languages-2024)

Python reigns in AI and education, while SQL remains crucial for employers. Typescript's static typing increases reliability, and Rust's memory safety gains it a solid following. Meanwhile, C is declining, but legacy languages like Fortran and Cobol persist in niche areas.

### [e18e: Improving JS Performance One Package at a Time](https://e18e.dev/?ck_subscriber_id=2328911063)

e18e is a community project focused on cleaning up outdated dependencies, speeding up widely-used JavaScript packages, and leveling up the ecosystem with modern alternatives.

### [Introducing InformAI: Let Your LLMs See What Your Users See](https://edspencer.net/2024/8/26/introducing-inform-ai)

InformAI allows developers to expose UI and component data to large language models (LLMs) with a few lines of code, enabling smarter AI responses based on app state.

### Quick Links

- [Say No to console.log!](https://dev.to/alishgiri/say-no-to-consolelog-556n): Explore alternatives to `console.log`
- [Structured Outputs in the OpenAI API](https://openai.com/index/introducing-structured-outputs-in-the-api/)
- [GitHub Models: A New Generation of AI Engineers](https://github.blog/news-insights/product-news/introducing-github-models/)

# New Tools

### [Waku: Making React Development Fun Again](https://waku.gg/)

Waku offers a lightweight, fun alternative for React development in the server components era.

### [Formity: Build Complex, Multi-Step Forms with JSON](https://www.formity.app/)

Formity makes building dynamic, customizable forms easy by defining them with JSON. It simplifies complex form development with conditions, loops, variables, and operators.

### [Rspack 1.0: A High-Performance JavaScript Bundler](https://rspack.dev/blog/announcing-1-0)

Rspack 1.0, built in Rust, delivers significant performance improvements over webpack, offering compatibility with its ecosystem while being up to 10 times faster. It introduces key features such as better bundle size optimization, support for Module Federation 2.0, and stable APIs, with growing adoption from enterprises like ByteDance, Microsoft, and Amazon.

### Quick Links

- [Coolify: Open-Source Heroku/Netlify Alternative](https://coolify.io/)
- [Web Vitals Chrome Extension](https://chromewebstore.google.com/detail/web-vitals/ahfhijdlegdabablpippeagghigmibma)
- [React Email 3.0](https://resend.com/blog/react-email-3)

## Commentary

- [It’s Time to Talk About “CSS5”](https://www.smashingmagazine.com/2024/08/time-to-talk-about-css5/)
- [Microfrontends Should Be Your Last Resort](https://www.breck-mckye.com/blog/2023/05/Microfrontends-should-be-your-last-resort)
- [Japanese Web Design: Weird, But It Works](https://www.youtube.com/watch?v=vi8pyS076a8)
- [Practices of Reliable Software Design](https://two-wrongs.com/practices-of-reliable-software-design)
- [Why Micro-Libraries Should Die](https://bvisness.me/microlibraries)
- [The Secret Behind One Million Checkboxes](https://eieio.games/essays/the-secret-in-one-million-checkboxes)
- [Is Tailwind CSS Too Redundant?](https://www.reddit.com/r/webdev/comments/1f2abca/anyone_else_find_tailwind_css_a_bit_too_redundant/)
- [React: Is It Time to Move On?](https://www.youtube.com/watch?v=0tvfC9r9lcw)
