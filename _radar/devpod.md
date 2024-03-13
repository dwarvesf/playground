---
tags: null
title: Devpod
date: null
description: null
authors: null
menu: radar
type: null
hide_frontmatter: false
confidence: null
assign: null
priority: null
status: Assess
quadrant: Tools
tag: null
---

<!-- table_of_contents f9784ea6-bc24-4b76-a097-e07b6e0cec47 -->

### Description
→ 

**Devpod** is a client-only tool that allows developers to create reproducible development environments based on a **devcontainer.json** file on any backend. Each developer environment runs in a container and is specified through a devcontainer.json. Through Devpod providers, these environments can be created on any backend, such as the local computer, a Kubernetes cluster, any reachable remote machine, or in a VM in the cloud. You can think of Devpod as the glue that connects your local IDE to a machine where you want to develop on. So depending on the requirements of your project, you can either create a workspace locally on the computer, on a beefy cloud machine with many GPUs or a spare remote computer. [Within Devpod, every workspace is managed the same way, which also makes it easy to switch between workspaces that might be hosted somewhere else](https://github.com/loft-sh/devpod).

Devpod is an extension of devcontainers, that allow seamless deployment of developer environments not just locally, but also on managed servers and providers.

### What’s better about this method or library
? Devpods extend and simplify devcontainers for developers, making it easier run developer environments locally or on the cloud. This means we can simplify resource and security management of developer environments for certain projects.

### What can we do with it
? 

### How should we adopt it
? Similar to devcontainers, we only need to setup a `.devcontainer` folder once and it should be available for use with Devpod. 

<!-- child_database c91c99c6-6058-4b39-8182-62e092c5b19a -->
