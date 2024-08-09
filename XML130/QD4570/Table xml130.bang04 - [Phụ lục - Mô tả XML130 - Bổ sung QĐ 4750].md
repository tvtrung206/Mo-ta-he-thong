<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang4: Chỉ tiêu chi tiết dịch vụ cận lâm sàng.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X|Như 4210|
|2|stt|NUMERIC(10,0)|X|Là số thứ tự tăng từ 1 đến hết trong một lần gửi dữ liệu.||Như 4210|
|3|ma_dich_vu|VARCHAR(15)|X|Ghi mã dịch vụ kỹ thuật cận lâm sàng, thực hiện theo Phụ lục số 1 ban hành kèm theo [Quyết định số 7603/QĐ-BYT](https://syt.binhdinh.gov.vn/index.php/vi/van-ban-chi-dao-dieu-hanh/detail/Quyet-dinh-ve-viec-ban-hanh-bo-ma-danh-muc-dung-chung-ap-dung-trong-quan-ly-kham-benh-chua-benh-va-thanh-toan-bao-hiem-y-te-Phien-ban-so-6-261/) ngày 25 tháng 12 năm 2018 của Bộ trưởng Bộ Y tế.|X|Xét, nếu `chidinhcls.macls_byt` khác rỗng `ma_dich_vu = chidinhcls.macls_byt`, ngược lại `ma_dich_vu =dmcls.macls_byt` [^2024-07-24]|
|4|ma_chi_so|VARCHAR(50)||Ghi mã chỉ số xét nghiệm, chẩn đoán hình ảnh, thăm dò chức năng theo Phụ lục số 11 ban hành kèm theo [Quyết định số 7603/QĐ-BYT](https://syt.binhdinh.gov.vn/index.php/vi/van-ban-chi-dao-dieu-hanh/detail/Quyet-dinh-ve-viec-ban-hanh-bo-ma-danh-muc-dung-chung-ap-dung-trong-quan-ly-kham-benh-chua-benh-va-thanh-toan-bao-hiem-y-te-Phien-ban-so-6-261/) ngày 25 tháng 12 năm 2018 của Bộ trưởng Bộ Y tế. Trường hợp chưa có mã chỉ số thì để trống trường thông tin này.||`= dmcls.ma_chi_so`|
|5|ten_chi_so|VARCHAR(255)||Ghi tên chỉ số xét nghiệm, chẩn đoán hình ảnh, thăm dò chức năng, theo Phụ lục số 11 ban hành kèm theo [Quyết định số 7603/QĐ-BYT](https://syt.binhdinh.gov.vn/index.php/vi/van-ban-chi-dao-dieu-hanh/detail/Quyet-dinh-ve-viec-ban-hanh-bo-ma-danh-muc-dung-chung-ap-dung-trong-quan-ly-kham-benh-chua-benh-va-thanh-toan-bao-hiem-y-te-Phien-ban-so-6-261/) ngày 25 tháng 12 năm 2018 của Bộ trưởng Bộ Y tế. Trường hợp chưa có tên chỉ số thì để trống trường thông tin này.||`= dmcls.ten_chi_so`|
|6|gia_tri|VARCHAR(50)||Ghi giá trị chỉ số (kết quả xét nghiệm, chẩn đoán hình ảnh, thăm dò chức năng).<br/>Trường hợp người bệnh ra viện nhưng chưa có kết quả xét nghiệm thì để trống trường thông tin này khi gửi dữ liệu XML thông tuyến và bổ sung đầy đủ thông tin kết quả xét nghiệm trước khi gửi đề nghị giám định theo khoản 1 Điều 7 [Thông tư số 48/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=149470).<br/>Trường hợp sau 7 ngày mới có kết quả thì cơ sở KBCB nhập thông tin kết quả xét nghiệm trực tiếp trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam nhưng không quá 30 ngày kể từ ngày kết thúc đợt KBCB.||Chỉ áp dụng đối với xét nghiệm:<br/>`= psmotaxn.ketqua`|
|7|don_vi_do|VARCHAR(50)||Ghi đơn vị đo của chỉ số xét nghiệm, chẩn đoán hình ảnh, thăm dò chức năng theo Phụ lục 11 ban hành kèm theo [Quyết định số 7603/QĐ-BYT](https://syt.binhdinh.gov.vn/index.php/vi/van-ban-chi-dao-dieu-hanh/detail/Quyet-dinh-ve-viec-ban-hanh-bo-ma-danh-muc-dung-chung-ap-dung-trong-quan-ly-kham-benh-chua-benh-va-thanh-toan-bao-hiem-y-te-Phien-ban-so-6-261/) ngày 25 tháng 12 năm 2018 của Bộ trưởng Bộ Y tế. Đối với các chỉ số không có đơn vị đo thì để trống trường thông tin này.||`=dmcls.don_vi_do`|
|8|mo_ta|VARCHAR||Ghi các mô tả do người đọc kết quả ghi.<br/>Trường hợp không có kết quả thì để trống trường thông tin này.||Không áp dụng đối với xét nghiệm:<br/>`= pskhamha.mota_text`|
|9|ket_luan|VARCHAR||Ghi các kết luận của người đọc kết quả.<br/>Trường hợp không có kết quả thì để trống trường thông tin này.||Không áp dụng đối với xét nghiệm:<br/>`= pskhamha. ketluan_plaintext`|
|10|ngay_kq|VARCHAR(12)|X|Ghi thời điểm có kết quả cận lâm sàng; gồm 12 ký tự, theo cấu trúc: yyyymmddHHMM, trong đó: 04 ký tự năm (yyyy) + 02 ký tự tháng (mm) + 02 ký tự ngày (dd) + 02 ký tự giờ, tính theo 24 giờ (HH) + 02 ký tự phút (MM).<br/>Ví dụ: ngày 31/03/2017 15:20 được hiển thị là: 201703311520<br/>Trường hợp người bệnh ra viện nhưng chưa có kết quả xét nghiệm thì để trống trường thông tin này khi gửi dữ liệu XML thông tuyến và bổ sung đầy đủ thông tin thời điểm có kết quả xét nghiệm trước khi gửi đề nghị giám định theo khoản 1 Điều 7 [Thông tư số 48/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=149470). Trường hợp sau 7 ngày mới có kết quả thì cơ sở KBCB nhập thông tin ngày kết quả cận lâm sàng trực tiếp trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam nhưng không quá 30 ngày kể từ ngày kết thúc đợt KBCB.<br/><br/>**Đính chính**:<br/>- Trường hợp sau 07 ngày mới có kết quả thì cơ sở KBCB nhập thông tin ngày kết quả cận lâm sàng trực tiếp trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam, nhưng không quá 60 ngày kể từ ngày kết thúc đợt KBCB (để phù hợp với kết quả xét nghiệm nuôi cấy vi khuẩn lao).||Thực hiện theo [mô tả 4210](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/Vinh%20-%20Mo%20ta%20cot%20%5Bdien_bien%5D%20%5Bhoi_chan%5D%20va%20%5Bphau_thuat%5D%20XML5%20-%2020220602.4.pdf):<br/>`= chidinhcls.ngaykq`|
|11|ma_bs_doc_kq|VARCHAR(255)|X|Ghi mã của người có thẩm quyền đọc hoặc duyệt kết quả đọc, ghi mã của người này theo mã định danh y tế.<br/><br/>**Bổ sung lưu ý**: Trường này không bắt buộc trong trường hợp thực hiện chuyển gửi xét nghiệm cận lâm sàng.||✳️[^2024-08-09] `ma_bs_doc_kq = ghép các dmnhanvien.macc_hanhnghe_cv2348` cách nhau bởi dấu `;` thông qua `dmnhanvien.manv` theo quy tắc: `pskhamha.manv; psmotaxn.manv; pssinhthiet.manvtraketqua; pstebaotucung.manv_th; psdom.manv_th; ekippt.manv`.<br/>Trong đó:<br/>➡️ `pskhamha.manv`: `macc_hanhnghe_cv2348` của nhân viên/bác sĩ đọc kết quả `Chẩn đoán hình ảnh/Thăm dò chức năng`. Được tham chiếu chi tiết: `chidinhcls.mabn = pskhamha.mabn AND chidinhcls.makb = pskhamha.makb AND chidinhcls.macls = pskhamha.macls AND chidinhcls.ngaykcb = pskhamha.ngaykcb`.<br/>➡️ `psmotaxn.manv`: `macc_hanhnghe_cv2348` của nhân viên thực hiện trả kết quả Xét nghiệm cơ bản `(Huyết học; Sinh hóa; Nước tiểu; Miễn dịch; Vi sinh; ...)`. Được tham chiếu chi tiết: `chidinhcls.mabn = psmotaxn.mabn AND chidinhcls.makb = psmotaxn.makb AND chidinhcls.macls = psmotaxn.macls AND chidinhcls.ngaykcb = psmotaxn.ngaykcb`.<br/>➡️ `pssinhthiet.manvtraketqua`: `macc_hanhnghe_cv2348` của nhân viên đọc kết quả Xét nghiệm `Sinh thiết`. Được tham chiếu chi tiết: `chidinhcls.mabn = pssinhthiet.mabn AND chidinhcls.makb = pssinhthiet.makb AND chidinhcls.macls = pssinhthiet.macls AND chidinhcls.ngaykcb = pssinhthiet.ngaykcb AND COALESCE(pssinhthiet.manvtraketqua,'') != ''`.<br/>➡️ `pstebaotucung.manv_th`: `macc_hanhnghe_cv2348` của nhân viên đọc kết quả Xét nghiệm `Tế bào cổ tử cung`. Được tham chiếu chi tiết: `chidinhcls.mabn = pstebaotucung.mabn AND chidinhcls.makb = pstebaotucung.makb AND chidinhcls.macls = pstebaotucung.macls AND chidinhcls.ngaykcb = pstebaotucung.ngaykcb`.<br/>➡️ `psdom.manv_th`: `macc_hanhnghe_cv2348` của nhân viên đọc kết quả `Xét nghiệm Đờm`. Được tham chiếu chi tiết: `chidinhcls.mabn = psdom.mabn AND chidinhcls.makb = psdom.makb AND chidinhcls.macls = psdom.macls AND chidinhcls.ngaykcb = psdom.ngaykcb`.<br/>➡️ `ekippt.manv`: Gom tất cả các `macc_hanhnghe_cv2348` của nhân viên trong ekip thực hiện `Thủ thuật/Phẫu thuật`. Được tham chiếu chi tiết: `chidinhcls.mabn = ekippt.mabn AND chidinhcls.makb = ekippt.makb AND chidinhcls.id = ekippt.id`.[^2024-07-08]|
|12|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần thiết.|||
||mabn|VARCHAR(20)|X|psdangky.mabn|X||
||makb|VARCHAR(20)|X|psdangky.makb|X||
||macls|VARCHAR(20)|X|chidinhcls.macls|X||
||ngaykcb|TIMESTAMP|X|chidinhcls.ngaykcb|X||

[^2024-08-09]: Thay đổi ngày 09/08/2024: Thay đổi điều kiện ghi nhận cột  `ma_bs_doc_kq` theo `macc_hanhnghe_cv2348` và loại bỏ bác sĩ chỉ định. Chi tiết theo y/c tại: [Kiểm tra XML4.ma_bs_doc_kq với mô tả #591](https://github.com/dh-hos/To_Lap_Trinh/issues/591)
[^2024-07-24]: Thay đổi ngày 24/07/2024: Thay đổi điều kiện cột  `ma_dich_vu`.
[^2024-07-08]: Thay đổi ngày 08/07/2024: Thay đổi liên kết hướng dẫn ghi nhận cột  `ma_bs_doc_kq`.
