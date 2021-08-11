---
tags: stale, cache
---
When you set the HTTP response header like below, this setting means
```text
Cache-Control: max-age=1, stale-while-revalidate=59
```
- If a request for the time is repeated within the next 1 second, the previously cached value will still be fresh, and used as-is, without any revalidation.
- If a request is repeated between 1 and 60 seconds later, then the cached value will be stale, but will be used to fulfill the API request. At the same time, "in the background," a revalidation request will be made to populate the cache with a fresh value for future use.
- If a request is repeated after more than 60 seconds, then the stale response isn't used at all, and both fulfilling the browser's request and the cache revalidation will depend on getting a response back from the network.

**Side note:**

**Reference **
- https://web.dev/stale-while-revalidate
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control
- https://nextjs.org/blog/next-9-5

---

#### Citations