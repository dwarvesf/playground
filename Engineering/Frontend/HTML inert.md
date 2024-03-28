---
tags: html, a11y, accessibility, engineering/frontend
author: Pham Duc Thanh
github_id: zlatanpham
date: 2022-06-12
---

`inert` is a boolean HTML property that makes the browser ignore the user input events for an element, including focus events and events from assistive technologies.

When an element has `inert` attribute, it will be removed from the tab order (interactivity), and from the accessibility tree (discoverability). While discoverability, previously, could be suppressed by `aria-hidden=true`, interactivity is more difficult as developers normally have to combine with `tabindex="-1"` to get it disabled.

The born of `inert` helps to eliminate the need for [[Focus trap | focus trap]] which is being combined with `aria-hidden` to improve the accessibility of a web page containing an open dialog (see the attachment), though we still have to manually move the focus to the dialog and return focus the element that triggered it after the dialog is closed.

![](assets/html-inert_pasted-image-20220612104313.png)

```html
<!-- Before -->
<div id="main" aria-hidden="true">...</div>
<div class="dialog">...</div>
<script>
  // ...initiate focus trap for .dialog
</script>

<!-- After -->
<div id="main" inert>...</div>
<div class="dialog">...</div>
```

#### References
- https://developer.chrome.com/articles/inert/
- https://patrickhlauke.github.io/aria/demos/modal/index-aria-inert.html

---
<!-- cta -->

### Contributing
At Dwarves, we encourage our people to read, write, share what we learn with others, and [[CONTRIBUTING|contributing to the Brainery]] is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?
- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)