<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ GIẤY CUNG CẤP THÔNG TIN VÀ CAM KẾT CHUNG VỀ NHẬP VIỆN NỘI TRÚ

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **23/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thay đổi cấu trúc dữ liệu

 SQL: Cập nhật cấu trúc bảng current.bnnoitru
```sql
ALTER TABLE current.bnnoitru
  ADD COLUMN bansao_cccd NUMERIC(1,0);
COMMENT ON COLUMN current.bnnoitru.bansao_cccd
IS '0: Không nộp
1: Có nộp';

ALTER TABLE current.bnnoitru
  ADD COLUMN the_bhyt NUMERIC(1,0);
COMMENT ON COLUMN current.bnnoitru.the_bhyt
IS '0: Không nộp
1: Có nộp
2: Có, không mang theo';

ALTER TABLE current.bnnoitru
  ADD COLUMN giay_cv NUMERIC(1,0);
COMMENT ON COLUMN current.bnnoitru.giay_cv
IS '0: Không nộp
1: Có nộp';

ALTER TABLE current.bnnoitru
  ADD COLUMN giay_to_khac NUMERIC(1,0);
COMMENT ON COLUMN current.bnnoitru.giay_to_khac
IS 'Giấy tờ khác';
```

:blue_book: Bảng bnnoitru thêm cột
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |INDEX|
|:-------:|-------|:-------:|-------|:-------:|
|1|la_benh_nhan|VNUMERIC(1,0)|0: là bệnh nhân, 1: là người thân||
|2|la_benh_nhan|VNUMERIC(1,0)|0: là bệnh nhân, 1: là người thân||
|3|la_benh_nhan|VNUMERIC(1,0)|0: là bệnh nhân, 1: là người thân||
|4|la_benh_nhan|VNUMERIC(1,0)|0: là bệnh nhân, 1: là người thân||

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



