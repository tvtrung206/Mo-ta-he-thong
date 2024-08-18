<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.psxml: Bảng lưu thông tin chung, ghi nhận thông tin sau khi dữ liệu XML đã được xuất (đã được lưu trữ từ bảng 1 đến bảng 15).**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Ngày cập nhật: **11/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)||Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh).|X|Như 4210|
|2|loaihosokcb|VARCHAR(50)|X|Loại hồ sơ KCB. Giá trị:<br/>- NGOAI_TRU: khám bệnh ngoại trú.<br/>- BA_NGOAITRU: bệnh án ngoại trú<br/>- BA_NOI_TRU: bệnh án nội trú|X||
|3|mabn|VARCHAR(20)|X|Mã bệnh nhân|X||
|4|makb|VARCHAR(20)|X|Mã khám bệnh|X||
|5|maba|VARCHAR(20)||Mã bệnh án|||
|6|mabattconbh2|VARCHAR(20)||Mã bệnh án con, thẻ BHYT 2|||
|7|daguibhxh|NUMERIC(10,0)||Đã gửi BHXH (0:Chưa gửi, >0: Số lần gửi)|||
|8|ngay_ttoan|TIMESTAMP||Ngày thanh toán|||
|9|thang_qt|VARCHAR(2)||Tháng thanh toán|||
|10|nam_qt|VARCHAR(4)||Năm thanh toán|||
|11|checkin_cls|NUMERIC(1,0)||Ghi nhận trạng thái đã gửi thông tin xml check-in có công khám lên cổng giám định BHYT. Giá trị:<br/>- 0 (hoặc null): chưa gửi xml check-in công khám phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.<br/>- 1: đã gửi xml check-in công khám phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.|||
|12|checkin_thuoc|NUMERIC(1,0)||Ghi nhận trạng thái đã gửi thông tin xml check-in có thuốc lên cổng giám định BHYT. Giá trị:<br/>- 0 (hoặc null): chưa gửi xml check-in thuốc phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.<br/>- 1: đã gửi xml check-in thuốc phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.|||
|13|checkin_vtyt|NUMERIC(1,0)||Ghi nhận trạng thái đã gửi thông tin xml check-in có VTYT lên cổng giám định BHYT. Giá trị:<br/>- 0 (hoặc null): chưa gửi xml check-in VTYT phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.<br/>- 1: đã gửi xml check-in VTYT phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.|||
|14[^2024-07-01]|macls|varchar(20)||Ghi nhận thông tin mã cận lâm sàng check in|||
|15|mahh_thuoc|varchar(20)||Ghi nhận thông tin mã hàng hóa check in thuốc |||
|16|mahh_vtyt|varchar(20)||Ghi nhận thông tin mã hàng hóa check vtyt|||
|17[^2024-08-18]|ngay_checkin|TIMESTAMP WITHOUT TIME ZONE||Ghi nhận ngày thực hiện check in|||

[^2024-07-01]: Thay đổi ngày 01/07/2024: Thêm cấu trúc ghi nhận macls,mahh khi thực hiện checkin.
[^2024-08-18]: Thay đổi ngày 18/08/2024: Thêm cấu trúc ghi nhận ngày thực hiện checkin.