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

|TT|Tên cột|Diễn giải|Ghi chú[^2024-10-15-01]|Kiểu dữ liệu|Bắt buộc|Index|
|:----:|-------|-------|-------|:-------:|:-------:|:----:|
|1|ma_lk|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh).|`=bang1.ma_lk`|VARCHAR(100)||X|
|2|loaihosokcb|Loại hồ sơ KCB. Giá trị:<br/>- NGOAI_TRU: khám bệnh ngoại trú.<br/>- BA_NGOAITRU: bệnh án ngoại trú<br/>- BA_NOI_TRU: bệnh án nội trú||VARCHAR(50)|X|X|
|3|mabn|Mã bệnh nhân||VARCHAR(20)|X|X|
|4|makb|Mã khám bệnh||VARCHAR(20)|X|X|
|5|maba|Mã bệnh án||VARCHAR(20)|||
|6|mabattconbh2|Mã bệnh án con, thẻ BHYT 2||VARCHAR(20)|||
|7|daguibhxh|Đã gửi BHXH (0:Chưa gửi, >0: Số lần gửi)||NUMERIC(10,0)|||
|8|ngay_ttoan|Ngày thanh toán||TIMESTAMP|||
|9|thang_qt|Tháng thanh toán||VARCHAR(2)|||
|10|nam_qt|Năm thanh toán||VARCHAR(4)|||
|11|checkin_cls|Ghi nhận trạng thái đã gửi thông tin xml check-in có công khám lên cổng giám định BHYT. Giá trị:<br/>- 0 (hoặc null): chưa gửi xml check-in công khám phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.<br/>- 1: đã gửi xml check-in công khám phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.||NUMERIC(1,0)|||
|12|checkin_thuoc|Ghi nhận trạng thái đã gửi thông tin xml check-in có thuốc lên cổng giám định BHYT. Giá trị:<br/>- 0 (hoặc null): chưa gửi xml check-in thuốc phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.<br/>- 1: đã gửi xml check-in thuốc phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.||NUMERIC(1,0)|||
|13|checkin_vtyt|Ghi nhận trạng thái đã gửi thông tin xml check-in có VTYT lên cổng giám định BHYT. Giá trị:<br/>- 0 (hoặc null): chưa gửi xml check-in VTYT phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.<br/>- 1: đã gửi xml check-in VTYT phát sinh đầu tiên của người bệnh lên cổng giám định BHYT.||NUMERIC(1,0)|||
|14[^2024-07-01]|macls|Ghi nhận thông tin mã cận lâm sàng check in||varchar(20)|||
|15|mahh_thuoc|Ghi nhận thông tin mã hàng hóa check in thuốc ||varchar(20)|||
|16|mahh_vtyt|Ghi nhận thông tin mã hàng hóa check vtyt||varchar(20)|||
|17[^2024-08-18]|ngay_checkin|Ghi nhận ngày thực hiện check in||TIMESTAMP WITHOUT TIME ZONE|||

[^2024-10-15-01]: Thay đổi ngày 15/10/2024: Bổ sung mô tả giá trị các cột `ma_lk`. Chi tiết theo yêu cầu [#684](https://github.com/dh-hos/To_Lap_Trinh/issues/684).
[^2024-07-01]: Thay đổi ngày 01/07/2024: Thêm cấu trúc ghi nhận macls,mahh khi thực hiện checkin.
[^2024-08-18]: Thay đổi ngày 18/08/2024: Thêm cấu trúc ghi nhận ngày thực hiện checkin.
