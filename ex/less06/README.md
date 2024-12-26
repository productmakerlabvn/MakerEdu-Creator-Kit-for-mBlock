# Bài 6: Cổng tự động - MakerEdu Creator Kit for mBlock

## Mô tả dự án

Trong bài này bạn sẽ làm quen với một cảm biến mới, là cảm biến siêu âm.

Cảm biến này có thể đo khoảng cách giữa vật thể phía trước đến cảm biến, bằng cách dùng nguyên lý phản xạ sóng.

Kết hợp với động cơ Servo học ở bài trước. Bạn hoàn toàn có thể làm được một bộ mở cửa tự động.

Khi có người hay vật đến gần cửa, Servo sẽ quay là cửa mở tự động.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor](https://makerlab.vn/mkes01)
- 1x [Động cơ RC Servo](https://hshop.vn/dong-co-rc-servo-9g)

### Chuẩn bị trước dự án

- Tải và cài đặt phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm mblock theo hướng dẫn **[tại đây]**.
- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phầm mềm mBlock và **"ngôn ngữ lập trình kéo thả khối"** theo hướng dẫn **[tại đây]**.

### Sơ đồ kết nối

| MakerEdu Creator | Devices              |
|------------------|----------------------|
| Port (D3+D2)     | Cảm biến Siêu âm     |
| Port D10         | Động cơ RC Servo     |

### Kết nối Servo đúng cách

Trên mạch MakerEdu Creator bạn tìm đến cụm chân cắm Servo có 3 màu (vàng - đỏ - đen) và kết nối như sau:

- Dây cam → chân vàng (S)
- Dây đỏ → chân đỏ (+)
- Dây đen → chân đen (-)

### Chương trình

- Download file code **"Bai_6.mblock"**.
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices

![Creator mBlock Bai 6 1](/ex/less06/image/825px-Creator_mBlock_Bai_6_1.png)

### Giải thích code

Vai trò của biến **"count"**, **"min"** và **"max"**:

Chương trình này hoạt động chủ chốt dựa trên biến **"count"**. Đây là biến đếm để ra quyết định có cho Servo mở cửa hay đóng cửa.
Giới hạn của biến được thiết đặt bởi biến **"max"** và **"min"**. Trong đó **"max"** là 10 và **"min"** là 1.
Nếu **"count"** chạm tới ngưỡng trên, bằng **"max"**. Bo mạch sẽ điều khiển Servo quay góc 90º, làm mở cửa.
Ngược lại, **"count"** chạm tới ngưỡng dưới, bằng **"min"**. Bo mạch sẽ điều khiển Servo quay góc 0º, làm đóng cửa.

Chương trình hoạt động:

Đầu tiên, khi bo mạch mới khởi động, có 3 khối được thực hiện một lần trước khi bước vào khối **[forever]**.

- Tạo ra một biến tên **"max"** và lưu giá trị 10.
- Tạo ra một biến tên **"min"** và lưu giá trị 1.
- Điều khiển Servo ở chân D10 quay đến góc 0º.

Bên trong khối **[forever]**.

- Đầu tiên, bo mạch đọc giá trị khoảng cách từ cảm biến Siêu âm ở cụm chân D3+D2 và cho lưu vào biến **"distance"**. Nhân vật Panda sẽ nói bạn biết giá trị này.
- Kế tiếp dùng khối **[constrain...]** để lọc giá trị biến **"distance"**, đảm bảo giá trị chỉ dao động trong khoảng từ **"5cm đến 50cm"**.
- Sau đó thực hiện khối **[check]** để thay đổi giá trị biến **"count"** → Đây là khối chức năng do người dùng tự lập trình.

### Tính năng "My Blocks" trong mBlock

Đây là tính năng cho phép bạn tạo ra một khối chức năng của riêng mình.
Bạn bấm vào **[My Blocks]** chọn **[Make a Block]** rồi đặt tên cho khối.
Khối **[define...]** là nơi bạn thiết kế chức năng cho nó.

Cuối cùng, nếu biến **"count"** bằng **"max"** thì điều khiển Servo ở chân D10 cho mở cửa.
Tương tự, nếu biến **"count"** bằng **"min"** thì điều khiển Servo ở chân D10 đóng cửa.
Còn nếu biến **"count"** chưa chạm tới một trong hai giá trị trên thì không làm gì cả.
Nhân vật Bat sẽ thông báo cho bạn biết trạng thái hiện tại của cửa.

### Cách khối **[check]** hoạt động

- Nếu **"distance"** < 30cm thì cho tăng biến **"count"** lên 1 đơn vị, nhưng không vượt qua giá trị **"max"**.
- Ngược lại, nếu **"distance"** ≥ 30cm, thì cho giảm biến **"count"** xuống 1 đơn vị, nhưng không vượt qua giá trị **"min"**.
- Bằng cách này giá trị **"count"** luôn dao động quanh phạm vi **"từ min đến max"**.

### Kết quả

Sau khi đã nạp code thành công ...

![hình dự án hoạt động](project_image.png)

## Bài tập thêm

- Thử một chút điều chỉnh, bản hãy thử làm một bộ thùng rác thông minh, khi có người đừng gần mới mở nắp, và tự đống nắp lại khi người rời đi.

## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 5: Đồng hồ đếm ngược](/ex/less05/README.md)
- [Bài 7: Cảnh báo va chạm](/ex/less07/README.md)
