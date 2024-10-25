<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ GIẤY CAM KẾT CHẤP THUẬN PHẪU THUẬT, THỦ THUẬT VÀ GÂY MÊ HỒI SỨC

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **23/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thay đổi cấu trúc dữ liệu

 SQL: Cập nhật cấu trúc bảng current.chuyenvien thêm cột la_nguoi_benh
```sql
ALTER TABLE current.phauthuat
  ADD COLUMN phauthuat_capcuu NUMERIC(1,0);
COMMENT ON COLUMN current.phauthuat.phauthuat_capcuu
IS '1: Cấp cứu, 2: Bán cấp, 3: Chương trình/phiên';

ALTER TABLE current.phauthuat
  ADD COLUMN manv_bspt VARCHAR(20);
COMMENT ON COLUMN current.phauthuat.manv_bspt
IS 'Mã Bs phẫu thuật';

ALTER TABLE current.phauthuat
  ADD COLUMN manv_bsgm VARCHAR(20);
COMMENT ON COLUMN current.phauthuat.manv_bsgm
IS 'Mã Bs gây mê';

ALTER TABLE current.phauthuat
  ADD COLUMN vande_lienquan VARCHAR(20);
COMMENT ON COLUMN current.phauthuat.vande_lienquan
IS 'Vấn đề liên quan: chẩn đoán, lý do phẫu thuật, thủ thuật,...(chọn 1 hoặc nhiều vấn đề)';

ALTER TABLE current.phauthuat
  ADD COLUMN ketqua_sau_phauthuat VARCHAR;
COMMENT ON COLUMN current.phauthuat.ketqua_sau_phauthuat
IS 'Kết quả sau phẫu thuật (dự kiến)';

ALTER TABLE current.phauthuat
  ADD COLUMN phuongphap_phauthuat NUMERIC(1,0);
COMMENT ON COLUMN current.phauthuat.phuongphap_phauthuat
IS 'Phương pháp phẫu thuật, thủ thuật.
- 1: Phẫu thuật mở
- 2: Phẫu thuật nội soi
- 3: Thủ thuật';

ALTER TABLE current.phauthuat
  ADD COLUMN phuongphap_gayme VARCHAR(20);
COMMENT ON COLUMN current.phauthuat.phuongphap_gayme
IS 'Phương pháp gây mê (Chọn 1 hoặc nhiều phương pháp gây mê)';

ALTER TABLE current.phauthuat
  ADD COLUMN dieutri_ngoai_phauthuat NUMERIC(1,0);
COMMENT ON COLUMN current.phauthuat.dieutri_ngoai_phauthuat
IS 'Điều trị ngoài phẫu thuật/thủ thuật.
- 0: Không
- 1: Có';

ALTER TABLE current.phauthuat
  ADD COLUMN dieutri_ngoaipt_cuthe VARCHAR;
COMMENT ON COLUMN current.phauthuat.dieutri_ngoaipt_cuthe
IS 'Phương pháp điều trị ngoài phẫu thuật, bắt buột nhập khi cột dieutri_ngoai_phauthuat = 1';

ALTER TABLE current.phauthuat
  ADD COLUMN taibien_phauthuat VARCHAR;
COMMENT ON COLUMN current.phauthuat.taibien_phauthuat
IS 'Nguy cơ, tai biến trong và sau phẫu thuật (Chọn 1 hoặc nhiều nhiều)';

ALTER TABLE current.phauthuat
  ADD COLUMN taibien_khac VARCHAR;
COMMENT ON COLUMN current.phauthuat.taibien_khac
IS 'Nguy cơ/rủi ro khác';

ALTER TABLE current.phauthuat
  ADD COLUMN noidung_danghe VARCHAR;
COMMENT ON COLUMN current.phauthuat.noidung_danghe
IS 'Nội dung đã nghe bác sĩ giải thích có thể gặp khi phẫu thuật, thủ thuật';
```
:blue_book: Bảng dữ liệu
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |INDEX|
|:-------:|-------|:-------:|-------|:-------:|
|1|phauthuat_capcuu|NUMERIC(1,0)|1: Cấp cứu, 2: Bán cấp, 3: Chương trình/phiên||
|2|manv_bspt|VARCHAR(20)|Mã Bs phẫu thuật. Tương đương với cột `dmnhanvien.manv`. <br/>**Lưu ý**:<br/>- Họ tên, chức danh: tương đương với các cột `dmnhanvien.holot, holot_thuan, ten`.<br/>- Khoa: tương đương với cột `dmnhanvien.madv --> dmdonvi.tendv`||
|3|manv_bsgm|VARCHAR(20)|Mã Bs gây mê. Tương đương với cột `dmnhanvien.manv`. <br/>**Lưu ý**:<br/>- Họ tên, chức danh: tương đương với các cột `dmnhanvien.holot, holot_thuan, ten`.<br/>- Khoa: tương đương với cột `dmnhanvien.madv --> dmdonvi.tendv` ||
|4|chandoan|| Chẩn đoán bệnh. Tương dương với cột `phauthaut.maicdt` , `phauthaut.kqcdoant`, `phauthaut.kqcdoanpt` ||
|5|vande_lienquan|VARCHAR(20)| Vấn đề liên quan: chẩn đoán, lý do phẫu thuật, thủ thuật,...(chọn 1 hoặc nhiều vấn đề) ||
|6|ketqua_sau_phauthuat|VARCHAR| Kết quả sau phẫu thuật (dự kiến) ||
|7|phuongphap_phauthuat|NUMERIC(1,0)| Phương pháp phẫu thuật, thủ thuật.<br/> - 1: Phẫu thuật mở<br/> - 2: Phẫu thuật nội soi<br/> - 3: Thủ thuật||
|8|phuongphap_gayme|VARCHAR(20)| Phương pháp gây mê (Chọn 1 hoặc nhiều phương pháp gây mê)||
|9|dieutri_ngoai_phauthuat|NUMIRIC(1,0)| Điều trị ngoài phẫu thuật/thủ thuật.<br/> - 0: Không<br/> - 1: Có||
|10|dieutri_ngoaipt_cuthe|VARCHAR| Phương pháp điều trị ngoài phẫu thuật, bắt buột nhập khi cột dieutri_ngoai_phauthuat = 1||
|11|taibien_phauthuat|VARCHAR| Nguy cơ, tai biến trong và sau phẫu thuật (Chọn 1 hoặc nhiều nhiều)||
|12|taibien_khac|VARCHAR| Nguy cơ/rủi ro khác||
|13|noidung_danghe|VARCHAR| Nội dung đã nghe bác sĩ giải thích có thể gặp khi phẫu thuật, thủ thuật||

:white_check_mark: **Treatment: xứ lý**

:blue_book: Form: Tình hình phẫu thuật

![image](https://github.com/user-attachments/assets/653fdcb2-d0c9-4115-93bc-17b9c3bec9a6)

Xử lý thêm chức năng và in phiếu GIẤY CAM KẾT CHẤP THUẬN PHẪU THUẬT, THỦ THUẬT VÀ GÂY MÊ HỒI SỨC

![image](https://github.com/user-attachments/assets/7a3e00d3-48da-44dc-9ced-c2cc9793f192)

![image](https://github.com/user-attachments/assets/19414123-bbd2-41db-8fc3-b677afbc7d20)







