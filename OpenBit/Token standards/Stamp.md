- Explorer: [BITCOIN STAMPS (stampchain.io)](https://stampchain.io/)
- Bao gồm: Classic (OLGA - does not require base64 encoding? ), SRC-20, SRC-721
- Là giao thức:
	- cho phép nhúng hình ảnh vào Bitcoin Blockchain -> Cho phép tính toàn vẹn và bất biến của tác phẩm nghệ thuật kĩ thuật số.
	- An toàn cho lưu trữ dữ liệu và linh động hơn so với Bitcoin Ordinals
- Cơ chế:
	- digital art -> base64 string.
	- Nối thêm vào đầu string prefix: "STAMP:".
	- Dữ liệu này được phân tán tới nhiều outputs sử dụng multi-sig (Nghiên cứu thêm [Counterpart protocol/Counterparty meta-protocol](https://krellenstein.com/adam/get/counterparty-whitepaper_2024-03-29.pdf)).
	- Mỗi Bitcoin Stamp nhận 1 số đặc biệt như là STT. 'For a Stamp to be officially recognized, it must meet certain rules, like being part of the first transaction that includes a valid "STAMP:base64" string.'
- Phân loại:
	- SRC-20: ...
	- SRC-721: ...
- Bitcoin STAMPS vs. Bitcoin Ordinals

|                  | Stamp                                                           | Ordinals                                                                                   |
| ---------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Data pruning     | Data được nhúng vào UTXOs, không thể prune.                     | Lưu ở witness data - Có thể prune bởi blockchain node.                                     |
| Data size & cost | 24x24 or higher. Fee thay đổi dựa vào size, giúp flexible size. | Limit size dựa trên block size. Giúp nhất quán phí giao dịch, nhưng không flexible về size |
| Signature type   | Multi-sig                                                       | Single-sig                                                                                 |
- github: [mikeinspace/stamps (github.com)](https://github.com/mikeinspace/stamps/tree/main?tab=readme-ov-file)
- swagger: [Swagger UI (stampchain.io)](https://stampchain.io/docs)
	- /api/v2/balance/{address}
	- /api/v2/src20/balance{address}
	- /api/v2/src20/balance{address}/{tick}
	- /api/v2/stamps/balance/{address}
- tool decode: 
	- [Decode - tool](https://jpja.github.io/Electrum-Counterparty/decode_tx.html)
	- [Decode - github](https://github.com/Jpja/Electrum-Counterparty/blob/master/decode_tx.html)
- Có thể hiển thị balance trên cả 84 và 86. Chỉ thực hiện được giao dịch sử dụng multi-sig transaction.
- Prefix: 434e545250525459/CNTRPRTY/5354414d503a/STAMP:

- Mua bán STAMPS: [OpenStamp](https://openstamp.io/)
- Top 3 SRC-20 tokens: [STAMPS](https://www.stampscan.xyz/tick?value=STAMP), [BITDN](https://www.stampscan.xyz/tick?value=BITDN), [KEVIN](https://www.stampscan.xyz/tick?value=KEVIN)

- Có thể support hiển thị balance SRC-20 và stamp. Chưa thể filter out ra khỏi bitcoin balance vì cần xử lí phần utxo của stamp (trên indexer của team stamp không thấy có). Cần cân nhắc việc support Stamp, cũng như SRC-20, RGB++ bởi vì dữ liệu hiện thấy khá là rác, trong khi đó việc support sẽ ảnh hưởng tới hiệu năng cũng như efford của team vì cần xử lí indexer cho cả STAMPS UTXOs và STAMPS balance.
- OLGA để tối ưu về mặt lưu trữ
- Index Stamp dựa trên transaction history, không dựa trên UTXOs set => Ko cần filter UTXOs balance.