1. Runes
	1.1 Tech:
		- Để transfer rune, cần ghi dữ liệu lên bitcoin transaction dựa trên runestone message ([Đọc thêm ở đây](https://www.notion.so/subwallet/C-c-kh-i-ni-m-c-b-n-2e07316f42014439aaae153d4c82bed8?pvs=4#c3ca5655827541578ee4ae1d1d9a205f)) lên UTXO. Triển khai phần này sẽ rất khó, cần thời gian nghiên cứu. -> Sử dụng ord.
		- Ord là 1 index & command-line wallet. Ord cung cấp các command-line để tương tác với bitcoin blockchain. Để transfer, đầu tiên cần tạo 1 file yaml với format và metadata như [đã nghiên cứu](https://www.notion.so/subwallet/C-c-kh-i-ni-m-c-b-n-2e07316f42014439aaae153d4c82bed8?pvs=4#e50cc07ff8ca4b5b82d33461a3c309e1). Để send rune, sử dụng command:
			`ord --cookie-file <COOKIE_PATH> --data-dir <ENV PATH> wallet send <RECEIVE_ADDRESS><AMOUNT>:<RUNENAME> --fee-rate 1`.
			Mine another block, done in a separate command window:
			`bitcoin-cli -datadir=env generatetoaddress <number_of_blocks> <ADDRESS>`
		- **Chưa tìm thấy cmd send rune dựa trên edicts** 
		- Cần có:
			- Bitcoin Core (v25/v26)
			- Ord v0.17.1
		- Có thể tham khảo thêm [code unisat](https://github.com/unisat-wallet/extension).
	1.2 Non-tech:
		- Việc transfer runes sẽ tương tự như mint/etch chỉ khác về mặt dữ liệu được ghi lên UTXOs. Để có thể transfer runes, cần đưa runestone message vào transaction. runestone message có mục đích ghi các bản Edicts lên UTXO trong phần data sau `OP_RETURN OP_13` với format `Edict {RuneId, amount, output}`
		- Runestone có. thể chứa số lượng edicts bất kì
		- Nếu amount > 0 hoặc amount > possible => Lấy amount = max available
		- Trong trường hợp etched rune chưa xác định được block của nó, ID `0:0` sẽ được sử dụng thay thế để xác định Rune Etched và transfer trong transaction này.
		- Khi etch rune, nếu transaction có inscription -> inscription sẽ được coi là image của rune, hiển thị ở phần /rune page (tìm hiểu thêm đoạn này).

	References: 
	- ![[Testing_Runes_Getting_Started_Guide_ (1).pdf]]
	- [Specification - Ordinal Theory Handbook (ordinals.com)](https://docs.ordinals.com/runes/specification.html)
	- [unisat-wallet/extension: The first open-source browser extension wallet for Bitcoin NFTs (github.com)](https://github.com/unisat-wallet/extension)
	- Example:
		- [Etching](https://mempool.space/testnet/tx/b2da2f0bd26b1b0bb2816d426b7200be6009b0b1e3da1eeb615ddfcda97a82bb)
		- [Minting](https://mempool.space/testnet/tx/91b56946bef8d338de7a3f586d8a0e018a5bb251e04e2e259b5b2b0884d82927)
		- [Multi-transfering](https://mempool.space/testnet/tx/1e677c900341076211e73d8f12670e9f26cb4c63ed89750fd1b5cf191bda3a0d)

Leather bảo ([Bitcoin Runes - Runes Wallet | Leather Bitcoin Wallet](https://leather.io/blog/bitcoin-runes-have-come-to-leather-unpacking-the-runes-protocol)):
![[Pasted image 20240522152955.png]]

1.3. Discuss:
- Cách transfer nào đang phổ biến hơn? Sử khác biệt giữa 2 kiểu transfer? An toàn, theo chuẩn?
	- 2 cách transfer: (1) Sử dụng edicts, (2) transfer utxo
	- Theo e thấy, cách transfer sử dụng edicts (runestone message) an toàn và đảm bảo theo chuẩn hơn. Kiểu (1) đã được mô tả trong official docs của runes, trong khi chưa thấy sự đề cập về phương pháp transfer theo kiểu (2), chỉ thấy RuneAlpha xác định đó là giao dịch transfer runes: [Thông tin giao dịch](https://runealpha.xyz/txs/6333599e5abe3891bb62eb0d9af8c2f30d445da0c23942d633529c0e94a997ca). Theo 1 số thông tin trao đổi với dev mate thì transfer theo kiểu (2) có thể sẽ luôn transfer tất cả runes có trong utxo.
		-> **cần verify lại**
	- Việc transfer edicts qua runestone message sẽ đảm bảo tính hợp lệ của rune. Cần check thêm data về runestone thay vì check op_return. 
- Cách sinh ra data từ runestone message?
	- Tool decode mempool runestone message: [Runes For Mempool](https://chromewebstore.google.com/detail/runes-for-mempool/gladlkdaclmeneojkbbfnoelhbjpkkhm). Tool này ko xác định được kiểu transfer (2).
	- Script decode và cách decode tx runestone: [Decode runestone](https://github.com/magicoss/runestone-lib?tab=readme-ov-file#decode-runestone)
- Tại sao edict phải đi kèm với etching?
	- Edict không cần phải đi kèm với etching. Có thể tạo 1 runestone message riêng biệt để sử dụng mỗi edict, mục đích là để transfer rune token với 1 lượng amount:
		![[Pasted image 20240524181652.png]]
- Nghiên cứu cách transfer của ord và unisat.
	- Chưa triển khai

1. BRC-20
	2.1. Non-tech: 
		- Cần hiểu cấu trúc lưu trữ của inscription và cách tương tác để mint/transfer inscription, khi đó sẽ giải quyết được cả việc transfer inscription và BRC-20.
		- Leather wallet đã triển khai phần transfer này -> Cần tham khảo.
	
	2.2. Non-tech: 
		- Bản chất sự tồn tại của BRC-20 là dựa trên Ordinal theory và inscription. Mint/transfer BRC-20 đều cần tạo 1 inscription mô tả điều đó.
		- Các bước để transfer BRC-20:
			- Mint 1 transfer inscription
			- Gửi inscription vừa mint cho người nhận

	Reference: 
	- [leather-wallet/extension: Bitcoin for the rest of us (github.com)](https://github.com/leather-wallet/extension)	

Discussion:
-> **Chưa triển khai, cần tìm hiểu trước về SegWit transaction**
1. Tìm cách decode thông tin inscription trong transaction.
2. Tìm format thông tin cần lưu trong transfer tx inscription/brc-20.

---
Tham khảo Runes trên các ví, sàn
1. Leather: 
	1. Chỉ mới filter out runeUtxo, view runes, chưa support transfer runes. Etch/mint/transfer khi connect qua [OrdinalsBot](https://ordinalsbot.com/runes) và [Luminex](https://luminex.io/runes/mint) (Tìm code)
	2. Đang fix UI khi mint Runes trên dApp này: [Luminex](https://luminex.io/).
	3. Lên issue tích hợp price runes qua BestInSlot API: [Show fiat value for Runes · Issue #5300 · leather-wallet/extension (github.com)](https://github.com/leather-wallet/extension/issues/5300)
2. Unisat:
	1. Gọi sendRune qua txHelpers từ @unisat/wallet-sdk. Send Runes: https://github.com/unisat-wallet/extension/blob/584dde04ede01db16bc826658582e50779a1be9e/src/background/controller/wallet.ts#L1829. @unisat/wallet-sdk/lib/tx-helpers/send-runes.js
	2. Safe check: atomicalNfts, inscription,
	3. v.3.2. - Optimized the UTXO selection strategy of runes to reduce gas fees: Có nhiều utxo chứa cùng 1 loại runes. Sort descending utxo theo amount -> tìm utxo chứa runeAmount = chính lượng amount user muốn chuyển (tối ưu nhất) -> nếu ko có utxo to thì + đến khi nào đủ.
		![[Pasted image 20240527172721.png]]
		??
3. xVerse:
	1. [Github](https://github.com/secretkeylabs). xverse-web-extension, sử dụng thư viện xverse-core.
	2. [Generate tx](https://github.com/secretkeylabs/xverse-web-extension/blob/b9661ed110e43884c92eeb325358da803145edb2/src/app/screens/sendRune/helpers.ts#L12) -> [Send Rune in lib](https://github.com/secretkeylabs/xverse-core/blob/b679bc726eea6bf457ba42f6f9cc43e94f99878f/transactions/runes.ts#L29)
		1. Get all rune utxos -> sort desc amout
		2. Get enough balance -> calculate change -> getEncodedScriptHex -> api
		3. https://api-3.xverse.app/v1/runes/tools/encode-edicts -> Chỉ xử lí edicts (transfer).
		4. [Runes transfer - sats connect](https://docs.xverse.app/sats-connect/bitcoin-methods/runes_transfer)
	3. 
4. Magic Eden:
	1. [Github](https://github.com/magiceden)
5. Runestone-lib: decode/encode implement khá đầy đủ các nội dụng trong Runes specifications
		Tổng quan:
	1. encode, decode ( xử lí tất cả: etching, minting, edicts, pointer)
		1. Trong etching runes có implement commit-reveal protocol. -> etchingCommitment buffer
	2. Xử lí các bước encipher
		1. xử lí payload cho từng field (etching, mint, edicts)
		2. concat payload
		3. compile stack payload
	3. Xử lí các bước decipher
		1. Tương tự encipher
		2. Xử lí đầy đủ các Tag, Flag
		Cụ thể (Encode):
```
interface RuneId {
	block: u64Strict,
	tx: u32Strict
}

function encodeRunestone (runestone): {sriptHexRunes, scriptHexCommitment?} {
	// if has mint: 
	if has etching {
		handleRuneSpace()
	}
}
```
	1. Hàm encodeRunestone
			1. Đầu vào: json metadata runes
			2. Đầu ra: scriptHex Runestone + scriptHex Commitment (trong trường hợp etching)
		1. Xử lí dữ liệu các field mint nếu có -> đưa về type RuneId (u64, u32)
		2. Xử lí dữ liệu pointer nếu có -> đưa về type u32
		3. Xử lí dữ liệu **edicts** nếu có -> đưa về type Array<{RuneId (u64, u32), u128, u32}>
		4. Xử lí dữ liệu etching nếu có:
			1. Xử lí spaced rune name, symbol, divisibility, premine, spacer, turbo.
			2. Handle các điều kiện (Max divisibility, max script size, commit confỉmation).
			3. Xử lí các điều kiện trong term (amount, cap, height, offset).
			4. Xử lí parse commitment (Quan trọng khi etch). Giao thức commit-reveal (Đọc thêm [1](https://github.com/magicoss/runestone-lib/blob/196617942be49e3497e58704ed70c53bacff07f6/src/rune.ts#L5), [2](https://docs.ordinals.com/runes/specification.html#:~:text=To%20prevent%20front,etching%20is%20ignored.)
		5. Mã hoá đống data đã đưa về chuẩn thành unsigned message (encipher)
			1. Khởi tạo 1 payloads chứa datapush
			2. Lần lượt check etching, mint, edict và đẩy data tương ứng vào payloads, dựa theo Tag, Flag -> Mục đích đoạn này để kiểm soát cenotaph (Cenotaphs may be created if a runestone contains an unrecognized even tag).
				1. Phần Edicts trước khi đẩy vào sẽ được sort theo block, tx.
				2. Sau đó list Edicts sẽ được push lần lượt theo 'delta' encoded.
					![[Pasted image 20240528152326.png]]
				3. Đẩy vào stack: OP return + OP_13 (MAGIC_NUM) + payload
				4. Compile stack.
					....
	2. Decode: Lật ngược tất cả các bước, từ việc mapping các opcode.
				
1. Luminex: 
	1. Không opensoure Dapp - Đã thử hỏi mod discord bên đấy
	2. [Github](https://github.com/luminexord/runes)
	3. [Dapp](https://luminex.io/runes/mint)
	4. [Docs](https://luminex.gitbook.io/luminex/runes/faqs-general-concepts)
2. OrdinalsBot:
	1. Không opensource
	2. [Github](https://github.com/ordinalsbot)
	3. [Dapps](https://ordinalsbot.com/runes)
	4. [Docs](https://docs.ordinalsbot.com/)