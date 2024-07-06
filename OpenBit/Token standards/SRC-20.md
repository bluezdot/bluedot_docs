- Dựa trên Bitcoin Stamps. Sử dụng Counterparty transaction (Counterparty protocol) trước block 796k. Từ sau block 796k, encode trực tiếp SRC-20 transaction lên BTC, Counterparty transaction từ sau block này được tính là invalid.
- [Specification](https://github.com/stampchain-io/stamps_sdk/blob/main/docs/src20specs.md)
- [SRC20 Protocol | OpenStamp](https://docs.openstamp.io/introduction/src20-protocol)
- bc1q?

- Tính Account Balance:
	- Mint không được vượt quá max balance.
	- Deploys same tick -> invalid.
	- Negative mint/transfer -> invalid.
	- ...

- Transaction:
	- Owner của input đầu tiên là owner của tx.
	- Owner của output đầu tiên là dest của transfer.
	- Mint/deploys: vout-0 là minter hoặc deployer.
	- ScriptPubKeys: luôn là 1 of 3 cho SRC-20 (1 sigop)
	- 2 cái hash đầu là encoded data, hash cuối là 1 địa chỉ keyburn hợp lệ

- Decode transaction:
	- Lấy hết phần encoded data ra
	- Loại bỏ sign và nonce bytes (bytes đầu và cuối)
	- Nối lại và decode sử dụng ARC4 decoding.
	-  2 bytes đầu tiên sau khi decode là data length. Nối tiếp theo sau là `7374616d703a` (Là hexadecimal `stamp:`)
	- UTF-8 decodes phần dữ liệu còn lại => ...
	- Ví ko nên sử dụng space -> optimize transaction size -> optimize fees.


- Wallet support:
	- [The Stamp Wallet](https://www.thestampwallet.com/): Support deploy/mint/transfer SRC-20 và view STAMPS & SRC-20. Chưa support connect dApp.
	- [Leather Wallet](https://leather.io/): Support view STAMP và SRC-20. Support connect dApp.
