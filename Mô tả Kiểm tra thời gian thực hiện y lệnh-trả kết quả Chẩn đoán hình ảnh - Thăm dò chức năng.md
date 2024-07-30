<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ KIỂM TRA THỜI GIAN THỰC HIỆN Y LỆNH/TRẢ KẾT QUẢ ĐỐI VỚI CHẨN ĐOÁN HÌNH ẢNH/THĂM DÒ CHỨC NĂNG
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **30/07/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Mô tả - Thêm chức năng cảnh báo, chặn theo thời gian thực hiện CLS (Chỉ định -> Bắt đầu thực hiện -> Kết quả) (#527) ⏳Dự kiến : 2024-07-31  #528](https://github.com/dh-hos/To_Lap_Trinh/issues/528)
- **Lưu ý: Chỉ áp dụng đối với cận lâm sàng có kho thuộc HA và CN.**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Quy trình áp dụng:** 

:blue_book: Cập nhật cấu trúc cho **tham số**:<br/>
1️⃣ Điều chỉnh tham số **`ha.sophuttoithieu`**:
+ Thay đổi diễn giải: Số phút tối thiểu kể từ `[thời điểm chỉ dịnh cận lâm sàng]` đến `[thời điểm thực hiện y lệnh]`. *Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.*
+ Phạm vi áp dụng: Từ thời điểm chỉ định đến thời điểm thực hiện y lệnh.
 
2️⃣ Thêm mới các tham số:
| STT | TÊN THAM SỐ | KIỂU |PHÂN HỆ| DIỄN GIẢI |
|:-------:|-------|:-------:|-------|-------|
|1|ha.sophuttraketqua|Số|Tham số chung|Số phút tối thiểu kể từ `[thời điểm thực hiện y lệnh]` đến `[thời điểm trả kết quả]`. Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.|

:blue_book: Cập nhật cấu trúc table **`current.dmloaicls`**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU |DIỄN GIẢI|
|:-------:|-------|:-------:|-------|
|1|sophutthuchienylenh|NUMERIC(5,0)|Số phút tối thiểu kể từ `[thời điểm chỉ định]` đến `[thời điểm thực hiện y lệnh]` cho cận lâm sàng thuộc loại này.|
|2|sophuttraketqua|NUMERIC(5,0)|Số phút tối thiểu kể từ [thời điểm thực hiện y lệnh] đến [thời điểm trả kết quả] cho cận lâm sàng thuộc loại này.|

:blue_book: Cập nhật cấu trúc table **`current.dmcls`**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU |DIỄN GIẢI|
|:-------:|-------|:-------:|-------|
|1|sophutthuchienylenh|NUMERIC(5,0)|Số phút tối thiểu kể từ `[thời điểm chỉ định]` đến `[thời điểm thực hiện y lệnh]` cho cận lâm sàng này.|
|2|sophuttraketqua|NUMERIC(5,0)|Số phút tối thiểu kể từ [thời điểm thực hiện y lệnh] đến [thời điểm trả kết quả] cho cận lâm sàng này.|

:blue_book: Module Admin:
- Tại form **[Danh mục loại cận lâm sàng]**: bổ sung thêm cột trên lưới và Control có: <br/>
➡️ Nhãn `[Số phút thực hiện y lệnh]`, tương ứng với dữ liệu cột `dmloaicls.sophutthuchienylenh`.<br/>
➡️ Nhãn `[Số phút trả kết quả]`, tương ứng với dữ liệu cột `dmloaicls.sophuttraketqua`.
- Tại form **[Danh mục cận lâm sàng]**: bổ sung thêm *(có thể tạo TAB mới để cập nhật các thông tin này)* cột trên lưới và Control có: <br/>
➡️ Nhãn `[Số phút thực hiện y lệnh]`, tương ứng với dữ liệu cột `dmcls.sophutthuchienylenh`.<br/>
➡️ Nhãn `[Số phút trả kết quả]`, tương ứng với dữ liệu cột `dmcls.sophuttraketqua`.
 
:blue_book: Module Diagnose: Tại các form thực hiện trả kết quả, thực hiện kiểm tra `[thời gian thực hiện y lệnh]` và `[thời gian trả kết quả]` (trước khi lưu) tuần tự như sau:<br/>
1️⃣ Kiểm tra thời gian thực hiện y lệnh:
- `sophutthuchienylenh` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmcls.sophutthuchienylenh ⇒  dmloaicls.sophutthuchienylenh ⇒ [tham số ha.sophuttoithieu]`). 
- Nếu `sophutthuchienylenh > 0`, kiểm tra **`[chidinhcls.ngaykcb + sophutthuchienylenh] > [Ngày thực hiện y lệnh đã chọn trên form]`** ⇒ 🚫KHÔNG thực hiện lưu kết quả.

2️⃣ Kiểm tra thời gian trả kết quả:
- `sophuttraketqua` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmcls.sophuttraketqua ⇒  dmloaicls.sophuttraketqua ⇒ [tham số ha.sophuttraketqua]`).
- Nếu `sophuttraketqua> 0`, kiểm tra **`[Ngày thực hiện y lệnh đã chọn trên form] + sophuttraketqua > [Ngày kết quả đã chọn trên form]`** ⇒ 🚫KHÔNG thực hiện lưu kết quả.

☑️ Bổ sung quy trình kiểm tra `[Số phút tối thiểu để trả kết quả từ lần trả kết quả gần nhất của một tài khoản]` *(đã áp dụng)*:
- Tham số `ha.sophut_thuchien_toithieu`.
- Diễn giải: `Số phút tối thiểu để trả kết quả từ lần trả kết quả gần nhất của một tài khoản (giá trị rỗng hoặc 0: không áp dụng).`
- Quy trình áp dụng *(khi giá trị tham số `ha.sophut_thuchien_toithieu > 0`)*:<br/>
⇒ Lấy thông tin thời gian đã trả kết quả mới nhất trước đó của bác sĩ đọc kết quả (lưu trữ tại table `pskhamha.ngaycd` lấy theo điều kiện `pskhamha.manv`, tương ứng với bác sĩ đang đọc kết quả) `(nếu có)` `[1]`.<br/>
⇒ Nếu `pskhamha.ngaycd` tại `[1]` tồn tại: Kiểm tra  **`pskhamha.ngaycd + ha.sophut_thuchien_toithieu > [Ngày kết quả đã chọn trên form]`** ⇒ 🚫KHÔNG thực hiện lưu kết quả.
