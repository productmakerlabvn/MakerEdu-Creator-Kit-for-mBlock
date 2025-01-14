# Bài 8: Radar phát hiện xâm nhập - MakerEdu Creator Kit for mBlock

## Mô tả dự án

Dùng cảm biến siêu âm kết hợp với còi Buzzer và động cơ Servo để phát hiện xâm nhập.

Bài này bạn sẽ dùng thêm động cơ Servo kết hợp với cảm biến Siêu âm và còi báo.

Để làm một hệ thống Radar phát hiện xâm nhập.

Servo làm nhiệm vụ quay cảm biến, điều này giúp tăng thêm góc quét của cảm biến.

Khi cảm biến phát hiện có vật xuất hiện trong vùng quét sẽ bật còi báo động.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor](https://makerlab.vn/mkes01)
- 1x [Mạch còi báo MKE-M03 buzzer module](https://makerlab.vn/mkem03)
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
| Port A1          | Còi báo              |
| Port D10         | Động cơ RC Servo     |

### Kết nối Servo đúng cách!

Trên mạch MakerEdu Creator bạn tìm đến cụm chân cắm Servo có 3 màu (vàng - đỏ - đen) và kết nối như sau:
- Dây cam → chân vàng (S)
- Dây đỏ → chân đỏ (+)
- Dây đen → chân đen (-)

### Chương trình

- [Download file code "Bai8.mblock".](/ex/less08/mBlock5/Bai8.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices:

![Creator mBlock Bai 8 1](/ex/less08/image/825px-Creator_mBlock_Bai_8_1.png)
![Creator mBlock Bai 8 2](/ex/less08/image/825px-Creator_mBlock_Bai_8_2.png)

### Giải thích code

Chương trình hoạt động:

Đầu tiên, khi bo mạch mới khởi động, có 1 khối được thực hiện một lần trước khi bước vào khối **[forever]**.

- Khối **[set Servo port...]** sẽ điều khiển Servo ở chân D10 quay đến góc 0º.

Chương trình có 2 nhóm thiết bị hoạt động độc lập:

- Nhóm 1, là động cơ Servo → có chức năng làm trục quay Radar.
- Nhóm 2, là cảm biến Siêu âm và Còi báo → có chức năng làm Radar.

Hoạt động của nhóm 1, được khối **[checkServo]** đảm nhận → Đây là khối chức năng do người dùng tự lập trình thêm vào.

### Cách khối **[checkServo]** hoạt động:

- Đầu tiên nhân vật Bat sẽ nói cho bạn biết giá trị góc quay hiện tại của Servo qua khối **[get current angle of Servo port...]**.
- Dựa theo giá trị góc quay hiện tại, chương trình sẽ có 3 quyết định:
  - Nếu góc đang là 0º, thì khối **[set Servo port...]** được thực hiện để điều khiển quay đến góc 180º.
  - Tương tự nếu góc đang là 180º, Servo sẽ được điều khiển quay trở lại góc 0º.
  - Còn nếu góc quay chưa tới mốc 0º hoặc 180º thì không làm gì cả.

Bên trong khối **[forever]**:

- Khối **[checkServo]** được thực hiện.
- Sau đó, bo mạch đọc giá trị khoảng cách từ cảm biến Siêu âm ở cụm chân D3+D2 và cho lưu vào biến **"distance"**. Nhân vật Panda sẽ nói bạn biết giá trị này.
- Kế tiếp dùng khối **[constrain...]** để lọc giá trị biến **"distance"**, đảm bảo giá trị chỉ dao động trong khoảng từ **"5cm đến 50cm"**.
- Dựa theo giá trị **"distance"**, chương trình ra 2 quyết định:
  - Nếu **"distance"** < 15cm, nhân vật Snail thông báo "Thief" và bật còi báo động.
  - Ngược lại, **"distance"** ≥ 15cm, sẽ thông báo "Safe" và tắt còi báo động.

### Kết quả

Sau khi đã nạp code thành công ...

![hình dự án hoạt động](project_image.png)

## Bài tập thêm

- Thử một chút điều chỉnh, bạn hãy thử làm một bộ thùng rác thông minh, khi có người đứng gần mới mở nắp, và tự đóng nắp lại khi người rời đi.

## Tài liệu tham khảo

... link down code mẫu

## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 7: Cảnh báo va chạm](/ex/less07/README.md)
- [Bài 9: Phát nhạc với với còi Buzzer](/ex/less09/README.md)