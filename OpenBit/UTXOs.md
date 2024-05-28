- Trên Bitcoin blockchain sẽ có UTXOs set. Mỗi UTXO gồm:
	- value
	- cryptographic puzzle (scriptPubKey): Ai dùng sig giải được thì được tiêu thụ.
	![[Pasted image 20240411193408.png]]
- Quá trình serialize - deserialize để đưa scriptPubKey ở dạng cấu trúc - dạng hash:
	![[Pasted image 20240411185244.png]]
- Mỗi UTXO khi dùng để tiêu thụ sẽ được gắn là 1 input. Input bao gồm:
	- Pointer đến UTXO (transaction hash & vout)
	- unlocking script (ScriptSig)
	- sequence number
	![[Pasted image 20240411191326.png]]
- UTXOs có thể hợp nhất: [What Is UTXO Management & Why Is It Important? (xverse.app)](https://www.xverse.app/blog/utxo-management)

- Bitcoin version number: 1 or 2
	- Ver2 means that BIP 68 applies: [bips/bip-0068.mediawiki at master · bitcoin/bips](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki#specification)
	- [Transactions — Bitcoin](https://developer.bitcoin.org/reference/transactions.html)
	![[Pasted image 20240412110802.png]]