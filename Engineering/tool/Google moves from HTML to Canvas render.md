---
tag: canvas, render, google, html
URL: https://workspaceupdates.googleblog.com/2021/05/Google-Docs-Canvas-Based-Rendering-Update.html
title: Google moves from HTML to Canvas render
---

**1. Consistency across different platforms**. 

Each [[browser]] has different method to display the [[HTML]] code. Seeing things in Safari is different from Chrome, obviously.

A canvas-based approach gives [[Google]] Docs a much more consistent framework to display content. It speeds up the ability to get text, objects, graphs, and images rendered in a quicker fashion for the end user

Less painful in supporting multiple browsers since rendering no longer relies on HTML/CSS. 

**2. Support Flutter** 

They've already gotten CanvasKit built for Flutter. This move can somehow predicts the future of Google featuring Flutter web


Its impact on extension 
Changeing into canvas-based also change the logic of building UI (how backend used to be structured with specific bits of HTML), which prevents some extension to function as it used to. 

