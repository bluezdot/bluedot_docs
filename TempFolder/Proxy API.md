## 1. Thiếu API

Inscription:
- Thiếu api lấy inscription content: https://api.hiro.so/ordinals/v1/inscriptions/:id/content

Rune:
- Thiếu api all runes: https://mainnet-indexer-api.runealpha.xyz/rune?limit=10&offset=0&text=&type=All&sortBy=is_hot&sortOrder=DESC
- Thiếu api runes balance: https://mainnet-indexer-api.runealpha.xyz/address/bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy/runes?total=0&limit=10&offset=0&text=bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy
- Thiếu api rune transactions: https://mainnet-indexer-api.runealpha.xyz/address/bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy/txs?total=0&limit=10&offset=0 (có api lấy rune utxos sẽ không cần api này).
- Thiếu api lấy rune utxos của address
	- Input: address 
	- Output: rune utxos thuộc address đó
- Thiếu api lấy rune metadata của 1 rune id:
	- Input: rune ID
	- Output: rune metadata

Ngoài ra thiếu:
- [electrs.openbit.app/blocks](https://electrs.openbit.app/blocks) -> Mục đích là để lấy block time.
- https://api.hiro.so/ordinals/v1/brc-20/tokens/:ticker -> Lấy brc-20 info.
- https://api.hiro.so/ordinals/v1/brc-20/balances/:address -> Lấy brc-20 balance.

## 2. Cần cập nhật:
- Sai chính tả: 
	![[Pasted image 20240603155009.png]]
- `total` bản ghi không khớp với api hiro trả về (thiếu dữ liệu):
	![[Pasted image 20240603155105.png]]
- Query offset và limit cú phát khác trên các api đang dùng, và chưa rõ limit tối đa, nếu set cao quá thì query ko ra kết quả:
	![[Pasted image 20240603155248.png]]