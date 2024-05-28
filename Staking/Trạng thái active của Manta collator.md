- Trong pallet của manta node thì nó có định nghĩa status trong candidateInfo này là trạng thái của collator tham gia mạng. Có extrinsics go_offline và go_online để tạm thời bật tắt chế độ active mà không cần unbond cho collator. 
- Thực tế khi query thông tin này thì dữ liệu trả về tất cả đều đang active, khác so với bên dApp của Manta. 
- Src của dApp thì e chưa tìm thấy, trước mình cũng tìm để xem cái withdraw time mà không thấy. 
--> Phương án: hỏi bên manta xem họ đang hiện Inactive theo thông tin onchain nào.

[https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/types.rs#L341](https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/types.rs#L341 "https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/types.rs#L341")

[https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/types.rs#L86](https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/types.rs#L86 "https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/types.rs#L86")

[https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/lib.rs#L1107](https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/lib.rs#L1107 "https://github.com/Manta-Network/Manta/blob/bd4aa433dfeeee1cfc867e46dabcfeed0cad77e4/pallets/parachain-staking/src/lib.rs#L1107")

---
Hi A, Can you let me know how to get on-chain information about the active/inactive status of collators?

In the collatorInfo, I see that all 65 collators are active. But on the dApp, there are some inactive collators.
Here is a collator account for references: "dfYCDPFoLhU9GjAu5L7qXqM3WJ6UHvkgsBRVj3PLR56cQDi1k"
![[Pasted image 20240410185024.png]]