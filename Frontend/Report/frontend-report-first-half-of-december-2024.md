---
tags:
  - frontend
  - market-report
title: Frontend Report First Half of December 2024
short_title: "Dec 2024 (First Half)"
description: A comprehensive update on key advancements in frontend development for the first half of December 2024, highlighting official release of React 19 and the cool updates in Next.js 15.1, along with some innovative tools that are making waves in the industry.
date: 2024-12-18
authors:
  - hthai2201
---

## React

### [React 19 is officially here](https://react.dev/blog/2024/12/05/react-19)

The moment we've all been waiting for! React 19 has officially landed. React 19 is here with game-changing features! Actions simplify state management with built-in handling for errors and optimistic updates. New hooks like useOptimistic and useActionState make development smoother than ever. Plus, enhanced Suspense boosts performance for better user experiences. Dive into the future of React now!

### [React 19: Ref callbacks - More than just DOM access](https://tkdodo.eu/blog/ref-callbacks-react-19-and-the-compiler)

Ref callbacks in React 19 can now return cleanup functions, similar to useEffect, allowing for tasks like measuring DOM nodes with ResizeObserver. While ref callbacks are useful for accessing nodes, useEffect is better suited for side-effects unrelated to the node, and Tanstack React Query should be used for async operations.

### Quick Links

- [Mastering React internationalization with i18next](https://lingual.dev/blog/getting-more-out-of-i18next-in-react/)
- [Boost React app speed with INP optimization](https://kurtextrem.de/posts/improve-inp-react)

## Next.js

### [Next.js 15.1 embraces React 19!](https://nextjs.org/blog/next-15-1)

Next.js 15.1 is here, embracing React 19 with official support! Enjoy seamless integration, enhanced debugging tools, and smarter error handling for a smoother development experience.

### [Next.js on Deno deploy: A new frontier](https://deno.com/blog/nextjs-on-deno-deploy)

Next.js SSR apps can now run on Deno Deploy. It’s fast, scalable, and a glimpse into the future of serverless tech.

### [Scaling micro-frontends with Next.js multi zones](https://techhub.iodigital.com/articles/building-scalable-micro-frontends-with-next-js-multi-zones)

Managing independent deployments for large teams just got easier! Next.js multi zones make building scalable micro-frontends a breeze.

### Quick Links

- [Introducing efficient Valkey-based caching for Next.js](https://blog.platformatic.dev/introducing-efficient-valkey-based-caching-for-nextjs)
- [SSR: Debunking myths and delivering real value](https://t3.gg/blog/post/ssr-is-not-expensive)
- [Why Dato CMS chose Astro over Next.js](https://www.datocms.com/blog/why-we-switched-to-astro)

## Others

### [Bring AI to your browser with Transformers.js](https://www.raymondcamden.com/2024/12/03/using-transformersjs-for-ai-in-the-browser)

Run AI tasks right in the browser! Transformers.js leverages a pipeline API that is easy to use and can perform tasks like sentiment analysis and object detection. All processing occurs client-side, no server needed

### [Architectures of modern front-end applications](https://blog.meetbrackets.com/architectures-of-modern-front-end-applications-8859dfe6c12e)

This article goes over various front-end application architectures. The `classic` approach organizes projects into basic folders like pages, components, and helpers, but can quickly become chaotic and hard to maintain as the app scales. The `modular` approach divides applications into layers (pages, modules, components, and UI), making sure of encapsulated logic and clear separation of responsibilities. The `feature-sliced design` approach is a more refined modular approach that structures the project by functional features instead of layers.

### [New HTML and CSS features: Making interactive elements easier without JavaScript](https://zeroheight.com/blog/the-lowdown-on-dropdowns-in-html-css/)

The popover attribute allows developers to add popovers effortlessly, while CSS Anchoring offers more reliable positioning. The new calc-size() function makes it possible to animate elements to and from auto height, bringing more flexibility to animations. Plus, updates to `<details>` and `<select>` elements enhance their styling and customization capabilities. These innovations make building interactive and dynamic web elements smoother and more accessible than ever before.

### Quick Links

- [Headless, Boneless, Skinless, & Lifeless UI: 4 categories of UI abstractions](https://nerdy.dev/headless-boneless-and-skinless-ui)

## Trending

### [Tailwind CSS v4.0 Beta: New features, concerns, and what you should know](https://nmn.sh/blog/2024-11-30-thoughts-on-tailwind-4)

Tailwind CSS v4 has great improvements like the switch to LightningCSS and native CSS cascade layers, but this author has concerns about the performance implications of CSS variables, the potential for abuse with new descendant variants, and the lack of clarity in some class names.

### [Top 5 CSS features of 2024: Level up your styles!](https://bytes.dev/archives/351)

Check out the 5 hottest CSS features of 2024! From animating heights to scroll-driven magic, it's time to make your webpages pop.

### [Isomorphic web components: Overcoming SSR challenges](https://jakelazaroff.com/words/isomorphic-web-components)

While basic web components (using `template` and custom elements) can be easily rendered on the server, true isomorphic rendering (running the same code client-side and server-side) requires more sophisticated techniques. Libraries like Lit and Enhance offer SSR capabilities, but often introduce dependencies and deviate from `vanilla` web component development. Instead, a direct isomorphic approach using a DOM emulator like Happy DOM is probably better.

### Quick Links

- [Tailwind CSS hits 1 billion downloads!](https://bsky.app/profile/adamwathan.com/post/3lcxcb73yfk2i)
- [My Go-To React tech stack for 2025](https://www.robinwieruch.de/react-tech-stack/)

## Tools

### [Onlook: The open-source Figma for React that lets you design in real-time](https://onlook.dev)

Onlook is an open-source tool designed for visually editing React applications, similar to Figma. It allows users to design and modify React UI components in real-time while writing changes directly to the code. Currently in alpha, it supports React apps styled with Tailwind and enables seamless code integration. Onlook aims to streamline design-to-code workflows, with a focus on security and flexibility for developers, ensuring that all code remains local and version-controlled.

### [Boost React performance with Million](https://million.dev/)

Million is a lightweight tool designed to optimize React websites by identifying slow components and improving performance and integrates directly into your IDE for real-time performance insights. Million also provides features like production observability and replay for investigating performance issues.

### Quick links

- [React, visualized: An interactive guide to understanding React concepts](https://react.gg/visualized)
- [InclusiveColors: Create accessible color palettes with ease](https://www.inclusivecolors.com)

## Commentary

- [Why I ditched React for Go, HTMX, and Templ](https://blog.erodriguez.de/dependency-management-fatigue-or-why-i-forever-ditched-react-for-go-htmx-templ)
- [React and similar frontend frameworks, used incorrectly, can lead to performance and accessibility issues.](https://infrequently.org/2024/11/if-not-react-then-what)
- [The open social web is the future of the internet. Here's why I'm excited](https://werd.io/2024/the-open-social-web-is-the-future-of-the-internet)
