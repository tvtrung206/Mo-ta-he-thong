<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang12: Chỉ tiêu dữ liệu giám định y khoa.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Ngày cập nhật: **09/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750]()**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|nguoi_chu_tri|VARCHAR(255)|X |Ghi họ và tên người chủ trì trong danh mục người chủ trì hội đồng giám định y khoa đã nhập trên Cổng tiếp nhận của cơ quan BHXH.||psgiamdinhykhoa.nguoi_chu_tri|
|2|chuc_vu|NUMERIC(1,0)|X |Ghi chức vụ của người chủ trì, trong đó: mã "1": Chủ tịch; mã "2": Người ký thay chủ tịch.||psgiamdinhykhoa.chuc_vu|
|3|ngay_hop|VARCHAR(8)| X |Ghi ngày, tháng, năm họp hội đồng giám định y khoa, theo định dạng yyyymmdd||to_char(psgiamdinhykhoa.ngay_hop,’yyyyMMdd’)|
|4|ho_ten|VARCHAR(255)| X |Ghi họ và tên người được giám định y khoa.||ho_ten = dmbenhnhan.holot + “ ” + dmbenhnhan.ten<br/><br/>tham chiếu psgiamdinhykhoa.mabn = dmbenhnhan.mabn|
|5|ngay_sinh|VARCHAR(8)| X |Ghi ngày, tháng, năm sinh của người được giám định y khoa, theo định dạng yyyymmdd||ngay_sinh = to_char(dmbenhnhan.ngaysinh,’yyyyMMdd’)<br/><br/>tham chiếu psgiamdinhykhoa.mabn = dmbenhnhan.mabn|
|6|so_cccd|VARCHAR(15)| X |Ghi số căn cước công dân hoặc số chứng minh thư nhân dân hoặc số hộ chiếu của người được giám định y khoa.<br/>Trường hợp không có số căn cước công dân hoặc số chứng minh thư nhân dân hoặc số hộ chiếu thì sử dụng mã tài khoản định danh điện tử.||dmbenhnhan.cmnd<br/><br/>Đổi kiểu dữ liệu thành chuỗi|
|7|ngay_cap_cccd|VARCHAR(8)| X |Ghi ngày cấp chứng minh nhân dân hoặc thẻ căn cước công dân hoặc hộ chiếu của người được giám định y khoa, theo định dạng yyyymmdd||= to_char(dmbenhnhan.ngaycap,’yyyyMMdd’)|
|8|noi_cap_cccd|VARCHAR(1024)| X |Ghi nơi cấp chứng minh nhân dân hoặc thẻ căn cước công dân hoặc hộ chiếu của người được giám định y khoa.||dmbenhnhan.noicap|
|9|dia_chi|VARCHAR(1024)| X |Ghi địa chỉ nơi cư trú hiện tại của người được giám định y khoa.<br/>**Lưu ý**: Ghi cụ thể số nhà hoặc Thôn/Xóm; phường/xã; quận, huyện/thị xã/TP thuộc tỉnh; tinh, thành phố trực thuộc trung ương.||dmbenhnhan.diachi|
|10|matinh_cu_tru|VARCHAR(3)|X  |Mã đơn vị hành chính cấp tỉnh nơi cư trú hiện tại của người bệnh. Ghi theo 02 ký tự cuối của mã đơn vị hành chính của tỉnh, thành phố trực thuộc Trung ương nơi người bệnh cư trú (Quy định tại Phụ lục 1 [Thông tư số 07/2016/TT-BCA](https://congan.quangngai.gov.vn/documents/8878324/9231653/0_20200704221919.pdf/fcd11c17-3599-43f0-ae40-0d5e467bb10d) của Bộ trưởng Bộ Công an).|||
|11|mahuyen_cu_tru|NUMERIC(3,0)|X  |Mã đơn vị hành chính cấp huyện nơi cư trú hiện tại của người bệnh. Ghi mã đơn vị hành chính cấp huyện theo [Quyết định số 124/2004/QĐ-TTg](https://vanban.chinhphu.vn/default.aspx?pageid=27160&docid=14081) ngày 08/7/2004 của Thủ tướng Chính phủ ban hành danh mục mã đơn vị hành chính.|||
|12|maxa_cu_tru|VARCHAR(5)| X |Mã đơn vị hành chính cấp xã nơi cư trú hiện tại của người bệnh. Ghi mã đơn vị hành chính cấp xã theo [Quyết định số 124/2004/QĐ-TTg](https://vanban.chinhphu.vn/default.aspx?pageid=27160&docid=14081) ngày 08/7/2004 của Thủ tướng Chính phủ ban hành danh mục mã đơn vị hành chính.|||
|13|ma_bhxh|VARCHAR(10)|X  |Ghi mã số bảo hiểm xã hội của người được giám định y khoa, tìm kiếm tại địa chỉ: https://baohiemxahoi.gov.vn/Pages/default.aspx||Đổi kiểu dữ liệu thành chuỗi<br/><br/>- Khám ngoại trú: ma_bhxh = substr(psdangky.mathe,6,10) tham chiếu psgiamdinhykhoa.mabn = psdangky.mabn và psgiamdinhykhoa.makb = psdangky.makb<br/>- Nội trú: ma_bhxh = substr(bnnoitru.mathe,6,10) tham chiếu psgiamdinhykhoa.mabn = bnnoitru.mabn và psgiamdinhykhoa.makb = bnnoitru.makb|
|14|ma_the_bhyt|VARCHAR(15)||Ghi mã thẻ BHYT của người được giám định y khoa (nếu có).||- Khám ngoại trú: ma_the_bhyt = psdangky.mathe tham chiếu psgiamdinhykhoa.mabn = psdangky.mabn và psgiamdinhykhoa.makb = psdangky.makb<br/>- Nội trú: ma_the_bhyt = bnnoitru.mathe tham chiếu psgiamdinhykhoa.mabn = bnnoitru.mabn và psgiamdinhykhoa.makb = bnnoitru.makb|
|15|nghe_nghiep|VARCHAR(100)||Ghi nghề nghiệp của người đề nghị khám giám định y khoa (nếu có).||nghe_nghiep = dmnghe.tennghe<br/>Tham chiếu psgiamdinhykhoa.mabn = dmbenhnhan.mabn và dmbenhnhan.manghe = dmnghe.manghe|
|16|dien_thoai|VARCHAR(15)| X |Ghi số điện thoại liên hệ của người đề nghị giám định y khoa||dien_thoai = dmbenhnhan.dienthoai|
|17|ma_doi_tuong|VARCHAR(20)|X  |Ghi mã đối tượng giám định (BB: Bệnh binh; BHXH1L: Hưởng BHXH 1 lần; BNN: Bệnh nghề nghiệp; CĐHH: Chất độc hóa học; KNLĐH: Nghỉ hưu trước tuổi; KNLĐT: Tuất; NKT: Người khuyết tật; NVQS: Khám tuyển nghĩa vụ quân sự; TB: Thương binh; TH: Giám định tổng hợp; TNLĐ: Tai nạn lao động).<br/>**Ghi chú**: Trường hợp một đối tượng mà có từ hai mã đối tượng trở lên thì liệt kê các mã đối tượng, giữa các mã đối tượng cách nhau bằng dấu chấm phẩy ";".||psgiamdinhykhoa.ma_doi_tuong|
|18|kham_giam_dinh|NUMERIC(1,0)| X |Ghi mã khám giám định, trong đó:<br/>- Mã "1": Khám giám định lần đầu;<br/>- Mã "2": Khám giám định lại;<br/>- Mã "3": Khám giám định tái phát;<br/>- Mã "4": Khám phúc quyết (vượt khả năng chuyên môn, hoặc đối tượng không đồng ý, hoặc theo đề nghị của Cục Quản lý KCB/Cục Người có công/BHXH);<br/>- Mã "5": Khám phúc quyết lần cuối;<br/>- Mã "6": Khám bổ sung;<br/>- Mã "7": Khám vết thương còn sót;<br/>- Mã "8": Giám định tổng hợp.||psgiamdinhykhoa.kham_giam_dinh|
|19|so_bien_ban|VARCHAR(200)|X  |Ghi số thứ tự trong biên bản họp hội đồng giám định y khoa.||psgiamdinhykhoa.so_bien_ban|
|20|tyle_ttct_cu|NUMERIC(3,0)||Ghi tỷ lệ (%) tổn thương cơ thể do thương tật, bệnh tật, bệnh nghề nghiệp của lần giám định trước (lần gần nhất) theo kết luận của Hội đồng giám định y khoa.<br/>**Ghi chú**: Trường thông tin này để trống nếu không có tỷ lệ tổn thương cơ thể của lần giám định trước (lần gần nhất).||psgiamdinhykhoa.tyle_ttct_cu|
|21|dang_huong_che_do|NUMERIC(3,0)|X  |Ghi mã chế độ đang hưởng, trong đó: <br/>- Mã "1": Thương binh; <br/>- Mã "2": Bệnh, tật; <br/>- Mã "3": Bệnh nghề nghiệp;<br/>- Mã "4": Tai nạn lao động;<br/>- Mã "5": Chất độc hoá học;<br/>- Mã "6": Bệnh binh;<br/>- Mã "7": Khác (không thuộc một trong các đối tượng quy định từ mã "1" đến mã "6" của trường thông tin này).<br/>**Ghi chú**: <br/>- Trường hợp đang được hưởng cùng lúc nhiều chế độ khác nhau thì ghi mã các chế độ đang được hưởng, phân cách bằng dấu chấm phẩy “;”;<br/>- Trường thông tin này để trống nếu không thuộc một trong các chế độ nêu trên.||psgiamdinhykhoa.dang_huong_che_do|
|22|ngay_chung_tu|VARCHAR(8)|X  |Ghi ngày chứng từ (ngày họp Hội đồng giám định y khoa), theo định dạng yyyymmdd||= to_char(dmbenhnhan.ngay_chung_tu,’yyyyMMdd’)|
|23|so_giay_gioi_thieu|VARCHAR(200)|X  |Ghi số giấy giới thiệu.||psgiamdinhykhoa.so_giay_gioi_thieu|
|24|ngay_de_nghi|VARCHAR(8)|X  |Ghi ngày đề nghị, theo định dạng yyyymmdd||= to_char(dmbenhnhan.ngay_de_nghi,’yyyyMMdd’)|
|25|ma_donvi|VARCHAR(200)| X |Ghi mã cơ quan, đơn vị quản lý hoặc cơ quan, đơn vị giới thiệu đối tượng khám giám định y khoa.||psgiamdinhykhoa.ma_donvi|
|26|gioi_thieu_cua|VARCHAR(1024)|X  |Ghi tên đầy đủ của cơ quan, đơn vị quản lý hoặc cơ quan, đơn vị giới thiệu đối tượng khám giám định y khoa.||psgiamdinhykhoa.gioi_thieu_cua|
|27|ket_qua_kham|VARCHAR|X  |Ghi kết quả khám của Hội đồng Giám định y khoa (được thể hiện trong Biên bản giám định y khoa).||psgiamdinhykhoa.ket_qua_kham|
|28|so_van_ban_can_cu|VARCHAR(200)| X |Ghi số văn bản (Ghi đầy đủ số và ký tự của văn bản) làm căn cứ khám giám định y khoa phù hợp với đối tượng giám định (Ví dụ: Thông tư 34/2012/TTLT-BYT-BLĐTBXH; Thông tư 28/2013/TTLT-BYT-BLDTBXH; Thông tư 20/2016/TTLT-BYT-BLĐTBXH; Thông tư 52/2017/TT-BYT; [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005); [Thông tư số 01/2019/TT-BLĐTBXH](https://vanban.chinhphu.vn/?pageid=27160&docid=196549); Thông tư 45/2014/TTLT-BYT-BLĐTBXH; Nghị định 28/2012/NĐ-CP;...). <br/>Nếu có nhiều văn bản làm căn cứ giám định, kết luận thì ghi đầy đủ các số hiệu văn bản, giữa các số hiệu văn bản phân cách bằng dấu chấm phẩy “;”.||psgiamdinhykhoa.so_van_ban_can_cu|
|29|tyle_ttct_moi|NUMERIC(3,0)| X |Ghi tỷ lệ (%) tổn thương cơ thể do thương tật, bệnh tật, bệnh nghề nghiệp của lần giám định này theo kết luận của Hội đồng giám định y khoa.||psgiamdinhykhoa.tyle_ttct_moi|
|30|tong_tyle_ttct|NUMERIC(3,0)||Ghi tổng tỷ lệ tổn thương cơ thể, do thương tật, bệnh tật, bệnh nghề nghiệp (nếu có) theo kết luận của Hội đồng giám định y khoa.<br/>**Lưu ý**: chỉ ghi trường thông tin này trong trường hợp khám giám định tổng hợp, khám bổ sung, khám vết thương còn sót.||psgiamdinhykhoa.tong_tyle_ttct|
|31|dang_khuyettat|NUMERIC(1,0)||Ghi mã dạng khuyết tật theo quy định về dạng khuyết tật tại Mẫu số 01 ban hành kèm theo [Thông tư số 01/2019/TT-BLĐTBXH](https://vanban.chinhphu.vn/?pageid=27160&docid=196549) ngày 02/01/2019 của Bộ Lao động - Thương binh - Xã hội, trong đó:<br/>- Mã "1": Khuyết tật vận động; <br/>- Mã "2": Khuyết tật nghe, nói; <br/>- Mã "3": Khuyết tật nhìn; <br/>- Mã "4": Khuyết tật thần kinh, tâm thần; <br/>- Mã "5": Khuyết tật trí tuệ; <br/>- Mã "6": Khuyết tật khác. <br/>Trường thông tin này chỉ ghi trong trường hợp khám giám định người khuyết tật.||psgiamdinhykhoa.dang_khuyettat|
|32|muc_do_khuyettat|NUMERIC(1,0)||Ghi mã mức độ khuyết tật theo quy định về mức độ khuyết tật tại Mẫu số 01 ban hành kèm theo [Thông tư số 01/2019/TT-BLĐTBXH](https://vanban.chinhphu.vn/?pageid=27160&docid=196549) ngày 02/01/2019 của Bộ Lao động - Thương Binh - Xã hội, trong đó: <br/>- Mã "1": Thực hiện được; <br/>- Mã "2": Thực hiện được nhưng cần trợ giúp; <br/>- Mã "3": Không thực hiện được; <br/>- Mã "4: Không xác định được.<br/>Trường thông tin này chỉ ghi trong trường hợp khám giám định người khuyết tật.||psgiamdinhykhoa.muc_do_khuyettat|
|33|de_nghi|VARCHAR|X  |Ghi nội dung đề nghị.||psgiamdinhykhoa.de_nghi|
|34|duoc_xacdinh|VARCHAR| X |Ghi ghi chú được xác định, ghi đầy đủ nội dung theo quy định tại khoản 2 Điều 4 [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005): Đối với các trường hợp không tự kiểm soát hoặc không tự thực hiện được các hoạt động đi lại, mặc quần áo, vệ sinh cá nhân và những việc khác phục vụ nhu cầu sinh hoạt cá nhân hằng ngày mà cần có người theo dõi, trợ giúp, chăm sóc hoàn toàn.||psgiamdinhykhoa.duoc_xacdinh|
|35|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần.|||
||ma_lk|VARCHAR(100)|X|Lưu ý: Được lấy từ xml130.checkin.ma_lk|X||
||makb|VARCHAR(20)|X|psgiamdinhykhoa.makb|X||
||mabn|VARCHAR(20)|X|psgiamdinhykhoa.mabn|X||
