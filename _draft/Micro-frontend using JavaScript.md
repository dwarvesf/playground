---
tags: micro-frontend
---

**Run-time integration via JavaScript** - Each micro frontend is included onto the page using a `<script>` tag, and upon load exposes a global function as its entry-point. The container application then determines which micro frontend should be mounted, and calls the relevant function to tell a micro frontend when and where to render itself.

```html
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
```

