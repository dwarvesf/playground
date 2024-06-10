---
tags: null
title: Devcontainers
date: 2023-10-13
description: null
authors: null
confidence: High
assign: Tom X Nguyen
priority: 🌟 NEW , 🎯FOCUS
status: Trial
quadrant: Tools
tag: DevOps, Engineering
---

<!-- table_of_contents 4521d678-6c77-4478-9787-1c5f108fd675 -->

### Description
→ **Devcontainers** are a feature of Visual Studio Code that allow developers to use a container as a full-featured development environment. A **devcontainer.json** file in your project tells VS Code how to access (or create) a development container with a well-defined tool and runtime stack. This container can be used to run an application or to separate tools, libraries, or runtimes needed for working with a codebase. Workspace files are mounted from the local file system or copied or cloned into the container. Extensions are installed and run inside the container, where they have full access to the tools, platform, and file system. This means that you can seamlessly switch your entire development environment just by connecting to a different container. The Dev Containers extension supports two primary operating models: You can use a container as your full-time development environment or you can attach to a running container to inspect it.

### What’s better about this method or library
? We use Darwin (Mac) systems to run and develop our applications, meaning there are a set of particular quirks that we must include in development environments that satisfy these machines. However, this creates a particular cost of entry for new engineers that would face 2 indirect issues: purchase a Mac (that of which most of our team has migrated to Apple Silicon) or have our team supply a Mac for the engineer. 

On top of this, we also need to create extensive Makefiles and documentation in order to run our applications. Previously this was a non-issue, but as applications grow in size and complexity, so does the requirement of these documentations.

Devcontainers as a specification for containerizing developer environments means that we can automate installation, setup, and even runtime patterns inside containers to avoid the problem of “it runs on my machine”. We can achieve Day Zero onboarding and removing the friction and move our engineers from being solely frontend or backend engineers to more well-rounded full-stack engineers.

### What can we do with it
? Use it as a basis for a clean installation and to help new engineers onboard our projects.

### How should we adopt it
? Devcontainers only requires to be setup once by any senior engineer. Adding the `.devcontainer` folder to any project should not affect current setups and enables other engineers to interface it with Devcontainers, Codespaces, and DevPod setups.

<!-- child_database b2fbfe57-f42d-4e69-82e5-a13d9d207398 -->
