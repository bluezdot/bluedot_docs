
- Để lấy thông tin token implement từ smart contract sẽ phải tương tác thông qua Contract ABI. Các smart contract "thường" viết theo standard ERC20, ERC721, ... được định nghĩa sẵn 
	--> Có các hàm từ Contract ABI để lấy thông tin.
	
- Nếu smartcontract viết theo kiểu tuỳ chọn và không có các hàm để gọi (balance, tokenId, ...) thì sẽ phải quét smartcontract trong toàn bộ blocks trên blockchain để lấy thông tin của token. -> tốn nhiều efford (Trên ví hiện tại sẽ ko support).