<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN HÀM API TRA CỨU THÔNG TIN THÔNG TUYẾN TRÊN BHXH THEO CÔNG VĂN CV 1923-BHXHVN

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **07/07/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **15/07/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thay đổi hàm tra cứu API theo công văn CV 1923-BHXHVN
- [CV 1923-BHXHVN.pdf](<../File-ho-tro/CV 1923-BHXHVN.pdf>)
- [Ham API tra cuu TT.pdf](<../File-ho-tro/Ham API tra cuu TT.pdf>)

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm `ngaysinh`,`cmnd`,`api_bhxh_username`, `api_bhxh_password`, `api_bhxh_donvi`, `api_bhxh_benhvien` vào bảng `current.dmnhanvien`: để lưu thông tin sử dụng trong quá trình sử dụng API kiểm tra thông tuyến.

- `api_bhxh_password`: Mã hóa theo phương thức chung của DHG.Hospital.

:white_check_mark: **Nguyên tắc sử dụng tài khoản để gọi API thông tuyến**

- Sử dụng tài khoản đăng nhập để kiểm tra thông tuyến. Thứ tự ưu tiên để lấy thông tin tài khoản đã được đăng ký trên cổng giám định BHXH như sau:

1. Trường hợp tài khoản đăng nhập có cấu hình các thông tin thông tin tài khoản API-BHXH, sẽ thực hiện API theo thông tin cấu hình.

2. Trường hợp tài khoản chưa cấu hình thông tin tài khoản API-BHXH 👉 sẽ dựa vào `Đơn vị (khoa phòng)` của tài khoản này trực thuộc để tìm tài khoản có cấu hình thông tin thông tin tài khoản API-BHXH, và được check `Đơn vị (khoa phòng), api_bhxh_donvi=1` theo `madv` (`Đơn vị (khoa phòng)`, `lấy tài khoản có cấu hình đầu tiên`).

3. Trường hợp tài khoản chưa cấu hình, bước 2 cũng không có 👉 sẽ tìm tài khoản có cấu hình thông tin tài khoản API-BHXH theo cả bệnh viện (`api_bhxh_benhvien=1`,`lấy tài khoản có cấu hình đầu tiên`).

:white_check_mark: **Module Admin**

- Thêm chức năng cập nhật các dữ liệu phát sinh trên bảng `current.dmnhanvien`
- ![](https://i.imgur.com/i7MRcj1.png)

:white_check_mark: **Các module, chức năng sử dụng API kiểm tra thông tuyến**

- Kiểm tra API thông tuyến như cũ
