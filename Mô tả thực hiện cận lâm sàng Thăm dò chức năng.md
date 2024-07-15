<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ THỰC CẬN LÂM SÀNG THĂM DÒ CHỨC NĂNG `(KHO = 'CN')`
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **09/07/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - Thêm loại CLS bổ sung mẫu kết quả Thăm do chức năng.  #309](https://github.com/dh-hos/To_Lap_Trinh/issues/309)
- Áp dụng cho tất cả các cận lâm sàng có `dmcls.kho = 'CN'`.
###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Quy trình áp dụng:** 

:blue_book: Cập nhật cấu trúc, bổ sung các cột vào table `current.pskhamha`: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|diadiemthuchien|VARCHAR(500)|Địa điểm thực hiện|
|2|hentraketqua|TIMESTAMP|Thời gian hẹn trả kết quả|
|3|hinhthuctraketqua|NUMERIC(1,0)|Hình thức trả kết quả.<br/>- 1: Trực tiếp.<br/>- 2: Trực tuyến.|
|4|traketquatructieptai|VARCHAR(500)|Nơi trả kết quả trực tiếp. Áp dụng khi `hinhthuctraketqua = 1`.|

:blue_book: DHG.Hospital Admin: 
- Tại form `[Danh mục Loại cận lâm sàng]`: Đối với cận lâm sàng có `dmcls.kho = 'CN'`. 
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/ac0a9d8e-3bb2-4474-a2bc-20dc060328ad)

⇒ **[I]** Giữ nguyên các loại cận lâm sàng đang có **(không được XÓA)**, bao gồm:
|Mã loại cận lâm sàng|Tên loại cận lâm sàng|
|:-------:|-------|
|LHN|Lưu huyết não|
|SLSS|Sàng lọc sơ sinh|
|TL|Trắc nghiệm tâm lý|
|DT|Điện tim|
|DN|Điện não|
|CN|Chức năng hô hấp|

⇒ **[II]** Cho phép **thêm/sửa/xóa** các loại cận lâm sàng mới thuộc `kho = 'CN'` (ngoài các loại cận lâm sàng ở **[I]**).

:blue_book: DHG.Hospital Diagnose:
- Ngoài các form thực hiện và các mẫu kết quả cận lâm sàng hiện có đối với **[I]**, bổ sung thêm form cho phép thực hiện các cận lâm sàng thuộc loại cận lâm sàng ở mục **[II]** và **`dmcls.thuchien = 1`** [^2024-07-15] theo mẫu `MS: CD-01` *(xem ảnh)*, `Phụ lục 1` - [Công văn số 65/KCB-QLCL&CĐT của Cục quản lý khám, chữa bệnh, Bộ Y tế ban hành ngày 12/01/2024](https://kcb.vn/cong-van/trien-khai-mau-benh-an-mau-giay-phieu-y-theo-thong-tu-so-32-2023-tt-byt-va-tiep-tuc-nghien-cuu-thu-nghiem-thi-diem-mot-s.html). Thiết kế form trả kết quả bao gồm:
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/b9668bb2-4d18-4bae-857a-3972caaffd92)
- Các thông tin cần ghi nhận khi thực hiện cận lâm sàng thuộc các loại này gồm:

| STT | THÔNG TIN GHI NHẬN KHI THỰC HIỆN | DỮ LIỆU LƯU TRỮ TƯƠNG ỨNG |
|:-------:|-------|-------|
|1|Địa điểm thực hiện|pskhamha.diadiemthuchien|
|2|Người thực hiện|pskhamha.taikhoan_traketqua|
|3|Thời gian thực hiện|pskhamha.ngaytraketqua|
|4|Thời gian hẹn trả kết quả|pskhamha.hentraketqua|
|5|Hình thức trả trả kết quả (1: trực tiếp; 2: Trực tuyến)|pskhamha.hinhthuctraketqua|
|6|Trực tiếp tại (áp dụng khi `hinhthuctraketqua = 1`)|pskhamha.traketquatructieptai|
|7|Mô tả|pskhamha.mota_text|
|8|Kết luận|pskhamha.ketluan_plaintext|
|9|Diễn giải/xem xét/cảnh báo/khuyến nghị|pskhamha.loidan|
- Thiết kế mẫu kết quả (tự thiết kế) theo mẫu `MS: CD-01`, `Phụ lục 1` - [Công văn số 65/KCB-QLCL&CĐT của Cục quản lý khám, chữa bệnh, Bộ Y tế ban hành ngày 12/01/2024](https://kcb.vn/cong-van/trien-khai-mau-benh-an-mau-giay-phieu-y-theo-thong-tu-so-32-2023-tt-byt-va-tiep-tuc-nghien-cuu-thu-nghiem-thi-diem-mot-s.html).
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/58ffae93-96b9-4d08-83d2-bc86e1086f23)

[^2024-07-15]: Thay đổi ngày 15/07/2024: Bổ sung điều kiện thực hiện CLS thăm dò chức năng đối với `loại CLS [II]` phải có `dmcls.thuchien = 1`.
