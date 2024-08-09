---
tags: 
  - devbox
  - nix
title: "Nix Flakes: Reproducible and Discoverable Nix Packages"
date: 2024-08-01
description: An overview of Nix Flakes, a feature that allows for creating reproducible and discoverable Nix packages
authors:
  - bievh
---
A Flake is essentially a file system managed by a file named `flake.nix` that we can modify. Additionally, a `flake.lock` file is used to lock dependency versions. This structure is similar to `package.json` and `package-lock.json` in the Node.js ecosystem.

Imagine we have application source code that we want to expose as a Nix package for others to use in a reproducible and discoverable way, without worrying about incompatibility or build issues. Nix Flakes allows us to do that.

By defining `flake.nix`, we can not only specify information about all the dependencies we need to run our application as the input of the flake, but also decide what the output of our flake will be, based on our source code.

Finally, our application can be fetched and used by other Nix packages freely.

---
#### References
*Flakes — nix.dev documentation*. (n.d.). nix.dev. Retrieved July 23, 2024, from https://nix.dev/concepts/flakes.html
*nix flake - Nix Reference Manual*. (n.d.). nix.dev. Retrieved July 23, 2024, from https://nix.dev/manual/nix/2.22/command-ref/new-cli/nix3-flake
*Can someone explain to me what a flake is like I'm 5?* : r/NixOS. (2023, April 28). Reddit. Retrieved July 23, 2024, from https://www.reddit.com/r/NixOS/comments/131fvqs/can_someone_explain_to_me_what_a_flake_is_like_im/
