---
tags: CSS, guides, responsive design, engineering/frontend
author: Tran Tien An
date: 2022-09-02
---

Published on August 30, 2022, Chrome 105 included Container Queries, one of the most highly requested features in CSS.

## The Problem With Media Queries

  When we want to create a responsive layout, we usually use media queries. Media queries are a great tool for creating responsive layouts. However, they have some limitations. For example, we can't use media queries to style a component based on its parent width. We can only use media queries to style the entire page. This is a problem because we can't create responsive components. We can only create responsive pages.

## What is Container Queries?

  Container Queries allows us to style elements according to the size of a container element. It is similar to a Media Queries, except it evaluates against the size of a container instead of the size of the viewport.

## How to use Container Queries?

To query a component based on its parent width, we need to use the `container-type` property with possible values: `size`, `inline-size`, `block-size`, `style`, `state`.

```css
.sidebar {
  container-type: inline-size;
}
```

Now we can start to query a container using `@container`. This will query the nearest containment context.

```css
@container (min-width: 300px){
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

https://caniuse.com/?search=Container%20Queries
  - Chrome 105
  - Safari 15
  - Edge 105

## Reference

- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Container_Queries
- https://javascript.plainenglish.io/css-container-queries-3393fbeb6ea8
- https://ishadeed.com/article/container-queries-are-finally-here/
- https://developer.chrome.com/docs/devtools/css/container-queries/
