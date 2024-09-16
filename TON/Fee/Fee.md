- Basic: https://docs.ton.org/develop/smart-contracts/fees
- Low-level: https://docs.ton.org/develop/howto/fees-low-level#computation-fees
- NFT Market thường lấy thêm 1TON và hoàn 1 - txFee sau đó: https://docs.ton.org/develop/smart-contracts/fees#:~:text=That%20is%20why%20even%20NFT%20marketplaces%20usually%20take%20an%20extra%20amount%20of%20TON%20(~1%20TON)%20and%20return%20(1%20%2D%20transaction_fee)%20later.
- Overview: https://telegra.ph/Commissions-on-TON-07-22

- Công thức: 
```
	Fee = storage_fees (1)
		+ in_fwd_fees (2)
		+ computation_fees (3) 
		+ action_fees (4)
		+ out_fwd_fees (5)
```

`(1) storage_fees`: Phí lưu trữ contract mỗi giây trên blockchain. Chi trả mỗi khi nhận hay gửi tx.
	+ Account state -> present time.
	+ storage_fee = (cells_count * cell_price + bits_count * bit_price) * time_delta /2^16.
		+ `cell_price` và `bit_price` phụ thuộc config mạng.
	
`(2) in_fwd_fees`: Phí vận chuyển messages từ offchain (External msg) đến các validators.

`(3) computation_fees`: Phí chi trả cho tính toán trong TVM.
	+ computation_fees = total computation cost

`(4) action_fees`: Phí thực thi các actions sau khi tính toán từ bước trước: cập nhật contract code, cập nhật thư viện, gửi out going message, etc.
	+ action_fees = sum(out_ext_msg_fwd_fee) + sum(int_msg_mine_fee)
	+ Hành động cần trả phí actions: 
		+ `SENDRAWMSG`, `RAWRESERVE`, `RAWRESERVEX`, `SETCODE`, `SETLIBCODE`, `CHANGELIB`, `FB08–FB3F`.

`(5) out_fwd_fees`: Phí gửi msg từ onchain -> offchain service & blockchain bên ngoài
	+ msg_fwd_fees = (lump_price  + ceil((bit_price * msg.bits + cell_price * msg.cells) / 2^16))  
	+ ihr_fwd_fees = ceil((msg_fwd_fees * ihr_price_factor) / 2^16)

Tất cả khoản fee trên đều cố định là 1 khoản đơn vị gas, nhưng gas price sẽ không cố định.

## Fee's config file
- storage_fees = [p18](https://tonviewer.com/config#18)
- in_fwd_fees = [p24](https://tonviewer.com/config#24), [p25](https://tonviewer.com/config#25)
- computation_fees = [p20](https://tonviewer.com/config#20), [p21](https://tonviewer.com/config#21)
- action_fees = [p24](https://tonviewer.com/config#24), [p25](https://tonviewer.com/config#25)
- out_fwd_fees = [p24](https://tonviewer.com/config#24), [p25](https://tonviewer.com/config#25)


https://answers.ton.org/question/1487087471022837760/how-are-ton-transaction-fees-calculated