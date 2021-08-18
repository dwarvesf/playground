---
tags: nextjs
---

### Nextjs Rewrites
Bế tắc => googling => sau 1 thời gian research thì tìm ra được một solution ntn.

Nextjs có 1 feature là `Rewrites`. Rewrites cho phép chúng ta map 1 cái income request  path cho một cái destination request path khác.  Chúng ta sẽ Rewrite ntn:

```async rewrites() {
    return [
      {
        has: [
          {
            type: "host",
            value: "(?<host>.*)",
          },
        ],
        source: "/",
        destination: "/hosts/:host",
      }
    ];
  },```
Sau khi apply rewrite, mỗi lần user truy cập `<username>.example.com` => request sẽ được rewrite lại thành `example.com/hosts/<username>`, ta hoàn toàn có thể sử dụng hàm `getStaticProps`  ( cơ chế SG) để get ra `username` => query user info => render html. => cải thiện performance 

P/s: bài viết liên quan đến nextjs nên bạn nào k làm với nextjs sẽ thấy khá khó hiểu. Mình thấy hay nên note lại, sau này a/c/e có gặp trường hợp tương tự có thể tham khảo .

Ref:
- https://nextjs.org/docs/basic-features/data-fetching
- https://nextjs.org/docs/api-reference/next.config.js/rewrites

---

#### Citations