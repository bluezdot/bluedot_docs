Bước 1: Fetch data mới nhất về chainlist (nhánh dev) và check lại thông tin trên repo

- git pull → Mục đích là để cập nhật trạng thái mới nhất của branch trong trường hợp có người thay đổi
- yarn
- yarn fetch:beta → Mục đích là kéo dữ liệu mới nhất từ Strapy về (xem lệnh vào package.json)
- yarn build:beta → Tạo bản build local

Bước 2: Commit thay đổi

- Commit thay đổi
- Commit version beta
- Push

Bước 3: Thay đổi bản build vào repo Subwallet extension

- Cập nhật version chainlist
- yarn
- yarn dev để test

Bước 4: Test thử trên ví
[[Check trên ví (dev)]]