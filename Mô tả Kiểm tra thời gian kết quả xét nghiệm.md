<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ KIỂM TRA THỜI GIAN THỰC HIỆN Y LỆNH (LẤY MẪU)/TRẢ KẾT QUẢ ĐỐI VỚI XÉT NGHIỆM
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **24/10/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - Bổ sung tham số bắt lại thời gian lấy mẫu đến có kết quả của XN  #710](https://github.com/dh-hos/To_Lap_Trinh/issues/710)
- **Lưu ý: Chỉ áp dụng đối với người bệnh đối tượng BHYT thực hiện cận lâm sàng có kho thuộc ('XN').**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Quy trình áp dụng:** 

:blue_book: Thêm mới các tham số:
| STT | TÊN THAM SỐ | KIỂU |PHÂN HỆ| DIỄN GIẢI |
|:-------:|-------|:-------:|-------|-------|
|1|xn.sophuttoithieu|Số|Laboratory|Số phút tối thiểu kể từ `[thời điểm chỉ định cận lâm sàng]` đến `[thời điểm thực hiện y lệnh (lấy mẫu)]`. *Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.*|
|2|xn.sophuttraketqua|Số|Laboratory|Số phút tối thiểu kể từ `[thời điểm thực hiện y lệnh (lấy mẫu)]` đến `[thời điểm trả kết quả]`. *Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.*|
|3|xn.canhbaovuotthoigian|Số|Laboratory|Cảnh báo khi đã vượt quá `[Thời gian thực hiện y lệnh (lẫy mẫu)]/[Thời gian trả kết quả]`. Giá trị:<br/>- 0: Cảnh báo và `KHÔNG` cho phép lưu kết quả.<br/>- 1: Cảnh báo và `CHO PHÉP` lưu kết quả.|

:blue_book: Cấu hình `[Số phút tối thiểu]/[Số phút trả kết quả]` theo giá trị tham số `xn.sophuttoithieu/xn.sophuttraketqua` và `[Danh mục loại cận lâm sàng]` trên module Admin:
<p align="center"><img src="https://i.imgur.com/VYwqWhZ.png" width="70%"></p>

:blue_book: Module Laboratory:

1️⃣ Kiểm tra thời gian thực hiện y lệnh (lấy mẫu):
- `sophutthuchienylenh` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmloaicls.sophutthuchienylenh ⇒ [tham số xn.sophuttoithieu]`). 
- Nếu `sophutthuchienylenh > 0`, kiểm tra **`[chidinhcls.ngaykcb + sophutthuchienylenh] > [Ngày thực hiện y lệnh (lấy mẫu) đã chọn trên form]`**, kiểm tra giá trị tham số `xn.canhbaovuotthoigian`:<br/>⇒ `= 0`:  ⚠️ Cảnh báo `(có hiển thị số phút được phép thực hiện y lệnh/lấy mẫu)` và 🚫KHÔNG thực hiện lưu kết quả.<br/>⇒ `= 1`:  ❓ Hiển thị hộp thoại xác nhận `(có hiển thị số phút được phép thực hiện y lệnh/lấy mẫu)` và ✅CHO PHÉP thực hiện lưu kết quả.

2️⃣ Kiểm tra thời gian trả kết quả:
- `sophuttraketqua` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmloaicls.sophuttraketqua ⇒ [tham số xn.sophuttraketqua]`).
- Nếu `sophuttraketqua > 0`, kiểm tra **`[Ngày thực hiện y lệnh (lấy mẫu) đã chọn trên form] + sophuttraketqua > [Ngày kết quả đã chọn trên form]`**, kiểm tra giá trị tham số `xn.canhbaovuotthoigian`: <br/>⇒ `= 0`:  ⚠️ Cảnh báo `(có hiển thị số phút được phép trả kết quả)` và 🚫KHÔNG thực hiện lưu kết quả.<br/>⇒ `= 1`:  ❓ Hiển thị hộp thoại xác nhận `(có hiển thị số phút được phép trả kết quả)` và ✅CHO PHÉP thực hiện lưu kết quả.
