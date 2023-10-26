---
tags: javascript, DOM, fundamental, frontend, engineering/frontend
author: Pham Duc Thanh
github_id: zlatanpham
date: 2022-08-09
---

Actually, the DOM is not slow. Adding or removing a DOM node is not much more than setting a property on the JS object. However, _layout_ is slow. Imagine adding a DOM node changes the height of the document, it would invoke a bunch of [rendering processes](https://web.dev/rendering-performance/) to redraw the screen. And all the complex algorithms behind the those processes makes any changes in DOM potentially expensive.


---
<!-- CTA -->
### Contributing

At Dwarves, we encourage our people to read, write, share what we learn with others, and [[CONTRIBUTING|contributing to the Brainery]] is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?

- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)