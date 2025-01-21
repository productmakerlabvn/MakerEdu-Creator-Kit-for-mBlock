# Bài 10: Đàn Piano không chạm - MakerEdu Creator Kit for mBlock

## Mô tả dự án

![](/ex/less10/image/BAI10.png)

Đàn nhạc bằng không khí, tại sao không.

Bằng cách sử dụng cảm biến siêu âm, ta có thể chọn từng vùng khoảng cách để phát note nhạc mình muốn.

Ta dùng còi để phát các note nhạc đó. Mình sẽ chọn ra 7 note nhạc cơ bản để làm đàn nào.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor](https://makerlab.vn/mkes01)
- 1x [Mạch còi báo MKE-M03 buzzer module](https://makerlab.vn/mkem03)

### Chuẩn bị trước dự án

[Hướng dẫn nạp chương trình & cài đặt Extension trên mBlock với các phần cứng MakerEdu](https://github.com/makerlabvn/mBlock-MakerEdu-Creator)

- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phần mềm mBlock và "ngôn ngữ lập trình kéo thả khối" theo hướng dẫn [tại đây](https://support.makeblock.com/hc/en-us/articles/12738783754903-Block-Reference).

![](/ex/less03/image/700px-Connect_MakerEdu_Creator_with_Computer_by_USB-C_cable.jpg)

### Sơ đồ kết nối

| MakerEdu Creator | Devices              |
|------------------|----------------------|
| Port (D3+D2)     | Cảm biến Siêu âm     |
| Port D10         | Còi báo              |

### Chương trình

- [Download file code "Bai10.mblock".](/ex/less10/mBlock5/Bai10.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn [tại đây](https://github.com/makerlabvn/mBlock-MakerEdu-Creator).

#### Blocks Devices

![Creator mBlock Bai 10 1](/ex/less10/image/825px-Creator_mBlock_Bai_10.png)

#### Blocks Sprites

##### Bat

![spritesBat](/ex/less10/image/spritesBat.png)

##### Fox

![spritesFox](/ex/less10/image/spritesFox.png)

##### Panda

<img src="/ex/less10/image/spritesPanda.png" width="200" height="100">

### Giải thích code

Vai trò của của biến **"level"**:

Có tất cả 8 mức độ. Trong đó 7 mức tương ứng với 7 note nhạc cơ bản, và một mức tương ứng không có note nào cả.

- Mức 1 tương ứng note Do.
- Mức 2 tương ứng note Re.
- Mức 3 tương ứng note Mi.
- Mức 4 tương ứng note Fa.
- Mức 5 tương ứng note Sol.
- Mức 6 tương ứng note La.
- Mức 7 tương ứng note Si.
- Mức 8 tương ứng không có note nào cả.

Chương trình hoạt động:

Bên trong khối **[forever]**.

- Đầu tiên, bo mạch đọc giá trị khoảng cách từ cảm biến Siêu âm ở cụm chân D3+D2 và cho lưu vào biến **"distance"**. Nhân vật Panda sẽ nói bạn biết giá trị khoảng cách thực tế hiện tại.
- Kế tiếp dùng khối **[constrain...]** để lọc giá trị biến **"distance"**, kết hợp với khối **[round...]**, đảm bảo giá trị nhận được là số nguyên và chỉ dao động trong khoảng từ **"5cm đến 25cm"**. Nhân vật Fox sẽ nói cho bạn biết giá trị này.
- Rồi dùng khối **[map...]** để ánh xạ giá trị biến **"distance"** có phạm vi (5 - 25) sang giá trị biến **"level"** có phạm vi (1 - 8).
- Dựa theo giá trị của biến **"level"**, chương trình có 8 trường hợp xảy ra:
  - Nếu bằng 1, sẽ điều khiển còi ở chân D10 phát note Do. Nhân vật Bat cũng nói **"Do"** cho bạn biết.
  - Nếu bằng 2, còi phát note Re và hiển thị **"Re"**.
  - Nếu bằng 3, còi phát note Mi và hiển thị **"Mi"**.
  - Nếu bằng 4, còi phát note Fa và hiển thị **"Fa"**.
  - Nếu bằng 5, còi phát note Sol và hiển thị **"Sol"**.
  - Nếu bằng 6, còi phát note La và hiển thị **"La"**.
  - Nếu bằng 7, còi phát note Si và hiển thị **"Si"**.
  - Nếu bằng 8, thì cho tắt còi và hiển thị **"..."**.

### Kết quả


https://github.com/user-attachments/assets/47e56139-610d-4efa-82ab-e548ba682cc1


## Bài tập thêm

- Tăng thêm số note nhạc, chẳng hạn các note thăng, giáng giữa các note cơ bản. Bạn cũng có thể mở rộng thêm ra nhiều note nữa cũng được.


## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 9: Phát nhạc với với còi Buzzer](/ex/less09/README.md)
