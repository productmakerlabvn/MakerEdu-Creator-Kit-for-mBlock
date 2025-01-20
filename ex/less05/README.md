# Bài 5: Đồng hồ đếm ngược - MakerEdu Creator Kit for mBlock

## Mô tả dự án

![](/ex/less05/image/BAI5.png)

Trong bài này, bạn sẽ làm quen với một thiết bị mới tên là động cơ RC Servo. Thiết bị này có tính năng đặc biệt chỗ bạn có thể điều khiến góc xoay của thiết bị bao nhiêu độ theo ý muốn cũng được, giới hạn trong phạm vi từ 0 độ đến 180 độ.

Với khả năng này của Servo, bạn sẽ được hướng dẫn làm một bộ đồng hồ đếm ngược.

Sử dụng biến trở để chọn mức thời gian muốn đếm, chọn được trong khoảng từ 0 đến 60s, giá trị bạn chọn sẽ hiển thị qua các nhân vật Sprite trên phần mềm mBlock

Sau khi đã chọn mức thời gian bạn muốn, thao tác nút nhấn để bắt đầu đếm ngược.

Servo sẽ quay kim đồng hồ từng giây, cho đến khi đếm xong.

## Các bước thực hiện

### Danh sách thiết bị



- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Mạch biến trở MKE-M04 potentiometer module](https://makerlab.vn/mkem04)
- 1x [Mạch nút nhấn MKE-M02 push button tact switch module](https://makerlab.vn/mkem02)
- 1x [Động cơ RC Servo](https://hshop.vn/dong-co-rc-servo-9g)

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
| Port D10         | Động cơ RC Servo |

### Kết nối Servo đúng cách!

Trên mạch MakerEdu Creator bạn tìm đến cụm chân cắm Servo có 3 màu (vàng - đỏ - đen) và kết nối như sau:
- Dây cam → chân vàng (S)
- Dây đỏ → chân đỏ (+)
- Dây đen → chân đen (-)

### Chương trình

- [Download file code "Bai5.mblock".](/ex/less05/mBlock5/Bai5.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices:

![Creator mBlock Bai 5](/ex/less05/image/Creator_mBlock_Bai_5.png)
![spritesBear](/ex/less05/image/spritesBear.png)
![spritesBird](/ex/less05/image/spritesBird.png)
![spritesPanda](/ex/less05/image/spritesPanda.png)

### Giải thích code

Chương trình hoạt động:

- Bên trong khối **[forever]**.
- Đầu tiên bo mạch đọc giá trị Analog từ chân A1 (Biến trở) rồi cho lưu vào biến **"pot"**.
- Sau đó biến **"pot"** sẽ qua khối **[constrain...]** để lọc giá trị, đảm bảo luôn nằm trong khoảng **"từ 0 đến 676"**.
- Rồi dùng khối **[map...]** để ánh xạ giá trị biến **"pot"** của thang đo Analog sang giá trị biến **"time"** của thang đo thời gian (0 giây - 60 giây). Nhân vật Bird sẽ cho biết thời gian đếm bạn đang chọn.
- Động cơ Servo là thiết bị có thể điều khiển góc quay **"từ 0º đến 180º"**.
  - Nếu đặt cứ mỗi một góc quét 3º tương ứng 1 giây, thì với góc quét 180º của Servo hoàn toàn có thể hiển thị cho 60 giây.
  - Dùng công thức { angle = time * 3 } để tính góc quay cho Servo (biến **"angle"**) tương ứng với số giây hiện tại (biến **"time"**).
  - Dùng khối **[set Servo port...]** để điều khiển Servo ở chân D10 quay đến góc theo giá trị biến **"angle"**. Bạn có thể xem giá trị này qua nhân vật Panda mBlock.
- Cuối cùng, bo mạch sẽ kiểm tra liên tục chân A2, xem có ai thao tác với nút nhấn không?
  - Nếu không có, thì không làm gì cả và quay lại bước đầu tiên. Nếu có phát hiện nút vừa được nhấn 1 click:
    - Sao lưu giá trị biến **"time"** vào biến **"count"**.
    - Dùng khối **[repeat...]** tạo một vòng lặp {time} lần.
      - Mỗi vòng lặp:
        - Giảm biến **"count"** xuống 1 đơn vị.
        - Tính công thức {angle = count * 3}.
        - Điều khiển Servo ở chân D10 quay theo giá trị biến **"angle"**.
        - Nhân vật Bear sẽ cho bạn biết đang đếm còn bao nhiêu giây.
        - Chờ 1 giây và thực hiện lại vòng lặp này đủ {time} lần.

### Kết quả


https://github.com/user-attachments/assets/892d0141-8cc3-4fdc-8eae-29eb5f0cafce



## Bài tập thêm

- Dùng bìa cartoon để làm mặt đồng hồ, vẽ lên mặt bìa các dấu gạch tương ứng cho từng giây, và vẽ lên các con số để mình dễ xem giờ. Thiết kế các chỗ để lắp đặt các thiết bị khác như nút nhấn hay biến trở làm thành một hộp kín. Thế là bạn đã có một bộ đếm xịn xò của riêng mình rồi đó. Trang trí thêm trên hộp với bất kì hình vẽ nào bạn thích nhé.
- Dùng thêm còi báo, để nâng cấp bộ này nào. Chẳng hạn như khi bộ đếm bắt đầu và kết thúc còi sẽ báo tick tick để biết nè. Hay khi chỉ còn vài giây, từ 10s chẳng hạn, nhịp còi sẽ tăng nhanh dần.
- Thay vì chỉnh được trong 1 phút, bạn thử mở rộng lên 5 phút, lên 10 phút, hay cả 30 phút thử xem.

## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 4: Đèn ngủ thông minh](/ex/less04/README.md)
- [Bài 6: Cổng tự động](/ex/less06/README.md)
