---
tags: 
---
Để giải quyết vấn đề này thì đầu tiên mình nghĩ  đến chuyện sử dụng hàm: 
`export async function getServerSideProps(context)`
Dùng biến `context` (cái này kiểu như `*gin.Context` trong golang) ta có thể access đc property `req` (chính là http request) sau đó lấy ra được hostname.
`const hostname = context.req.host; // vincenzo `
Hostname chính là subdomain (username của user) =>  dùng subdomain này, query info của user và content của blog => render ra trang html gửi về user.
Cách này work nhưng vấn đề là khi chúng ra sử dụng `getServerSideProps`, nextjs sẽ render trang web của chúng ta theo cơ chế `server side rendering (SSR)` (render per request) => ảnh hưởng đến performance

Chuyển sang dùng cơ chế `Static Generation (SG)` thì lại không work vì hàm `getStaticProps`  chỉ chạy trong lúc build (compile time), không thể access được host name (runtime)

---

#### Citations