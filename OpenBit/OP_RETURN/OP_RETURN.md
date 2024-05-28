# OP RETURN

Trong 1 transaction Bitcoin bao gồm 2 dữ liệu chính:
- List các Inputs (Outputs của giao dịch trước): Xác định lượng bitcoin đầu vào trong giao dịch.
- List các Outputs (UTXOs): Xác định lượng bitcoin đầu ra trong giao dịch. Mỗi UTXO sẽ gắn với một địa chỉ sở hữu.

OP_RETURN là 1 dữ liệu nằm trong UTXO. Mỗi transaction chỉ có tối đa 1 UTXO chứa OP_RETURN. Runes Protocol dựa trên OP_RETURN này để định nghĩa thông tin Runes token như sau:
	1. Tìm UTXO đầu tiên có "OP_RETURN OP_PUSHNUM_13"
	2. Dữ liệu còn lại đi theo sau là Runes message. sử dụng để giải mã ra thông tin runes token (etch/mint/transfer/).

Ví dụ:
[Example rune transactions](https://mempool.space/tx/5b28a2071a3d04e2dce458590ee50b6a7f54e6b125c41016950349b601025fc7)
![[Pasted image 20240426174724.png]]

OP_RUNE, OP_RUNES không có trong định nghĩa của Bitcoin Blockchain. OP_RUNE chỉ là 1 cách gọi ngắn gọn cho "OP_RETURN OP_PUSHNUM_13".

OP_CAT: Ban đầu được sử dụng để nối 2 phần tử dữ liệu. Sau đó vì rủi ro về mặt bảo mật nên Update -> Transaction chứa OP_CAT sẽ invalid mà không cần bất cứ điều kiện nào khác. Gần đây OP_CAT đang được một số cộng đồng đề xuất fork lại (ref 3) để giúp phát triển được nhiều tính năng hơn trên bitcoin blockchain, nhưng cũng tiềm tàng nhiều rủi ro.
Hiện tại vẫn đang discuss và chưa được accept.
Ref: 
1. https://opcodeexplained.com/opcodes/OP_CAT.html (Ban đầu)
2. https://nftplazas.com/bitcoin-devs-reintroduces-op-cat/
3. https://github.com/bitcoin/bips/pull/1525 (Đề xuất fork cho OP_CAT mới)
4. Mastering bitcoin (trang 155)