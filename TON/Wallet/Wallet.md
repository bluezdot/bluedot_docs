Wallet V1 -> V4: https://medium.com/@ipromise2324/%E6%8E%A2%E7%B4%A2ton%E9%8C%A2%E5%8C%85-%E5%BE%9Ev1%E5%88%B0v4%E7%9A%84%E6%BC%94%E8%AE%8A%E5%8F%8Awallet-v4%E6%B7%B1%E5%BA%A6%E8%A7%A3%E6%9E%90-6d7dc562edf3

### V1
- https://github.com/ton-blockchain/ton/blob/master/crypto/smartcont/wallet-code.fc.
- Không query được seqno và public key từ contract 1 cách dễ dàng (Đã được giải quyết ở V1R2/V1R3).
- Không có `valid_until` check.

### V2
- https://github.com/ton-blockchain/ton/blob/master/crypto/smartcont/new-wallet-v2.fif
- Add `valid_until` to limit the tx is not be confirmed to late
- Add get public key method

### V3
- https://github.com/ton-blockchain/ton/blob/master/crypto/smartcont/wallet-v3-code.fif
- Add `subwallet_id` feature

### V4
- https://github.com/ton-blockchain/wallet-contract
- Integrate `plugins`

### V5
- UI: support v5 contract as separate account
- ...

### Special wallet
- https://docs.ton.org/participate/wallets/contracts
- Highload Wallet v3
- Highload Wallet v2
- Lockup Wallet
- Restricted Wallet