---
tags: 
  - devbox
  - nix
title: "Nix Shell: Isolated Development Environments"
date: 2024-08-01
description: An overview of Nix Shell, a command that provides isolated shell environments for development without affecting the host system
authors:
  - bievh
---
Nix Shell is essentially a command provided by Nix that drops us into an isolated shell environment. In this environment, we can perform any operation without mutating the global state of the host machine's system.

To achieve this, Nix is implemented in the following ways:

- First, packages are installed in an isolated, immutable directory called the Nix store, typically located at `/nix/store`. This approach prevents conflicts with other packages in the system.

- Second, Nix uses a unique hash to identify the version of each build (for both different applications and different versions of the same application). This means we can install multiple versions of the same application on our machine, but we can only use one version for building or running a shell. For example:

  ```BASH
  /nix/store/1fxz1flmv4a4m5pvjmmzxlaznjzybjcp-go-1.21.3/ for Golang 1.21.3
  /nix/store/i04a1a6qgxhjw6c0ld2b3x1v815sbxjc-go-1.22.3/ for Golang 1.22.3
  ```

- Nix can create isolated user environments where users can install packages without root privileges. These environments are specific to the user and do not interfere with the system or other users' environments. These environments can use or not use our global `$PATH` environment variable for different purposes:
  - To have a completely isolated environment for developing applications in a team, we should use the shell without the global `$PATH` for consistency across team members' machines.
  - To use Nix Shell as our main shell, we should inherit the global `$PATH` to take advantage of our available applications.

---
#### References
*shell - Nix Reference Manual*. (n.d.). nix.dev. Retrieved July 23, 2024, from https://nix.dev/manual/nix/2.22/command-ref/nix-shell
*Why You Should Give it a Try - Nix Pills*. (n.d.). NixOS. Retrieved July 23, 2024, from https://nixos.org/guides/nix-pills/01-why-you-should-give-it-a-try
