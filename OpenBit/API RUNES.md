
API lấy all runes: https://api2.runealpha.xyz/rune?limit=10&offset=0&text=&type=All&sortBy=is_hot&sortOrder=DESC 

API lấy txs của address: https://api2.runealpha.xyz/address/bc1p4ajta58ucfnzje6n4uw6y0q2rg228u7d6z4qtr7gruwm4t0308kqnw82x7/txs?total=0&limit=10&offset=0

API lấy runes của address: https://api2.runealpha.xyz/address/bc1p4ajta58ucfnzje6n4uw6y0q2rg228u7d6z4qtr7gruwm4t0308kqnw82x7/runes?total=0&limit=10&offset=0&text=bc1p4ajta58ucfnzje6n4uw6y0q2rg228u7d6z4qtr7gruwm4t0308kqnw82x7

---
API lấy all runes: https://mainnet-indexer-api.runealpha.xyz/rune?limit=10&offset=0&text=&type=All&sortBy=is_hot&sortOrder=DESC

API lấy txs: [mainnet-indexer-api.runealpha.xyz/address/bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy/txs?total=0&limit=10&offset=0](https://mainnet-indexer-api.runealpha.xyz/address/bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy/txs?total=0&limit=10&offset=0)

API lấy runes của address: https://mainnet-indexer-api.runealpha.xyz/address/bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy/runes?total=0&limit=10&offset=0&text=bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy

---
### Interface của RunesByAddressInfo:
{
	"rune_id": "1:0",
	"amount": "9440",
	"address": "bc1q0dv855vavylrz8q9cmn0q6hr40dng2csy4y2qy",
	"rune": {
		"id": "84d8428d-3097-41a6-829c-fc7d0a37a7c8",
		"rune_id": "1:0",
		"deploy_block": "1",
		"deploy_transaction": "0000000000000000000000000000000000000000000000000000000000000000",
		"transaction_index": "0",
		"deploy_timestamp": "0",
		"rune": "2055900680524219742",
		"rune_name": "UNCOMMONGOODS",
		"divisibility": null,
		"premine": null,
		"spacers": "128",
		"symbol": "10697",
		"terms_cap": "340282366920938463463374607431768211455",
		"terms_height_start": "840000",
		"terms_height_end": "1050000",
		"terms_amount": "1",
		"terms_offset_start": null,
		"terms_offset_end": null,
		"burned": "0",
		"cenotaph": null,
		"is_reserved": false,
		"holder_count": "6247",
		"mints": "63477",
		"transaction_count": "65139",
		"is_hot": true,
		"turbo": true,
		"createdAt": "2024-04-20T05:09:00.170Z",
		"updatedAt": "2024-04-23T02:25:40.903Z"
	}
}

->


### Interface của RuneCollectionInfo

{
	"id": "84d8428d-3097-41a6-829c-fc7d0a37a7c8",
	"rune_id": "1:0",
	"deploy_block": "1",
	"deploy_transaction": "0000000000000000000000000000000000000000000000000000000000000000",
	"transaction_index": "0",
	"deploy_timestamp": "0",
	"rune": "2055900680524219742",
	"rune_name": "UNCOMMONGOODS",
	"divisibility": null,
	"premine": null,
	"spacers": "128",
	"symbol": "10697",
	"terms_cap": "340282366920938463463374607431768211455",
	"terms_height_start": "840000",
	"terms_height_end": "1050000",
	"terms_amount": "1",
	"terms_offset_start": null,
	"terms_offset_end": null,
	"burned": "0",
	"cenotaph": null,
	"is_reserved": false,
	"holder_count": "6247",
	"mints": "63466",
	"transaction_count": "65139",
	"is_hot": true,
	"turbo": true,
	"createdAt": "2024-04-20T05:09:00.170Z",
	"updatedAt": "2024-04-23T02:06:04.857Z"
}

Thiếu API Runes:
- Lấy tất cả rune utxos của 1 address:
	  Input: address
	  Output: utxos
- Lấy rune metadata của 1 rune ID:
	Input: runeID
	Output: metadata