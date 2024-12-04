---
tags:
  - frontend
  - market-report
title: Frontend Report Second Half of November 2024
short_title: "Nov 2024 (Second Half)"
description: A second half of November 2024 frontend development digest covering major updates to React Router v7, Tailwind CSS v4 Beta, and Vite 6.0, along with new tools and frameworks focused on improved performance, cross-platform development, and developer experience.
date: 2024-11-30
authors:
  - hthai2201
---

A second half of November 2024 frontend development digest covering major updates to React Router v7, Tailwind CSS v4 Beta, and Vite 6.0, along with new tools and frameworks focused on improved performance, cross-platform development, and developer experience.

## React

### [React Router v7: New features and flexible development options](https://remix.run/blog/react-router-v7)

React Router v7 introduces `framework mode` with features from Remix, including server rendering and improved type safety. It also includes enhanced templates for starting new projects, and comprehensive upgrade guides for React Router v6 and Remix v2 users.

### [React Anti-Pattern: Stop Passing Setters Down the Components Tree](https://matanbobi.dev/posts/stop-passing-setter-functions-to-components)

Passing `useState` setters as props can lead to abstraction leaks, reducing clarity and reusability, making it harder to reason about the state. A better approach is to use callback functions to handle state changes, making your code more maintainable and flexible.

### Quick links

- [React Server Components vs. SSR: 5 key differences](https://www.tymzap.com/blog/5-differences-between-react-server-components-and-server-side-rendering)
- [React Portals: Escaping the DOM hierarchy](https://techhub.iodigital.com/articles/what-are-react-portals)
- [Tremor: React components for dashboards & charts](https://tremor.so/)

## Next.js

### [Next Cloudinary: A game-changer for client-side file handling](https://robiul.dev/next-cloudinary-a-game-changer-for-client-side-file-handling)

Next Cloudinary is a flexible tool that simplifies file handling and image optimization in Next.js applications. It supports various file sources like Google Drive and offers advanced image effects, real-time adjustments, video transformations, watermarking and responsive rendering.

### [Solito 4.3: Bridge the gap between React Native and Next.js](https://solito.dev)

Solito enables seamless development of universal React Native and web applications by sharing components and navigation across platforms. Built to integrate with Expo and Next.js, it ensures high performance and a consistent user experience across mobile and web.

### Quick links

- [Payload 3.0: A Next.js-Native CMS](https://payloadcms.com/blog/payload-30-the-first-cms-that-installs-directly-into-any-nextjs-app)

## Others

### [Building React forms with ease using React Hook Form, Zod and Shadcn](https://wasp-lang.dev/blog/2024/11/20/building-react-forms-with-ease-using-react-hook-form-and-zod)

React Hook Form, Zod, and Shadcn can be used to create adaptable forms with ease. A Zod validation schema defines validation rules, while React Hook Form manages form state and validation. Shadcn provides reusable UI components with built-in support for React Hook Form and Zod.

### [Mastering JavaScript Symbols: Unique keys, custom behaviors, and advanced usages](https://www.trevorlasn.com/blog/symbols-in-javascript)

Delve into JavaScript Symbols, the powerful tool for creating unique property keys and enabling custom behaviors in your objects. Explore practical applications, from controlling primitive conversions with `Symbol.toPrimitive` to building specialized arrays with `Symbol.species`. Learn about their uniqueness, serialization quirks, and how `Symbol.for()` enables global sharing. Perfect your JavaScript knowledge with these essential insights!

### [A simple guide to importing JavaScript libraries without a build system](https://jvns.ca/blog/2024/11/18/how-to-import-a-javascript-library/)

This guide walks you through importing JavaScript libraries like Chart.js and @atcute/oauth-browser-client, covering global variables, ES modules, and CommonJS. It explores using UMD files, ES modules with importmaps, and converting CommonJS modules, highlighting challenges and the importance of a build step for dependency updates.

### Quick links

- [Essential TypeScript for React: Quick productivity tips](https://www.jacobparis.com/content/react-ts)
- [Easy Light/Dark Modes: No fuss!](https://frontendmasters.com/blog/no-fuss-light-dark-modes/)

## Trending

### [Tailwind CSS v4 Beta: Built for speed and modern web development](https://tailwindcss.com/blog/tailwindcss-v4-beta)

Tailwind CSS v4 Beta introduces a revolutionary engine with 5x faster full builds and 100x faster incremental builds. Enjoy a unified toolchain, CSS-first configuration, and modern web features like cascade layers, container queries, and popovers.

### [Vite 6.0: Faster, simpler, more extensible!](https://vitejs.dev/blog/announcing-vite6/)

Vite 6 brings groundbreaking updates, including a 10M+ weekly npm downloads milestone, faster builds, and a new experimental Environment API for better development experiences. With modern features, broader framework support, and seamless upgrades, it's the most significant release since Vite 2.

### Quick links

- [Building Reddit's frontend with Vite](https://www.reddit.com/r/RedditEng/comments/1dhztk8/building_reddits_frontend_with_vite/)
- [Vitest vs. Jest: The ultimate showdown](https://www.speakeasy.com/post/vitest-vs-jest)
- [Framer Motion goes solo: New adventures in animation!](https://motion.dev/)

## New Tools

### [Extism: Unlocking WebAssembly for everyone](https://extism.org/)

Extism is a lightweight, universal framework for building with WebAssembly (Wasm), supporting its use across various platforms. It offers a flexible, plug-in system designed to make all software programmable.

### Quick links

- [SmarkForm: Effortless markup-driven and extendable forms](https://smarkform.bitifet.net/)
- [SVG to Font generator](https://wangchujiang.com/svgtofont/)
- [Nova: A JavaScript engine built with Rust](https://trynova.dev/)

## Commentary

- [Which IDEs do devs actually love? (And why!)](https://substack.com/redirect/cd81c4f0-4acd-4366-b3d4-896fe33c2d65)
- [Web platform challenges](https://bkardell.com/blog/debt.html)
- [An Elixir/Elm dev's take on React](https://korban.net/posts/elm/2024-11-16-typescript-react-impressions/)
- [PostHog's Engineering: Solving challenges with trust and future-focused tech decisions](https://dub.link/bytes-nov25)
