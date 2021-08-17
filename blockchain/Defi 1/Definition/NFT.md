---
tags: blockchain, defi, nft
---

NFT là viết tắt của non-fungibility tokens và chúng là một trong những loại token có thể đại diện cho quyền sở hữu hàng hóa kỹ thuật số khan hiếm như tác phẩm nghệ thuật hoặc đồ sưu tầm.
Trong kinh tế học, tính thay thế là đặc tính của hàng hóa hoặc hàng hóa mà mỗi đơn vị riêng biệt có thể thay thế cho nhau và không thể phân biệt được với nhau. 
VD: hàng hóa, tiền tệ.

![](https://finematics.com/wp-content/uploads/2020/09/nfts-fungibility-2048x1122.png)

Không thay thế được: 
VD: Tranh vẽ gốc. 

Thuộc tính của NFT: 
- Unique: Mỗi NFT là duy nhất, không có bản sao thay thế tương đương
- Indivisible: không thể phân chia NFT thành nhiều phần có mệnh giá nhỏ hơn, không thể trade một phần NFT

NFT được mint bằng smart contract, trong đó quy định một số thuộc tính của NFT như TokenID (unique), owner address và một số thuộc tính khác để nhận dạng NFT (graphic, image,...). NFT được giao dịch trên blockchain, nên tất cả các history transaction từ lúc được mint đến các giao dịch qua nhiều owner sẽ được minh bạch.

Mặc dù NFT có thể được thực hiện trên bất kì blockchain nào hỗ trợ smart contract, nhưng hiện nay phổ biến nhất là ERC-721 và ERC-1155 trên Ethereum
- ERC-721 là tiêu chuẩn chung để tạo NFT, ERC-721 cho phép tạo contract có thể được sử dụng để tạo các token có thể phân biệt với các thuộc tính khác nhau. ERC721 được tạo ra bằng cách viết code trong smart contract theo một chuẩn chung, bằng ngôn ngữ như Solidity.
- ERC-1155 là tiêu chuẩn để tạo cả NFT và token có thể thay thế. VD: game có 2 loại asset, non-fungibility và fungibility. 

Lưu trữ:
- NFT được lưu on-chain, thường là blockchain đầu tiên nơi NFT được mint. NFT được mint trên blockchain này có thể không được transfer sang chain khác. 
- "Nội dung" của NFT (graphic, image,...) được lưu off-chain. Dữ liệu trong NFT sẽ lưu nơi NFT đang được lưu trữ trên một server nào đó, hoặc IPFS 
	- IPFS:  (InterPlanetary File System):  decentralized, dữ liệu tải lên được mã hoá và tải lên các máy tính khác cùng tham gia với mạng => ko sợ máy chủ sập + truy cập nhanh hơn, có thể tải dữ liệu từ máy chứa dữ liệu gần nhất. 
	
**Source**
https://www.christies.com/features/NFT-101-Collection-Guide-to-NFT-11654-7.aspx
https://finematics.com/what-are-nfts-and-how-can-they-be-used-in-defi/