---
tags: 
  - devbox
title: "Running Your Own Shell with Devbox"
date: 2024-08-01
description: A guide on how to run and manage your own shell environment using Devbox, both globally and locally within a project
authors:
  - bievh
---
Once we installed Devbox using `curl -fsSL https://get.jetify.com/devbox | bash`, we can run our own shell in two ways global or local inside our specific project.

#### Devbox Local
The goal of this usage is to create an isolated development environment or a separate shell which we can install/execute anything without mutating the global state of the system of the host machine.

Devbox has 2 files to manage our shell: `devbox.json` and `devbox.lock`. It looks similar to [¶ Nix Shell](../introduction//¶%20Nix%20Shell.md). `devbox.json` is a JSON file that contains information about our environment. `devbox.lock` is a lock file that contains information about our environment.

To create them automatically, we can use the `devbox init` command.
```
> cd path/to/Wer/project
> devbox init
```

Then search and add any package we want to install to execute in our shell by `devbox search` and `devbox add` commands.
```
> devbox search go

Found 49+ results for "go":

* go  (1.23rc2, 1.23rc1, 1.22.5, 1.22.3, 1.22.2, 1.22.1, 1.22.0, 1.22rc2, 1.21.12, 1.21.11 ...)
* go-2fa  (1.2.0, 1.1.0)
* go-audit  (1.2.0, 1.1.1, 1.0.0)
* go-autoconfig  (2022-08-03)
* go-bare  (0-unstable-2021-04-06)
* go-bindata  (4.0.2, 3.24.0, 3.23.0, 3.22.0, 2015-10-23)
* go-callvis  (0.7.0)
* go-camo  (2.5.1, 2.5.0, 2.4.13, 2.4.12, 2.4.11, 2.4.10, 2.4.9, 2.4.8, 2.4.5, 2.4.4 ...)
* go-check  (2018-12-24, 2018-09-12)
* go-chromecast  (0.3.1, 0.2.12, 0.2.11, 0.2.10, 0.2.9, 0.2.8, 0.2.7, 0.2.6, 0.2.5)

Warning: Showing top 10 results and truncated versions. Use --show-all to show all.

> devbox add go
Info: Adding package "go@latest" to devbox.json
```

After all the above steps, we receive the following JSON file at the root of the project with `go@latest` listed in the `packages` array. The other is just a part of the initial JSON file that we will go on later.
```
{
  "$schema":  "https://raw.githubusercontent.com/jetify-com/devbox/0.12.0/.schema/devbox.schema.json",
  "packages": ["go@latest"],
  "shell": {
    "init_hook": [
      "echo 'Welcome to devbox!' > /dev/null"
    ],
    "scripts": {
      "test": [
        "echo \"Error: no test specified\" && exit 1"
      ]
    }
  }
}
```

Finally, using `devbox shell` to start the shell.

> Side Note: `devbox shell` is actually use a global ENV variables. To make it completely isolated, we need to use `devbox shell --pure` command. If this flag is specified, devbox creates an isolated shell inheriting almost no variables from the current environment. A few variables, in particular HOME, USER and DISPLAY, are retained.

#### Devbox Global
Once we want to use Devbox as our primary package manager, we can use this way.

Simple to say it is similar to local usage except putting the `devbox.json` and `devbox.lock` to the root of the machine. Under the hood, it is similar, we can do everything manually. But it is not recommended.

We know that except for dependencies, a shell has its ENV variables. And Devbox also has its own ENV variables. So firstly we need to merge all of them by `devbox global shellenv` command. But actually, we don't want to manually run it each time open the terminal. So we can add the following command to our `~/.*rc` files such as `~/.zshrc`, `~/.bashrc` depending on our shell.

```
eval "$(devbox global shellenv)"
```

Then restart the terminal and use Devbox normally.

```
> devbox global add go

Info: Adding package "go@latest" to devbox.json
✓ Computed the Devbox environment.
Warning: Your shell environment may be out of date. Run `refresh-global` to update it.

> refresh-global
```

As I mentioned above, everything should result `devbox.json` and `devbox.lock`. Where are they? Try `which go` to see.
```
> which go

/Users/sp.bean/.local/share/devbox/global/default/.devbox/nix/profile/default/bin/go

> ls /Users/sp.bean/.local/share/devbox/
```

Depending on the result of `which go`, we can see Devbox is placed in the `~/.local/share/` directory. Looking around there, I see that the `devbox.json` and `devbox.lock` are in `devbox/global/default/`.

Another simple way to check is using `devbox global path`, it results in the same directory as we see above.

Under the hood, Devbox provides an ENV variable named `XDG_DATA_HOME` to determine where the `devbox.json` and `devbox.lock` are placed. If it is not set, it will default to `~/.local/share/devbox/global/default`.

Because it is global, so you do not need to type `devbox shell` to start another shell.

---
#### References
*Installing Devbox | Devbox*. (n.d.). Jetify. Retrieved July 25, 2024, from https://www.jetify.com/devbox/docs/installing_devbox/
*Create a Dev Environment with Devbox | Devbox*. (n.d.). Jetify. Retrieved July 25, 2024, from https://www.jetify.com/devbox/docs/quickstart/
(n.d.). Use Devbox as your Primary Package Manager | Devbox. Retrieved July 25, 2024, from https://www.jetify.com/devbox/docs/devbox_global/
