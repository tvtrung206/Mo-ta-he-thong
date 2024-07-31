<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: TÓM TẮT BỆNH ÁN THEO THÔNG TƯ [32/2023/TT-BYT](https://github.com/user-attachments/files/16156783/Thong.t.-32-2023-TT-BYT.docx)

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **29/07/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
- Script tạo bổ sung sẽ liệu: `UPDATE CURRENT.TOMTATBA`
  'ALTER TABLE current.tomtatba
  ADD COLUMN tsbenh VARCHAR;
COMMENT ON COLUMN current.tomtatba.tsbenh
IS 'Ghi nhận tiền sử bệnh của bệnh nhân.';

ALTER TABLE current.tomtatba
  ADD COLUMN dhlamsang VARCHAR;
COMMENT ON COLUMN current.tomtatba.dhlamsang
IS 'Ghi nhận những dấu hiệu lâm sàng chính.';

ALTER TABLE current.tomtatba
  ADD COLUMN ppdieutri NUMERIC(1,0);
COMMENT ON COLUMN current.tomtatba.ppdieutri
IS 'Ghi nhận phương pháp điều trị nội khoa.
Giá trị:
- 0: Không
- 1: Có';

ALTER TABLE current.tomtatba
  ADD COLUMN ppdieutri_ghichu VARCHAR;
COMMENT ON COLUMN current.tomtatba.ppdieutri_ghichu
IS 'Ghi rõ phương pháp điều trị nếu giá trị cột ppdieutri = 1.';

ALTER TABLE current.tomtatba
  ADD COLUMN pttt NUMERIC(1,0);
COMMENT ON COLUMN current.tomtatba.pttt
IS 'Ghi nhận có phẫu thuật, thủ thuật.
Giá trị:
- 0: Không
- 1: Có';

ALTER TABLE current.tomtatba
  ADD COLUMN pttt_ghichu VARCHAR;
COMMENT ON COLUMN current.tomtatba.pttt_ghichu
IS 'Ghi rõ phương pháp điều trị nếu giá trị cột pttt_ghichu = 1.';'
  
:blue_book: Cập nhật cấu trúc table **tomtatba**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
| 1 | qtbenhly | VARCHAR | Ghi nhận tóm tắt quá trình bệnh lý và diễn biến lâm sàng.|
|2|tsbenh|VARCHAR| Ghi nhận tiền sử bệnh của bệnh nhân.|
|3|dhlamsang|VARCHAR| Ghi nhận những dấu hiệu lâm sàng chính.|
|4|ppdieutri|NUMERIC(1,0)| Ghi nhận phương pháp điều trị nội khoa. <br/>Giá trị:<br/> - 0: Không</br> - 1: Có |
|5|ppdieutri_ghichu|VARCHAR| Ghi rõ phương pháp điều trị nếu giá trị cột ppdieutri = 1. |
|6|pttt|NUMERIC(1,0)| Ghi nhận có phẫu thuật, thủ thuật. <br/>Giá trị:<br/> - 0: Không</br> - 1: Có |
|7|pttt_ghichu|VARCHAR| Ghi rõ phương pháp phẫu thuật nếu giá trị cột pttt = 1. |
