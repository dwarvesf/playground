---
tags: engineering/frontend, wai-aria, accessibility
author: Nguyen Dinh Nam
date: 2022-09-30
---

Since modern websites and applications contain huge amounts of dynamic content and complex components with no semantics to describe what they mean, users with **no mouse** equiped or those dependent on technologies such as **[Screen Reader](https://chrome.google.com/webstore/detail/screen-reader/kgejglhpjiefppelpmljglcjbhoiplfn/related?hl=en)** might not be able to interact with those components.

Web Accessibility Initiative’s Accessible Rich Internet Applications or simply **WAI-ARIA** is a technology that can help with such problems.

## What is WAI-ARIA?
Before semantic elements like `<nav>` or `<footer>` were introduced that define specific features of a web page, some developers would rely on JavaScript libraries that generate a bunch of **nested `<div>`s**, then styled them with CSS and controlled with JavaScript. 

Even though they work fine, screen readers cannot make any sense of what those components are, no semantics provided so that they can assist their users. WAI-ARIA has **roles**, **states** and **properties** to solve this problem, giving an opportunity to add attributes to content and components that make them **meaningful** and enhance **accessibility**.

### Roles:
[WAI-ARIA roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles) define **what that HTML is or does**, add the required additional information in cases the markup does not provide the required role. If we write `<a role="button">`, the screen reader will recognize it as a button.

```javascript
<div role="button" aria-pressed="false" tabindex="0">Button 1</div>
```

We can have `button`s, `tab`s,... representing widget roles working as part of larger components, or `heading`, `row`, `rowgroup`,... describing content structure in a page.

### Properties:
Represent the **data value associated** with the object. When combined with roles, the user agent can supply the assistive technologies with user interface information to convey to the user at any time. Properties are **less** likely to change. `aria-label`, `aria-required` and `aria-describedby` are some instances for [WAI-ARIA properties](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes).

```javascript
<form>
	<label for="name">Enter your name:</label>
	<input type="text" name="name" aria-label="Your name" aria-required="true" placeholder="Your name">

	<label for="age">Enter your age:</label>
	<input type="number" name="age" aria-label="Your age" aria-required="true" placeholder="Your age">

	<input type="submit">
</form>
```

### States:
Have the same characteristics as properties, except for one thing that states are frequently changed during the life cycle of the component. Some commonly used [WAI-ARIA states](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes) are `aria-pressed`, `aria-expanded`, `aria-selected`,...

```javascript
  
<ul role="tablist">
	<li class="active" role="tab" aria-selected="true" tabindex="0">Tab 1</li>
	<li role="tab" aria-selected="false" tabindex="0">Tab 2</li>
	<li role="tab" aria-selected="false" tabindex="0">Tab 3</li>
</ul>
```

Below is a small demonstration, you can add this [Screen Reader extension](https://chrome.google.com/webstore/detail/screen-reader/kgejglhpjiefppelpmljglcjbhoiplfn/related?hl=en) and interact with it to know how WAI-ARIA helps enhance accessibility before reading further about benefits of using it:
<iframe height="400" style="width: 100%;" scrolling="no" title="WAI-ARIA" src="https://codepen.io/nguyend-nam/embed/XWqZPPE?default-tab=result" frameborder="no" allowfullscreen="true"></iframe>

## Why use WAI-ARIA?
Note that WAI-ARIA attributes **do not** change the behavior of the supplied component, they don't affect anything about the web page. The difference is that the [browser's accessibility APIs](https://wiki.mozilla.org/Accessibility/WebAccessibilityAPI) will expose that information and the assistive technologies can rely on that information to enhance users' accessibility.

WAI-ARIA will become handy in some cases as listed below:
- WAI-ARIA roles are useful when defining specific **regions on a web page** (e.g. banner, navigation, main,...).
![](https://i.imgur.com/R1s3rBm.jpg)

- `aria-live` can inform screen reader users when a component is **dynamically updated**.
- Strong support **keyboard users**: some HTML elements already have built-in keyboard accessibility (e.g. `<buttons>`, `<inputs>`,... where users can navigate to using tab key), but some need JavaScript along with to do that. WAI-ARIA provides `tabindex` attribute to allow focusing on those elements.
- **Improve accessibility** of non-semantic components: as modern web pages are getting more and more complex, UI components might have a bunch of nested `<div>`s inside. WAI-ARIA helps cover that with roles (e.g. button, tablist), it also improves functionality (e.g. `aria-required`).

## Reference
- https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics
- https://www.maxability.co.in/trainings/advanced-web-accessibility-testing/what-is-wai-aria
- https://www.w3.org/WAI/ARIA/apg/example-index/button/button
- https://pressbooks.library.torontomu.ca/wafd/chapter/wai-aria-landmarks/#:~:text=WAI%2DARIA%20landmarks%20are%20used,bypass%20links%20and%20page%20headings
