<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ GIẤY CAM KẾT CHUYỂN CƠ SỞ KHÁM BỆNH, CHỮA BỆNH

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **23/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thay đổi cấu trúc dữ liệu

 SQL: Cập nhật cấu trúc bảng current.chuyenvien thêm cột la_nguoi_benh
```sql
ALTER TABLE current.chuyenvien
  ADD COLUMN la_nguoi_benh NUMERIC(1,0);

COMMENT ON COLUMN current.chuyenvien.la_nguoi_benh
IS '0: Là người bệnh
1: Là người thân';
```
 SQL: Cập nhật cấu trúc bảng current.psdangky
```sql

ALTER TABLE current.psdangky
  ADD COLUMN namsinhqh DATE;
COMMENT ON COLUMN current.psdangky.namsinhqh
IS 'Ngày tháng năm sinh người thân bệnh nhân';

ALTER TABLE current.psdangky
  ADD COLUMN tuoiqh NUMERIC(2,0);
COMMENT ON COLUMN current.psdangky.tuoiqh
IS 'Tuổi người thân bệnh nhân';
```

:blue_book: Bảng chuyenvien thêm cột
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |INDEX|
|:-------:|-------|:-------:|-------|:-------:|
|1|la_benh_nhan|NUMERIC(1,0)|0: là bệnh nhân, 1: là người thân||

:blue_book: Bảng psdangky thêm cột
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |INDEX|
|:-------:|-------|:-------:|-------|:-------:|
|1|namsinhqh|DATE|Năm sinh người thân bệnh nhân||
|2|tuoiqh|NUMERIC(2,0)|Tuổi người thân bệnh nhân||

:white_check_mark: **Prescription: xử lý**

:blue_book: Form nhập viện

    - Cập nhật thêm thông tin người thân: loại quan hệ, họ và tên quan hệ, địa chỉ, điện thoại (nếu chưa cập nhật ở form đăng ký)
    - Bổ sung thêm: ngày tháng năm sinh và tuổi của người thân
    
:white_check_mark: **Treatment: xứ lý**

:blue_book: Form: Thông tin bệnh nhân

![image](https://github.com/user-attachments/assets/fd3c6162-c893-4140-8470-2807445b0677)

    - Cập nhật thêm thông tin người thân: loại quan hệ, họ và tên quan hệ, địa chỉ, điện thoại (nếu chưa cập nhật ở form đăng ký)
    - Bổ sung thêm: ngày tháng năm sinh và tuổi của người thân

:blue_book: Form: chuyển viện

![image](https://github.com/user-attachments/assets/7a991950-05d0-4404-8f0d-6ae0bde64eb4)

Thêm nút xử lý và in ra giấy cam kết chuyển viện

![image](https://github.com/user-attachments/assets/312a7c30-244d-443c-b09f-52575fcdc9c5)


