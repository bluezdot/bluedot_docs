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
		application/json...: Hiện content giống text
	- Ordinal Alpha: https://ordinals.com/preview/
		- VD: [ordinals.com/preview/9b93eb2068fd675a1a30321f2c0620c68ce8e6e37dac82283a9a93c03f9befa6i0](https://ordinals.com/preview/9b93eb2068fd675a1a30321f2c0620c68ce8e6e37dac82283a9a93c03f9befa6i0)
		 [9b93eb2068fd675a1a30321f2c0620c68ce8e6e37dac82283a9a93c03f9befa6i0 (700×700) (ordinals.com)](https://ordinals.com/content/9b93eb2068fd675a1a30321f2c0620c68ce8e6e37dac82283a9a93c03f9befa6i0)
- Rarity: Common, Uncommon, Rare, Epic, Legendary, Mythic
	-> Đề xuất: Có thể thêm hiệu ứng khung cho ins có rare lớn hơn.

2. Hiển thị các thông tin:
	- Inscription type
	- Satoshi number
	- Satoshi rarity

Thử api của ordinal.com:[ordinals.com/preview/50a4589012d4ca22634d601f259c40f92cfd4e9d12846a559b968c85696c5cffi0](https://ordinals.com/preview/50a4589012d4ca22634d601f259c40f92cfd4e9d12846a559b968c85696c5cffi0)
Thử api của ordin: [ordin.s3.amazonaws.com/inscriptions/50a4589012d4ca22634d601f259c40f92cfd4e9d12846a559b968c85696c5cffi0](https://ordin.s3.amazonaws.com/inscriptions/50a4589012d4ca22634d601f259c40f92cfd4e9d12846a559b968c85696c5cffi0)