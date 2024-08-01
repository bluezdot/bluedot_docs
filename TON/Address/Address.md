User-friendly: EQDKbjIcfM6ezt8KjKJJLshZJJSqX7XOA4ff-W72r5gqPrHF  
Raw: 0:ca6e321c7cce9ecedf0a8ca2492ec8592494aa5fb5ce0387dff96ef6af982a3e

| Address beginning | Binary form | Bounceable | Testnet-only |     |
| :---------------: | :---------: | :--------: | :----------: | --- |
|       E...        |  000100.01  |    yes     |      no      |     |
|       U...        |  010100.01  |     no     |      no      |     |
|       k...        |  100100.01  |    yes     |     yes      |     |
|       0...        |  110100.01  |     no     |     yes      |     |

### Account ID
- account_id = hash(initial code, initial state)

### Addresses state
- nonexist: Chưa có bất kì transaction nào, chưa chứa code.
- uninit: Có chứa data liên quan đến balance và meta info. Chưa có persistent data/smart contract code. Ex: xảy ra khi nonexist và có ai đó gửi tokens đến.
- active: Chứa smart contract code, persistent data và balance.
- frozen: Không thể thực hiện hành động gì. Trạng thái này chỉ chứa 2 hashes của trạng thái trước: code & state cells. Để unfreeze, gửi internal message gồm state_init và code lưu trữ hashes mô tả ở trên cùng với 1 lượng TON. (https://unfreezer.ton.org/)

Địa chỉ của TON Foundation: https://tonscan.org/address/EQCD39VS5jcptHL8vMjEXrzGaRcCVYto7HUn4bpAOg8xqB2N
