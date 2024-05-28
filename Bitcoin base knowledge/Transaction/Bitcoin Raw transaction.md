Có 2 loại transaction:
- Legacy transaction
- SegWit transaction

## Legacy transaction

Ví dụ 1 raw transaction:
![[Pasted image 20240523162030.png]]

Format Raw Transaction : 
- Version: 4 bytes

- Input count: 1 byte

- Input:
	- Tx:
	- Vout
	- ScriptSig Size: 1 byte
	- ScriptSig
	- Sequence

- Output count: 1 byte

- Output:
	- Amount
	- ScriptPubKey size:
	- ScriptPubKey

	- Amount
	- ScriptPubKey size
	- ScriptPubKey

	- Locktime

Với 1 byte transaction data = 4 weight unit và 1 byte witness data = 1 weight unit. Từ raw transaction tính được:
- Bytes: 234 + 0
- Weight units = 234 x 4 + 0 x 1
- Virtual bytes = 234 x 1 + 0 x 0.25

## SegWid transaction
// todo:

Reference:
[Example tx above](https://learnmeabitcoin.com/explorer/tx/1db6251a9afce7025a2061a19e63c700dffc3bec368bd1883decfac353357a9d#output-1)
[Transaction Splitter](https://learnmeabitcoin.com/tools/)