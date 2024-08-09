---
tags: 
  - nix
  - docker
  - devbox
title: "Content-addressable Storage in Docker"
date: 2024-08-01
description: An overview of Docker's content-addressable storage model and its limitations in Docker build
authors:
  - bievh
---
For your information if you don't know or just forget that Docker image is layered. Each instruction in Dockerfile lets a separate layer be built. 

Introduced from Docker 1.10, the content addressable storage model gives Docker the ability to more efficiently store built layers by identifying them by a hash of its content. However, it is not used effectively in Docker build.

Docker writes about Docker build cache [here](https://docs.docker.com/guides/docker-concepts/building-images/using-the-build-cache/) as follows. 

> When you run the docker build command to create a new image, Docker executes each instruction in your Dockerfile, creating a layer for each command and in the order specified. For each instruction, Docker checks whether it can reuse the instruction from a previous build. If it finds that you've already executed a similar instruction before, Docker doesn't need to redo it. Instead, it'll use the cached result.

Clearly, the Docker build executes instructions in the Dockerfile sequentially. Each instruction creates a new layer once the content of the instruction is not changed. It means instead of knowing the content of the layer, Docker build just only detects the changes depending on the changes of commands such as RUN, COPY, etc. Then it invalidates this layer and every layer behind it.

Can't say it is bad or not. In practice, we have some ways to resolve it with Docker. But the use of Nix is more effective.

---
#### References
*Using the build cache.* (n.d.). Docker Docs. Retrieved August 2, 2024, from https://docs.docker.com/guides/docker-concepts/building-images/using-the-build-cache/
