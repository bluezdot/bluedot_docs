[https://medium.com/coinmonks/understanding-ton-transactions-how-to-track-transaction-results-and-utilize-tonclient-b992336eb3a3](https://medium.com/coinmonks/understanding-ton-transactions-how-to-track-transaction-results-and-utilize-tonclient-b992336eb3a3 "https://medium.com/coinmonks/understanding-ton-transactions-how-to-track-transaction-results-and-utilize-tonclient-b992336eb3a3")

### Transaction
Gồm:
- incoming message khởi tạo trigger tới contract.
- cập nhật contract dựa trên incoming message, như cập nhật storage.
- outgoing message gửi tới các tác nhân khác (optional).

Khác với các blockchain đồng bộ khác, giao dịch trên Ton là bất đồng bộ, bạn không thể lấy response từ destination smart contract trong cùng 1 transaction. Một lời gọi hợp đồng có thể mất vài blocks để xử lí, phụ thuộc vào tuyến đường message giữa nguồn và đích, tức các message để xử lí 1 hành động có thể nằm trên các block khác nhau.

### Track transaction status

- Check dựa trên seqno thay đổi. Không check chính xác được tx hash, có thể gặp lỗi khi thực hiện nhiều giao dịch trong 1 khoảng thời gian https://answers.ton.org/question/1542513974774337536/how-do-i-get-the-result-and-status-of-transactions-with-the-tonweb-sdk

### Message hash vs. Tx hash
https://answers.ton.org/question/1552695172104458240/what-is-the-difference-between-messagehash-and-transactionhash

