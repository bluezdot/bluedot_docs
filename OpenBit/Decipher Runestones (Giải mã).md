1. Tìm utxo đầu tiên có script pubkey bắt đầu bằng OP_RETURN OP_13.
2. Ghép tất cả data đẩy vào payload buffer.
3. Decode 1 chuỗi 128-bit ([LEB128](https://en.wikipedia.org/wiki/LEB128)) số nguyên từ payload buffer.
4. Parse sequence interger -> untyped message
5. Parse untyped message -> runestone.