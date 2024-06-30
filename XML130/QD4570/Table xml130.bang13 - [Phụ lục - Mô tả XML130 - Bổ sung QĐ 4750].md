<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang13: Chỉ tiêu dữ liệu giấy chuyển tuyến khám bệnh, chữa bệnh bảo hiểm y tế.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Dữ liệu bảng này phải phát sinh ở table `current.chuyenvien`. [^2024-06-30-01]

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).| X||
|2|so_hoso|VARCHAR(50)|X|Ghi số hồ sơ giấy chuyển tuyến KBCB BHYT do cơ sở KBCB quy định theo mẫu số 6 của Phụ lục ban hành kèm theo [Nghị định 75/2023/NĐ-CP](https://vanban.chinhphu.vn/?pageid=27160&docid=208813) của Chính phủ.||`=chuyenvien.makb`  [^2024-06-30-02]|
|3|so_chuyentuyen|VARCHAR(50)|X|Ghi số của sổ chuyển tuyến do cơ sở KBCB quy định theo mẫu số 6 của Phụ lục ban hành kèm theo [Nghị định 75/2023/NĐ-CP](https://vanban.chinhphu.vn/?pageid=27160&docid=208813) của Chính phủ.||`=chuyenvien.socv`|
|4|giay_chuyen_tuyen|VARCHAR(50)|X|Ghi số giấy chuyển tuyến do cơ sở KBCB cấp theo mẫu số 6 của Phụ lục ban hành kèm theo [Nghị định 75/2023/NĐ-CP](https://vanban.chinhphu.vn/?pageid=27160&docid=208813) của Chính phủ.||`=chuyenvien.socv` + `=chuyenvien.namkt` + `/GCT`|
|5|ma_cskcb|VARCHAR(5)||Ghi mã cơ sở KBCB nơi cấp giấy chuyển tuyến||`=tham số mabvbh`|
|6|ma_noi_di|VARCHAR(5)||Sử dụng thông tin tại trường MA_NOI_DI trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_noi_di`|
|7|ma_noi_den|VARCHAR(5)||Sử dụng thông tin tại trường MA_NOI_DEN trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_noi_den`|
|8|ho_ten|VARCHAR(255)|X|Ghi họ và tên của người bệnh được chuyển tuyến.||`= dmbenhnhan.holot + “ ” + dmbenhnhan.ten`|
|9|ngay_sinh|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_SINH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_sinh`|
|10|gioi_tinh|NUMERIC(1,0)||Sử dụng thông tin tại trường GIOI_TINH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.gioi_tinh`|
|11|ma_quoctich|VARCHAR(3)||Sử dụng thông tin tại trường MA_QUOCTICH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_quoctich`|
|12|ma_dantoc|VARCHAR(2)||Sử dụng thông tin tại trường MA_DANTOC trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_dantoc`|
|13|ma_nghe_nghiep|VARCHAR(5)||Sử dụng thông tin tại trường MA_NGHE_NGHIEP trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_nghe_nghiep`|
|14|dia_chi|VARCHAR(1024)||Sử dụng thông tin tại trường DIA_CHI trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.dia_chi`|
|15|ma_the_bhyt|VARCHAR(50)||Sử dụng thông tin tại trường MA_THE_BHYT trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_the_bhyt`|
|16|gt_the_den|VARCHAR(50)||Sử dụng thông tin tại trường GT_THE_DEN trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.gt_the_den`|
|17|ngay_vao|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_VAO trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_vao`|
|18|ngay_vao_noi_tru|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_VAO_NOI_TRU trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_vao_noi_tru`|
|19|ngay_ra|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_RA trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_ra`|
|20|dau_hieu_ls|VARCHAR|X|Ghi các dấu hiệu lâm sàng của người bệnh khi chuyển tuyến||`=chuyenvien.dauhieuls`|
|21|chan_doan_rv|VARCHAR||Sử dụng thông tin tại trường CHAN_DOAN_RV trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.chan_doan_rv`|
|22|qt_benhly|VARCHAR|X|Ghi quá trình bệnh lý và diễn biến lâm sàng.||`=chuyenvien.tinhtrang`|
|23|tomtat_kq|VARCHAR||Ghi tóm tắt kết quả xét nghiệm, cận lâm sàng có giá trị chẩn đoán.|||
|24|pp_dieutri|VARCHAR||Sử dụng thông tin tại trường PP_DIEUTRI trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.pp_dieutri`|
|25|ma_benh_chinh|VARCHAR(7)||Sử dụng thông tin tại trường MA_BENH_CHINH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_benh_chinh`|
|26|ma_benh_kt|VARCHAR(100)||Sử dụng thông tin tại trường MA_BENH_KT trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_benh_kt`|
|27|ma_benh_yhct|VARCHAR(255)||Sử dụng thông tin tại trường MA_BENH_YHCT trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_benh_yhct`|
|28|ten_dich_vu|VARCHAR(1024)|X|Ghi tên dịch vụ kỹ thuật đã sử dụng cho người bệnh.<br/>**Lưu ý**:<br/>- Đối với dịch vụ kỹ thuật, trường hợp cần ghi rõ vị trí, phương pháp thực hiện hoặc phân biệt các mức giá khác nhau thì sau tên dịch vụ kỹ thuật ghi phần mô tả chi tiết trong ngoặc vuông [ ];<br/>- Đối với DVKT sử dụng phương pháp vô cảm gây tê, bổ sung cụm từ "[gây tê]" sau tên dịch vụ.||Gom các tên CLS `bang3.ten_dich_vu`|
|29|ten_thuoc|VARCHAR(1024)||Sử dụng thông tin tại trường TEN_THUOC trong Bảng 2 ban hành kèm theo Quyết định này||Gom các tên thuốc `bang2.ten_thuoc`|
|30|pp_dieu_tri|VARCHAR||Sử dụng thông tin tại trường PP_DIEU_TRI trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.pp_dieu_tri`|
|31|ma_loai_rv|NUMERIC(1,0)||Sử dụng thông tin tại trường MA_LOAI_RV trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_loai_rv`|
|32|ma_lydo_ct|NUMERIC(1,0)|X|Ghi mã lý do chuyển tuyến. Ghi mã 1 trong trường hợp đủ điều kiện chuyển tuyến phù hợp với quy định chuyển tuyến; Ghi mã 2 trong trường hợp đủ điều kiện chuyển tuyến do không phù hợp với khả năng đáp ứng của cơ sở KBCB; Ghi mã 3 trong trường hợp chuyển tuyến theo yêu cầu của người bệnh hoặc người đại diện hợp pháp của người bệnh.||Xét `chuyenvien.lydoct = 0` thì `ma_lydo_ct = 1`, ngược lại `ma_lydo_ct = 2`|
|33|huong_dieu_tri|VARCHAR|X|Ghi hướng điều trị sắp tới cho người bệnh.||`=chuyenvien.huongdt`|
|34|phuongtien_vc|VARCHAR(255)|X|Ghi phương tiện vận chuyển người bệnh khi thực hiện chuyển tuyến.||`=chuyenvien.phuongtien`|
|35|hoten_nguoi_ht|VARCHAR(255)||Ghi họ và tên người hộ tống người bệnh (nếu có).||`= dmnhanvien.holot + “ ” + dmnhanvien.ten`, tham chiếu từ `chuyenvien.manvc`|
|36|chucdanh_nguoi_ht|VARCHAR(255)||Ghi chức danh, trình độ chuyên môn người hộ tống người bệnh (nếu có).|||
|37|ma_bac_si|VARCHAR(255)|X|Ghi mã bác sỹ, y sỹ khám, điều trị (mã hóa theo số Chứng chỉ hành nghề).||`= dmnhanvien. macc_hanhnghe_cv2348`, trong đó tham chiếu: `chuyenvien.manv = dmnhanvien.manv`|
|38|ma_ttdv|VARCHAR(10)|X|Ghi mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được uỷ quyền có thẩm quyền ký giấy chuyển tuyến KBCB BHYT.||`= tham số ma_ttdv`|
|39|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần thiết.|||
||makb|VARCHAR(20)|X||X||
||mabn|VARCHAR(20)|X||X||

[^2024-06-30-01]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-30-02]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu chi tiết cho các cột.
