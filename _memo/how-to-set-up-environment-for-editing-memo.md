---
tags:
  - content
  - instructions
  - guideline
title: How to set up environment to edit memo
date: 2024-03-14
description: This is a guide on how to setup your environment and settings to push content to our notes website, memo.d.foundation.
authors:
  - minhcloud
menu: memo
type: memo
hide_frontmatter: false
pinned: true
hide_title: false
---
Before you enter the tutorial, please generate your SSH key by following this [instruction](https://g.co/gemini/share/3972239af940). The process includes 3 steps:
1. Create ssh key pair (public, private)
2. Save private key to your computer
3. Submit public key to github

## A. Install the Visual Studio Code
Firstly, you have to install Visual Studio Code, [here](https://code.visualstudio.com/)

## B. Install the Devbox
1. Open the Terminal on VScode
You can use the shortcut `Control + ~` to open Terminal.

![](https://media.discordapp.net/attachments/1064565585800876083/1217838498464141463/setup_env_b11.png?ex=66057b7c&is=65f3067c&hm=2bfa1ade8635c2e474b8dbb10797186eb0ccca98a835ee4245d0a52e85dece24&=&format=webp&quality=lossless&width=1540&height=1134)

Then run this command in the Terminal to install Devbox: `curl -fsSL https://get.jetpack.io/devbox | bash`.

## C. Pull the Github Source to your local disk 
You have 2 ways to pull the Github source to the local disk:

![ ](https://media.discordapp.net/attachments/1064565585800876083/1217838498984230913/setup_env_b12.png?ex=66057b7c&is=65f3067c&hm=d6af0dc1661e2ebc6154bf1f78516b7c0a4e932bff74c29cb7b34db4ba2938f0&=&format=webp&quality=lossless&width=1618&height=334)

### Method 1: Link VScode with your Github account
1. Connect your github account with the VScode
2. Search repo `note.d.foundation` and select to clone it

![](https://media.discordapp.net/attachments/1064565585800876083/1217838499776958474/setup_env_c11.png?ex=66057b7c&is=65f3067c&hm=3a5b23cafa5bda553f69d16bbfe4d4285cce3179ea2af8ffaa89660f4b17e49d&=&format=webp&quality=lossless&width=1540&height=1134)

![](https://media.discordapp.net/attachments/1064565585800876083/1217838500909551656/setup_env_c12.png?ex=66057b7c&is=65f3067c&hm=3172263a041cb2f2f426fe034539fa7906644c14bcabb542c2389fc7dfba4199&=&format=webp&quality=lossless&width=1540&height=1134)

### Method 2: Using the terminal 
1. Run these 2 commands seperately in Terminal to connect the Github account to the VScode:
```sh
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
2. Run this command in Terminal to clone the repository:
```sh
git clone https://github.com/dwarvesf/note.d.foundation.git
```

## D. Setup the environment on your laptop

1. Run submodule update by running these 3 commands in order and seperately:
```sh
git submodule update --init --recursive
git submodule update --recursive --remote
git submodule foreach --recursive 'git checkout main || git checkout master
```

2. Create folder "content" under node.d.foundation folder

![](https://media.discordapp.net/attachments/1064565585800876083/1217838501937020968/setup_evn_d2.png?ex=66057b7d&is=65f3067d&hm=d24b328ccc8efd196b9754480ff0ccca33c9b4a9359576c2707af1483fd52389&=&format=webp&quality=lossless&width=1540&height=1134)

3. Run the this command in Terminal `devbox shell` to set up the environment and wait until all files are installed
4. Run the command `make watch-run` to rebuild the site and get the local link

## E. Sync all repo before editting 
Everytime you want to edit or create a post, you have to go to `Source Control` and sync all file. 

![](https://media.discordapp.net/attachments/1064565585800876083/1217838502977343568/setup_evn_e1.png?ex=66057b7d&is=65f3067d&hm=dbc1332fd9de7ed3d5b49bca3f4ad07784a36ef6629ec0263d65a22976106f55&=&format=webp&quality=lossless&width=1410&height=1040)
