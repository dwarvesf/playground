---
tags: blockchain
---
context:
- contract khi được deploy lên thì sẽ luôn immutable (không đc chỉnh sửa edit). Nhưng real life thì sẽ luôn có vấn đề cần edit contract đó (fix bug, upgrade). 
- thông thường khi muốn thay đổi thì flow sẽ là: deploy contract mới -> move state contract cũ sang contract mới -> năn nỉ end-user đổi sang contract mới.
- có 1 hướng tiếp cận khác là proxy patterns, hướng này thì chủ yếu architecture contract để đạt được mục đích là có thể update contract sau khi đã deploy lên chain.
- này cơ bản là sẽ có 1 contract làm Proxy (contract này immutable) config dc 1 target contract (real contract handle logic của mình). End user sẽ luôn connect vào proxy contract, proxy contract sẽ sử dụng 1 kỹ thuật là `delegatecall` để fwd nó sang target contract.
- khi mình cần thay đổi code contract thì mình chỉ cần deploy contract mới lên chain, config proxy contract call sang contract mới là được.
https://blog.openzeppelin.com/proxy-patterns/

---

#### Citations