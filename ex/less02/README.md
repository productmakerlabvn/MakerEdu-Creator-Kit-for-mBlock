# Bài 2: Điều khiển độ sáng đèn Led - MakerEdu Creator Kit for mBlock

## Mô tả dự án

![](/ex/less02/image/BAI2.png)

Tiếp nối bài học trước, trong bài này các bạn cũng sẽ làm dự án điều khiển đèn LED, nhưng dùng biến trở điều khiển.

Không chỉ làm bật tắt đèn LED, thiết bị này còn cho phép bạn điều khiển được độ sáng đèn LED theo ý muốn.

## Các bước thực hiện

### Danh sách thiết bị

- 1x [Mạch MakerEdu Creator](https://www.makerlab.vn/creator)
- 1x [Cáp USB-C](https://hshop.vn/cap-usb-type-c)
- 1x [Mạch biến trở MKE-M04 potentiometer module](https://makerlab.vn/mkem04)
- 1x [Mạch led đơn MKE-M01 10mm single LED module](https://makerlab.vn/mkem01)

### Chuẩn bị trước dự án

- Tải và cài đặt phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn **[tại đây]**.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm mblock theo hướng dẫn **[tại đây]**.
- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phầm mềm mBlock và **"ngôn ngữ lập trình kéo thả khối"** theo hướng dẫn **[tại đây]**.

### Sơ đồ kết nối

| MakerEdu Creator | Devices  |
|------------------|----------|
| Port A1          | Biến trở |
| Port D10         | LED đơn  |

### Chương trình

- [Download file code "Bai2.mblock".](/ex/less02/mBlock5/Bai2.mblock)
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn **[tại đây]**.

#### Blocks Devices:

![Creator mBlock Bai 2](/ex/less02/image/Creator_mBlock_Bai_2.png)

### Giải thích code

Chương trình hoạt động:

- Bên trong khối **[forever]**.
- Việc đầu tiên bo mạch làm là đọc giá trị Analog từ chân A1 (Biến trở) rồi cho lưu vào biến **"pot"**.
- Bằng cách dùng khối **[send upload mode message...]**, bạn có thể xem giá trị này qua nhân vật Panda nói trên phần mềm mBlock.
- Sau đó giá trị trong biến **"pot"** sẽ được lọc một lần nữa bằng khối **[constrain...]** để đảm bảo giá trị luôn nằm trong khoảng **"từ 0 đến 676"**.
- Rồi ánh xạ giá trị **"pot"** sang một giá trị tương ứng ở thang đo (%) và lưu vào biến **"led"**. Bạn có thể xem giá trị này qua nhân vật Bird nói trên phần mềm mBlock.
- Cuối cùng là điều khiển chân D10 (LED) xuất tín hiệu PWM theo giá trị của biến **"led"** giúp điều khiển độ sáng đèn LED.

#### Ý nghĩa con số 676 là gì?

- Bởi vì phạm vi kết quả mà giá trị Analog trả về là **"từ 0 đến 1023"**. Tương ứng mức điện áp **"từ 0V đến 5V"**. Các module của hệ sinh thái MakerEdu đều hoạt động ở mức điện áp **"từ 0V đến 3,3V"**.
- Vậy nên nếu nguồn điện áp lý tưởng cấp cho bo mạch là đúng chính xác 5V, thì giá trị lớn nhất đọc được từ module Biến trở sẽ là 676, tương ứng mức điện áp 3,3V.
- Nhưng thật tế nguồn điện chúng ta sử dụng cấp cho thiết bị, mỗi bạn mỗi khác. Thường dao động quanh mức 5V, có thể là 4,9V cũng có thể là 5,1V chẳng hạn. Cho nên bước lọc kết quả trên là rất quan trọng!

#### Chức năng khối **[constrain...]**:

- Như cái tên của khối, sự ràng buộc. Trong chương trình này, khối sẽ kiểm tra giá trị trong biến **"pot"**.
  - Nếu giá trị nhỏ hơn 0, sẽ chỉnh lại biến **"pot"** giá trị 0.
  - Nếu giá trị lớn hơn 676, sẽ lưu lại vào biến **"pot"** giá trị 676.
  - Còn nếu giá trị **"pot"** trong khoảng **"từ 0 đến 676"**, thì vẫn giữ nguyên giá trị của biến.

#### Chức năng khối **[map...]**:

- Khối này có chức năng ánh xạ một giá trị từ thang đo này sang một giá trị tương ứng ở thang đo khác.
- Trong chương trình này, khối sẽ ánh xạ giá trị biến **"pot"** trong thang đo Analog (0 - 676) sang một giá trị tương ứng ở thang đo % (0 - 100) rồi lưu vào biến **"led"**.

### Kết quả

Sau khi đã nạp code thành công ...  

![hình dự án hoạt động](project_image.png)  

## Bài tập thêm

- Bạn đã biết cách đọc giá trị từ biến trở, hãy thử dùng chính giá trị này, có thể biến đổi hệ số hay thang đo tùy ý bạn, để điều khiển tốc độ chớp tắt của đèn LED xem hiệu ứng hiệu lại như thế nào.
- Nhân vật Bird sẽ nói cho bạn biết giá trị của **"led"** hiện đang là bao nhiêu
- Cuối cùng, chương trình dùng giá trị của biến **"led"** để xuất tín hiệu PWM trên chân D10, điều khiển độ sáng đèn LED.

## Bài viết liên quan

- [MakerEdu Creator Kit for mBlock](/README.md)
- [Bài 1: Điều khiển bật tắt đèn Led](/ex/less01/README.md)
- [Bài 3: Chống trộm ngăn kéo](/ex/less03/README.md)