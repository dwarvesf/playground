---
tags: blockchain, evm, zk, zk-snarks
author: Pham Ngoc Thanh
---

Trước khi bắt đầu, bạn cần nắm được kiến thức về zero-knowledge (ZK) và cách thức hoạt động căn bản của Block và cơ chế đồng thuận PoS hay PoW. 

### ZK-SMARKs là gì?

ZK-SNARK is an acronym for Zero-Knowledge Succinct Non-Interactive Argument of Knowledge. The ZK-SNARK protocol has the following qualities:
- Zero-knowledge: A verifier can validate the integrity of a statement without knowing anything else about the statement. The only knowledge the verifier has of the statement is whether it is true or false.
- Succinct: The zero-knowledge proof is smaller than the witness and can be verified quickly.
- Non-interactive: The proof is 'non-interactive' because the prover and verifier only interact once, unlike interactive proofs that require multiple rounds of communication.
- Argument: The proof satisfies the 'soundness' requirement, so cheating is extremely unlikely.
- (Of) Knowledge: The zero-knowledge proof cannot be constructed without access to the secret information (witness). It is difficult, if not impossible, for a prover who doesn’t have the witness to compute a valid zero-knowledge proof.
For the ZK-SNARK protocol to work, the creation of a Common Reference String (CRS) is necessary: ​​The CRS provides public parameters to prove and verify valid proofs. The security of the proof system depends on the CRS setting; If the information used to create the public parameters falls into the possession of malicious actors, they can create false validators.
- Some ZK-rollups attempt to solve this problem by using multiparty computation (MPC), involving trusted individuals, to create public parameters for the ZK-SNARK circuit. Each party contributes a random number (called "hazardous waste") to the construction of the CRS, which they must destroy immediately.
- Trusted settings are used because they increase the security of the CRS setup. As long as an honest participant discards their input, the security of the ZK-SNARK system is guaranteed. However, this approach still requires the trust of the stakeholders to erase their sampled randomness and not undermine the security guarantees of the system.
- Reliability assumptions aside, ZK-SNARK is very popular because of its small proof size and continuous time verification. Since verifying proofs on L1 constitutes a greater operating cost of ZK-rollup, L2 uses ZK-SNARK to generate proofs that can be quickly and cheaply verified on the Mainnet.

ZK-SNARK is a protocol for generating zero-knowledge proofs to verify the authenticity of information without exposing the underlying data. The acronym means Zero-Knowledge Succinct Non-Interactive Argument of Knowledge.

Một giao thức ZK-SNARK liên quan đến hai bên: người đăng tin (Alice) và người xác minh (Bob). Người xác nhận (Alice) là bên đưa ra yêu cầu, trong khi người xác minh (Bob) là bên chịu trách nhiệm xác minh yêu cầu.
Thông tin được tham chiếu trong yêu cầu được gọi là nhân chứng hoặc bí mật. Một câu châm ngôn (Alice) sử dụng cơ chế ZK-SNARK để tạo ra bằng chứng cho người xác minh (Bob) rằng tuyên bố đó là đúng… mà không tiết lộ thông tin được tham chiếu.

