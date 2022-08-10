---
tags: frontend, css-in-js
author: Tran khac Vy
---

**CSS-in-JS** is a styling technique where Javascript is used to style the component. These are multiple implementation of this concept in the form of libraries such as [emotion](https://emotion.sh), [styled-component](https://styled-components.com/), [JSS](https://cssinjs.org). They airm to tacke the limitations of CSS, such as lack of dynamic functionality, scoping, and portability.

## Benefits of using CSS-in-JS

### Scoping
- With CSS-in-JS, writing new styles cannot affect anything else in other places on the site, so there’s no need to worry about writing a style that has bad or unintended consequences elsewhere due to a selector in the global scope.

### Avoid naming collisions
- CSS-in-JS libraries automaticly generate unique selectors for what’s being styled. We don't need to think about name.

### Dynamic Functionality
- As CSS-in-JS is essentially JavaScript code, you can apply complex logic to your style rules, such as loops, conditionals, variables, state-based styling, and more.

### Dead code elimination
- CSS-in-JS helps with removing dead code. The only styles that are loaded are the styles for the components in use at any given time. There’s no shipping any unused styles. When a component dies, so does its styles.

### Developer ergonomics
- It can be nice to have styles in the same file (or otherwise very close to) the component itself. In the same way, some developers feel very comfortable in JSX. Also being able to style things without any scoping worry means developers may feel empowered about styling rather than intimidated by it.

## Disadvantages of CSS-in-JS

### Runtime cost
- When CSS is generated from JavaScript at runtime, in the browser, there is an inherent overhead.

### Learning curve
- CSS-in-JS definitely has a learning curve, especially if you have used neither component-based frameworks nor web components before. Besides learning the new syntax, you also need to pick up a new way of thinking, which needs time and might slow down your development workflow for a while.

### Unreadable class names
- Automatically generated selectors significantly worsen code readability. This can be a huge concern for you if you regularly use your browser’s developer tools for debugging. 

## Reference
- https://en.wikipedia.org/wiki/CSS-in-JS
- https://webdesign.tutsplus.com/articles/an-introduction-to-css-in-js-examples-pros-and-cons--cms-33574
- https://medium.com/dailyjs/what-is-actually-css-in-js-f2f529a2757


