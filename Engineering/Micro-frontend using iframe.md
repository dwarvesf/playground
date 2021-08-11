---
tags: micro-frontend
---

**Run-time integration via iframes** - Use `iframe` to connect other micro frontends.

``` html
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
```

**Cons** - Difficult to make page responsive - Difficult to integrate between different parts of application, make routing, history, and deep-linking more complicated |