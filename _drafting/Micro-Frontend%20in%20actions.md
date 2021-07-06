---
tags: 
---
**Build-time integration**
-    Publish each micro frontend as a package and have the container application include them all as library dependencies.

```
{
  "name": "@shop/container",
  "version": "1.0.0",
  "description": "E-commercial website",
  "dependencies": {
    "@shop/products": "^1.0.0",
    "@shop/order": "^1.0.0",
    "@shop/user-profile": "^1.0.0"
  }
}
```
**Cons**
-    Have to re-compile and release every single micro frontend in order to release a change to any individual part of the product.
|

---

#### Citations