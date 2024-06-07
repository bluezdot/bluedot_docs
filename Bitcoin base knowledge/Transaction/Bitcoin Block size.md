
## Giới hạn Block size

Một block có giới hạn 4,000,000 weight units = Block Header + Tổng transaction weight. Mỗi transaction có độ lớn khác nhau

![[Pasted image 20240524161243.png]]

## Các cách đo lường
1. Bytes: Sử dụng phổ biến trong máy tính
2. Weight Units (WU)
	WU và VB (mục dưới) sử dụng trong bitcoin blockchain để giảm độ lớn cho 1 số phần trong transaction data và được sử dụng khi tính toán lượng transactions có thể fit block cũng như tính fee.
	![[Pasted image 20240524160022.png]]
	
| Field    | Multiplier |
| -------- | ---------- |
| version  | x4         |
| marker   | x1         |
| flag     | x1         |
| input    | x4         |
| output   | x4         |
| witness  | x1         |
| locktime | x4         |

3. Virtual Bytes (VB): Tương tự WU. Nhưng tất cả chia 4.
   Cụ thể: 

| Field    | Multiplier |
| -------- | ---------- |
| version  | x0.25      |
| marker   | x0.25      |
| flag     | x0.25      |
| input    | x1         |
| output   | x1         |
| witness  | x0.25      |
| locktime | x1         |

Lý do phần witness data được tính với độ lớn ít hơn là gì? 
- Điều này giúp cần bằng hơn giữa chi phí tạo output và chi phí sử dụng output. Phần witness data chính là phần dữ liệu để sử dụng output (signature).
![[Pasted image 20240603111356.png]]