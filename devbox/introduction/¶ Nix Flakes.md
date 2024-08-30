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

Enough theory, let's look at an example of using flakes in practice. Basically, I want to serve my Backend server using a PostgreSQL database that supports the TimescaleDB extension. However, when searching around, I could only find empty PostgreSQL packages without TimescaleDB. So, I wrote a flake to customize the PostgreSQL database with TimescaleDB attached inside. With `postgresql_15` and the package `postgresql15Packages.timescaledb` at [Nixpkgs Githib repository](https://github.com/NixOS/nixpkgs), we can build a flake as following. 

```nix
{
  description = "A flake that adds the timescaledb extension to Postgresql";

  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";
    flake-utils.url = "github:numtide/flake-utils";
  };

  outputs = { self, nixpkgs, flake-utils }:
    flake-utils.lib.eachDefaultSystem (system:
      let
        pkgs = import nixpkgs {
          inherit system;
          config.allowUnfree = true;
        };
        psqlExtensions = [
          "timescaledb"
        ];
      in {
        packages = {
          postgresql = pkgs.postgresql_15.withPackages (ps:
              (map (ext: ps."${ext}") psqlExtensions));
        };

        defaultPackage = self.packages.${system}.postgresql;
      });
}
```

Let's break it down:

1. Description:
   The flake is described as adding the TimescaleDB extension to PostgreSQL.

2. Inputs:
   - `nixpkgs`: Points to the unstable branch of the Nixpkgs repository.
   - `flake-utils`: A utility library for working with flakes.

3. Outputs:
   The `outputs` function takes the inputs and returns a set of derivations for each default system supported by flake-utils.

4. For each system:
   - It imports `nixpkgs` with `allowUnfree = true`, which allows the use of non-free packages if needed.
   - Defines `psqlExtensions` as a list containing only "timescaledb".

5. Packages:
   - Defines a `postgresql` package using PostgreSQL 15.
   - Uses `withPackages` to customize PostgreSQL, adding the extensions listed in `psqlExtensions`.
   - The `map` function is used to convert each extension name to its corresponding package in the PostgreSQL package set.

6. Default Package:
   Sets the default package for this flake to be the customized PostgreSQL package.

In essence, this flake provides a way to easily create a PostgreSQL 15 installation with the TimescaleDB extension pre-installed. Users of this flake can simply reference it to get a PostgreSQL setup with TimescaleDB support without having to manually configure the extension.

---
#### References
*Flakes — nix.dev documentation*. (n.d.). nix.dev. Retrieved July 23, 2024, from https://nix.dev/concepts/flakes.html
*nix flake - Nix Reference Manual*. (n.d.). nix.dev. Retrieved July 23, 2024, from https://nix.dev/manual/nix/2.22/command-ref/new-cli/nix3-flake
*Can someone explain to me what a flake is like I'm 5?* : r/NixOS. (2023, April 28). Reddit. Retrieved July 23, 2024, from https://www.reddit.com/r/NixOS/comments/131fvqs/can_someone_explain_to_me_what_a_flake_is_like_im/
