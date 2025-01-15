# Bài 4: Đèn ngủ thông minh - MakerEdu Creator Kit for mBlock

## Mô tả dự án

![](/ex/less04/image/BAI4.png)

Ở những bài trước bạn đã học cách điều khiển thiết bị, cụ thể ở đây là đèn LED theo cách thao tác bằng tay lên các thiết bị nhận biết như nút nhấn hay biến trở.

Trong bài này bạn sẽ làm một dự án điều khiển thiết bị hoàn toàn tự động. Cũng dùng cảm biến ánh sáng để điều khiển độ sáng của LED theo môi trường xung quanh.

Khi trời càng sáng, đèn LED sẽ tắt dần. Và ngược lại, khi trời càng tối, đèn LED sẽ càng sáng dần.

Với tính năng này các bạn có thể sử dụng cho nhiều ứng dụng, như bộ đèn ngủ trong phòng, hay hệ thống đèn tự động ngoài sân vườn.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Cảm biến ánh sáng quang trở MKE-S02 LDR light sensor](https://makerlab.vn/mkes02)
- 1x [Mạch led đơn MKE-M01 10mm single LED module](https://makerlab.vn/mkem01)

### Chuẩn bị trước dự án

- Tải và cài đặt phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm mblock theo hướng dẫn **[tại đây]**.
- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phầm mềm mBlock và **"ngôn ngữ lập trình kéo thả khối"** theo hướng dẫn **[tại đây]**.

### Sơ đồ kết nối

| MakerEdu Creator | Devices            |
|------------------|--------------------|
| Port A1          | Cảm biến Quang trở |
| Port D10         | LED đơn            |

### Chương trình

- [Download file code "Bai4.mblock".](/ex/less04/mBlock5/Bai4.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices:

![Creator mBlock Bai 4](/ex/less04/image/750px-Creator_mBlock_Bai_4.png)

### Giải thích code

Chương trình hoạt động:

- Bên trong khối **[forever]**.
- Đầu tiên bo mạch đọc giá trị Analog từ chân A1 đang kết nối với cảm biến Quang trở, và cho lưu vào biến **"LDR"**. Nhân vật Panda sẽ nói bạn biết giá trị này.
- Sau đó biến **"LDR"** sẽ qua khối **[constrain...]** để lọc giá trị, đảm bảo luôn nằm trong khoảng **"từ 0 đến 676"**.
- Rồi dùng khối **[map...]** để ánh xạ giá trị biến **"LDR"** của thang đo Analog sang giá trị biến **"light"** của thang đo %. Nhân vật Bird sẽ nói bạn biết giá trị này.
- Cuối cùng, để điều khiển độ sáng đèn LED trong dãi phạm vi **"từ 30% đến 70%"** của **"light"**, tương tự.
  - Dùng khối **[constrain...]** để lọc giá trị cho biến **"light"**.
  - Dùng khối **[map...]** để ánh xạ giá trị biến **"light"** sang biến **"led"**.
  - Lúc này có thể dùng biến **"led"** để điều khiển độ sáng đèn LED ở chân D10. Nhân vật Bear sẽ nói bạn biết giá trị này.

### Kết quả


https://github.com/user-attachments/assets/7f6807d2-c00f-40e3-b3a0-d992a396cbf4


## Bài tập thêm

- Sẵn ôn lại bài cũ đã học trước đó. Bạn thử kết hợp thêm nút nhấn và biến trở để tích hợp tính năng cho hệ thống đèn của mình nào. Với nút nhấn để thao tác chuyển đổi chế độ **"AUTO"** và **"MANUAL"**. Nếu ở chế độ tự động, thì đèn LED hoạt động dựa theo giá trị của cảm biến. Còn ở chế độ thủ công, bạn có thể dùng biến trở để điều khiển độ sáng đèn LED theo ý mình.


## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 3: Chống trộm ngăn kéo](/ex/less03/README.md)
- [Bài 5: Đồng hồ đếm ngược](/ex/less05/README.md)
