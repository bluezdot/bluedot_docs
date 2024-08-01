- Everything in TON stored in Cells
	- up to 1023 bits
	- up to 4 liên kết tới cells khác
	- Kết nối theo đồ thị DAG

![[Pasted image 20240724190346.png]]

- BoC (Bag of Cells): là một định dạng để chuỗi hoá cells thành byte arrays

- Cell types
	- ord
	- Pruned branch cell
	- Library reference cell
	- Merkle proof cell
	- Merkle update cell

- Cell flavors
	- Builder: cấu trúc các cells lại với nhau
	- Slice: Mổ xẻ các cells để lấy thông tin

- Serialization of data to cells
	- Mọi object được chuỗi hoá thành Cell: message, message queue, block, whole blockchain state, contract code and data
	- Chuỗi hoá được mô tả trong TL-B scheme

	- ![[Pasted image 20240725120110.png]]

Ref: 
 - https://docs.ton.org/learn/overviews/cells#serialization-of-data-to-cells
 - https://docs.ton.org/develop/data-formats/cell-boc
 - https://docs.ton.org/develop/data-formats/tl-b-language