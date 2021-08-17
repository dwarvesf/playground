---
tags: blockchain, bitcoin, protocol
---

- BIP39 là protocol để generate ra mnemonic sentence (e.g seed phrase trong metamask)
- under the hood thì từ seed phrase đó sẽ generate một key wallet, muốn generate tiếp các key sau thì sẽ đc input từ seed phrases + (key1+key2) (ví dụ với metamask mình có thể generate đc nhieều key wallet, sau này khi sang máy khác import lại seed phrases thì các key đó cũng sẽ dc re-generate từ seed phrases chứ ko cần phải nhớ)
- dictionary bank của bip39 có 2048 word
- entropy của 1 metamask voi 12 phrase là 128 -> có 2^128 possible phrases. Nếu brute force 1 seed / 1 microsecond thì cũng sẽ mất 1,07 * 10^23 năm

**Source**
- https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki
- https://www.reddit.com/r/ledgerwallet/comments/6cjvam/probability_of_seed_phrase_collisionbrute_forcing/