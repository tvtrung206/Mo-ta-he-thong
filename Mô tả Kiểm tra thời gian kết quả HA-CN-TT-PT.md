<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ KIỂM TRA THỜI GIAN THỰC HIỆN Y LỆNH/TRẢ KẾT QUẢ ĐỐI VỚI CHẨN ĐOÁN HÌNH ẢNH/THĂM DÒ CHỨC NĂNG VÀ THỜI GIAN BẮT ĐẦU/KẾT THÚC ĐỐI VỚI THỦ THUẬT/PHẪU THUẬT [^2024-08-02-01]
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **30/07/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Mô tả - Thêm chức năng cảnh báo, chặn theo thời gian thực hiện CLS (Chỉ định -> Bắt đầu thực hiện -> Kết quả) (#527) ⏳Dự kiến : 2024-07-31  #528](https://github.com/dh-hos/To_Lap_Trinh/issues/528)
- **Lưu ý: Chỉ áp dụng đối với người bệnh đối tượng BHYT thực hiện cận lâm sàng có kho thuộc ('HA', 'CN','TT','PT').** [^2024-07-30-01]

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Quy trình áp dụng:** 

:blue_book: Cập nhật cấu trúc cho **tham số**:<br/>
1️⃣ Điều chỉnh tham số **`ha.sophuttoithieu`**:
+ Thay đổi diễn giải: Số phút tối thiểu kể từ `[thời điểm chỉ dịnh cận lâm sàng]` đến `[thời điểm thực hiện y lệnh]`. *Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.*
+ Phạm vi áp dụng: Từ thời điểm chỉ định đến thời điểm thực hiện y lệnh.
 
2️⃣ Thêm mới các tham số:
| STT | TÊN THAM SỐ | KIỂU |PHÂN HỆ| DIỄN GIẢI |
|:-------:|-------|:-------:|-------|-------|
|1|ha.sophuttraketqua|Số|Diagnose|Số phút tối thiểu kể từ `[thời điểm thực hiện y lệnh]` đến `[thời điểm trả kết quả]`. Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.|
|2|ha.canhbaovuotthoigian [^2024-07-30-02]|Số|Diagnose|Cảnh báo khi đã vượt quá [Thời gian thực hiện y lệnh]/[Thời gian trả kết quả]. Giá trị:<br/>- 0: Cảnh báo và `KHÔNG` cho phép lưu kết quả.<br/>- 1: Cảnh báo và `CHO PHÉP` lưu kết quả.|

🆕 Cập nhật thay đổi thông tin tham số: [^2024-08-02-02]<br/>
➡️Tham số `ha.sophuttoithieu`:<br/>
⇒ Phạm vi phân hệ: `Thông số chung`.<br/>
⇒ Thay đổi diễn giải: Số phút tối thiểu kể từ `[thời điểm chỉ dịnh cận lâm sàng]` đến `[thời điểm thực hiện y lệnh]/[thời điểm bắt đầu]` áp dụng đối với thực hiện `Chẩn đoán hình ảnh/Thăm dò chức năng/Thủ thuật/Phẫu thuật`. *Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.*<br/><br/>
➡️Tham số `ha.sophuttraketqua`:<br/>
⇒ Phạm vi phân hệ: `Thông số chung`.<br/>
⇒ Thay đổi diễn giải: Số phút tối thiểu kể từ `[thời điểm thực hiện y lệnh]/[thời điểm bắt đầu]` đến `[thời điểm trả kết quả]/[thời điểm kết thúc]` áp dụng đối với thực hiện `Chẩn đoán hình ảnh/Thăm dò chức năng/Thủ thuật/Phẫu thuật`. *Lưu ý: giá trị 0 hoặc rỗng là không giới hạn.*<br/><br/>
➡️Tham số `ha.canhbaovuotthoigian`:<br/>
⇒ Phạm vi phân hệ: `Thông số chung`.<br/>
⇒ Thay đổi diễn giải: Cảnh báo khi đã vượt quá `[Thời gian thực hiện y lệnh]/[Thời gian trả kết quả]/[Thời gian bắt đầu]/[Thời gian kết thúc]` khi thực hiện `Chẩn đoán hình ảnh/Thăm dò chức năng/Thủ thuật/Phẫu thuật`. Giá trị:<br/>- 0: Cảnh báo và `KHÔNG` cho phép lưu kết quả.<br/>- 1: Cảnh báo và `CHO PHÉP` lưu kết quả.

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

🆕 Cập nhật thay đổi: [^2024-08-02-03] 
- Thay đổi các thông tin form **`[Danh mục loại cận lâm sàng]`**:<br/>
1️⃣ Điều chỉnh nhãn `[Số phút thực hiện y lệnh]` thành **`[Số phút Thực hiện y lệnh/Bắt đầu]`**.<br/>
2️⃣ Điều chỉnh nhãn `[Số phút trả kết quả]` thành **`[Số phút Trả kết quả/Kết thúc]`**.<br/>
<p align="center"><img src="https://github.com/user-attachments/assets/8134f793-d5f3-4d26-8621-d7ec457f745f" width="70%"></p>

- Thay đổi các thông tin form **`[Danh mục cận lâm sàng] ⇒ Tab [Cấu hình thơi gian thực hiện CĐHA,CN]`**: Điều chỉnh tiêu đề tab thành **`[Cấu hình thơi gian thực hiện CĐHA,CN,TT,PT]`**<br/>
1️⃣ Điều chỉnh nhãn `[Số phút thực hiện y lệnh]` thành **`[Số phút Thực hiện y lệnh/Bắt đầu]`**.<br/>
2️⃣ Điều chỉnh nhãn `[Số phút trả kết quả]` thành **`[Số phút Trả kết quả/Kết thúc]`**.<br/>
<p align="center"><img src="https://github.com/user-attachments/assets/ecae27f3-a908-4fe3-a9c9-8d26a2e212d5" width="70%"></p>

:blue_book: Module Diagnose: Tại các form thực hiện trả kết quả, thực hiện kiểm tra `[thời gian thực hiện y lệnh]` và `[thời gian trả kết quả]` (trước khi lưu) tuần tự như sau:
<p align="center"><img src="https://github.com/user-attachments/assets/507047f8-c30b-4af6-9b96-ad853b21d683" width="70%"></p>

1️⃣ Kiểm tra thời gian thực hiện y lệnh:
- `sophutthuchienylenh` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmcls.sophutthuchienylenh ⇒  dmloaicls.sophutthuchienylenh ⇒ [tham số ha.sophuttoithieu]`). 
- Nếu `sophutthuchienylenh > 0`, kiểm tra **`[chidinhcls.ngaykcb + sophutthuchienylenh] > [Ngày thực hiện y lệnh đã chọn trên form]`**, kiểm tra giá trị tham số `ha.canhbaovuotthoigian`: [^2024-07-30-03]<br/>⇒ `= 0`:  ⚠️ Cảnh báo `(có hiển thị số phút được phép thực hiện y lệnh)` và 🚫KHÔNG thực hiện lưu kết quả.<br/>⇒ `= 1`:  ❓ Hiển thị hộp thoại xác nhận `(có hiển thị số phút được phép thực hiện y lệnh)` và ✅CHO PHÉP thực hiện lưu kết quả.

2️⃣ Kiểm tra thời gian trả kết quả:
- `sophuttraketqua` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmcls.sophuttraketqua ⇒  dmloaicls.sophuttraketqua ⇒ [tham số ha.sophuttraketqua]`).
- Nếu `sophuttraketqua > 0`, kiểm tra **`[Ngày thực hiện y lệnh đã chọn trên form] + sophuttraketqua > [Ngày kết quả đã chọn trên form]`**, kiểm tra giá trị tham số `ha.canhbaovuotthoigian`: [^2024-07-30-04]<br/>⇒ `= 0`:  ⚠️ Cảnh báo `(có hiển thị số phút được phép trả kết quả)` và 🚫KHÔNG thực hiện lưu kết quả.<br/>⇒ `= 1`:  ❓ Hiển thị hộp thoại xác nhận `(có hiển thị số phút được phép trả kết quả)` và ✅CHO PHÉP thực hiện lưu kết quả.

🔄 **Bổ sung quy trình kiểm tra** `[Số phút tối thiểu để trả kết quả từ lần trả kết quả gần nhất của một tài khoản]`: [^2024-08-02-05]<br/>
- Tham số `ha.sophut_thuchien_toithieu`.<br/>
- Thay đổi kiểu giá trị từ: `số ⇒ chuỗi`.<br/>
- Thay đổi diễn giải: `Số phút tối thiểu để trả kết quả từ lần trả kết quả gần nhất của người đọc kết quả theo loại cận lâm sàng. Giá trị được ghi nhận theo quy cách '<maloai>:<số phút tối thiểu>', nếu nhiều loại thì cách nhau bởi ký tự '|'. Ví dụ giá trị: 'SA:5|NS1:5|XQ:5|DT:5' tương ứng siêu âm, Xquang và điện tim cấu hình tối thiểu 5 phút.`
- Quy trình áp dụng:<br/>
⇒ Lấy giá trị tham số `ha.sophut_thuchien_toithieu`. Tách giá trị theo ký tự `'|'`, `sophuttoithieu = (tách maloai của cận lâm sàng đang thực hiện và lấy số phút tương ứng)`.  Ví dụ: `SA:5` lấy số phút tối thiểu của siêu âm đang thực hiện:`sophuttoithieu = 5`. **Lưu ý: Chỉ thực hiện kiểm tra khi `sophuttoithieu > 0`**.<br/>
⇒ Lấy thông tin thời gian đã trả kết quả mới nhất trước đó của bác sĩ đọc kết quả (lưu trữ tại table `pskhamha.ngaycd` lấy theo điều kiện `pskhamha.manv`, tương ứng với bác sĩ đang đọc kết quả) `(nếu có)` `[*]`.<br/>
⇒ Nếu `pskhamha.ngaycd` tại `[*]` tồn tại: Kiểm tra  **`pskhamha.ngaycd + sophuttoithieu > [Ngày kết quả đã chọn trên form]`** ⇒ ⚠️ Cảnh báo *(có hiển thị thông tin thời gian đã trả kết quả gần nhất)* và 🚫KHÔNG thực hiện lưu kết quả.

:blue_book: Module Prescription/Treatment [^2024-08-02-04]: Tại các form thực hiện trả kết quả Thủ thuật/Phẫu thuật, thực hiện kiểm tra `[Thời gian bắt đầu]` và `[Thời gian kết thúc]` thủ thuật/phẫu thuật (trước khi lưu) tuần tự như sau:
<p align="center"><img src="https://github.com/user-attachments/assets/60e90fac-868b-497a-a42d-c08706b84a10" width="70%"></p>

1️⃣ Kiểm tra thời gian `[Bắt đầu]`:
- `sophutbatdau` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmcls.sophutthuchienylenh ⇒  dmloaicls.sophutthuchienylenh ⇒ [tham số ha.sophuttoithieu]`). 
- Nếu `sophutbatdau > 0`, kiểm tra **`[chidinhcls.ngaykcb + sophutbatdau] > [Thời gian bắt đầu đã chọn trên form]`**, kiểm tra giá trị tham số `ha.canhbaovuotthoigian`:<br/>⇒ `= 0`:  ⚠️ Cảnh báo `(có hiển thị số phút bắt đầu được phép)` và 🚫KHÔNG thực hiện lưu kết quả.<br/>⇒ `= 1`:  ❓ Hiển thị hộp thoại xác nhận `(có hiển thị số phút bắt đầu được phép)` và ✅CHO PHÉP thực hiện lưu kết quả *(nếu đồng ý)*. 

2️⃣ Kiểm tra thời gian `[Kết thúc]`:
- `sophutketthuc` = (ưu tiên lấy tuần tự nếu khác 0 theo trình tự: `dmcls.sophuttraketqua ⇒  dmloaicls.sophuttraketqua ⇒ [tham số ha.sophuttraketqua]`).
- Nếu `sophutketthuc > 0`, kiểm tra **`[Thời gian bắt đầu đã chọn trên form] + sophutketthuc > [Thời gian kết thúc đã chọn trên form]`**, kiểm tra giá trị tham số `ha.canhbaovuotthoigian`: <br/>⇒ `= 0`:  ⚠️ Cảnh báo `(có hiển thị số phút kết thúc được phép)` và 🚫KHÔNG thực hiện lưu kết quả.<br/>⇒ `= 1`:  ❓ Hiển thị hộp thoại xác nhận `(có hiển thị số phút kết thúc được phép)` và ✅CHO PHÉP thực hiện lưu kết quả *(nếu đồng ý)*.

[^2024-08-02-05]: Thay đổi ngày 02/08/2024: Thay đổi kiểu từ số sang chuỗi tham số `ha.sophut_thuchien_toithieu`, cấu hình số phút tối thiểu để trả kết quả từ lần trả kết quả gần nhất của người đọc kết quả theo loại cận lâm sàng đối với module `Diagnose`.
[^2024-08-02-04]: Thay đổi ngày 02/08/2024: Bổ sung chức năng kiểm soát thời gian bắt đầu và thời gian kết thúc khi thực hiện Thủ thuật/Phẫu thuật tại module `Prescription/Treatment`.
[^2024-08-02-03]: Thay đổi ngày 02/08/2024: Thay đổi nhãn và tiêu đề tại form `[Danh mục Loại cận lâm sàng]` và `[Danh mục Cận lâm sàng]` module `Admin`.
[^2024-08-02-02]: Thay đổi ngày 02/08/2024: Thay đổi phạm vi và diễn giải các tham số: `ha.sophuttoithieu, ha.sophuttraketqua, ha.canhbaovuotthoigian`.
[^2024-08-02-01]: Thay đổi ngày 02/08/2024: Bổ sung mô tả áp dụng thêm đối với Thủ thuật/Phẫu thuật.
[^2024-07-30-04]: Thay đổi ngày 30/07/2024: Thay đổi cảnh báo `[Thời gian trả kết quả]` theo tham số `ha.canhbaovuotthoigian`.
[^2024-07-30-03]: Thay đổi ngày 30/07/2024: Thay đổi cảnh báo `[Thời gian thực hiện y lệnh]` theo tham số `ha.canhbaovuotthoigian`.
[^2024-07-30-02]: Thay đổi ngày 30/07/2024: Bổ sung tham số `ha.canhbaovuotthoigian` cảnh báo khi đã vượt quá `[Thời gian thực hiện y lệnh]/[Thời gian trả kết quả]`.
[^2024-07-30-01]: Thay đổi ngày 30/07/2024: Bổ sung điều kiện áp dụng đối với người bệnh BHYT.
