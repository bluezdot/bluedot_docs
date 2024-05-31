Fee = Tổng input - tổng Output
![[Pasted image 20240523162246.png]]

## Memory pool
Memory Pool chứa pending transaction, Miner thường chọn các transaction có fee cao với space nhỏ để đưa vào candidate block.
![[Pasted image 20240523162851.png]]
Nếu lượng txs trong memory pool có thể fit trong block tiếp theo, chỉ cần set [minimum fee](https://learnmeabitcoin.com/technical/transaction/fee/#minimum-relay-fee).

## Fee rates
Fee rates = Fee/block size
![[Pasted image 20240523164323.png]]

3 ways measure:
1. sats/byte (deprecated): Trước đây, max size của 1 block là 1M bytes. Từ SegWid upgrate, chuyển bytes -> weight unit.
2. sats/wu (Used Internally): SegWid upgrate quy đổi max size block từ 1M bytes -> 4M weight unit. Weight unit tính bằng cách: Với tx data, lấy 4 x bytes. Với witness data, lấy 1 x bytes.
![[Pasted image 20240523165655.png]]
3. sats/vbyte (Most common): vbyte tương tự wu. Đơn giản là wu/4. Bởi vì wu là upgrade mới nên có nhiều node vẫn đi theo software cũ (chưa upgrade version) -> Sẽ sử dụng cách tính theo vbytes. Với Legacy transaction (Không có phần witness data), sats/byte sẽ vẫn = sats/vbyte; với Segwid transaction (Có witness data), sats/byte sẽ chênh lệch với sats/vbyte. Khi đó sử dụng sats/vbyte sẽ dễ dàng so sánh và hiểu được trong cả 2 trường hợp. Chính vì vậy cách tính sats/wu thường được người dùng đưa trở lại sats/vbyte để đồng nhất trong 1 scale (thay vì lúc thì tính theo sats/wu, lúc thì tính theo sats/bytes).
Example (Mempool):
![[Pasted image 20240523164807.png]]

## Fee Bumping
Khi người dùng send 1 tx low-fee tới Memory Pool và hiện tại đã có rất nhiều transactions, tỉ lệ tx low-fee được chọn sẽ thấp và có thể phải đợi lâu. Lúc này có thể thay đổi fee để tăng khả năng được chọn. Có 2 cách
1. Replace By Fee (RBF - BIP125)
	Để kích hoạt được tính năng này, cần phải set 1 sequence field bất kỳ thành `0xFFFFFFFD` hoặc nhỏ hơn. Khi đó người dùng có thể gửi transaction mới tới memory pool với fee cao hơn. Khi node hoặc miner nhận được tx sử dụng cùng inputs và với fee cao hơn, họ sẽ thay thế với tx cũ trong mempool. Nếu RBF ko enabled, chỉ có thể đợi, hoặc sử dụng CPFP.
2. Child Pays For Parent (CPFP)
	Cách này tận dụng 2 nguyên tắc:
	- Bạn có thể sử dụng output của transaction đang nằm trong memory pool
	- Miner luôn thêm parents tx của bất kì tx nào được đưa vào block.
	Lúc này, khi bạn đưa vào 1 child tx có fee rất ngon. Mặc dù fee của parent tx thấp, miner sẽ tính toán average fee nhận được của cả 2 tx, nếu đủ tốt thì sẽ đưa cả 2 vào block mới.
	Không có lý do nào để xử dụng CPFP thay thế cho RBF bơi vì nó không có ích lợi gì hơn về mặt kinh phí kể cả cách sử dụng. Lý do duy nhất sử dụng CPFP là khi RBF ko enable và tx của bạn bị kẹt trong Memory pool

## Minimum Relay Fee
Mỗi node có thể set min relay fee. Lý do của việc set min fee là để tránh lãng phí tài nguyên cho những giao dịch low-fee hoặc no-fee. Default min relay fee hiện tại là 1 sat/vbyte.
Tuy nhiên, min relay fee chỉ là 1 chiến lược, không phải consensus rule. Cho nên việc 1 no-fee tx được mined không phải là bất khả thi.

Để check min relay fee node của bạn: `bitcoin-cli getmempoolinfo`.
Để set: thay đổi `minrelaytxfee=<amt>` trong Bitcoin Core config file.

