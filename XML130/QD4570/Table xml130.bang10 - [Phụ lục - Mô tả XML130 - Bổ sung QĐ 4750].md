<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang10: Chỉ tiêu dữ liệu giấy chứng nhận nghỉ dưỡng thai.**

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
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X||
|2|so_seri|VARCHAR(200)|X |Ghi số Seri chứng từ (Giấy chứng nhận nghỉ dưỡng thai) do cơ sở KBCB quy định theo mẫu tại Phụ lục 6 ban hành kèm theo [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005) của Bộ trưởng Bộ Y tế.|||
|3|so_ct|VARCHAR(200)| X|Ghi số chứng từ phục vụ việc quản lý nội bộ của cơ sở KBCB quy định theo mẫu tại Phụ lục 6 ban hành kèm theo [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005) của Bộ trưởng Bộ Y tế.|||
|4|so_ngay|NUMERIC(3,0)|X |Ghi số ngày nghỉ căn cứ vào tình trạng sức khỏe của người bệnh (SO_NGAY = DEN_NGAY - TU_NGAY).|||
|5|don_vi|VARCHAR(1024)|X |Ghi tên đơn vị của người hưởng.<br/>**Lưu ý**:<br/>- Ghi rõ đơn vị nơi người bệnh làm việc và đóng bảo hiểm xã hội theo thông tin do người đến khám bệnh cung cấp;<br/>- Thực hiện việc ghi giấy chứng nhận nghỉ dưỡng thai theo hướng dẫn tại Phụ lục 6 ban hành kèm theo [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005) của Bộ trưởng Bộ Y tế.|||
|6|chan_doan_rv|VARCHAR| X|Ghi đầy đủ chẩn đoán xác định bệnh chính, bệnh kèm theo và/hoặc các triệu chứng hoặc hội chứng, được bác sỹ ghi trong hồ sơ KBCB tại thời điểm kết thúc KBCB đối với người bệnh.<br/>Lưu ý: Đối với việc ghi chẩn đoán ra viện để phục vụ việc tạo lập giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội thì thực hiện theo hướng dẫn tại [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005) của Bộ trưởng Bộ Y tế, trong đó:<br/>- Nội dung chẩn đoán phải mô tả cụ thể về tình trạng sức khỏe hoặc ghi tên bệnh hoặc mã bệnh.<br/>- Trường hợp mắc bệnh cần chữa trị dài ngày thì ghi mã bệnh; trường hợp chưa có mã bệnh thì ghi đầy đủ tên bệnh. Việc ghi mã bệnh và tên bệnh thực hiện theo quy định tại [Thông tư số 46/2016/TT-BYT](https://chinhphu.vn/default.aspx?pageid=27160&docid=189279) ngày 30 tháng 12 năm 2016 của Bộ trưởng Bộ Y tế ban hành danh mục bệnh dài ngày;<br/>- Trường hợp điều trị dưỡng thai: Ghi rõ cụm từ “dưỡng thai”.||- Khám ngoại trú: chan_doan_rv = psdangky.kqcdoan<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: chan_doan_rv = bnnoitru.kqcdoan + ‘;’ + bnnoitru.kqcdoanp|
|7|tu_ngay|VARCHAR(8)| X|Ghi ngày bắt đầu nghỉ dưỡng thai, theo định dạng yyyymmdd.<br/>**Lưu ý**: Việc ghi ngày bắt đầu được nghỉ phải trùng với ngày người bệnh đến khám.<br/>Ví dụ: Ngày khám là ngày 13 tháng 7 năm 2018 và phải nghỉ 30 ngày thì tại phần số ngày nghỉ để điều trị bệnh ghi là 30 ngày và ghi rõ là từ ngày 13 tháng 7 năm 2018 đến ngày 11 tháng 8 năm 2018).|||
|8|den_ngay|VARCHAR(8)| X|Ghi ngày kết thúc nghỉ dưỡng thai, theo định dạng yyyymmdd|||
|9|ma_ttdv|VARCHAR(10)|  X|Ghi mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được uỷ quyền ký xác nhận giấy chứng nhận nghỉ dưỡng thai.||Được lấy từ tham số ma_ttdv<br/><br/>Đổi kiểu dữ liệu từ số thành chuỗi|
|10|ten_bs|VARCHAR(255)| X|Ghi họ và tên của Trưởng khoa hoặc Phó trưởng khoa hoặc Bác sỹ hành nghề KBCB được uỷ quyền ký tên theo quy định của Thủ trưởng cơ sở KBCB.|||
|11|ma_bs|VARCHAR(200)| X|Ghi mã số định danh y tế (mã số BHXH) của Trưởng khoa hoặc Trưởng phòng hoặc Phó trưởng khoa hoặc Phó trưởng phòng hoặc Bác sỹ hành nghề KBCB ký tên theo quy định của Thủ trưởng cơ sở KBCB.|||
|12|ngay_ct|VARCHAR(8)||Ghi ngày cấp chứng từ, theo định dạng yyyymmdd|||
|13|du_phong|VARCHAR||Bổ sung trường mới: Trường dữ liệu dự phòng khi cần thiết.|||
||makb|VARCHAR(20)|X|bnnoitru.makb|X||
||mabn|VARCHAR(20)|X|bnnoitru.mabn|X||
