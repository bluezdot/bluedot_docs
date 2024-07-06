Giao thức RGB: Cipher (Nervos CKB team)
[Exploring Bitcoin Scaling Solutions: RGB ++ | by Conflux Devs | Medium](https://medium.com/@confluxdevs/exploring-bitcoin-scaling-solutions-rgb-f5738b02a2e3)
[RGB++ Protocol Light Paper (Translation) - English / CKB Development & Technical Discussion - Nervos Talk](https://talk.nervos.org/t/rgb-protocol-light-paper-translation/7790/5)

Keyword:
- RGB/RGB++ protocol
- single-use seals
- client-side validation (CSV)
- RGB Commitment
- CKB Cell/Shadow Cell (Turing-complete Bitcoin UTXO transactions validation)
- Isomorphic bindings
- Transaction folding
- Shared state across contracts
- Unhosted contract
- Non-interactive/interactive transfer
- AluVM
- Asset issuance protocol
- CKB script constrains
- xUDT standard
- Spore Protocol
- CoTa protocol
- Bitcoin Lightning Network
Hạn chế RGB:
- DA (Decentralized Authentication): Client k lưu full history, khó cung cấp bằng chứng mã hoá.
- P2P Network: Hạn chế về mặt tương tác. Phải cả sender, receiver live khi tạo giao dịch.
- VM & Contract Languages: AluVM còn non trẻ.
- Shared States & Unhosted Contracts:

RGB++ main process:
- Offchain computation
- BTC submit transaction
- CKB submit transaction
- Onchain validation

---
Explain:
- [A Quick Rundown On The Design Of RGB And RGB++ Protocols In Layman's Terms. (gate.io)](https://www.gate.io/learn/articles/a-quick-rundown-on-the-design-of-rgb-and-rgb-protocols-in-laymans-terms/2501)
	- P2P assets protocol
	- Cần có sự tương tác khi tạo giao dịch.
	- Bảo vệ quyền riêng tư, bởi vì không dùng giao thức đồng thuận -> tất cả node sẽ có thể thấy. Đổi lại, bảo mật có thể giảm, làm sao để cân bằng? -> CSV.
	- Client-side verify (Verify by yourself)
	- Ex:
		- Alice tạo transfer information tx.
		- Alice gửi transfer information tx cho Bob.
		- Bob check and confirm.
	- Mỗi người đều store data liên quan tới bản thân -> Không nhất quán (data islands)
	- Khi transfer phải gửi cả history utxo?
	- Workload of RGB protocol:
		- Người nhận thiết lập  transaction và quyết định UTXO dùng để liên kết RGB assetl.
		- Người gửi gửi history data của RGB assets và transaction data.
		- Người nhận verify asset & transactiions.
		- Người nhận gửi confirmation receipts.
		- Người gửi submit commitment lên mạng 
		- ![[Pasted image 20240705103727.png]]
	- Tốn chi phí, lưu trữ. User phải tự chạy client để xác thực dữ liệu, khi được gửi asset với lịch sử dữ liệu lớn, user cần phải verify toàn bộ lịch sử.
	- RGB Network không có consensus.

	- RGB++: Kết hợp RGB protocol + UTXO-supported public chains (CKB, Cardano, Fuel). Vì dựa trên third-party -> Centrailized.
	- RGB++ và RGB tương thích với nhau; tức có thể switch về RGB từ RGB++, và 2 giao thức có thể tồn tại đồng thời.
- [A quick guide to RGB and RGB++ protocol design in a few minutes: a vernacular guide (coinlive.com)](https://www.coinlive.com/news/a-quick-guide-to-rgb-and-rgb-protocol-design-in)

- Integration SDK: [ckb-cell/rgbpp-sdk: Utilities for Bitcoin and RGB++ asset integration (github.com)](https://github.com/ckb-cell/rgbpp-sdk)

