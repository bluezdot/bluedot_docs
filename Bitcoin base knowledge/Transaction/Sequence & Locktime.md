## Sequence
Sequence là 1 trường dữ liệu có trong mọi transaction input, giúp kiểm soát 1 tx có thể được mined hoặc tx có thể thay thế khi nó đang ở trong Memory Pool. Hay nói cách khác, sequence giúp kiểm soát điều kiện để 1 tx có thể được mined trong 1 block. Nếu nó chưa ở trạng thái 'final', việc thay thế tx đó trước khi nó được mined và nằm vĩnh viễn trong blockchain là khả thi.

Những thiết lập trường Sequence phổ biến:
1. Sequence <=0xFFFFFFFE — **Locktime**: Kiểu thiết lập này cho phép trường locktime được sử dụng.
2. Sequence <=0xFFFFFFFD — **Replace-By-Fee (RBF)**: Kiểu thiết lập này cho phép tính năng RBF, giúp người dùng có thể tăng phí trả cho transaction đang pending.
3. Sequence <=0xEFFFFFFF — **Relative Locktime**: Kiểu thiết lập này cho phép người dùng thiết lập locktime tương ứng với thời điểm khi output được được mined:
	1. 0x00000000 to 0x0000FFFF: Thiết lập relative locktime = số lượng **blocks** 
	2. 0x00400000 to 0x0040FFFF: Thiết lập relative locktime = số lượng **giây**
	Relative locktime áp dụng riêng biệt cho từng input

*Recommend*: *Lựa chọn phổ biến thường là 0xFFFFFFFD, để enable Locktime và RBF - 2 tính năng thường được sử dụng và khá hữu ích.*

## Locktime
Tương tự Sequence, Locktime là 1 trường dữ liệu trong mọi transaction input dùng để kiểm soát điều kiện khi nào tx được phép mined (cho tới 1 block height/timestamp).
- Nếu set Sequence = 0xFFFFFFFF (max) cho tất cả input, tx đó sẽ được coi là đã ở trạng thái 'final' và không thể thay thế hay ngăn chặn việc được mined.
- Nếu set 1 Sequence bất kì < 0xFFFFFFFF (hay <= 0xFFFFFFFE), tx sẽ không ở trạng thái final và có thể sử dụng locktime field


Liệu 1 tx có expired trong memory pool không?
- https://learnmeabitcoin.com/technical/transaction/input/sequence/#:~:text=expires%20from%20the%20memory%20pool
- [mempool - Do unconfirmed transactions expire after some time? - Bitcoin Stack Exchange](https://bitcoin.stackexchange.com/questions/43155/do-unconfirmed-transactions-expire-after-some-time)
Hiện tại: -mempoolexpiry = 336h ~ 14 ngày. Đây k phải là 1 đặc điểm tin cậy bởi vì bất kì ai có thể rebroadcast tx.