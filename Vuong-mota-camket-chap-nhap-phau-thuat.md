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
ALTER TABLE current.chuyenvien
  ADD COLUMN la_nguoi_benh NUMERIC(1,0);

COMMENT ON COLUMN current.chuyenvien.la_nguoi_benh
IS '0: Là người bệnh
1: Là người thân';
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




