# Bài 7: Cảnh báo va chạm - MakerEdu Creator Kit for mBlock

## Mô tả dự án

![](/ex/less07/image/BAI7.png)

Trong bài này, ta sẽ nâng độ khó sử dụng cảm biến siêu âm lên hơn nữa.

Dựa theo giá trị khoảng cách mà cảm biến trả về. Bạn sẽ làm một bộ cảnh báo cho xe ở bãi đậu.

Sẽ có 3 mức cảnh báo từ "Chú ý" đến "Cảnh báo" và cuối cùng là "Nguy hiểm". Với mỗi mức độ sẽ ở mức khoảng cách khác nhau. Vật thể càng tiến gần cảm biến, còi sẽ kêu càng nhanh.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor](https://makerlab.vn/mkes01)
- 1x [Mạch còi báo MKE-M03 buzzer module](https://makerlab.vn/mkem03)

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
| Port D10         | Còi báo              |

### Chương trình

- [Download file code "Bai7.mblock".](/ex/less07/mBlock5/Bai7.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices

![Creator mBlock Bai 7](/ex/less07/image/825px-Creator_mBlock_Bai_7.png)

### Giải thích code

Hiệu ứng âm thanh từ khối **[set Digital port _ , HIGH _ (s), LOW _ (s), then repeat forever]**:

Khối này khi được gọi, sẽ xuất tín hiệu Digital ở chân được chọn. Với chu kỳ là khoảng thời gian xuất mức HIGH và mức LOW do bạn chọn.
Bằng cách kết nối module Còi đến chân D10, còi sẽ được bật/tắt liên tục.
Khoảng thời gian bật/tắt càng ngắn, nhịp còi kêu càng nhanh, và ngược lại.
Để còi dừng kêu, bạn dùng khối **[set Digital port _ stop!]**.

Chương trình hoạt động:

Bên trong khối **[forever]**.

- Đầu tiên, bo mạch đọc giá trị khoảng cách từ cảm biến Siêu âm ở cụm chân D3+D2 và cho lưu vào biến **"distance"**. Nhân vật Panda sẽ nói bạn biết giá trị này.
- Kế tiếp dùng khối **[constrain...]** để lọc giá trị biến **"distance"**, đảm bảo giá trị chỉ dao động trong khoảng từ **"5cm đến 50cm"**.
- Dựa theo giá trị **"distance"**, chương trình ra 4 quyết định:
  - Nếu **"distance"** ≥ 30cm, nhân vật Bat thông báo "Safe" và còi không bật, hay tắt còi.
  - Nếu **"distance"** trong khoảng [20cm - 30cm), sẽ gửi thông báo "Attention" và bật còi báo.
  - Nếu **"distance"** trong khoảng [10cm - 20cm), sẽ gửi thông báo "Warning" và tăng tốc nhịp còi báo.
  - Nếu **"distance"** < 10cm, sẽ gửi thông báo "Danger" và tăng tốc nhịp còi báo nhanh hơn nữa.

### Kết quả

Sau khi đã nạp code thành công ...

![hình dự án hoạt động](project_image.png)

## Bài tập thêm

- Thử một chút điều chỉnh, bạn hãy thử làm một bộ thùng rác thông minh, khi có người đứng gần mới mở nắp, và tự đóng nắp lại khi người rời đi.

## Tài liệu tham khảo

... link down code mẫu

## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 6: Cổng tự động](/ex/less06/README.md)
- [Bài 8: Radar phát hiện xâm nhập](/ex/less08/README.md)
