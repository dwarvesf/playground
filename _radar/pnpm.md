---
tags: null
title: Pnpm
date: null
description: null
authors: null
confidence: null
assign: Toan Ho
priority: null
status: Adopt
quadrant: Tools
tag: Frontend
---

<!-- table_of_contents b574801d-0144-447a-8f85-5dc94d17ebc7 -->

### Description
A package manager for JavaScript that aims to improve the performance of the installation process and reduce disk space usage. It uses a unique approach to store dependencies in a shared store, rather than installing them multiple times for different projects. pnpm supports features such as multi-registry support, global installation, and zero-disk installations.

> *pnpm's unique approach to dependency management is based on the concept of a "shared store." Instead of installing each dependency separately in each project directory, pnpm creates a single, centralized store where all packages are installed. When a project requires a package, pnpm creates a symbolic link from the project's *`***node_modules***`* directory to the shared store. This means that multiple projects can share the same copy of a package, which can help to reduce disk usage and avoid redundancies.*

### What’s better about this method or library
1. Improved installation performance: pnpm's unique approach to dependency management can significantly reduce installation times, especially for monorepo projects with many dependencies.
1. Reduced disk usage: by using a shared store to manage dependencies, pnpm can help to reduce disk usage and avoid redundancies.
1. Monorepo support: pnpm provides features such as automatic workspace detection, parallel installation, and selective installation, which can make it a good choice for managing dependencies in monorepo projects.
1. Multi-registry support: pnpm can be configured to work with multiple registries, which can be useful for projects that rely on both public and private packages.
1. Zero disk installation: pnpm can install packages without creating any files on disk, which can be useful for quickly trying out new packages or testing different configurations.

### What can we do with it
From a business standpoint:

1. Improved development efficiency:  help to install packages more quickly and efficiently, reducing the time and effort required to set up new projects or make changes to existing ones.
1. Reduced infrastructure costs: by using a shared store to manage dependencies, help to reduce the amount of disk space required to store packages, potentially reducing the need for expensive storage infrastructure.
1. Better scalability: pnpm's monorepo support and other features can make it easier to manage large and complex projects
1. Increased flexibility: pnpm's support for multiple registries and package formats can make it easier to work with a wide range of third-party packages and tools

### How should we adopt it
* Research blog posts for a better understanding of the concepts and principles behind, and also help to educate others in the team
* Case studies into existing projects that already applied this
* POC/Boilerplate that uses pnpm, bonus point if we also uses monorepo

<!-- child_database 36feff7c-7c54-4ae8-a386-4fbd835ce444 -->
