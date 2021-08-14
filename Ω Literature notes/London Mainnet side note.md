---
tags: blockchain, ethereum
---

lost track of the time for this. london hardfork sẽ go live ở mainnet vào block 1296500 (Aug 3-5)
- Thay đổi chính mà mọi người quan tâm chắc chắn là EIP-1559 -> implementation này sẽ thay đổi cơ chế transaction fee của ETH
- Lúc trước cơ chế giá của ETH sẽ là `transaction_fee = gas * gasPrice` 1 function execute sẽ tốn X gas, gasPrice là do user set, miner sẽ lựa các transaction có gasPrice cao để execute trước
- Khi thay đổi thì `transaction_fee = base_fee + priority_fee (tip)`. base_fee sẽ bị burn đi và miner sẽ giữ lại priority_fee. eth bảo rằng làm vậy sẽ remove incentive việc miner cố tình manipulate fee để gain đc nhiều tx_fee nhat có thể
- Nhìn chung thì fee mà miner nhận được sẽ giảm nên update này còn vài cái để balance lại là tăng block size lên gấp đôi (x2 transaction trong 1 block) việc này cũng sẽ giảm congestion trong network -> tăng giá trị của ETH
- anw in my opinion thì hard fork này là 1 stepping stone tương đối lớn cho ETH2.0, vì với cơ chế tx_fee này sẽ phù hợp với 1 network nhiều tx + ít congestion của eth2.0 hơn

---
More
[London Mainnet Announcement](https://blog.ethereum.org/2021/07/15/london-mainnet-announcement/)