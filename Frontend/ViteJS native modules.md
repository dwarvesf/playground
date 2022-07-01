---

tags:  frontend, native-modules, vitejs, esm

author:  Tran Hoang Nam

---
Before ES modules was supported in the browser, we have no native mechanism for authoring JavaScript in a modularized fashion. That is why the concept of **"bundling"** and tools like webpack, Rollup and Parcel exists to improved the development experience for frontend developers.

Howerver, when our project started to expand more, the amount of modules might increase from a hundred to thousands of modules which lead to performance bottleneck for **JavaScript-based** toolings. 

**Vite** take full advantage of the availability of native ES modules in the browser and the rise of JavaScript tools written in compile-to-native languages by introducing `pre-bundles dependancies` using `esbuild` which was written in Go which 10-100x faster than JavaScript-based bundlers.

---
### Server built architecture 

#### Bundle based dev server
Bundle based dev server like Webpack built your application by combinning all the source-code and modules into a JavaScript-based bundle, every thing is done on the server-side and when you change something, the entire application have to build from the start.

![](https://vitejs.dev/assets/bundler.37740380.png)

#### Native ESM based dev server
Vite appoarch was instead of bundling all everything on the server, it only bundle modules when the browser require it through HTTP request.

This architecture provide a faster dev server by avoid bundle all the application on the server and utilize the power of modules hadling of the browsers.

![enter image description here](https://vitejs.dev/assets/esm.3070012d.png)

### Update when built
Rebuilding the whole bundle after making changes to your source code in a bundler-based build system is inefficient for the obvious reason that the update speed would degrade linearly with the app's size.

**HMR (Hot module replacement)** is applied to native ESM in Vite. Vite consistently performs HMR updates quickly regardless of the size of your application by only needing to precisely invalidate the chain between the updated module and its nearest HMR boundary when a file is changed.

### Native modules in production
While `esbuild` is lightning-quick and a very capable bundler for libraries, some crucial features required for bundling apps, specifically code-splitting and CSS handling, are still **under development**. `Rollup` is currently more capable and adaptable in several areas and being used in production.

#### References

- https://vitejs.dev/guide/why.html
- https://www.telerik.com/blogs/whats-vite-guide-modern-super-fast-project-tooling



