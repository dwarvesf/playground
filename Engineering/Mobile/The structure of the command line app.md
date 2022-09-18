---
tags: iOS, MacOS, Swift, engineering/mobile
author: Phan Viet Trung
date: 2022-09-018
---

# How to create an XCode build tools with Swift

As a developer, we are using command line tools(app) frequently, like a simple task such as: navigation between directories with `cd /Desktop`, make a new folder with `mkdir newfolder` , delete files with `rm -f filename` to friendly GIT commands: `git checkout master` `git pull`. Command line tools is easy to use, very lite weight and running fast (by bypass user interface).

Bunch of them build in in your machine. You can easly to find them at following paths: `/usr/bin` and `/usr/local/bin`

Command line tools are powerful and flexible. Not only using it directly in `Terminal` we can also embed it to support automation task, create build tools, release tools (like Jenkin, Fastlane...) or wrap it to use with any language and create a friendly user interface (GitHuh Desktop, Source tree...). The limitation of command line tools is just your imagnation.

In the end of this serial, the sample CommandLine tools can automaticaly convert all assert catalog in the Xcode project to Swift file to eliminated all typing error, get free benefits of SDK auto completion and take advantage of Compiler to safety check all assert at the compile time.

Not only apply in XCode, the SwiftCLI can using in anywhere by mixing with `shell` script.

In this serial of `Command line tools` brainery we go though three main topics:

    1. The structure of the CommandLine tool app.
    2. Build a CommandLine app using Swift.
    3. Create an XCode build tools using Swift CLI.

## The structure of the CommandLine tool app

```command [arguments] [options] [flag]```

Ex: `git push origin master -f`

### Command

`command` is the begin to start a CLI command, we also call it main command (because we have subcommand and default command later). Think it like the way we open an app.

Ex: `git, cd, ls, mkdir` are very popular command.

_Note: Somewhere may call main command is `app` and subcommand is `command`_

### Argruments

`arguments` are using to parse data to commandline app.

`command agr1 agr2`

The position of agruments is master, we can't change it.

Ex: `adb push /User/Download/sample.ipk /installs`

The Android NDK adb push sample packge from `/User/Download` folder to device `/installs` folder. You can't swap position of args.

They are may required or not. If not the default value will be apply.

Ex: We are in master branch, default remote is origin and run:

 `git fetch` => fetch default remote origin branch, it equal with:
`git fetch origin` fetch the remote origin (master) branch.

In the example above the arg `origin` is not required and it auto set base on current checkout branch.

### Options

`Options` are named parameters that can be passed to a command and are represented by key-value pairs.

`Options` are generally preceded by a hyphen (-), and for most commands, more than one option can be strung together.

`Options` position is not importance.

If the parameter is required, using `Arguments` instead.

`command -[option][option][option]`

Ex:```git commit --message "commit message"```

`--message` is the key and `"commit message"` is the value.

### Flag

Flag is the 'Options' that don't required value

Ex: `git push -f`. `-f` is the optional to tell we want force push, ignore and replace all contents of the current remote brand.

### Long and sort options

Unlike `Agruments` using position to determite what agruments is it, the position of `Optional` is not master, we are using 'Key' to filter what is the type of Option, hence the name may long to type.

To quick and easy to type we can add a sort version of 'Key'

Ex: `git push --force` | `git push -f`,
`npm install --help`

Here we can see many forms of `--help` flag like: `-h, -?, -H`, that is the sort version of `--help`

### The Subcommands

The CommanLine tool app usually have many feature, to easy to use and seprated them we're using subcommands to seprated it.

A subcommand is passed follow the main command. It have it own set of `Option(s)` and `Flag(s)`.

Ex:
`git checkout`
`git commit`

`checkout` and `commit` are two commond subcommands of git.

The subcommand `commit` have an `optional` message `-m` (`git commit -m "Hello"`) that `checkout` doesn't have. That is they own `Optionals` and `Flags`

Using subcommand not only easy to use, easy to read, but also helping us easy to learn how to use it with the `--help` flags instead of print all the help of the app and lookup in the very long text.

You going to learn about `Help` command and flag later.

### The default command

The default command is the command call when you parse nothing to the the app

Ex: `git`
will print out the help which is equal with `git help`. `help` is very poppular default command for many CLI app.

```shell
git                                                                                                                            [20:13:35]
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] 
........           
```

### The `help` command/flags for documentation

The lack of user interface required some guild on how to use the command line app.
There are 2 types of help: the subcommand and the flag.

**[command `help`]**

This `help` subcommand usually using when you begin with a new CLI app. It will print out the details how to use the app, all the commands, subcommands, options, flags.

Ex: `git help`

```shell
git help                                                                                                     [13:27:57]
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           [--super-prefix=<path>] [--config-env=<name>=<envvar>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one
...........
```

**[command [subcommand] [option] `-h`]**

The `--help` `-h` `-?` or `-H` flags depend on app like `git checkout -h` provice the help for Subcommand/Options. Those flags print out the guild for related command/optional only. It's save you from digging in the whole long documents of the main app.

When you type in the wrong command, option, flag, the help may also automatically print out to show us how to use related function.

Ex: `git commit ---m`. We don't have any flag `---m` it should be `-m` for commit message.

```shell
git commit ---m                                                                                              [13:01:13]
error: unknown option `-m'
usage: git commit [<options>] [--] <pathspec>...

    -q, --quiet           suppress summary after successful commit
    -v, --verbose         show diff in commit message template

Commit message options
    -F, --file <file>     read message from file
    --author <author>     override author for commit
    --date <date>         override date for commit
    -m, --message <message>
                          commit message
............
```

_Note: The include of `help`  does not required but we're highly recommend to have it in your CLI app._

#### Reference

- <https://dev.to/paulasantamaria/command-line-interfaces-structure-syntax-2533>
