<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CÁCH GHI NHẬN GIÁ TRỊ CỘT XML3.MA_BENH (cột 26, bảng 3 - XML4210)
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **01/07/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: Biên bản họp `NAS: \DuLieuCongTy\Van Ban Ban Hanh\Bien ban hop\BienBanHop_20240627_Nhom.pdf`.
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/6a6f56f8-f21a-48b2-8afb-2238ce21279b)

###### :eight_spoked_asterisk: Xử lý yêu cầu: Các phân hệ xuất dữ liệu theo 4210
:blue_book: Cập nhật cấu trúc: Bổ sung tham số
| STT | TÊN THAM SỐ | KIỂU | DIỄN GIẢI |
|:-------:|-------|:-------:|-------|
|1|xml4210.xml3.ma_benh|Số (tham số chung)|Cách thể hiện mã bệnh tại cột số 26, bảng 3 XML4210.<br/>Giá trị:<br/>- 0: Ghép [Mã bệnh chính (theo ICD 10)] và [Mã bệnh phụ (theo ICD 10, nếu có).]<br/>- 1: Mã bệnh y học cổ truyền.<br/>- 2: Ghép [Mã bệnh chính (theo ICD 10)], [Mã bệnh phụ (theo ICD 10, nếu có) và [Mã bệnh y học cổ truyền (nếu có)].]|

:blue_book: Các phân hệ xuất dữ liệu XML4210: Ghi nhận giá trị cột `xml3.ma_benh` như sau:
| Giá trị tham số<br/>`xml4210.xml3.ma_benh` | Cách ghi nhận<br/>`xml3.ma_benh` |
|:-------:|-------|
|`0`|`chidinhcls.maicd` + `";"` + `chidinhcls.maicdp`|
|`1`|`chidinhcls.mayhct`|
|`2`|`chidinhcls.maicd` + `";"` + `chidinhcls.maicdp` + `";"` + `chidinhcls.mayhct`|
