---
tags: null
title: React Server Component
date: null
description: null
authors: null
confidence: null
assign: Chinh Le
priority: null
status: Assess
quadrant: Frameworks
tag: Frontend
---

<!-- table_of_contents b596fd58-9f87-442b-bfaa-20487549c3ef -->

### Description
React Server Components (RSCs) offer the flexibility to decide where to render components based on their purpose, diverging from the client-side rendering approach of Single-Page Applications. By breaking down the page into smaller components, it becomes evident that many components are non-interactive and can be rendered on the server as Server Components. This can improve performance, reduce bundle size and also improve the initial page loading time.

### What’s better about this method or library
RSCs offer several advantages over traditional methods of handling server-side rendering in React applications.

* Better separation of concerns between the server and the client, as server-side components can be written independently of the client-side code.
* Improve the application's performance, as pre-rendered HTML can be sent to the client more quickly than if rendered on the client-side.
* Easier to maintain and update the application, as server-side components can be changed without affecting the client-side code.

### What can we do with it
Using RSC with Next.js can bring several benefits to your application, such as:

* Improved performance: reduce the amount of data that needs to be transferred between the server and the client, as well as the amount of code that needs to be parsed and executed on the client. This can result in faster page loads and better user experience.
* Reduced bundle size: this allows you to move large dependencies or logic that are only needed on the server to RSC files, which are not included in the client bundle. This can reduce the size of your client-side code and improve performance and caching.
* Simplified data fetching: eliminate the need for using APIs or fetching data on the client for some parts of your application via access directly to backend resources. This can simplify your code, reduce dependencies complexity, errors and keep sensitive information on the backend.

### How should we adopt it
?

<!-- child_database d54a8aab-7ff8-4731-a327-9b09a25ff1f4 -->
