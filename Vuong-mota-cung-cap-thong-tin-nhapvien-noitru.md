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
  ADD COLUMN giay_to_khac VARCHAR;
COMMENT ON COLUMN current.bnnoitru.giay_to_khac
IS 'Giấy tờ khác';
```

:blue_book: Bảng bnnoitru thêm cột
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |INDEX|
|:-------:|-------|:-------:|-------|:-------:|
|1|bansao_cccd|NUMERIC(1,0)|Bản sao căn cước/hộ chiếu||
|2|the_bhyt|NUMERIC(1,0)|Nộp thẻ bảo hiểm y tế||
|3|giay_cv|NUMERIC(1,0)|Nộp giấy chuyển viện||
|4|giay_to_khac|VARCHAR|Nộp giấy tờ khác||

:white_check_mark: **Treatment: xử lý**

:blue_book: Form danh sách điều trị

  ![image](https://github.com/user-attachments/assets/b8a6ca7e-ea49-469c-b2c4-dbe5369d0325)

  Bổ sung chức năng cho người dùng cập nhật và in giấy cung cấp thông tin và cam kết chung về nhập viện nội trú

  ![image](https://github.com/user-attachments/assets/e3b6869d-540c-4a5b-9316-52d44966f1db)

    



