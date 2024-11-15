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
###### :eight_spoked_asterisk: Ngày cập nhật: **12/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Diễn giải|Ghi chú[^2024-10-16-01]|Kiểu dữ liệu|Bắt buộc|Index|
|:-------:|-------|-------|-------|:-------:|:-------:|:-------:|
|1|ma_lk|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|`= bang1.ma_lk`|VARCHAR(100)|X|X|
|2|stt|Là số thứ tự tăng từ 1 đến hết trong một lần gửi dữ liệu.|Là số thứ tự tăng từ 1 đến hết trong một lần gửi dữ liệu.|NUMERIC(10,0)|X||
|3|dien_bien_ls|Ghi diễn biến lâm sàng của người bệnh trong lần khám và/hoặc ghi nội dung chăm sóc của nhân viên y tế.<br/><br/>**Bổ sung hướng dẫn**: Trường hợp người bệnh có được đo các chỉ số sinh tồn khi mô tả diễn biến của người bệnh thì ghi chỉ số sinh tồn theo quy ước như sau: Mạch (M), nhiệt độ (T), huyết áp (HA), nhịp thở (NT), SPO2 (SP), chế độ hộ lý (HL),....<br/>Ví dụ: Mạch 75 lần/phút, nhiệt độ 370C, huyết áp 120/70 mmHg, nhịp thở 18 lần/phút, chế độ hộ lý cấp II được ghi là: “CSST<M75_T37_HA120/70_ NT18_HL2>”.|➡️ Đối với khám ngoại trú/Bệnh án ngoại trú quyết toán ngày: Ghi theo cú pháp:[^2024-06-12]<br/>`dien_bien_ls` = **CSST<M(1)_T(2)_HA(3)_NT(4)>**<br/>Trong đó:<br/>(1) = khambenh.mach<br/>(2) = khambenh.nhietdo<br/>(3) = khambenh.huyetap<br/>(4) = khambenh.nhiptho<br/>**Lưu ý**: Các giá trị trong (1), (2), (3), (4) không có thì bỏ luôn tiền tố tương ứng của nó trong cú pháp.<br/><br/>➡️ Đối với bệnh án nội trú/Bệnh án ngoại trú quyết toán cuối đợt:[^2024-09-26-01]<br/>`dien_bien_ls` =<br/>- `qtdieutri.dienbien` + <br/>- `[qtdieutri.maicd]` + `qtdieutri.kqcdoan` +<br/>- Huyết áp: `qtdieutri.huyetap` +<br/>- Nhiệt độ: `qtdieutri.nhietdo` +<br/>- Mạch: `qtdieutri.mach` +<br/>- Nhịp thở: `qtdieutri.nhiptho` +<br/>- Chiều cao: `qtdieutri.chieucao` +<br/>- Cân nặng: `qtdieutri.cannang`|VARCHAR|X||
|4|giai_doan_benh|Ghi giai đoạn bệnh trong trường hợp người bệnh đã được cơ sở KBCB xác định giai đoạn bệnh.|= qtdieutri.giai_doan_benh|VARCHAR|||
|5|hoi_chan|Ghi kết quả hội chẩn (nếu có).|Ghi nhận theo cột xml5.hoi_chan (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|VARCHAR|||
|6|phau_thuat|Ghi mô tả cách thức phẫu thuật, thủ thuật (nếu có).|Ghi nhận theo cột xml5.phau_thuat (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|VARCHAR|||
|7|thoi_diem_dbls|Ghi thời điểm diễn biến lâm sàng, gồm 12 ký tự, theo cấu trúc: yyyymmddHHMM, trong đó: 04 ký tự năm (yyyy) + 02 ký tự tháng (mm) + 02 ký tự ngày (dd) + 02 ký tự giờ, tính theo 24 giờ (HH) + 02 ký tự phút (MM).<br/>Ví dụ: ngày 31/03/2015 15:20 được hiển thị là: 201503311520|Ghi nhận theo cột xml5.ngay_yl (bảng 5 - XML4210). [Xem chi tiết mô tả tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf).|VARCHAR(12)| X||
|8|nguoi_thuc_hien|Ghi mã định danh y tế của nhân viên y tế thực hiện ghi chép diễn biến lâm sàng.<br/>**Lưu ý**: Trường hợp có nhiều người thực hiện ghi chép diễn biến lâm sàng thì ghi người thực hiện chính đầu tiên, giữa các người thực hiện ghi chép diễn biến lâm sàng cách nhau bằng dấu chấm phẩy “;”.|- Đối với khám ngoại trú/BA ngoại trú quyết toán ngày:<br/>= dmnhanvien. macc_hanhnghe_cv2348, trong đó tham chiếu: khambenh.manv = dmnhanvien.manv<br/><br/>- Đối với BA nội trú/BA ngoại trú quyết toán cuối đợt:<br/>= dmnhanvien. macc_hanhnghe_cv2348, trong đó tham chiếu: qtdieutri.manv = dmnhanvien.manv|VARCHAR(255)|X ||
|9|du_phong|Trường dữ liệu dự phòng khi cần thiết.||VARCHAR|||
||mabn|psdangky.mabn||VARCHAR(20)|X|X|
||makb|psdangky.makb||VARCHAR(20)|X|X|

[^2024-10-16-01]: Thay đổi ngày 16/10/2024: Bổ sung mô tả giá trị các cột `ma_lk`, `stt`. Chi tiết theo yêu cầu [#684](https://github.com/dh-hos/To_Lap_Trinh/issues/684).
[^2024-09-26-01]: Thay đổi ngày 26/09/2024: Thay đổi cách ghi nhận giá trị cho `dien_bien_ls` đối với bệnh án nội trú/bệnh án ngoại trú quyết toán cuối đợt. Chi tiết theo yêu cầu [#658](https://github.com/dh-hos/To_Lap_Trinh/issues/658).
[^2024-06-12]: Thay đổi ngày 12/06/2024: thay đổi cách ghi nhận giá trị cho `dien_bien_ls`
