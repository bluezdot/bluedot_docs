Em tìm hiểu thì theo official docs, owner của 1 inscriptions có thể tạo ra 1 collections bằng cách như sau:

- Liên tục tạo ra inscription mới, trong đó metadata sẽ có pointer tới satoshi number của parent inscription.
- Sau khi mint đủ Child inscription thì owner có thể burn parent inscription để dừng việc mint tiếp.
- Child inscription có thể là parent của inscription khác.

![[Pasted image 20240617095526.png]]

Ex: [https://magiceden.io/ordinals/marketplace/ordinalsigmax](https://magiceden.io/ordinals/marketplace/ordinalsigmax "https://magiceden.io/ordinals/marketplace/ordinalsigmax") Ngoài ra thì có trường hợp collection không có mối quan hệ parent - children nhưng Magic Eden vẫn đang gom thành 1 collection thì e chưa rõ phụ thuộc vào thông tin gì Ex: [https://magiceden.io/ordinals/marketplace/bitcoin-puppets](https://magiceden.io/ordinals/marketplace/bitcoin-puppets "https://magiceden.io/ordinals/marketplace/bitcoin-puppets") Với API mà mình đang có thì có thể query thông tin của Parent của 1 inscription, nhưng đang ko query được children từ parent. Em nghĩ trước mắt tập trung tới việc xử lí các collection có mối quan hệ parent - children trước, khả năng cần 1 API để lấy thông tin children của parent inscription, em thấy ở đây có thông tin [https://ordinals.com/children/a23843f5674e1cb2d408c8399e542ac1f556058a1a5646e818b3a5ac60830f92i0](https://ordinals.com/children/a23843f5674e1cb2d408c8399e542ac1f556058a1a5646e818b3a5ac60830f92i0 "https://ordinals.com/children/a23843f5674e1cb2d408c8399e542ac1f556058a1a5646e818b3a5ac60830f92i0") 

Ref: 
- official docs: [https://docs.ordinals.com/inscriptions/provenance.html#provenance:~:text=Ordinal%20Theory%20Handbook-,Provenance,the%20children%20of%20those%20sub%20inscriptions%20being%20items%20in%20those%20collections.,-Specification](https://docs.ordinals.com/inscriptions/provenance.html#provenance:~:text=Ordinal%20Theory%20Handbook-,Provenance,the%20children%20of%20those%20sub%20inscriptions%20being%20items%20in%20those%20collections.,-Specification "https://docs.ordinals.com/inscriptions/provenance.html#provenance:~:text=Ordinal%20Theory%20Handbook-,Provenance,the%20children%20of%20those%20sub%20inscriptions%20being%20items%20in%20those%20collections.,-Specification") 
- pull request: [https://github.com/ordinals/ord/pull/2388](https://github.com/ordinals/ord/pull/2388 "https://github.com/ordinals/ord/pull/2388") 
- leather blog: [https://leather.io/learn/parent-child-inscriptions#:~:text=are%20digital%20artifacts.-,What%20are%20Parent-Child%20Inscriptions%3F,to%20be%20linked%20to%20each%20other%20to%20verify%20a%20game%20milestone.,-The%20Future%20of](https://leather.io/learn/parent-child-inscriptions#:~:text=are%20digital%20artifacts.-,What%20are%20Parent-Child%20Inscriptions%3F,to%20be%20linked%20to%20each%20other%20to%20verify%20a%20game%20milestone.,-The%20Future%20of "https://leather.io/learn/parent-child-inscriptions#:~:text=are%20digital%20artifacts.-,What%20are%20Parent-Child%20Inscriptions%3F,to%20be%20linked%20to%20each%20other%20to%20verify%20a%20game%20milestone.,-The%20Future%20of")
- Conversation: https://discord.com/channels/987504378242007100/1069465367988142110/1252089448137494589
---
- 1 child có thể have multiple parent. https://github.com/ordinals/ord/issues/2494 (Chưa implement).
- Dựa trên genesis hash và address inscribe. Trường hợp này ko thấy cùng genHash: [Bitdogs Bitdog #3684 | Magic Eden](https://magiceden.io/ordinals/item-details/9f76256f7d381c870536b45b658a1571a70ada906ea1fe3c54f007f0c7ba2c64i0)
- [Provenance spec by casey · Pull Request #2278 · ordinals/ord (github.com)](https://github.com/ordinals/ord/pull/2278)

---
Tổng hợp thông tin collection có được lưu theo kiểu parent-child hay không:
![[Pasted image 20240617154215.png]]
Top 10 collection by Volume (Magic Eden):
1. NodeMonkes: No
2. Bitcoin Puppets: No
3. Runestone: Yes
4. Frucks: No
5. Ordinal Maxi Biz: No
6. Quantum Cats: Yes
7. Blob: Yes
8. Bitcoin Frogs: No
9. The Royals: No
10. Rune Pups: No
    
- Với collection lưu theo parent-child -> Có thể dùng data on-chain từ ord để xử lí (Ko xử lí được các collection có metadata lưu off-chain)
- Tất cả collection từ Magic Eden/OKX. Các inscription cùng collection được lưu thông tin và query dựa trên collection slug được lưu trữ bởi sàn. -> Có thể xử lí thông qua API của bên họ.
	  - OKX: [OKX](https://www.okx.com/web3/build/docs/waas/marketplace-retrieve-ordinal-listings "https://www.okx.com/web3/build/docs/waas/marketplace-retrieve-ordinal-listings")
	  - Magic Eden: [Magic Eden](https://docs.magiceden.io/reference/getcollection-1 "https://docs.magiceden.io/reference/getcollection-1")

---
- Khi khởi tạo -> lấy 25 inscriptions
- Khi load more: Lấy tiếp 25 inscription (offset-offset+25) (Cần mạng: Bitcoin testnet, bitcoin mainnet).
- Khi Reload trong màn NFTs: Remove hết inscription và khởi tạo lại 25 inscriptions
- Khi Reload Extension: Giữ nguyên lượng inscription hiện có.