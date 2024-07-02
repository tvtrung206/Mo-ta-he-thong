<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang7: Chỉ tiêu dữ liệu giấy ra viện.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Tất cả các hồ sơ bệnh nhân có trong  [Table xml130.bang1: Chỉ tiêu tổng hợp khám bệnh, chữa bệnh;](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang01%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md) phải có  trong bảng này.  [^2024-06-30-01]

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X||
|2|so_luu_tru|VARCHAR(200)| X|Ghi số lưu trữ, là số hồ sơ bệnh án của người bệnh trong đợt điều trị||`= psdangky.makb`|
|3|ma_yte|VARCHAR(200)|X|Ghi mã y tế, lấy theo mã số người bệnh quy định tại trường MA_BN tại Bảng XML 1 ban hành kèm theo quyết định này.||`= psdangky.mabn`|
|4|ma_khoa_rv|VARCHAR(200)|X|Ghi mã khoa nơi tổng kết hồ sơ bệnh án của người bệnh.||`= dmdonvi.ma_khoa_cv2348`<br/>Trong đó tham chiếu:<br/>- Khám ngoại trú: `psdangky.madv_inphieu = dmdonvi.madv`<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: `bnnoitru.madv = dmdonvi.madv`|
|5|ngay_vao|VARCHAR(12)|X|Ghi thời điểm người bệnh đến KBCB, gồm 12 ký tự, theo định dạng yyyymmddHHMM.<br/>Ví dụ: người bệnh đến KBCB lúc 15 giờ 20 phút ngày 31/03/2017 được hiển thị là: 201703311520.||`= bang1.ngay_vao` [^2024-07-02-02]|
|6|ngay_ra|VARCHAR(12)|X|Ghi thời điểm người bệnh kết thúc điều trị nội trú, kết thúc điều trị nội trú ban ngày, kết thúc điều trị ngoại trú hoặc kết thúc khám bệnh, gồm 12 ký tự theo định dạng yyyymmddHHMM.<br/>Ví dụ: Thời điểm người bệnh kết thúc điều trị lúc 09 giờ 20 phút ngày 05/04/2022, khi đó được hiển thị là: 202204050920. <br/>**Lưu ý**:<br/>- Trường hợp khám bệnh (MA_LOAI_KCB = 01) thì ghi thời điểm kết thúc lần khám bệnh;<br/>- Trường hợp điều trị ngoại trú (MA_LOAI_KCB = 02), điều trị ngoại trú các bệnh mạn tính dài ngày liên tục trong năm (MA_LOAI_KCB = 05), nhận thuốc theo hẹn (không khám bệnh) (MA_LOAI_KCB = 07): Ghi ngày kết thúc của đợt KBCB (là ngày cuối cùng sử dụng thuốc hoặc dịch vụ theo chỉ định của bác sỹ), gồm 02 ký tự giờ + 02 ký tự phút và mặc định là 2359 (Thời điểm cuối cùng của ngày kết thúc đợt KBCB); <br/>- Trường hợp điều trị ngoại trú các bệnh mạn tính dài ngày liên tục trong năm (MA_LOAI_KCB = 08): Ghi thời điểm kết thúc của đợt KBCB (Ví dụ: Trường hợp chạy thận nhân tạo thì ghi ngày cuối cùng của đợt chạy thận nhân tạo);<br/>- Trường hợp người bệnh được chuyển tuyến đến cơ sở KBCB khác thì thời điểm người bệnh ra viện bằng thời điểm người bệnh được chuyển tuyến.||`=bang1.ngay_ra` [^2024-07-02-01]|
|7|ma_dinh_chi_thai|NUMERIC(1,0)||Ghi mã "1" là đình chỉ thai nghén, mã "0" là không đình chỉ thai nghén.<br/>Trường hợp đình chỉ thai nghén bắt buộc nhập thông tin vào trường thông tin tuổi thai (TUOI_THAI) và trường thông tin nguyên nhân đình chỉ thai nghén (NGUYENNHAN_DINHCHI)|||
|8|nguyennhan_dinhchi|VARCHAR|bắt buộc khi MA_DINH_CHI_THAI =1 |Ghi nguyên nhân đình chỉ thai nghén.<br/>**Lưu ý**: Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI là mã "1".|||
|9|thoigian_dinhchi|VARCHAR(12)|bắt buộc khi MA_DINH_CHI_THAI =1 |Ghi thời điểm đình chỉ thai nghén, gồm 12 ký tự, theo định dạng yyyymmddHHMM<br/>Ví dụ: ngày 31/10/2022 15:20 được hiển thị là: 202210311520<br/>**Lưu ý**: Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI = 1|||
|10|tuoi_thai|NUMERIC(2,0)|bắt buộc khi MA_DINH_CHI_THAI =1  |Ghi rõ tuần tuổi thai thực tế (kể cả trường hợp đình chỉ thai ngoài tử cung, thai trứng cần xác định rõ tuần tuổi thai), trong đó tuổi thai luôn luôn lớn hơn hoặc bằng 1 và nhỏ hơn hoặc bằng tuổi 42 tuần tuổi.<br/>**Lưu ý**: Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI = 1.|||
|11|chan_doan_rv|VARCHAR(1500)| X|Ghi đầy đủ chẩn đoán xác định bệnh chính, bệnh kèm theo và/hoặc các triệu chứng hoặc hội chứng, được bác sỹ ghi trong hồ sơ KBCB tại thời điểm kết thúc KBCB đối với người bệnh.<br/>Lưu ý: Đối với việc ghi chẩn đoán ra viện để phục vụ việc tạo lập giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội thì thực hiện theo hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế, trong đó:<br/>- Nội dung chẩn đoán phải mô tả cụ thể về tình trạng sức khỏe hoặc ghi tên bệnh hoặc mã bệnh.<br/>- Trường hợp mắc bệnh cần chữa trị dài ngày thì ghi mã bệnh; trường hợp chưa có mã bệnh thì ghi đầy đủ tên bệnh. Việc ghi mã bệnh và tên bệnh thực hiện theo quy định tại [Thông tư số 46/2016/TT-BYT](https://chinhphu.vn/default.aspx?pageid=27160&docid=189279) ngày 30 tháng 12 năm 2016 của Bộ trưởng Bộ Y tế ban hành danh mục bệnh dài ngày;<br/>- Trường hợp điều trị dưỡng thai: Ghi rõ cụm từ “dưỡng thai”.||- Khám ngoại trú: `= psdangky.kqcdoan`<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: `= bnnoitru.kqcdoan + ‘;’ + bnnoitru.kqcdoanp`|
|12|pp_dieutri|VARCHAR(1500)| X|Ghi phương pháp điều trị theo đúng hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||- Đối với khám bệnh ngoại trú/toa nội trú xuất viện ghi: `pp_dieu_tri = "Ngoại khoa"`<br/><br/>- Đối với người bệnh nội trú/BA ngoại trú quyết toán cuối đợt: `pp_dieu_tri = dmppdt.diengiai` (tham chiếu thông qua `bnnoitru.mappdt`) [^2024-06-30-02]|
|13|ghi_chu|VARCHAR(1500)||Trường thông tin này áp dụng đối với trường hợp cấp giấy ra viện để giải quyết chế độ BHXH.<br/>Ghi theo hướng dẫn tại mẫu Phụ lục 3 ban hành kèm theo [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||Đối với người bệnh nội trú: `= bnnoitru.loidan`|
|14|ma_ttdv|VARCHAR(10)|X|Ghi mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được người đứng đầu cơ sở KBCB ủy quyền được ký và đóng dấu của cơ sở KBCB đó.||Được lấy từ tham số `ma_ttdv`|
|15|ma_bs|VARCHAR(200)|X|Ghi mã số định danh y tế (mã số BHXH) của Trưởng khoa hoặc Phó trưởng khoa được uỷ quyền ký tên theo quy định của Thủ trưởng cơ sở KBCB.||`= dmnhanvien.sobhxh`<br/>Trong đó tham chiếu:<br/>- Khám ngoại trú: `psdangky.madv_inphieu = dmdonvi.madv AND dmdonvi.manv_truongkhoa = dmnhanvien.manv`<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: `bnnoitru.madv = dmdonvi.madv AND dmdonvi.manv_truongkhoa = dmnhanvien.manv`|
|16|ten_bs|VARCHAR(255)|X|Ghi họ và tên của Trưởng khoa hoặc Phó trưởng khoa được uỷ quyền ký tên theo quy định của Thủ trưởng cơ sở KBCB.||`= dmnhanvien.holot + “ ” + dmnhanvien.ten` <br/>Trong đó tham chiếu:<br/>- Khám ngoại trú: `psdangky.madv_inphieu = dmdonvi.madv AND dmdonvi.manv_truongkhoa = dmnhanvien.manv`<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: `bnnoitru.madv = dmdonvi.madv AND dmdonvi.manv_truongkhoa = dmnhanvien.manv`|
|17|ngay_ct|VARCHAR(8)|X|Ghi ngày chứng từ (Giấy ra viện), theo định dạng yyyymmdd, là ngày Trưởng khoa hoặc Trưởng phòng hoặc Phó trưởng khoa hoặc Phó trưởng phòng cấp giấy ra viện. <br/>**Lưu ý**: Việc ghi ngày, tháng, năm tại phần chữ ký của Trưởng khoa hoặc Trưởng phòng hoặc Phó trưởng khoa hoặc Phó trưởng phòng điều trị phải trùng với ngày ra viện.||`= ngay_ra`|
|18|ma_cha|VARCHAR(10)||Ghi mã số định danh y tế (mã số BHXH) của người cha đối với trường hợp người bệnh là trẻ em dưới 16 tuổi (Nếu có cha (bố)).<br/>Trường hợp không có cha hoặc người cha không có mã số BHXH thì để trống trường thông tin này.|||
|19|ma_me|VARCHAR(10)||Ghi mã số định danh y tế (mã số BHXH) của người mẹ đối với trường hợp người bệnh là trẻ em dưới 16 tuổi (Nếu có mẹ).<br/>Trường hợp không có mẹ hoặc người cha không có mã số BHXH thì để trống trường thông tin này.|||
|20|ma_the_tam|VARCHAR(15)||Ghi mã thẻ BHYT tạm thời của trẻ em sinh ra hoặc của người hiến tạng nhưng chưa được cơ quan BHXH cấp thẻ BHYT. Cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.||- Khám ngoại trú xét, nếu `psdangky.thetam = 1` thì: `ma_the_tam =  psdangky.mathe`<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: `bnnoitru.thetam = 1` thì: `ma_the_tam = bnnoitru.mathe (đối với thẻ 1)` hoặc `ttcon.thetam = 1` thì: `ma_the_tam = ttcon.mathe (đối với thẻ 2)`|
|21|ho_ten_cha|VARCHAR(255)||Ghi họ và tên cha đối với trường hợp người bệnh là trẻ em dưới 16 tuổi (Nếu có cha (bố)) theo quy định tại Phụ lục 3 [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005) của Bộ Y tế.<br/>Trường hợp không có cha (bố) thì để trống trường thông tin này.||Xét `psdangky.loaiqh` có chứa các từ `“cha”, “ba”` thì `ho_ten_cha = psdangky.hotenqh`|
|22|ho_ten_me|VARCHAR(255)||Ghi họ và tên mẹ đối với trường hợp người bệnh là trẻ em dưới 16 tuổi (Nếu có mẹ) theo quy định tại Phụ lục 3 [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005) của Bộ Y tế.||Xét `psdangky.loaiqh` có chứa các từ `“mẹ”, “má”` thì `ho_ten_me = psdangky.hotenqh`|
|23|so_ngay_nghi|NUMERIC(2,0)|Nếu 1 trường có dữ liệu thì bắt buộc nhập cả 3 trường (so_ngay_nghi, ngoaitru_tungay, ngoaitru_denngay) |Ghi họ và tên mẹ đối với trường hợp người bệnh là trẻ em dưới 16 tuổi (Nếu có mẹ) theo quy định tại Phụ lục 3 Thông tư số 56/2017/TT-BYT của Bộ Y tế.<br/>Trường hợp không có mẹ thì để trống trường thông tin này.|||
|24|ngoaitru_tungay|VARCHAR(8)|Nếu 1 trường có dữ liệu thì bắt buộc nhập cả 3 trường (so_ngay_nghi, ngoaitru_tungay, ngoaitru_denngay)|Ghi ngày bắt đầu nghỉ ngoại trú sau khi điều trị của người được cấp giấy ra viện theo định dạng yyyymmdd.|||
|25|ngoaitru_denngay|VARCHAR(8)|Nếu 1 trường có dữ liệu thì bắt buộc nhập cả 3 trường (so_ngay_nghi, ngoaitru_tungay, ngoaitru_denngay)|Ghi ngày kết thúc nghỉ ngoại trú sau khi điều trị của người được cấp giấy ra viện theo định dạng yyyymmdd.|||
||mabn|VARCHAR(20)|X|psdangky.mabn|X||
||makb|VARCHAR(20)|X|psdangky.makb|X||

[^2024-07-02-02]: Thay đổi ngày 01/07/2024: Thay đổi điều kiện cột `ngay_vao`.
[^2024-07-02-01]: Thay đổi ngày 01/07/2024: Bổ sung điều kiện cột `ngay_ra`.
[^2024-06-30-01]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-30-02]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu cột `pp_dieutri`.
