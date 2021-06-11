---
tag: canvas, render, google, html
---

### The purpose
**1. Consistency across different platforms**. 

Each [[browser]] has different method to display the [[HTML]] code. Seeing things in Safari is different from Chrome, obviously.

A canvas-based approach gives [[Google]] Docs a much more consistent framework to display content. It speeds up the ability to get text, objects, graphs, and images rendered in a quicker fashion for the end user

Less painful in supporting multiple browsers since rendering no longer relies on HTML/CSS. 

**2. Support Flutter** 

They've already gotten CanvasKit built for Flutter. This move can somehow predicts the future of Google featuring Flutter web


### Its impact on extension 
Changeing into canvas-based also change the logic of building UI (how backend used to be structured with specific bits of HTML), which prevents some extension to function as it used to. 

Semantic [[website]] work by reading metadata from text input and retrieve the result kbased on search engine. 

Using canvas = black box, there's no `metadata` to read. 

HTML-based website is usingd DOM to render UI from [[HTML]]. Some Chrome extension utilizes DOM to approach the content and using metadara to verify the text. 

Canvas has nothing to do with DOM => This means we still haven't figured out what to replace those HTML-based features with. 

#### Citation
- https://workspaceupdates.googleblog.com/2021/05/Google-Docs-Canvas-Based-Rendering-Update.html
- https://medium.com/young-coder/the-future-web-will-canvas-rendering-replace-the-dom-847be872884c