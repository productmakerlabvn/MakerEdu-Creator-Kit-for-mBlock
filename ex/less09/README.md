# Bài 9: Phát nhạc với với còi Buzzer - MakerEdu Creator Kit for mBlock

## Mô tả dự án

![](/ex/less09/image/BAI9.png)

Nhấn nút nhấn để bật 1 bài nhạc bất kỳ bằng còi Buzzer.

Trong bài này, bạn sẽ làm một hộp nhạc. Sử dụng biến trở để xoay nút chọn bài nhạc muốn phát.

Và dùng nút nhấn để play bài nhạc đã chọn đó. Ta sẽ dùng còi Buzzer phát các giai điệu bài nhạc.

Trong bài này, bạn sẽ học cách tạo các khối nhạc của riêng mình.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Mạch biến trở MKE-M04 potentiometer module](https://makerlab.vn/mkem04)
- 1x [Mạch nút nhấn MKE-M02 push button tact switch module](https://makerlab.vn/mkem02)
- 1x [Mạch còi báo MKE-M03 buzzer module](https://makerlab.vn/mkem03)

### Chuẩn bị trước dự án

- Tải và cài đặt phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm mblock theo hướng dẫn **[tại đây]**.
- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phầm mềm mBlock và **"ngôn ngữ lập trình kéo thả khối"** theo hướng dẫn **[tại đây]**.

### Sơ đồ kết nối

| MakerEdu Creator | Devices   |
|------------------|-----------|
| Port A1          | Biến trở  |
| Port A2          | Nút nhấn  |
| Port D10         | Còi báo   |

### Chương trình

- [Download file code "Bai9.mblock".](/ex/less09/mBlock5/Bai9.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices

![Creator mBlock Bai 9 1](/ex/less09/image/751px-Creator_mBlock_Bai_9_1.png)
![Creator mBlock Bai 9 2](/ex/less09/image/525px-Creator_mBlock_Bai_9_2.png)
![Creator mBlock Bai 9 3](/ex/less09/image/525px-Creator_mBlock_Bai_9_3.png)
![Creator mBlock Bai 9 4](/ex/less09/image/525px-Creator_mBlock_Bai_9_4.png)
![spritesBear](/ex/less09/image/spritesBear.png)
![spritesBird](/ex/less09/image/spritesBird.png)

### Giải thích code

Vai trò của các khối **[Song...]**:

Đây là khối chức năng do người dùng tự lập trình.
Hiện trong dự án này, mình muốn tạo hộp nhạc phát được 3 bài. Vậy nên cần tạo 3 khối, có tên lần lượt là: **"Song_1"**, **"Song_2"**, **"Song_3"**.
Mỗi khối gồm nhiều khối **[Play note...]** nhỏ. Các khối này có chức năng điều khiển còi Buzzer ở chân D10 phát ra từng note nhạc. Kết hợp các note nhạc lại, bạn sẽ tạo ra một bản nhạc.

Chương trình hoạt động:

Bên trong khối **[forever]**.

- Đầu tiên bo mạch đọc giá trị Analog từ chân A1 đang kết nối với Biến trở rồi cho lưu vào biến **"pot"**.
- Sau đó biến **"pot"** sẽ qua khối **[constrain...]** để lọc giá trị, đảm bảo luôn nằm trong khoảng **"từ 0 đến 676"**.
- Rồi dùng khối **[map...]** để ánh xạ giá trị biến **"pot"** của thang đo Analog sang giá trị biến **"song"** có thang đo **"từ 1 đến 3"**, tương ứng với 3 bài hát. Nhân vật Bird sẽ cho biết bạn đang chọn bài hát nào.
- Cuối cùng, bo mạch sẽ kiểm tra chân A2, xem có ai thao tác với nút nhấn không? Nếu không có, thì không làm gì cả và quay lại bước đầu tiên. Nếu có phát hiện nút vừa được nhấn 1 click. Dựa theo giá trị của biến **"song"** có 3 trường hợp:
  - Nếu **"song"** bằng 1, cho thực hiện khối **[Song_1]**. Nhân vật Bear sẽ thông báo **"We wish you a merry Christmas..."**.
  - Nếu **"song"** bằng 2, cho chạy khối **[Song_2]**, bạn sẽ thấy thông báo **"Happy Birthday..."**.
  - Nếu **"song"** bằng 3, cho chạy khối **[Song_3]**, bạn sẽ thấy thông báo **"Jingle Bells..."**.
- Cho đến khi bài nhạc phát xong, thông báo **"Done"** sẽ hiện lên. Lúc này chương trình quay lại bước đầu tiên.

### Kết quả


https://github.com/user-attachments/assets/3c2d920d-42ab-4b80-9f49-91205921e69a


## Bài tập thêm

- Tạo thêm 1 bài nhạc vào bộ hộp nhạc nào (cung cấp bảng Note nhạc và thời gian phát mỗi nốt nhạc), bài nhạc này là của Mario.


## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 8: Radar phát hiện xâm nhập](/ex/less08/README.md)
- [Bài 10: Đàn Piano không chạm](/ex/less10/README.md)
