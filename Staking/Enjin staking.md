
# General Information
---
### Nomination pool
![[Pasted image 20240419113531.png]]
- **Nomination pool with liquid staking** Sau khi stake pool, user nhận được token sENJ thay thế.
    - **Liquidity token**: Mỗi pool sẽ tạo một token sENJ tương ứng, token sENJ stake từ pool A sẽ không tương đương với token sENJ được stake từ pool B. Sau mỗi era, các pool được trả thưởng, lượng token ENJ tăng lên, nhưng lượng sENJ đã phát hành là không đổi ⇒ Có sự thay đổi về tỉ lệ ⇒ User tăng tài sản. Mỗi pool sẽ chỉ phát hành một lượng sENJ cố định ⇒ Khi phát hành đủ sẽ k join được pool nữa.
    - **Low minimum (1 ENJ)**: Min amount của pool.
    - **Immediate exit**: Unstake bản chất là burn lượng sENJ đang có để đổi lấy ENJ (Khi này đổi sẽ dựa trên ratio sENJ:ENJ tại thời điểm đó). Có thể sử dụng sENJ mà ko cần đợi bằng cách exchange sENJ - ENJ hoặc transfer sENJ.
    - Để tạo pool cần mint 1 NFT đặc biệt gọi là Degen.
	- 28 ngày unbonding

### Token overview
![[Pasted image 20240419114401.png]]
- **ENJ -** ENJ is the native token of the Enjin network. It is the token staked in the pool.
- **sENJ -** sENJ is the liquid token that represents staked ENJ. It is minted when ENJ is staked and burned when ENJ is unstaked. It can also be exchanged for ENJ through the exchange pallet.
- **Degen Token -** The degen token is an NFT in a special collection. It is required to create a pool and is also used to manage the pool. The owner of this NFT can optionally receive a commission. Each token is only usable in one pool at a time. Degen có thể chuyển được, ai sở hữu Degen thì sẽ sỡ hữu quyền manage pool và cả self-staked.

### Reward mechanisim
Có 2 loại balances trong 1 pool:
- Reward Balance: Chứa reward chung của pool.
- Bonus Balance: 1 Phần reward của pool và trả thưởng dần trong cycle.
![[Pasted image 20240419120050.png]]
Mỗi lần payout, 20% được validator giữ lại và gửi cho mỗi pool's Bonus account. 80% gửi trực tiếp về pool's Reward account.

![[Pasted image 20240419120336.png]]
Mỗi era, Bonus account chia bonus reward cho Reward account theo cơ chế tăng dần và gửi hết ở cuối cycle.
Công thức: Bonus Balance / Remaining Eras (Need recheck).

![[Pasted image 20240419121233.png]]

Các actions users:
- **bond**
- **unbond**
- **withdraw_unbonded**
- **manage sENJ (transfer, exchange)**
# Technical
---
### Nomination Pool
Khác so với Nomination Pool thông thường
1. subscribePoolInfo
	Không có consts.staking.historyDepth -> Tính APY
	Không có staking.erasTotalStake -> Tính APY
	Không có auctions. -> Tính Inflation // Todo: check stakingInfomation
	Không có staking.erasValidatorReward -> Tính APY
2. subscribePoolPosition:
	**Không có nominationPools.poolMembers** -> Mình đang subscribe theo sự thay đổi của thông tin này. Hiện chưa tìm được API nào thay thế. Cần theo dõi sENJ.
	Unbonding member thì có thể sử dụng nominationPools.unbondingMembers.
	Không có staking.maxExposurePageSize -> Không ảnh hưởng, có thể dùng hàm staking.maxNominatorRewardedPerValidator được.
	Không có nominationPools.metadata -> lấy min active stake.
3. getPoolTarget:
	Không có nominationPools.metadata -> lấy min active stake pool (ENJ nomination pool cóthể không có min active stake mà chỉ giới hạn tham gia pool khi pool bị đầy).
4. Join:
	Cũ: bond, bondExtra
	Mới: chỉ có bond
5. Unbond
6. Withdraw

Recheck điều kiện để validate cho các actions.
-> Ngoài ra cả phần extrinsics và chainstate có các thông tin earlyBirdBonus, earlyBirdShares liên quan đến reward.
-> Tìm cách lấy amount sENJ của account
### Native Staking
Giống với relaychain native staking
