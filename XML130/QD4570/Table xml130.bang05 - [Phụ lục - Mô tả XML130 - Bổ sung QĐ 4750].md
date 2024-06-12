<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang5: Chỉ tiêu chi tiết diễn biến lâm sàng.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Ngày cập nhật: **09/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X|Như 4210|
|2|stt|NUMERIC(10,0)|X|Là số thứ tự tăng từ 1 đến hết trong một lần gửi dữ liệu.||Như 4210|
|3|dien_bien_ls|VARCHAR|X|Ghi diễn biến lâm sàng của người bệnh trong lần khám và/hoặc ghi nội dung chăm sóc của nhân viên y tế.<br/><br/>**Bổ sung hướng dẫn**: Trường hợp người bệnh có được đo các chỉ số sinh tồn khi mô tả diễn biến của người bệnh thì ghi chỉ số sinh tồn theo quy ước như sau: Mạch (M), nhiệt độ (T), huyết áp (HA), nhịp thở (NT), SPO2 (SP), chế độ hộ lý (HL),....<br/>Ví dụ: Mạch 75 lần/phút, nhiệt độ 370C, huyết áp 120/70 mmHg, nhịp thở 18 lần/phút, chế độ hộ lý cấp II được ghi là: “CSST<M75_T37_HA120/70_ NT18_HL2>”.||Ghi nhận theo cột xml5.dien_bien (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|
|4|giai_doan_benh|VARCHAR||Ghi giai đoạn bệnh trong trường hợp người bệnh đã được cơ sở KBCB xác định giai đoạn bệnh.||= qtdieutri.giai_doan_benh|
|5|hoi_chan|VARCHAR||Ghi kết quả hội chẩn (nếu có).||Ghi nhận theo cột xml5.hoi_chan (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|
|6|phau_thuat|VARCHAR||Ghi mô tả cách thức phẫu thuật, thủ thuật (nếu có).||Ghi nhận theo cột xml5.phau_thuat (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|
|7|thoi_diem_dbls|VARCHAR(12)| X|Ghi thời điểm diễn biến lâm sàng, gồm 12 ký tự, theo cấu trúc: yyyymmddHHMM, trong đó: 04 ký tự năm (yyyy) + 02 ký tự tháng (mm) + 02 ký tự ngày (dd) + 02 ký tự giờ, tính theo 24 giờ (HH) + 02 ký tự phút (MM).<br/>Ví dụ: ngày 31/03/2015 15:20 được hiển thị là: 201503311520||Ghi nhận theo cột xml5.ngay_yl (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|
|8|nguoi_thuc_hien|VARCHAR(255)|X |Ghi mã định danh y tế của nhân viên y tế thực hiện ghi chép diễn biến lâm sàng.<br/>**Lưu ý**: Trường hợp có nhiều người thực hiện ghi chép diễn biến lâm sàng thì ghi người thực hiện chính đầu tiên, giữa các người thực hiện ghi chép diễn biến lâm sàng cách nhau bằng dấu chấm phẩy “;”.||- Đối với khám ngoại trú/BA ngoại trú quyết toán ngày:<br/>= dmnhanvien. macc_hanhnghe_cv2348, trong đó tham chiếu: khambenh.manv = dmnhanvien.manv<br/><br/>- Đối với BA nội trú/BA ngoại trú quyết toán cuối đợt:<br/>= dmnhanvien. macc_hanhnghe_cv2348, trong đó tham chiếu: qtdieutri.manv = dmnhanvien.manv|
|9|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần thiết.|||
||mabn|VARCHAR(20)|X|psdangky.mabn|X||
||makb|VARCHAR(20)|X|psdangky.makb|X||
