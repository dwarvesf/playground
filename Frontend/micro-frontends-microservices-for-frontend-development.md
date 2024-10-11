---
tags:
  - micro-frontend
title: Micro Frontends Microservices For Frontend Development
date: 2021-07-09
description: Micro Frontends is an architectural style where independently deliverable frontend applications are composed into a greater whole.
title: Micro Frontends Microservices For Frontend Development
authors: 
 - thanh
---

## What is Micro-frontend ?

> An architectural style where independently deliverable frontend applications are composed into a greater whole

## Benefits

- Smaller, more cohesive, and maintainable codebases
- More scalable organizations with decoupled, autonomous teams
- The ability to upgrade, update, or even rewrite parts of the frontend in a more incremental fashion than was previously possible
- Easier maintenance: Keeping frontend repositories small and specialized allows them to be more easily understood, and this simplifies long-term maintenance and testing.

## Micro frontends in actions

### Build-time integration

- Publish each micro frontend as a package and have the container application include them all as library dependencies.

```javascript
{

  "name": "@shop/container",

  "version": "1.0.0",

  "description": “Ecommerce website",

  "dependencies": {

    "@shop/products": "^1.0.0",

    "@shop/order": "^1.0.0",

    "@shop/user-profile": "^1.0.0"

  }

}
```

### Cons

- Have to re-compile and release every single micro frontend in order to release a change to any individual part of the product.

## Run-time integration via iframes

- Use `iframe` to connect other micro frontends

````javascript
	<html>

	  <head>

	    <title>Shop</title>

	  </head>

	  <body>

	    <h1>Welcome to Shop</h1>

	    <iframe id="app-container"></iframe>

	    <script type="text/javascript"> const microFrontendsByRoute = {

	        '/': 'https://products.shop.com/index.html',

	        '/order': 'https://order.shop.com/index.html',

	        '/user-profile': 'https://profile.shop.com/index.html',

	      };

	      const iframe = document.getElementById('app-container');

	      iframe.src = microFrontendsByRoute[window.location.pathname]; </script>

	  </body>

	</html>
	````  
  

### Cons

- Difficult to make the page responsive
- Difficult to integrate between different parts of an application, make routing, history, and deep-linking more complicated

## Run-time integration via JavaScript

-  Each micro frontend is included on the page using a `<script>` tag, and upon load exposes a global function as its entry-point. The container application then determines which micro frontend should be mounted, and calls the relevant function to tell a micro frontend when and where to render itself.

```javascript
<html>

  <head>

    <title>Shop</title>

  </head>

  <body>

    <h1>Welcome to Shop</h1>

    <!-- These scripts don't render anything immediately -->

    <!-- Instead they attach entry-point functions to `window` -->

    <script src="https://products.shop.com/bundle.js"></script>

    <script src="https://order.shop.com/bundle.js"></script>

    <script src="https://profile.shop.com/bundle.js"></script>

    <div id="app"></div>

    <script type="text/javascript"> // These global functions are attached to window by the above scripts

      const microFrontendsByRoute = {

        '/': window.renderProducts,

        '/order': window.renderOrder,

        '/user-profile': window.renderUserProfile,

      };

      const renderFunction = microFrontendsByRoute[window.location.pathname];

      // Having determined the entry-point function, we now call it,

      // giving it the ID of the element where it should render itself

      renderFunction('app'); </script>

  </body>

</html>
````

## Run-time integration via [Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components)

- Define each micro frontend as an HTML custom element for the container to instantiate.

```javascript
<html>

  <head>

    <title>Shop</title>

  </head>

  <body>

    <h1>Welcome to Shop</h1>

    <!-- These scripts don't render anything immediately -->

    <!-- Instead they each define a custom element type -->

    <script src="https://products.shop.com/bundle.js"></script>

    <script src="https://order.shop.com/bundle.js"></script>

    <script src="https://profile.shop.com/bundle.js"></script>

    <div id="app"></div>

    <script type="text/javascript">

  // These element types are defined by the above scripts

      const webComponentsByRoute = {

        '/': 'micro-frontend-products',

        '/order': 'micro-frontend-order',

        '/user-profile': 'micro-frontend-user-profile',

      };

      const webComponentType = webComponentsByRoute[window.location.pathname];

      // Having determined the right web component custom element type,

      // we now create an instance of it and attach it to the document

      const root = document.getElementById('app');

      const webComponent = document.createElement(webComponentType);

      root.appendChild(webComponent);

</script>

  </body>

</html>
```

### Cons

- Don't support server-side rendering
- No 100% [browser support](https://caniuse.com/#search=custom%20elements)

## Cross-application communication

1. [Custom event](https://developer.mozilla.org/en-US/docs/Web/Events/Creating_and_triggering_events)
1. Cross-application communication via routing

## Serverside Rendering / Universal Rendering

- Server-side rendering is always a tricky problem.
- Use [Server Side Includes](https://en.wikipedia.org/wiki/Server_Side_Includes) to plug in page-specific content from fragment HTML files

# Conclusion

- Duplication of dependencies => increase payload size
- App performance
- Learning curve
- Only suitable for medium, large projects

## References

- [Micro frontends](https://micro-frontends.org/)
- [Micro Frontends from Martinfowler](https://martinfowler.com/articles/micro-frontends.html)
- [Micro frontends—a microservice approach to front-end web development](https://www.tomsoderlund.com/programming/micro-frontends-a-microservice-approach-to-front-end-web-development)
- [Awesome Micro Frontends](https://github.com/ChristianUlbrich/awesome-microfrontends)
