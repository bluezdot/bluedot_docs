
- Script là ngôn ngữ lập trình mini (Lệnh thực thi) sử dụng cho cơ chế khoá outputs trong bitcoin transactions:
	- Locking script (ScriptPubKey) có trong mọi output của tx.
	- Unlocking script (ScriptSig/Witness) cần cung cấp để unlock output.

![[Pasted image 20240522184710.png]]

- Để giải mã 1 utxos khi muốn sử dụng, nối phần ScriptSig (hoặc Witness) với ScriptPubKey và giải mã từ trái sang phải dựa theo cấu trúc dữ liệu stack và opcode.
	- Valid: Khi chỉ còn OP_1 hoặc non-zero value
	- Invalid: Khi final stack:
		- Empty
		- OP_0
		- Nhiều hơn 1 element
		- OP_RETURN

- Các transactions được sắp xếp 2 scripts sẵn. Các node trên mạng sẽ giải mã lần lượt, nếu gặp failed ở transaction nào thì -> transaction đấy sẽ invalid và ko được mined trong một block đó.

- Tại sao không giải mã UTXO 1 cách đơn giản bằng cách so sánh public key với signature (chính là P2PK)? -> Bởi vì sử dụng Scripts sẽ tạo ra được nhiều loại locks -> Nhiều ứng dụng hơn. Để lock UTXOs 1 cách an toàn, các chuẩn dưới đây thường được sử dụng.

- Standard Scripts (before 2016):
	- P2PK (Pay 2 Public Key)
	- P2PKH (Pay 2 Public Key Hash)
	- P2MS (Pay 2 Multisig)
	- P2SH (Pay 2 Script Hash)
	- OP_RETURN
	![[Pasted image 20240523092311.png]]
- Standard Scripts (after SegWit update):
	- P2WPKH (Pay 2 Witness Public Key Hash)
	- P2WSH (Pay 2 Witness Script Hash)
	- P2TR (Pay 2 Taproot)

	![[Pasted image 20240523092332.png]]