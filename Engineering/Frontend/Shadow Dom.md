---
tags: frontend, shadow dom, engineering/frontend
author: Tran Khac Vy
github_id: trankhacvy
date: 2023-05-16
---

Recently, I have endeavored to develop an application on the platform of chat GPT, bearing the name Javis. It functions as a chrome extension, serving as an AI assistant to aid users during their web browsing experience. Upon testing the application on Chrome, I encountered an issue where Javis's CSS conflicted with the CSS of the running webpage, resulting in both my application and the webpage occasionally displaying inaccurately compared to their original interfaces. After conducting an extensive online search, I discovered a viable solution known as shadow dom. In this article, I shall introduce you to the concept of shadow dom and elucidate the myriad benefits it bestows.

## What is Shadow DOM?
Shadow DOM is a web standard that allows encapsulation of HTML, CSS, and JavaScript within a specific context. Shadow DOM allows hidden DOM trees to be attached to elements in the regular DOM tree — this shadow DOM tree starts with a shadow root, underneath which you can attach any element, in the same way as the normal DOM.

![[_assets/shadow-dom.svg]]
Source: https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_shadow_DOM

There are some bits of shadow DOM terminology to be aware of:
- **Shadow host**: The regular DOM node that the shadow DOM is attached to.
- **Shadow tree**: The DOM tree inside the shadow DOM.
- **Shadow boundary**: the place where the shadow DOM ends, and the regular DOM begins.
- **Shadow root**: The root node of the shadow tree.

When working with the shadow DOM, you have the power to manipulate its nodes just like you would with non-shadow nodes. This includes appending children, setting attributes, and applying styles using `element.style.color` or a `<style>` element within the shadow DOM. The key distinction is that any code within the shadow DOM remains encapsulated, unable to affect elements outside of it, providing a valuable encapsulation feature.
    
## Basic usage
Now that we understand the importance of Shadow DOM, let's explore how to create and manipulate Shadow DOM.
You can create Shadow Dom by attaching a shadow root to any element using the `Element.attachShadow()` method. This takes as its parameter an options object that contains one option — `mode` — with a value of `open` or `closed`:
    
```
const shadowOpen = host.attachShadow({ mode: "open" });
const shadowClosed = host.attachShadow({ mode: "closed" });
```    

- `open`: The shadow DOM/ internal DOM of the component is accessible from outside JavaScript.
- `closed`: The shadow DOM/ internal DOM of the component is not accessible outside JavaScript. The ``<video>`` tag is an example of closed-mode shadow root.


## References
- https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_shadow_DOM
