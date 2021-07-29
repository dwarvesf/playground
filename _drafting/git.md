---
tags: git, process, software development, basic, git-flow
---

# Why are we using git?
- Git is a revision control system for documents, therefore we usually use this system for tracking the changes in a set of files. It helps groups of developers work collaboratively on software projects.
- Git is a working standard in software development. Almost all company or development teams are using git for daily work, interview sessions.
- All open sources are using git for development, collaboration, therefore we must have experimented with git

# What is git?
- Git is a mature, actively maintained open source project originally developed in 2005 by Linus Torvalds. Git is software for tracking changes in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development.
- Git track all versions of your changes from the beginning of a project. We can compare the revision history to track, review the changes for codebase integration. Therefore, we can work and collaborate efficiently.

## Concept
- `snapshot` is the content (files and folders) of a repository at some point in time
- `commit` in a git repository records a snapshot of all the (tracked) files in your directory. A commit has reference to the parent commit.
- `branch` is similar to the branch of a tree which contains the commits. When we make a branch from existing branches, we have a new branch and the existed branch is called a base branch.
- `repository` (or repo for short) contains all of the project files and the entire revision history. There are 2 types of repositories: local repository and remote repository. A local repository is storing data in a computer gives you a personal working environment. A remote repository is storing a copy of your Git repo with an online host (such as GitHub or Bitbucket) gives you a centrally located place where you can upload your changes and download changes from others, letting you collaborate more easily with other developers.

# How to use git effectively?

## Git flow
Git flow was first published and made popular by Vincent Driessen. The Gitflow Workflow defines a strict branching model designed around the project release. This provides a robust framework for managing larger projects. Git flow focuses on stable and qualified products.
The central repo holds two main branches with an infinite lifetime is `master` and `develop`
The development model uses a variety of supporting branches to aid parallel development between team members, ease tracking of features, prepare for production releases, and to assist in quickly fixing live production problems. These are `feature branches`, `release branches`, `hotfix branches`.

### Develop feature flow
Base branch: develop
Merge back to: develop
Branch naming convention: feat/*
Person in-charge: developers
Objective: Implement a new feature of the software
Developers check out from the `develop` branch a new feature branch. They make an early merge request with a full description of the working task. Developers work on this branch and merge to `develop` after being reviewed by teammates or leaders.

### Release flow
Base branch: develop
Merge back to: develop and master branch
Branch naming convention: release/v*.*.*
Person in-charge: leader
Objective: prepare and release a new version of the software
The leaders check out from the `develop` branch a release branch. They should pump the version and update the release note. After preparing the release information, they merge the changes to `master` and `develop` branches. The leader creates a new tag from `master` branch.

### Hot-fix flow
Base branch: master
Merge back to: develop and master branch
Branch naming convention: hotfix/*, bugfix/*
Person in-charge: developer or leader
Objective: fix the urgent issue and release a new version of the software
Developers check out from the `master` branch a hot-fix branch. After working on the source code, they should pump the version and update the changelog. Developers merge the change to `master` and `develop` branches.

## Git-flow in Dwarves Foundation
Dwarves Foundation team is using the git-flow and some customization. We base on the idea about git-flow when working with the features branches. However, our team applies a different release flow.
There are 4 environments for the development of live-cycle in the Dwarves Foundation team: `develop`, `testing`, `staging`, and `production`. Instead of release on `develop` and `master` branches, we release the product on tags. `v*.*.*` tag for production, `v*.*.*-rc` for staging, and `v*.*.*-alpha` for testing.

### Release Testing version
Base branch: develop
Merge back to: develop
Branch naming convention: release/v*.*.*-alpha
Tag: `v*.*.*-alpha`
Person in-charge: developer or leader
Objective: prepare and release a new version for the testing

### Release Staging version
Base branch: release/v*.*.*-alpha
Merge back to: develop, release/v*.*.*-alpha
Branch naming convention: release/v*.*.*-rc
Tag: `v*.*.*-rc`
Person in-charge: developer or leader
Objective: prepare and release a new version for the staging

### Release Production version
Base branch: release/v*.*.*-rc
Merge back to: develop, release/v*.*.*-rc, master
Branch naming convention: release/v*.*.*
Tag: `v*.*.*`
Person in-charge: developer or leader
Objective: prepare and release a new version for the production

## Practices
Using simple flow for a small project or one-person project
Using Git flow or GitHub flow for collaborative projects, large projects, open-source projects

## Usage commands
structure: commit vs branch
where: remote vs local
file states: untracked vs tracked
file status: unmodified vs modified vs staged
travel between nodes: checkout vs reset
move nodes: merge vs rebase vs cherry-pick
alter node(s): amend vs squash vs rebase interactive
view history: log vs reflog
other: stash, clean, revert
reference: HEAD, FETCH_HEAD, HEAD~, HEAD^, tag

## Usage use-cases
Init project with git
Get a task and complete all thing
Release a software version
Get the conflict in the same branch
Get the conflict in another branch
Rebase a branch
Commit signature verification

# FAQ
Setup ssh keys
Setup GPG keys
Using multiple ssh keys
Git config

# References
https://learngitbranching.js.org
https://nvie.com/posts/a-successful-git-branching-model/
https://danielkummer.github.io/git-flow-cheatsheet/
