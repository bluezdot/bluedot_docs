- Opcode for message: https://github.com/EmelyanenkoK/modern_jetton/blob/master/contracts/op-codes.func
- Messages layout: https://docs.ton.org/develop/smart-contracts/guidelines/ecosystem-messages-layout
- Logical time: [[Logical time - Lamport time (lt)]]

### Message delivery
- tx với lt bé hơn sẽ được xử lí trước.

Trường hợp 1:
![[Pasted image 20240802102913.png]]
Khá đơn giản. A nhận 1 external message và trigger 2 internal message tới B. Khi đó sẽ xác định được chắc chắn message 1 sẽ đến trước message 2.

Trường hợp 2:
![[Pasted image 20240802103029.png]]
A trigger 2 internal message tới B và C. Lúc này chưa chắc chắn được msg1 hay msg2 xử lí trước vì còn phụ thuộc vào length và validator sets. Nếu C ở shard chains khác thì messages có thể mất thêm vài blocks để đến được đích.
Msg1' và Msg2' cũng xảy ra 2 trường hợp và k xác định được msg nào sẽ về trước.

### Kết luận
- Cấu trúc bất đồng bộ gây khó khăn trong việc giám sát vận chuyển message
- Lt giúp hình thành chuỗi sự kiện và thứ tự giao dịch, nhưng không giám sát được thứ tự vận chuyển message

