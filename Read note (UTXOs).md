
[Bitcoin’s UTXO Model: What Is It and How to Manage UTXOs | River](https://river.com/learn/bitcoins-utxo-model/#what-is-bitcoin-utxo-management)
- UTXOs là gì?: Tương tự 1 tờ tiền trong ví. Là output từ 1 giao dịch mà người nhận là bạn. Là input trong 1 giao dịch tương lai mà người sử dụng là bạn.
- UTXOs set: Tất cả UTXOs trên blockchain tại 1 thời điểm.
- Fee Bitcoin tính toán như nào? Dựa trên khối lượng dữ liệu phải xử lí trong một giao dịch -> Lượng inputs & outputs càng phức tạp thì càng tốn phí. Nhận nhiều small amount of bitcoin -> Trong tương lai, khi spend sẽ mất lượng fee lớn.
- Với model Inputs -> Outputs, vậy inputs đầu tiên lấy từ đâu ra? -> Coinbase transactions: Xảy ra ở đầu mỗi block, -> được miner sử dụng để đưa new bitcoin vào hệ thống giúp khởi tạo UTXOs ban đầu mà không cần prior inputs.
- Bitcoin dust: super small UTXO
- Ví hỗ trợ quản lí UTXOs: Sparrow, Trezor.
- Quản lí UTXOs:
	- Hợp nhất UTXOs khi phí thấp
	- Gán nhãn UTXOs
- UTXOs Model vs Acocunt Model: ![[Pasted image 20240517173129.png]]