---
title: Dwarves Tech Radar Volume 02
short_title: Tech Radar Volume 02
date: 2021-01-14
description: Dwarves Tech Radar v2 contains the practices to simplify the workflow, new techniques/ approach methods to upgrade our current standards and expand the domain knowledge.
authors: 
  - duy
tags: 
  - radar
  - forward-engineering
---

Once every month, we gather for Radar update to round up the cool techs and assess if we should adopt that to the team. Road to a wider and more diversified rings, Dwarves Tech Radar v2 contains the practices to **simplify the workflow**, new techniques/ approach methods to **upgrade our current standards** and **expand the domain knowledge.** 

## Trial
### Earthly: The combination Dockerfile + Makefile
[https://earthly.dev/](https://earthly.dev/)

A repeatable syntax builds to untangle the debugging process between the local environment and the CI platform. Earthly allows our DevOps to merge all the tools into one "Earth", and eventually simplify the whole CI/CD flow. As DevOps must integrate different files from both Makefile and Dockerfile for integration testing, Earthfile was created to remove this burden, automatically. Reproduce CI failures is also what makes Earthly more valuable. This enables developers to run CI on their local env, instead of the constantly `git commit -m "try again"`.

We applied it on Voconic, our complex on-going project about Cloud platform, to fully utilize the benefit. Earthly executes targets in parallel and makes our pipelines run much faster.

![](assets/dwarves-tech-radar-volume-02_ecb87e89c8fcfad298cc445cb3c4c76b_md5.webp)

## Assess
### Webflow: Build visual canvas without coding techniques
 [https://webflow.com/](https://webflow.com/) 

At some point, we figure the development phase might take more time and resources than we need. Therefore, a no-code platform is what can resolve the issue. Webflow removes the usual misunderstanding between designers and developers - enables them to convert stunning designs into production without any coding techniques. 

Duy P, our UI designer, approached this with KiwiPay: [https://kiwipay.webflow.io/](https://kiwipay.webflow.io/)

![](assets/dwarves-tech-radar-volume-02_3306d8d315bae18a20786c33778c2b25_md5.webp)

Besides the outstanding points: Sharing for multiple collaborators, easy working flow, codebases can be exported easily in HTML/ CSS & JSON data, Webflow still has its downside. The no-code mechanism prevents Webflow from performing complex animation, i.e., generates a limitation in the animated web. Furthermore, unstable responsiveness and errors in image display are things Webflow needs to work on.

### Volta: Hassle-free JS Tool Manager
[https://volta.sh/](https://volta.sh/) 

During our work with Javascript, each project comes with different node versions. Usually, managing these versions relies mostly on nvm, requiring developers to manually run their CLI every time switching between projects. It's a waste of time and can quickly cause errors.

One of our engineers started to work on Volta - a hassle-free approach to manage the CLIs. In short, Volta detects the node versions in the JSON package, unifies them into one place, and automatically switch them as developers change their projects. Since Volta supports quick engine setup, we get to install the npm package binaries into the toolchain once and for all and then let Volta take care of the rest.

## Adopt
### Upptime: Real time status update 
[https://upptime.js.org/](https://upptime.js.org/)

We tried out CState as our monitoring service, but CState requires low level setup at infrastructure level and therefore not suitable for our bootstrapping kit. Upptime, on the other hand, only requires a simple Github repository and a config file to get it started. We gave Upptime a twist, and rolled out our version at [stt.daf.ug](http://stt.daf.ug/).

![](assets/dwarves-tech-radar-volume-02_3b5bb41a5a96a78fadb9fef60f1d0c24_md5.webp)
