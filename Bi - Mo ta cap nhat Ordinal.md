
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CẬP NHẬT THAM SỐ HỆ THỐNG

</div>

###### :eight_spoked_asterisk: Người lập: [**NGHỊ VĂN BI**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **01/11/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Ghi nhận thời gian cụ thể (giờ, phút, giây) thời gian đăng ký tại Kios của bệnh nhân.

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
Bi cập nhật cấu trúc:
- Thêm cột ngaygiodk vào bảng current.pstiepnhan (Ghi nhận thời gian bệnh nhân đến lấy số tiếp nhận)

ALTER TABLE current.pstiepnhan
  ADD COLUMN ngaygiodk TIMESTAMP(0) WITHOUT TIME ZONE;
  
:white_check_mark: **Xử lý**
+ Module Ordinal:
 - Cập nhật thêm giá trị vào cột ngaygiodk.
 - Thêm một parameter ngaygiodk trên report in phiếu thứ tự hỗ trợ người dùng sử dụng khi có nhu cầu.
  


