---
tags: blockchain, defi
---

Các loại hack khác nhau
Làm thế nào bạn có thể giảm thiểu khả năng bị ảnh hưởng tiêu cực bởi hack?

### The Rug Pull
- Đột ngột loại bỏ phần lớn thanh khoản khỏi LP, việc mất mát đột ngột có thể tạo ra vòng xoáy tử thần cho mã thông báo vì chủ sở hữu mã thông báo cố gắng bán càng nhanh càng tốt để tiết kiệm lợi nhuận của họ => hình thức exit lừa đảo phổ biến, protocols xóa mọi dấu vết của phương tiện truyền thông xã hội và ôm tiền chạy (Ví dụ: meerkat Finance)
- Làm thế nào để tránh nó?
	- Kiểm tra thanh khoản bị khóa như thế nào: khóa thời gian? nhiều dấu hiệu
	- Ai đang ủng hộ nó
	- Mục đích của dự án là gì

### Khai thác kinh tế
- Flash Loan: cho phép vay số tiền lớn trong một khung thời gian rất ngắn. Sau đó, khoản vay này có thể được sử dụng để tận dụng các lỗ hổng trong code hoặc để thao túng giá cả và thu lợi nhuận từ hoạt động kinh doanh chênh lệch giá.
- Các khoản vay flash loan là các khoản vay không được phân cấp và an toàn, phải được trả lại trước khi giao dịch blockchain kết thúc. Nếu không được hoàn trả, hợp đồng thông minh sẽ đảo ngược giao dịch => khoản vay không bao giờ xảy ra ngay từ đầu. Bởi vì hợp đồng thông minh của khoản vay phải được thực hiện trong cùng một giao dịch mà nó được cho vay, người vay phải sử dụng các hợp đồng thông minh khác để thực hiện các giao dịch tức thì với các khoản vay trước khi giao dịch kết thúc.
- Hầu hết các cuộc tấn công flash loan đều liên quan đến việc thao túng giá token bằng cách sử dụng một lượng vốn lớn (Ví dụ: Harvest finance)
	1. Flash loan **50M USDT**
	2. Swap **11,4 triệu USDC** sang USDT => Giá USDT tăng
	3. Deposit **60,6 triệu USDT** vào volt, exchange **11,4 USDT** sang USDC => Giá USDT giảm
	4. Rút **61,1 triệu USDT** từ volt => một nửa lợi nhuận **1M USDT**, lặp lại 32 lần mà không cần bất kỳ thử nghiệm trước nào
	5. Chuyển đổi sang BTC và exit bằng BTC thông qua Tornado Cash, một dịch vụ cho phép thực hiện các giao dịch ẩn danh trên Ethereum => Che dấu vết của kẻ tấn công. Kẻ tấn công có thể rút thêm USDT ở bước 4 do giá USDT thay đổi

Flashloan được sử dụng để thao túng giá, cho phép bán chênh lệch giá ở những nơi không thể thực hiện được.
- Làm thế nào để tránh nó? Các protocol nên sử dụng các oracle đáng tin cậy
- Flashloan được sử dụng cho các phương thức tấn công khác: reentrancy, front running, arbitrage

### Arbitrage
- Arbitrage: Lợi dụng chênh lệch giá giữa các thị trường khác nhau để tạo ra lợi nhuận.
- Cơ hội kinh doanh chênh lệch giá có xu hướng giảm khi liquidity tăng lên và thị trường trở nên hiệu quả hơn.  If the pool is manipulated by flashloan, allow room for arbitrage then this may also be considered as an exploit





