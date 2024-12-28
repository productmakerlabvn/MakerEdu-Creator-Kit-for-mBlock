# Bài 3: Chống trộm ngăn kéo - MakerEdu Creator Kit for mBlock

## Mô tả dự án

Dùng cảm biến ánh sáng quang trở phát hiện mở tủ bật báo động bằng còi Buzzer, hiển thị giá trị cảm biến lên sprite ...

Giả sử bạn có một ngăn hộp tủ bí mật, chứa những món đồ bạn yêu thích, không muốn bị mấy đứa em quậy phá.

Bài học này sẽ chỉ bạn một bộ báo trộm cho ngăn tủ.

Dựa trên nguyên lý khi đóng tủ, ánh sáng trong hộc tủ rất tối. Và ngược lại khi mở tủ, ánh sáng không gian xung quanh sẽ tràn vào.

Bằng cách dùng cảm biến Quang trở, có thể đo đạc theo sự thay đổi cường độ ánh sáng. Và kết hợp với còi báo.

Mỗi khi có ai đó tự ý mở hộc tủ của bạn, còi sẽ bật cảnh báo.

## Các bước thực hiện

### Danh sách thiết bị

- 1x Mạch MakerEdu Creator.
- 1x Cáp USB-C.
- 1x Cảm biến ánh sáng quang trở MKE-S02 LDR light sensor.
- 1x Mạch còi báo MKE-M03 buzzer module.

### Chuẩn bị trước dự án

- Tải và cài đặt phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm mblock theo hướng dẫn **[tại đây]**.
- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phầm mềm mBlock và **"ngôn ngữ lập trình kéo thả khối"** theo hướng dẫn **[tại đây]**.

### Sơ đồ kết nối

| MakerEdu Creator | Devices              |
|------------------|----------------------|
| Port A1          | Cảm biến Quang trở   |
| Port D10         | Còi báo              |

### Chương trình

- Download file code **"Bai_3.mblock"**.
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices

![Creator mBlock Bai 3](/ex/less03/image/Creator_mBlock_Bai_3.png)

### Giải thích code

Chương trình hoạt động:

- Bên trong khối **[forever]**.
- Đầu tiên bo mạch đọc giá trị Analog từ chân A1 đang kết nối với cảm biến Quang trở, và cho lưu vào biến **"LDR"**. Nhân vật Panda sẽ nói bạn biết giá trị này.
- Sau đó biến **"LDR"** sẽ qua khối **[constrain...]** để lọc giá trị, đảm bảo luôn nằm trong khoảng **"từ 0 đến 676"**.
- Rồi dùng khối **[map...]** để ánh xạ giá trị biến **"LDR"** của thang đo Analog sang giá trị biến **"light"** của thang đo %. Nhân vật Bird sẽ nói bạn biết giá trị này.
- Cuối cùng dựa theo giá trị trong **"light"**.
  - Nếu lớn hơn 50% sẽ kích hoạt còi ở chân D10.
  - Ngược lại thì cho tắt còi.
- Nhân vật Sheep sẽ thông báo cho bạn biết trạng thái của hộp tủ.

### Kết quả

Sau khi đã nạp code thành công ...

![hình dự án hoạt động](project_image.png)

## Bài tập thêm

- Kết hợp thêm Nút nhấn để bật tắt tính năng báo trộm này. Đâu phải lúc nào bạn cũng muốn mỗi khi chính mình mở tủ còi lại kêu đúng chứ.
- Thao tắc Nút nhấn để bật tắt tính năng báo động thì dễ quá, ai cũng làm được. Bạn hãy thử thêm một chút tính năng bảo mật. Bằng cách thao tác số lần nút nhấn khác nhau mà chỉ riêng mình bạn biết để bật tắt tính năng báo động xem.

## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 2: Điều khiển độ sáng đèn Led](/ex/less02/README.md)
- [Bài 4: Đèn ngủ thông minh](/ex/less04/README.md)
