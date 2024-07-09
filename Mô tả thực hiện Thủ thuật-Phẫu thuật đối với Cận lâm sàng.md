<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ THỰC HIỆN THỦ THUẬT/PHẪU THUẬT ĐỐI VỚI CẬN LÂM SÀNG
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **08/07/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - PK Medic Miền Đông: Không cấu hình loại PT trên danh mục CLS vẫn lập được phiếu PT-TT  #435](https://github.com/dh-hos/To_Lap_Trinh/issues/435)
- **Lưu ý: Chỉ áp dụng đối với cận lâm sàng có kho thuộc TT hoặc PT.**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Quy trình áp dụng:** 

:blue_book: Cập nhật cấu trúc, bổ sung các tham số. [^2024-07-09-01]
| STT | TÊN THAM SỐ | KIỂU |PHÂN HỆ| DIỄN GIẢI |
|:-------:|-------|:-------:|-------|-------|
|1|phanloaipt.thuchien|Số|Tham số chung|Cho phép thực hiện Phẫu thuật/Thủ thuật (áp dụng đối với kho TT hoặc PT) mà không cần phân loại PT.<br/>Giá trị:<br/>- `0 (hoặc null)`: Chỉ thực hiện TT/PT đối với các cận lâm sàng có cấu hình `[Phân loại PT]`.<br/>- `1`: Cho phép thực hiện TT/PT bao gồm các TT/PT có hoặc không có cấu hình `[Phân loại PT]`.|
|2|phanloaipt.baocao|Số|Tham số chung|Thể hiện Phẫu thuật/Thủ thuật lên `Sổ Thủ thuật/Phẫu thuật`.<br/>Giá trị:<br/>- `0 (hoặc null)`: Chỉ thể hiện TT/PT đối với các cận lâm sàng có cấu hình `[Phân loại PT]`.<br/>- `1`: Thể hiện TT/PT lên sổ TT/PT, bao gồm các TT/PT có hoặc không có cấu hình `[Phân loại PT]`.|
 
:blue_book: Các phân hệ có thực hiện Thủ thuật/Phẫu thuật: `Prescription, Treatment`.  [^2024-07-09-02]
- Tại form thực hiện Phẫu thuật/Thủ thuật: xét giá trị tham số `phanloaipt.thuchien`:<br/>
⇒ 0: Chỉ load và thực hiện các cận lâm sàng TT/PT có cấu hình `[Phân loại PT]`. <br/>
⇒ 1: Load và thực hiện các cận lâm sàng TT/PT có hoặc không có cấu hình `[Phân loại PT]`. 

:blue_book: Các phân hệ có báo cáo Sổ Thủ thuật/Phẫu thuật: `Register/Prescription, Treatment, Reports`.  [^2024-07-09-03]
- Tại Sổ Phẫu thuật/Thủ thuật: xét giá trị tham số `phanloaipt.baocao`:<br/>
⇒ 0: Chỉ thể hiện TT/PT đối với các cận lâm sàng có cấu hình `[Phân loại PT]`. <br/>
⇒ 1: Thể hiện TT/PT lên sổ TT/PT, bao gồm các TT/PT có hoặc không có cấu hình `[Phân loại PT]`. 

[^2024-07-09-01]: Thay đổi ngày 09/07/2024: Giữ nguyên phương thức cập nhật `[Loại PT]` trên `[Danh mục Cận lâm sàng]`. Bổ sung tham số điều phối thực hiện TT/PT cho các trường hợp không phân loại PT.
[^2024-07-09-02]: Thay đổi ngày 09/07/2024: Thay đổi cách thực hiện TT/PT theo tham số `phanloaipt.thuchien`.
[^2024-07-09-03]: Thay đổi ngày 09/07/2024: Bổ sung tham số `phanloaipt.baocao`, điều khiển hiển thị các cận lâm sàng TT/PT lên sổ TT/PT.
