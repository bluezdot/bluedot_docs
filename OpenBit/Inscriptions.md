1. Explorer: [Hiro Ordinals Explorer](https://ordinals.hiro.so/)
- File type: Image, Video, Audio, Text, Binary
	-> Cần xử lí độ phân giải khi hiển thị.
	-> Cần xử lí metadata cho từng loại data:
	- From leather: 
		audio:
			- Info: [Inscription #66707766 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/069f79685c04af6357058eeeb65c4835ed13d00b5bf5a69c4cff5e513d9b0fffi0)
			- Metadata: https://ordinals.com/preview/069f79685c04af6357058eeeb65c4835ed13d00b5bf5a69c4cff5e513d9b0fffi0
		html:
			- Info: [Inscription #67911635 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/bc85e4eabd796133004c7247de3940aba3a98243374fab859f8eb0085c7009f4i2)
			- Metadata: https://ordinals.com/preview/069f79685c04af6357058eeeb65c4835ed13d00b5bf5a69c4cff5e513d9b0fffi0
		image:
			- Info: [Inscription #49575549 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/6dcaf195b468e773e227b18f266be07c7340046593d11007f9f9051fa605dcc9i0)
			- Metadata: [content (28×28) (hiro.so)](https://api.hiro.so/ordinals/v1/inscriptions/6dcaf195b468e773e227b18f266be07c7340046593d11007f9f9051fa605dcc9i0/content)
		svg:
			- Info: [Inscription #26697357 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/bf6f0ff4c6fbcb1e7248915ade1b34d9a06c4d0ed4e682a9d829a4872fd633cbi0)
			- Metadata: https://ordinals.com/preview/bf6f0ff4c6fbcb1e7248915ade1b34d9a06c4d0ed4e682a9d829a4872fd633cbi0
		video:
			- Info: [Inscription #67906329 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/2a5107d255c13ad32471ae0dd777fa48d78287d237e4435d7ecb3b8ddac245f6i0)
			- Metadata: https://ordinals.com/preview/2a5107d255c13ad32471ae0dd777fa48d78287d237e4435d7ecb3b8ddac245f6i0
		gltf: 
			- Info: [Inscription #66960169 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/c3a92c607f903c2fd79b34601af818c40eea4d92910a132e2561608ea2d9480di1)
			- Metadata: https://ordinals.com/preview/c3a92c607f903c2fd79b34601af818c40eea4d92910a132e2561608ea2d9480di1
		text:
			- Info: [Inscription #50179754 | Hiro Ordinals Explorer](https://ordinals.hiro.so/inscription/05ab994a5eb9a0d00c728cc39dea2ee2f11debf5d86f5c0c409cd82cec42da25i0)
		others:
			- Info: Tương tự, ko có metadata.
	-> Đề xuất: Inscription ko có collection như NFT, có thể hiển thị theo nhóm File type.
					![[Pasted image 20240408171546.png]]
- Rarity: Common, Uncommon, Rare, Epic, Legendary, Mythic
	-> Đề xuất: Có thể thêm hiệu ứng khung cho ins có rare lớn hơn.

2. API: [Ordinals API Overview | Hiro Docs](https://docs.hiro.so/ordinals-api)
	Các API quan trọng:
- **Get Inscription metadata (Bitcoin ordinals)**
- **Get Inscription content**
- **Get all inscriptions of an address**
- Get BRC-20 tokens metadata
- **Get ordinals data for a specific satoshi**
	-> Độ hiếm, thứ tự satoshi, ...

3. Sách: [A Developer's Guide to Bitcoin Ordinals.pdf (hiro.so)](https://assets.hiro.so/A%20Developer's%20Guide%20to%20Bitcoin%20Ordinals.pdf?utm_source=Iterable&utm_medium=email&utm_campaign=campaign_6911762)

## Interface
	Inscription
		id: string;             -> tx_id + i + offset
		number: number;         -> inscription ordinal (maybe)
		address: string;        -> owner
		block: number;          
		block_hash: string;  
		timestamp: number;  
		tx_id: string;          -> transaction hash
		location: string;       -> 
		output: string;  
		value: number;  
		fee: number;  
		sat_ordinal: number;     -> satoshi ordinal
		sat_rarity: string;      -> satoshi rarity
		content_type: string;    -> metadata type
		content_length: number;  
		content: any;            -> metadata


A @0xhieudao ơi, kiểu dữ liệu model/gltf bên hiro explore không hiển thị được, e thử xài endpoint của bên ordinalAlpha thì thấy hiển thị tốt. Có một vài image bên hiro cũng ko hiện được mà bên ordinalAlpha hiện đc. E cũng chưa test hết tất cả case được, không biết có nên xài endpoind của ordinalAlpha ko a nhỉ?

Hiro: https://ordinals.hiro.so/inscription/f581c5e15c56ed084ce4c47c66bd24abf4924b29eb6151a6e3e3b71390491c62i0
OrdinalAlpha: https://ordinals.com/preview/f581c5e15c56ed084ce4c47c66bd24abf4924b29eb6151a6e3e3b71390491c62i0

Hiro: https://ordinals.hiro.so/inscription/76a2ad5ecb62e2f3f4d15d05128440c5b28c5a3c63b4c00c9b1b913a6bda61cfi0
OrdinalAlpha: https://ordinals.com/preview/76a2ad5ecb62e2f3f4d15d05128440c5b28c5a3c63b4c00c9b1b913a6bda61cfi0

Hiro: https://ordinals.hiro.so/inscription/fe64f37161a41a0c149d7ec0ba3b358203e9a58452797744ccdcfcc86af568c8i0
OrdinalApha: https://ordinals.com/preview/fe64f37161a41a0c149d7ec0ba3b358203e9a58452797744ccdcfcc86af568c8i0

Note:
Dựa vào curse_type để biết children của collection.
[[UI_Inscription]]