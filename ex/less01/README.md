# Bài 1: Điều khiển bật tắt đèn Led - MakerEdu Creator Kit for mBlock

## Mô tả dự án

... hình thumnail dự án

Trong bài học đầu tiên này, bạn sẽ được làm quen với ngôn ngữ lập trình kéo thả khối mBlock qua dự án điều khiển bật tắt đèn LED bằng nút nhấn.

## Các bước thực hiện

### Danh sách thiết bị

- 1x Mạch MakerEdu Creator.
- 1x Cáp USB-C.
- 1x Mạch nút nhấn MKE-M02 push button tact switch module.
- 1x Mạch led đơn MKE-M01 10mm single LED module.

### Chuẩn bị trước dự án

- Tải và cài đặt phần mềm mBlock theo hướng dẫn tại đây.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn tại đây.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm mblock theo hướng dẫn tại đây.
- Kết nối mạch MakerEdu Creator với máy tính qua cáp USB-C sẽ thấy đèn nguồn (PWR) trên mạch phát sáng.
- Hiểu cấu trúc của một chương trình trên phầm mềm mBlock và "ngôn ngữ lập trình kéo thả khối" theo hướng dẫn tại đây.
... hình kết nối mạch MakerEdu Creator với máy tính

### Sơ đồ kết nối

| MakerEdu Creator | Devices  |
|------------------|----------|
| Port A1          | Nút nhấn |
| Port D10         | LED đơn  |

### Chương trình

- Download file code "Bai_1.mblock".
- Mở phần mềm mBlock vào **[File]** chọn **[Open from your computer]** và mở file code bạn vừa tải về.
- Ghép nối các thiết bị theo sơ đồ kết nối và tiến hành nạp chương trình **[Upload]** theo hướng dẫn tại đây.

### Blocks Devices

![](/ex/less01/image/524px-Creator_mBlock_Bai_1.png)

### Giải thích code

#### Cấu trúc chung của chương trình

- Tất cả chương trình đều bắt đầu từ khối **[ when MakerEdu Creator starts up ]**. Khối này chỉ thực hiện 1 lần và chương trình sẽ kết thúc. Bo mạch sẽ cần "reset" để chạy lại từ đầu.
- Vậy nên, để chương trình hoạt động liên tục, ta sẽ cần dùng thêm một khối **[ forever ]**. Những khối nào nằm trong khối này, sẽ được thực hiện tuần tự từ trên xuống, và cứ thế lặp lại.

#### Chương trình hoạt động

- Đầu tiên, khi bo mạch mới khởi động, có 2 khối được thực hiện một lần trước khi bước vào khối **[ forever ]**.
  - Khối **[ set Digital port... ]** sẽ điều khiển chân D10 (LED) xuất tín hiệu `LOW`, làm tắt đèn LED.
  - Khối **[ set (led)... ]** tạo ra một biến có tên **"led"** và lưu giá trị `0`. Biến này có vai trò lưu trạng thái hoạt động hiện tại của đèn LED, với giá trị `0` là đèn LED tắt và giá trị `1` là đèn LED sáng.
- Bên trong khối **[ forever ]**.
  - Bo mạch dùng khối **[ Button port... ]** để kiểm tra liên tục chân A1, xem có ai thao tác với nút nhấn không? Không có thì cho kiểm tra lại tiếp. Nếu có phát hiện nút vừa được nhấn 1 click, thì cho so sánh giá trị của biến **"led"**.
    - Nếu **"led"** bằng `0`, tức đèn LED đang tắt. Lúc này lưu **"led"** bằng `1` và cho chân D10 (LED) xuất tín hiệu `HIGH`, làm bật đèn LED.
    - Nếu **"led"** khác `0` (bằng `1`), tức đèn LED đang bật. Lúc này lưu **"led"** bằng `0` và cho chân D10 (LED) xuất tín hiệu `LOW`, làm tắt đèn LED.

### Kết quả

<div align="center">
    <video src="https://github.com/MinhKhanh614/MakerEdu-Creator-Kit-for-mBlock/blob/main/ex/less01/BAI1.mp4" alt="" height=200/>
</div>



### Bài tập thêm

Thay vì mỗi lần nhấn nút 1 cái, là đèn LED thay đổi trạng thái. Bạn hãy thử code sao cho khi nút đang được nhấn thì đèn sáng, và ngược lại nhả nút đèn sẽ tắt.


## Bài viết liên quan

...
