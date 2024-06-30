<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang14: Chỉ tiêu dữ liệu giấy hẹn khám lại.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Kiểm tra: [^2024-06-30-01]
- Đối với ngoại trú: `psdangky.ngaytaikham` khác rỗng.
- Đối với nội trú: `bnnoitru.ngaytaikham` khác rỗng.

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X||
|2|so_giayhen_kl|VARCHAR(50)|X|Ghi số giấy hẹn khám lại do cơ sở KBCB cấp theo mẫu số 5 của Phụ lục ban hành kèm theo [Nghị định 75/2023/NĐ-CP](https://vanban.chinhphu.vn/?pageid=27160&docid=208813) của Chính phủ.||`=psdangky.makb`  [^2024-06-30-02]|
|3|ma_cskcb|VARCHAR(5)|X|Ghi mã cơ sở KBCB nơi cấp giấy hẹn khám lại.||`=tham số mabvbh`|
|4|ho_ten|VARCHAR(255)|X|Ghi họ và tên của người bệnh được cấp giấy hẹn khám lại.||`=bang1.ho_ten`|
|5|ngay_sinh|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_SINH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_sinh`|
|6|gioi_tinh|NUMERIC(1,0)||Sử dụng thông tin tại trường GIOI_TINH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.gioi_tinh`|
|7|dia_chi|VARCHAR(1024)||Sử dụng thông tin tại trường DIA_CHI trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.dia_chi`|
|8|ma_the_bhyt|VARCHAR||Sử dụng thông tin tại trường MA_THE_BHYT trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_the_bhyt`|
|9|gt_the_den|VARCHAR||Sử dụng thông tin tại trường GT_THE_DEN trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.gt_the_den`|
|10|ngay_vao|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_VAO trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_vao`|
|11|ngay_vao_noi_tru|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_VAO_NOI_TRU trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_vao_noi_tru`|
|12|ngay_ra|VARCHAR(12)||Sử dụng thông tin tại trường NGAY_RA trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ngay_ra`|
|13|ngay_hen_kl|VARCHAR(12)|X|Ghi thời điểm người bệnh được hẹn khám lại, gồm 12 ký tự theo định dạng yyyymmddHHMM.<br/>Ví dụ: Thời điểm người bệnh được chuyển tuyến lúc 09 giờ 20 phút ngày 05/04/2022, khi đó được hiển thị là: 202204050920. ||- Khám ngoại trú: `ngay_hen_kl = to_char(psdangky.ngaytaikham, ‘yyyyMMdd’)`<br/>- Bệnh án nội trú: `ngay_hen_kl = to_char(bnnoitru.ngaytaikham, ‘yyyyMMdd’)`|
|15|chan_doan_rv|VARCHAR||Sử dụng thông tin tại trường CHAN_DOAN_RV trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.chan_doan_rv`|
|16|ma_benh_chinh|VARCHAR(7)||Sử dụng thông tin tại trường MA_BENH_CHINH trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_benh_chinh`|
|17|ma_benh_kt|VARCHAR(100)||Sử dụng thông tin tại trường MA_BENH_KT trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_benh_kt`|
|18|ma_benh_yhct|VARCHAR(255)||Sử dụng thông tin tại trường MA_BENH_YHCT trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_benh_yhct`|
|19|ma_doituong_kcb|VARCHAR(4)||Sử dụng thông tin tại trường MA_DOITUONG_KCB trong Bảng 1 ban hành kèm theo Quyết định này||`=bang1.ma_doituong_kcb`|
|20|ma_bac_si|VARCHAR(255)|X|Ghi mã bác sỹ, y sỹ khám bệnh (mã hóa theo số Chứng chỉ hành nghề).||`= dmnhanvien. macc_hanhnghe_cv2348`, trong đó tham chiếu:<br/> - Khám ngoại trú: `khambenh.manv = dmnhanvien.manv`<br/>- Bệnh án nội trú: `bnnoitru.manv = dmnhanvien.manv`|
|21|ma_ttdv|VARCHAR(10)|X|Ghi mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được uỷ quyền có thẩm quyền ký giấy hẹn khám lại.||`=tham số ma_ttdv`|
|22|ngay_ct|VARCHAR(8)|X|Ghi ngày cấp giấy hẹn khám lại, theo định dạng yyyymmdd|||
|23|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần thiết.|||
||makb|VARCHAR(20)|X||X||
||mabn|VARCHAR(20)|X||X||

[^2024-06-30-01]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-30-02]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu chi tiết cho các cột.
