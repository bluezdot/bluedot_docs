
Locked Balance?
- Với 1 walletContract bình thường sẽ ko chứa thông tin gì liên quan đến locked cả: Wallet v1 -> v5; Wallet highload v2,v3.
- Các wallet contract có thể deployed để lưu thông tin locked: Lockup-wallet (https://docs.ton.org/participate/wallets/contracts#lockup-wallet) & Restricted-wallet (https://docs.ton.org/participate/wallets/contracts#restricted-wallet). Tuỳ vào nhu cầu sử dụng thì người viết sẽ triển khai các loại wallet này để lock-token gửi đến.

=> Vậy thông tin cơ bản của wallet contract sẽ chỉ chứa thông tin balance (transferable balance) nên sẽ không xác định được locked blance, chỉ có thể duyệt tất cả transactions để xem địa chỉ đang check có gửi ton đến locked contract nào không và phải xác định trước cơ chế lock của contract đấy nữa.

Về Staking:
- Hiện tại có 1 standard nominator pool contract (https://github.com/ton-blockchain/nominator-pool). Validator và nominator gửi Ton vào contract này để tham gia staking.
- Để nominate token, nominator cần gửi 1 lượng tối thiếu 10001 TON tới nominator pool contract với message "d" để tham gia staking (logic được xử lí trong pool contract). Để unnominate token, nominator cần gửi 1 TON tới nominator pool contract với message "w", toàn bộ token nominate trước đó sẽ được hoàn trả hết sau khi kết thúc work cycle tiếp theo (thường upto 18h).
- Pool bắt đầu nhận được reward khi có >=300k TON Staked. Khi pool đạt 900k TON thì nominator mới tham gia sẽ ko nhận được reward.
- Ref: 
	- https://docs.ton.org/participate/network-maintenance/nominators
	- https://tonvalidators.org/#how_it_works
	- https://blog.ton.cat/how-to-stake/

=> Tương tự như nội dung chung phần locked Balance, thì để xác định được locked staking cần xác định được thông tin contract của nominator pool hoặc check transactions để xác định được locked amount của địa chỉ.