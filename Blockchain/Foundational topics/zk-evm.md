ZK-EVM loại 1 cố gắng trở thành Ethereum tương đương hoàn toàn và không khoan nhượng. Họ không thay đổi bất kỳ phần nào của hệ thống Ethereum để giúp tạo bằng chứng dễ dàng hơn. Chúng không thay thế các hàm băm, cây trạng thái, cây giao dịch, biên dịch trước hoặc bất kỳ logic đồng thuận nào khác, bất kể ngoại vi như thế nào.


Advantage: perfect compatibility

Mục tiêu là có thể xác minh các khối Ethereum như ngày nay - hoặc ít nhất, xác minh phía lớp thực thi (vì vậy, logic đồng thuận chuỗi beacon không được bao gồm, nhưng tất cả các quá trình thực hiện giao dịch, hợp đồng thông minh và logic tài khoản được bao gồm) .

ZK-EVM loại 1 là những gì cuối cùng chúng ta cần để làm cho chính lớp 1 của Ethereum có khả năng mở rộng hơn. Về lâu dài, các sửa đổi đối với Ethereum được thử nghiệm trong ZK-EVM Loại 2 hoặc Loại 3 có thể được đưa vào Ethereum thích hợp, nhưng việc tái kiến ​​trúc như vậy đi kèm với sự phức tạp của riêng nó.

ZK-EVM loại 1 cũng lý tưởng để cuộn lên, vì chúng cho phép cuộn lại sử dụng lại nhiều cơ sở hạ tầng. Ví dụ: các ứng dụng khách thực thi Ethereum có thể được sử dụng nguyên gốc để tạo và xử lý các khối cuộn lên (hoặc ít nhất, chúng có thể được thực hiện sau khi rút tiền và chức năng đó có thể được sử dụng lại để hỗ trợ ETH được gửi vào cuộn lên), vì vậy công cụ chẳng hạn như trình khám phá khối, sản xuất khối, v.v. rất dễ sử dụng lại.

Bất lợi: tục ngữ thời gian

Ethereum ban đầu không được thiết kế dựa trên sự thân thiện với ZK, vì vậy có nhiều phần của giao thức Ethereum cần một lượng lớn tính toán để ZK-proof. Loại 1 nhằm mục đích sao chép chính xác Ethereum, và vì vậy nó không có cách nào để giảm thiểu sự kém hiệu quả này. Hiện tại, các bằng chứng cho các khối Ethereum mất nhiều giờ để sản xuất. Điều này có thể được giảm thiểu bằng cách sử dụng kỹ thuật thông minh để song song hóa rộng rãi câu tục ngữ hoặc về lâu dài bằng ZK-SNARK ASICs.

### Type 2 (fully EVM-equivalent)
ZK-EVM loại 2 cố gắng tương đương EVM chính xác, nhưng không hoàn toàn tương đương Ethereum. Có nghĩa là, chúng trông giống hệt Ethereum "từ bên trong", nhưng chúng có một số khác biệt ở bên ngoài, đặc biệt là trong cấu trúc dữ liệu như cấu trúc khối và cây trạng thái.

Mục tiêu là tương thích hoàn toàn với các ứng dụng hiện có, nhưng thực hiện một số sửa đổi nhỏ đối với Ethereum để giúp phát triển dễ dàng hơn và tạo bằng chứng nhanh hơn.