Là OP_Return-based, UTXO-based Fungible token.
- data stored in 0 sat output where public key is OP_RETURN + data. 
- Main function:
	1. Etch: Create a new Rune
		- Commit-reveal protocol?
		![[Pasted image 20240405175203.png]]
	2. Mint: Claim an amount of etched Rune 
		- The only input: rune id, the amount is specified in etch. 
		- only one mint per tx
	3. Transfer: Transfer an amount of Runes (also called Edicts)
		- Edicts có thể tạo ra cenotaph, tx runes has cenotaph will burn all runes.
	![[Pasted image 20240412154823.png]]

- Flow Decipher Runestones (Giải mã):
1. Tìm utxo đầu tiên có script pubkey bắt đầu bằng OP_RETURN OP_13.
2. Ghép tất cả data đẩy vào payload buffer.
3. Decode 1 chuỗi 128-bit ([LEB128](https://en.wikipedia.org/wiki/LEB128)) số nguyên từ payload buffer.
4. Parse sequence interger -> untyped message
5. Perse untyped message -> runestone.
	![[Pasted image 20240412160457.png]]


- Invalid Runestone is called CENOTAPH
	- All runes input to a transaction chứa cenotaph are burned
	- Runestone tạo ra cenotaph chứa etch -> etched rune có supply = 0 và ko mint đc
	- Runestone tạo cenotaph chứa mint -> the mint count against the mint cap và burn
	![[Pasted image 20240412162612.png]]

[Runestone | Magic Eden](https://magiceden.io/ordinals/marketplace/runestone)

Collection
[stats-mainnet.magiceden.io/collection_stats/search/bitcoin?limit=108&window=1d&sort=volume&direction=desc](https://stats-mainnet.magiceden.io/collection_stats/search/bitcoin?limit=108&window=1d&sort=volume&direction=desc)

Token id
https://api-mainnet.magiceden.io/v2/ord/btc/tokens?limit=100&offset=0&sortBy=priceDesc&minPrice=0&maxPrice=0&collectionSymbol=runestone&disablePendingTransactions=false

[Mastering Bitcoin (ebooksworld.ir)](https://dl.ebooksworld.ir/motoman/Oreilly.Mastering.Bitcoin.Unlocking.Digital.Cryptocurrencies.www.EBooksWorld.ir.pdf)

![Screenshot 2024-04-10 at 16.51.38.png](app://a168555c930c3f44605da030603e2b41a86b/Users/bluedot/Documents/labidien/Screenshot%202024-04-10%20at%2016.51.38.png?1712742702838)

Transaction etch rune: [Rune explorer & services (runealpha.xyz)](https://runealpha.xyz/txs/e70237e1e029841e513913ed034a1e89d7c79b3ff1d14950381ffd1bc3db87ea)
Transaction transfer rune: [Rune explorer & services (runealpha.xyz)](https://runealpha.xyz/txs/9053195f6ad9f6defbd1248ed56698f6fe4e95f2462a81a82f5dbdff49380733)


OP_RETURN full node không lưu.

Mint rune bitcoin testnet

Nếu transactions chứa output có scriptPubkey gồm 1 OP_RETURN, theo sau OP_RETURN là dữ liệu -> chứa rune protocol message. ([A brief introduction to Runestone and the Runes Protocol](https://www.coinlive.com/news/a-brief-introduction-to-runestone-and-the-runes-protocol)). Rune protocol message không hợp lệ sẽ bị burned. -> Runes hiển thị trên RuneAlpha và các nền tảng khác hiện tại chỉ là demo, và dữ liệu của nó ko đúng chuẩn.
Ảnh dưới là 1 protocol message.
![[Pasted image 20240412114658.png]]

Pseudocode decode rune spacer
``` 
spacer = n  // interger
spacerHex = decimalToHex(n)
from i in range(rune_name.length):
  if (spacerHex[i] = 0):
    continue
  else:
    insert space
```
https://docs.ordinals.com/runes/specification.html#spacers

Rune mint guide: [Runes Mint Guide](https://doggfather.medium.com/runes-mint-guide-9b5b657d77d8)

[[API RUNES]][[Runes Explorer]][[Testing Rune]][[OP_RETURN TECHNICAL]][[Question?]]

https://github.com/ordinals/ord/commit/ead081de1795fd6a56c1ad837113ed27ab001c4f#diff-b0ed3b268d20be9e1f268f2ee80e2a8e6bc727cc10e6b945fb4358eb7d44915c