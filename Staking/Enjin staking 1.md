### Nomination Pool
Khác so với Nomination Pool thông thường
1. subscribePoolInfo
	Không có consts.staking.historyDepth -> Tính APY
	Không có staking.erasTotalStake -> Tính APY
	Không có auctions. -> Tính Inflation // Todo: Check stakingInfomation
	Không có staking.erasValidatorReward -> Tính APY
2. subscribePoolPosition:
	**Không có nominationPools.poolMembers** -> Mình đang subscribe theo sự thay đổi của thông tin này. Hiện chưa tìm được api nào thay thế. Unbonding member thì có thể sử dụng nominationPools.unbondingMembers.
	Không có staking.maxExposurePageSize -> Không ảnh hưởng, có thể dùng hàm staking.maxNominatorRewardedPerValidator được.
	Không có nominationPools.metadata -> lấy min active stake.
3. getPoolTarget:
	Không có nominationPools.metadata -> lấy min active stake (ENJ nomination pool có stake được hoặc ko stake được)
4. Join:
	Cũ: bond, bondExtra
	Mới: chỉ có bond
5. Unbond
6. Withdraw

Cần check thêm các điều kiện để validate cho các actions.
-> Ngoài ra cả phần extrinsics và chainstate có các thông tin earlyBirdBonus, earlyBirdShares.
-> Tìm thử cách lấy amount sENJ của account
### Native Staking
Giống với relaychain native staking


### General Information
----
Cấu trúc chung ENJIN:
![[Pasted image 20240419105034.png]]

![[Pasted image 20240419112242.png]]

---
![[Pasted image 20240419113531.png]]
- **Nomination pool with liquid staking** Sau khi stake pool, user nhận được token sENJ thay thế.
    - **Liquidity token**: Mỗi pool sẽ tạo một token sENJ tương ứng, token sENJ stake từ pool a sẽ không tương đương với token sENJ được stake từ pool B. Sau mỗi era, các pool được trả thưởng, lượng token ENJ tăng lên, nhưng lượng sENJ đã phát hành là không đổi ⇒ Có sự thay đổi về tỉ lệ ⇒ User tăng tài sản. Mỗi pool sẽ chỉ phát hành một lượng sENJ cố định ⇒ Khi phát hành đủ sẽ k join được pool nữa.
    - **Low minimum (1 ENJ)**: Min amount in pool.
    - **Immediate exit**: Unstake bản chất là burn lượng sENJ đang có để đổi lấy ENJ (Khi này đổi sẽ dựa trên rate sENJ:ENJ). Có thể Unstake mà ko cần đợi bằng cách exchange sENJ - ENJ.
    - Để tạo pool cần 1 mint NFT đặc biệt gọi là Degen.
- **Direct Staking**
	- High minimum
	- Phải chọn validator
	- staked token is locked (Không thể sử dụng như sENJ)
	- stash/controller account
	- 28 ngày unbonding
	
![[Pasted image 20240419114401.png]]
- **ENJ -** ENJ is the native token of the Enjin network. It is the token staked in the pool.
- **sENJ -** sENJ is the liquid token that represents staked ENJ. It is minted when ENJ is staked and burned when ENJ is unstaked. It can also be exchanged for ENJ through the exchange pallet.
- **Degen Token -** The degen token is an NFT in a special collection. It is required to create a pool and is also used to manage the pool. The owner of this NFT can optionally receive a commission. Each token is only usable in one pool at a time.
- Degen có thể chuyển được. Ai sở hữu Degen thì sẽ sỡ hữu quyền manage pool và cả self-staked.

![[Pasted image 20240419120050.png]]
![[Pasted image 20240419120336.png]]

Mỗi lần payout, 20% được giữ lại và gửi cho pool's bonus account. Mỗi era, bonus account distribute bonus rw cho reward account và tăng dần và gửi hết ở cuối cycle.
Công thức: Bonus Balance / Remaining Eras (Need recheck).

![[Pasted image 20240419121233.png]]

Các action users:
- bond
- unbond
- withdraw_unbonded

#### Other related informations
---
Token: ENJ, cENJ, sENJ
MinAmount: 0.01 ENJ
Deposit ENJ để mint token mới trên Enjin Blockchain: cần deposit unit_price * total_supply (token mới). -> Khi tokens bị destroyed thì lượng deposit tương ứng sẽ trả về issuer's account. => MintAmount của token mới cũng phải có value >= 0.01 ENJ
- For NFTs, ...
- For FTs, ...
Trong ENJ, mọi token đều nằm trong collection. 
- Tạo Collection -> Quản lí Mint Policy, Market Policy, Explicit Royalty Currencies
- Tạo Token
---
TokenID Structure:
We can has upto 16 games (4bits), 256 servers (8bits), 65536 items classes (16bits). A TokenID is 128 bits -> 100 bits for tokenID.
Account có thể lưu trữ mọi loại tài sản trên mọi games, servers
VD: 0x05ffa34f000000000000000000000001 (game 5, server 255, class Sword, ID 1)
