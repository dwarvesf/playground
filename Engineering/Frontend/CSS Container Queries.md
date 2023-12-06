---
tags: CSS, guides, responsive-design, engineering/frontend
author: Tran Tien An
github_id: tienan92it
date: 2022-09-02
---

Published on August 30, 2022, Chrome 105 included Container Queries, one of the most highly requested features in CSS.

## The Problem With Media Queries

When we want to create a responsive layout, we can use media queries to adjust styles based on the screen size of the device viewing our site. However, media queries have some limitations. For example, we cannot use them to style individual components based on their parent's width; we can only adjust the entire page. This is problematic because we cannot create responsive components; only responsive pages.

## What is Container Queries?

The CSS3 property "container queries" allows us to style elements based on the size of a container. It is similar to a Media Query, except it evaluates against the size of a container instead of the size of the viewport.

## How to use Container Queries?

To query a component based on its parent width, we need to use the `container-type` property with possible values: `size`, `inline-size`, `block-size`, `style`, `state`.

```css
.sidebar {
  container-type: inline-size;
}
```

Now we can start to query a container using `@container`. This will query the nearest containment context.

```css
@container (min-width: 300px) {
  .content {
    display: none;
  }
}
```

Additionally, Containers can be named with `container-name` property. This allows us to query a specific container.

```css
.sidebar {
  container-type: inline-size;
  container-name: my-sidebar;
}
```

or shorthand syntax

```css
.sidebar {
  container: my-sidebar / inline-size;
}
```

Then, to query a specific container, we can use `@container` with `container-name`.

```css
@container my-sidebar (min-width: 300px) {
  .content {
    display: none;
  }
}
```

## Browser Support

Currently, Container Queries is only available in [modern browsers](https://caniuse.com/?search=Container%20Queries):

- Chrome 105+
- Safari 15+
- Edge 105+

Universal support can be achieved by using [Polyfill](https://github.com/GoogleChromeLabs/container-query-polyfill).

## Reference

- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Container_Queries
- https://javascript.plainenglish.io/css-container-queries-3393fbeb6ea8
- https://ishadeed.com/article/container-queries-are-finally-here/
- https://developer.chrome.com/docs/devtools/css/container-queries/



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