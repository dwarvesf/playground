---
tags: 
  - nix
  - docker
  - devbox
title: "Nix - Minimum changes, Minimum redundancies"
date: 2024-08-01
description: An overview of how Nix addresses issues like shadow copies in Docker builds, improving build efficiency and speed
authors:
  - bievh
---
The reproducible issue is resolved in the [previous part](./≈%20Nix%20-%20Build%20the%20same%20thing%20at%20any%20time.md). But we still have another problem when using Docker build, it is shadow copies. This issue comes from the underutilization of Content-addressable storage in Docker of Docker build. It even lets build time slower.

- [Content-addressable storage in Docker](./Content-addressable%20storage%20in%20Docker.md)
- [Nix is faster than Docker build](./Nix%20is%20faster%20than%20Docker%20build.md)
