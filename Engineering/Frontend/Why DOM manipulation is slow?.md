---
tags: javascript, DOM, fundamental, frontend, engineering/frontend
author: Pham Duc Thanh
date: 2022-08-09
---

Actually, the DOM is not slow. Adding or removing a DOM node is not much more than setting a property on the JS object. However, _layout_ is slow. Imagine adding a DOM node changes the height of the document, it would invoke a bunch of [rendering processes](https://web.dev/rendering-performance/) to redraw the screen. And all the complex algorithms behind the those processes makes any changes in DOM potentially expensive.
