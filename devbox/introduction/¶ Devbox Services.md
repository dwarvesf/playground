---
tags: 
  - devbox
title: "Devbox Services: Managing Daemon Applications with process-compose"
date: 2024-08-01
description: An overview of Devbox Services, which uses process-compose to manage daemon applications in a non-containerized environment
authors:
  - bievh
---
Docker has `docker-compose`, Nix has `process-compose`, both of them are used as scheduler and orchestrator to manage daemon applications. For example: running postgresql locally, to serve your backend. But `process-compose` is non-containerized.

`process-compose` is highly recommended when you don't want to deal with docker files, volume definitions, networks and docker registries.

Devbox provides more simple and user-friendly way to use `process-compose` to manager daemon applications, and call it is `devbox services`. 

As `docker-compose.yml`, you can define `process-compose.yml` in your root directory of your project. For example:
