---
tags:
  - frontend
  - market-report
title: Frontend Report January 2025
short_title: "January 2025"
description: This January 2025 report explores key frontend advancements, including React 19's Actions, Next.js 15.1's Deno Deploy support, and innovative tools like Transformers.js for AI. Discover trending technologies, best practices, and expert commentary shaping the future of frontend development.
date: 2025-01-20
authors:
  - hthai2201
---

## React

### [React 19 is officially here](https://react.dev/blog/2024/12/05/react-19)

The moment we've all been waiting for! React 19 has officially landed. React 19 is here with game-changing features! Actions simplify state management with built-in handling for errors and optimistic updates. New hooks like useOptimistic and useActionState make development smoother than ever. Plus, enhanced Suspense boosts performance for better user experiences. Dive into the future of React now!

### [React 19: Ref callbacks - More than just DOM access](https://tkdodo.eu/blog/ref-callbacks-react-19-and-the-compiler)

Ref callbacks in React 19 can now return cleanup functions, similar to useEffect, allowing for tasks like measuring DOM nodes with ResizeObserver. While ref callbacks are useful for accessing nodes, useEffect is better suited for side-effects unrelated to the node, and Tanstack React Query should be used for async operations.

### [View Transition API: Smooth animations coming to React](https://motion.dev/blog/reacts-experimental-view-transition-api)

Explore React's experimental View Transition API and how it can create smoother, more engaging user experiences. This article dives into the details, showing practical examples and offering insights on how to utilize this feature in your own projects.

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

### [New HTML and CSS features: Making interactive elements easier without JavaScript](https://zeroheight.com/blog/the-lowdown-on-dropdowns-in-html-css/)

The popover attribute allows developers to add popovers effortlessly, while CSS Anchoring offers more reliable positioning. The new calc-size() function makes it possible to animate elements to and from auto height, bringing more flexibility to animations. Plus, updates to `<details>` and `<select>` elements enhance their styling and customization capabilities. These innovations make building interactive and dynamic web elements smoother and more accessible than ever before.

### [Lock down your OAuth2 implementations - protect against CSRF attacks](https://auth0.com/blog/prevent-csrf-attacks-in-oauth-2-implementations)

Secure your OAuth2 implementations against Cross-Site Request Forgery (CSRF) attacks with this comprehensive guide. This article explains what CSRF attacks are, how they work, and provides practical strategies to prevent them. It’s a crucial read for any developer using OAuth2 to safeguard user data and ensure application security.

### Quick Links

- [Headless, Boneless, Skinless, & Lifeless UI: 4 categories of UI abstractions](https://nerdy.dev/headless-boneless-and-skinless-ui)
- [A simple masonry-like composable layout](https://piccalil.li/blog/a-simple-masonry-like-composable-layout)
- [Architectures of modern front-end applications](https://blog.meetbrackets.com/architectures-of-modern-front-end-applications-8859dfe6c12e)

## Trending

### [Rising stars of JavaScript 2024](https://risingstars.js.org/2024/en)

Stay ahead of the curve by exploring the most promising and trending JavaScript projects of 2024! This site showcases the libraries, frameworks, and tools that are gaining popularity. It's an excellent resource for discovering new technologies and keeping up with the latest trends in the JavaScript ecosystem. A must-visit for any JavaScript enthusiast.

### [Offline-first apps: everything you need to know to get started!](http://devstarterpacks.com/blog/what-every-developer-should-know-about-offline-first-apps)

Learn the essentials of building offline-first applications in this guide. It covers the core concepts, techniques, and best practices for creating apps that function seamlessly even when the internet connection is unreliable. This article will help you understand data synchronization, caching, and handling user interactions in an offline environment.

### [Level up your CSS game with these 12 one-liners!](https://moderncss.dev/12-modern-css-one-line-upgrades)

Discover 12 incredibly useful and powerful CSS techniques that you can implement with just a single line of code each! Enhance your layouts, optimize for responsiveness, and create cool visual effects with these practical and efficient tips.

### Quick Links

- [My Go-To React tech stack for 2025](https://www.robinwieruch.de/react-tech-stack/)
- [Top 5 CSS features of 2024: Level up your styles!](https://bytes.dev/archives/351)
- [Isomorphic web components: Overcoming SSR challenges](https://jakelazaroff.com/words/isomorphic-web-components)

## Tools

### [Thinking of switching to Vite? this team did it and here's what they learned!](https://neon.tech/blog/from-webpack-to-vite)

A team shares their firsthand experience of migrating from Webpack to Vite, detailing their entire journey from planning to implementation, along with any hurdles they faced and the positive outcomes they achieved. This is an insightful read for anyone considering a build tool change, providing a real-world perspective on what to expect during such a migration and the benefits that Vite can offer.

### [Tailwind CSS v4.0 Beta: New features, concerns, and what you should know](https://nmn.sh/blog/2024-11-30-thoughts-on-tailwind-4)

Tailwind CSS v4 has great improvements like the switch to LightningCSS and native CSS cascade layers, but this author has concerns about the performance implications of CSS variables, the potential for abuse with new descendant variants, and the lack of clarity in some class names.

### [Node’s new built-in support for TypeScript](https://2ality.com/2025/01/nodejs-strip-type.html)

Big news for Node.js developers! Native TypeScript support is on the way through type stripping, meaning you'll soon be able to run TypeScript code directly in Node without needing to transpile it first. This article explains the implications, outlining what this change means for development workflows and how it will streamline the use of TypeScript within Node.js projects. A crucial read for anyone in the Node.js ecosystem.

### [Boost React performance with Million](https://million.dev/)

Million is a lightweight tool designed to optimize React websites by identifying slow components and improving performance and integrates directly into your IDE for real-time performance insights. Million also provides features like production observability and replay for investigating performance issues.

### Quick links

- [React, visualized: An interactive guide to understanding React concepts](https://react.gg/visualized)
- [Onlook: The open-source Figma for React that lets you design in real-time](https://onlook.dev)

## Commentary

- [Why I ditched React for Go, HTMX, and Templ](https://blog.erodriguez.de/dependency-management-fatigue-or-why-i-forever-ditched-react-for-go-htmx-templ)
- [React and similar frontend frameworks, used incorrectly, can lead to performance and accessibility issues.](https://infrequently.org/2024/11/if-not-react-then-what)
- [The open social web is the future of the internet. Here's why I'm excited](https://werd.io/2024/the-open-social-web-is-the-future-of-the-internet)
- [Struggling with complex code? see how Types can simplify things!](https://mayhul.com/posts/type-driven-design)
