Raw: 0:ca6e321c7cce9ecedf0a8ca2492ec8592494aa5fb5ce0387dff96ef6af982a3e
User-friendly: EQDKbjIcfM6ezt8KjKJJLshZJJSqX7XOA4ff-W72r5gqPrHF (4 kiểu dưới).

| Address beginning | Binary form | Bounceable | Testnet-only |
| :---------------: | :---------: | :--------: | :----------: |
|       EQ...       |  000100.01  |    yes     |      no      |
|       UQ...       |  010100.01  |     no     |      no      |
|       kQ...       |  100100.01  |    yes     |     yes      |
|       0Q...       |  110100.01  |     no     |     yes      |

### Account ID
- account_id = hash(initial code, initial state)
### Workchain ID
- Masterchain: workchain_id = -1
- Basic workchain: workchain_id = 0. Hiện tại chỉ có 1 basic workchain_id, sau này có thể có nhiều hơn.
### Address of Smart Contract
- workchain_id:account_id
### Addresses state
- nonexist: Chưa có bất kì transaction nào, chưa chứa code.
- uninit: Có chứa data liên quan đến balance và meta info. Chưa có persistent data/smart contract code. Ex: xảy ra khi nonexist và có ai đó gửi tokens đến.
- active: Chứa smart contract code, persistent data và balance.
- frozen: Không thể thực hiện hành động gì. Trạng thái này chỉ chứa 2 hashes của trạng thái trước: code & state cells. Để unfreeze, gửi internal message gồm state_init và code lưu trữ hashes mô tả ở trên cùng với 1 lượng TON. (https://unfreezer.ton.org/)

### Lý do không chỉ dùng Raw Address
- When using the raw address format, it's not possible to verify addresses to eliminate errors prior to sending a transaction. This means that if you accidentally add or remove characters in the address string prior to sending the transaction, your transaction will be sent to the wrong destination, resulting in loss of funds.
- When using the raw address format, it's impossible to add special flags like those used when sending transactions that employ user-friendly addresses. To help you better understand this concept, we’ll explain which flags can be used below.

### Cấu trúc địa chỉ User-friendly
36 bytes:
- flags - 1 byte
	- isBounceable
	- isTestnetOnly
	- isUrlSafe
- workchain_id - 1 byte (Giống nhau cho cả 4 loại)
- account_id - 32 bytes (Giống nhau cho cả 4 loại)
- address verification - 2 bytes

### Bounceable vs. Non-Bounceable address
- Mục đích chính là sự an toàn cho funds của người gửi.

Địa chỉ của TON Foundation: https://tonscan.org/address/EQCD39VS5jcptHL8vMjEXrzGaRcCVYto7HUn4bpAOg8xqB2N

Ref: https://docs.ton.org/learn/overviews/addresses


