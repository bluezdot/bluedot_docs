1. WorkchainId
	TON hỗ trợ nhiều phiên bản blockchain song song được gọi là _workchains_. Hiện nay, chỉ tồn tại hai workchains, workchain 0 được sử dụng cho tất cả các hợp đồng thông thường và workchain -1 (masterchain) được validators sử dụng. Trừ khi bạn đang làm điều gì đó đặc biệt, bạn sẽ luôn sử dụng workchain 0.
2. WalletId
3. Segno
	Tương tự Nonce, transaction index, concept của TVM.

	Seqno is one way to prevent Replay Attacks. When a transaction is sent to a wallet smart contract, it compares the seqno field of the transaction with the one inside its storage. If they match, it's accepted and the stored seqno is incremented by one. If they don't match, the transaction is discarded.

	Without seqno (or another mechanism to prevent Replay Attacks), anyone (usually the receiver of funds) can read the transaction data (for example from blockchain explorers) and create another fake transaction and resend it to the original wallet smart contract and force it to resend TON once more, ultimately draining all of its funds.[](https://answers.ton.org/signin?returnto=/question/1533191849462730752/what-is-seqno)
4. Bounceable and Non-bounceable
	 https://answers.ton.org/question/1543112814917324800
5. Shard
6. internalMessage & externalMessage
7. Cell & Bag of Cells (BoC)
8. TL-B (Type Language - Binary)