---
tags: 
  - devbox
title: "Devbox Plugins: Enhancing Package Setup and Configuration"
date: 2024-08-01
description: An overview of Devbox Plugins, their types, and how they simplify package setup and configuration in Devbox environments
authors:
  - bievh
---
Devbox is based on Nix. However, you don't need Nix knowledge to interact with Devbox. Some packages require additional setup to work, which is why Plugins were introduced to Devbox.

For example: If you want to install and use Nginx for your project:
- You need a default configuration to run Nginx; Devbox Plugins provide this when adding Nginx.
- If you need to customize Nginx, Devbox Plugins expose proper environment variables for you to set up Nginx.
- If you want to control all configuration files, Devbox Plugins group them, place them in a specific folder, and let you manage them.
- Everything mentioned above is automatically done for you when you add Nginx.

We have two types of Plugins:
- Built-in Plugins: These are already implemented in Devbox for several popular packages such as Nginx, PostgreSQL, etc. Check [Built-in Plugins](https://www.jetify.com/devbox/docs/guides/plugins/#using-plugins) for more information.
- Custom Plugins: These are implemented by you, following the [schema provided by Devbox](https://www.jetify.com/devbox/docs/guides/creating_plugins/#plugin-design).

Custom Plugins can be placed locally or on GitHub.

---
#### References
*Using Plugins | Devbox*. (n.d.). Jetify. Retrieved July 28, 2024, from https://www.jetify.com/devbox/docs/guides/plugins/
