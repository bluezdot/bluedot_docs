https://docs.ton.org/develop/smart-contracts/messages#message-modes
```
export enum SendMode {  
    CARRY_ALL_REMAINING_BALANCE = 128,  
    CARRY_ALL_REMAINING_INCOMING_VALUE = 64,  
    DESTROY_ACCOUNT_IF_ZERO = 32,  
    PAY_GAS_SEPARATELY = 1,  
    IGNORE_ERRORS = 2,
    NONE = 0  
}
```
Mode = 0 => Trả phí bằng token gửi đi luôn
Mode = 1 => Trả phí bằng token balance
Mode = 2 or 16 => Tương tự send non-bounce or bounce
Mode = 32 => Destroy contract nếu balance = 0. Thường kẹp với 128
Mode = 64 => Gửi all token ngoại trừ token khởi tạo
Mode = 128 => Gửi all token

Warning: 128 + 32 + 16: Ko sử dụng combo này bởi vì tất cả token sẽ bounce vào tài khoản destroyed.
