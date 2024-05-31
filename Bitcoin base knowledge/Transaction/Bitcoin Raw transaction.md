Có 2 loại transaction:
- Legacy transaction
- SegWit transaction

## 1. Legacy transaction

### 1.1. Ví dụ 1 raw transaction:
![[Pasted image 20240523162030.png]]

### 1.2. Format Raw Transaction : 
- Version: 4 bytes

- Input count: 1 byte?

- Input:
	{	
	- Txid: 32 bytes
	- Vout: 4 bytes
	- ScriptSig size: 1 byte?
	- ScriptSig: phụ thuộc value scriptSig size
	- Sequence: 4 bytes
	},
	{
		...
	},
	(Số input phụ thuộc value input count)

- Output count: 1 byte?

- Output:
	{
	- Amount: 8 bytes?
	- ScriptPubKey size: 1 byte?
	- ScriptPubKey: phụ thuộc value của scriptPubKey size
	}
	(Số output phụ thuộc value output count)

- Locktime: 4 bytes

### 1.3. Tính size
Với 1 byte transaction data = 4 weight unit và 1 byte witness data = 1 weight unit. 
Trường hợp trên không có witness data vì là Legacy transaction! Từ raw transaction tính được:
- Bytes: 234 + 0
- Weight units = 234 x 4 + 0 x 1
- Virtual bytes = 234 x 1 + 0 x 0.25

## 2. SegWit transaction
### 2.1. Ví dụ 1 raw transaction:
![[Pasted image 20240531162536.png]]

### 2.2. Format Raw Transaction : 
- version: 4 bytes

- marker: 1 bytes (related to segwit)
- flag: 1 bytes (related to segwit)

- input count: 1 byte?

- Input:
	- txid: 32 bytes
	- vout: 4 bytes
	- scriptSig size: 1 byte?
	- scriptSig: phụ thuộc value của scriptSig size
	- sequence: 4 bytes
	(Số input phụ thuộc value input count)

- output count: 1 byte?

- Output:
	- amount: 8 bytes
	- scriptPubKey size: 1 byte?
	- scriptPubKey: phụ thuộc scriptPubKey size
	(Số output phụ thuộc value output count)

- Witness (releated to segwit):
	Witness Field
	- StackItem: 1 byte?
		- size: 1 byte?
		- item: Phụ thuộc vào value của size
		(Số item phụ thuộc value stackItem)
	(Số Witness Field phụ thuộc vào input count? -> RECHECK THIS)

- Locktime: 4 bytes

### 2.3. Cách tính
Với 1 byte transaction data = 4 weight unit và 1 byte witness data = 1 weight unit. 
Trường hợp trên chứa witness data! Từ raw transaction tính được:
- Bytes: xxx + yyy
- Weight units = xxx x 4 + yyy x 1
- Virtual bytes = xxx x 1 + yyy x 0.25

Với 
- xxx là tổng tất cả các bytes không liên quan tới segwit.
- yyy là tổng tất cả các bytes liên quan tới segwit.


## 3. Reference:
- Legacy transaction:
[Example tx above](https://learnmeabitcoin.com/explorer/tx/1db6251a9afce7025a2061a19e63c700dffc3bec368bd1883decfac353357a9d#output-1)
[Transaction Splitter](https://learnmeabitcoin.com/tools/)

- SegWit transaction:
[SegWit transaction](https://learnmeabitcoin.com/technical/transaction/)
[Multisig SegWit](https://learnmeabitcoin.com/explorer/tx/684cf742893df9f43e7f11646a3f70db05ebc673e48514b4a4b1a61f57d89a29)

## 4. Phụ lục (Ai đam mê thì đọc)
1. Version?
	- Version 1: Basic transaction (2009-current)
	- Version 2: [BIP68](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki)[Relative locktime](https://learnmeabitcoin.com/technical/transaction/input/sequence/#relative-locktime) (2015-current)
	Discuss: Tại sao không chỉ dùng 1 hoặc 2 bytes cho phần này? Sợ quá nhiều version trong tương lai? -> Nếu dùng 4 bytes như hiện tại thì sẽ có thể có max 4294967295 versions :D.
2. Marker? (Segwit)
	Luôn là bytes 00. Mục đích chỉ là để xác định đây là Segwit transaction
3. Flag? (Segwit)
	Luôn là bytes 01, hoặc lớn hơn. Mục đích là xác định version của Segwit transaction, cấu trúc có thể thay đổi trong tương lai.
4. Sequence & Locktime? Đã giải thích kĩ ở bài viết [[Sequence & Locktime]]
5. Byte Order?
	Có 2 loại order chính:
	- Natural Byte Order (Dev): Hay còn gọi là Native Byte Order/Internal Byte Order/Little Endian. Kiểu này là thứ tự sau khi đi ra từ hàm hash, thường được dùng qua các hàm hash và raw data.
	- Reverse Byte Order (User): Hay còn gọi là RPC Byte Order/Network Byte Order/Big Endian. Kiểu này là đảo ngược thứ tự sau khi đi ra từ hàm hash, thường được dùng ở high-level, như tìm transactions/blocks trên explorers.
6. ScripSig?
	Có thể hiểu là unlocking script, sử dụng để giải mã 1 UTXO. Ghép với phần locking script để giải mã và sử dụng UTXO. 
	Gọi là ScriptSig vì thường chứa signature.
	Trong trường hợp giao dịch là segwit, nên set scriptSig size là 00 và scriptSig là "".
	Discuss: Tôi đoán là để tiết kiệm phí, vì phần unlocking code sẽ ở trong witness field.
7. ScriptPubKey?
	Có thể hiểu là locking script, sử dụng để mã hoá 1 UTXO. Tạo ra ở trong output của 1 giao dịch. Để sử dụng được UTXO này trong tương lai, cần unlocking script ghép vào và giải mã.
	Gọi là ScriptPubKey vì thường chứa PublicKey.
8. Witness?
	Để lưu trữ phần unlocking code khi unlock inputs P2WPKH, P2WSH, P2TR locking scripts. Có thể hiểu đơn giản đây là nơi mới để lưu trữ phần scriptSig (Vì 1 số lí do về tối ưu storage trên blockchain).
	Witness gồm nhiều witness field. Mỗi witness field dùng để unlock 1 input. 
	Ví dụ: P2WPKH: `0247{signature}21{publickey}`
		 02 items - size: 47 - item: signature - size 21 - item: public key
	Nếu có legacy input cùng với segwit input, phần legacy input vẫn phải có 1 witness field 00
9. wTXID
10. 