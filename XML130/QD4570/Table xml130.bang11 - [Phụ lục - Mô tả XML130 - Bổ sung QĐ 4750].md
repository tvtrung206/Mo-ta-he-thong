<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang11: Chỉ tiêu dữ liệu giấy chứng nhận nghỉ hưởng bảo hiểm xã hội.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Dữ liệu bảng này phải phát sinh ở table `current.nghiom`. [^2024-06-30-01]

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X||
|2|so_ct|VARCHAR(200)| X|Ghi số chứng từ, là mã lưu trữ giấy chứng nhận nghỉ việc hưởng BHXH tại cơ sở KBCB.||`=nghiom.makb`|
|3|so_seri|VARCHAR(200)| X |Ghi số định danh chứng từ (Giấy chứng nhận nghỉ việc hưởng BHXH) của mỗi đợt điều trị theo quy định của cơ sở KBCB.||`=nghiom.sophieu` [^2024-06-30-02]|
|4|so_kcb|VARCHAR(200)| X |Ghi số chứng từ phục vụ việc quản lý nội bộ của cơ sở KBCB theo Phụ lục 07 [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||`=nghiom.makb` + `/KCB`|
|5|don_vi|VARCHAR(1024)|  X|Ghi tên đơn vị của người hưởng BHXH.<br/>**Lưu ý**:<br/>- Ghi rõ đơn vị nơi người bệnh làm việc và đóng bảo hiểm xã hội theo thông tin do người đến khám bệnh cung cấp;<br/>- Trường hợp con ốm thì ghi tên đơn vị mà người cha (bố) hoặc mẹ đang làm việc và đóng bảo hiểm xã hội theo thông tin do người đến khám bệnh cung cấp. Thực hiện việc ghi giấy chứng nhận nghỉ việc hưởng BHXH theo hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||`=nghiom.noict`|
|6|ma_bhxh|VARCHAR(10)|  X|Ghi mã số BHXH của người bệnh.||`=nghiom.sobhxh`<br/>Đổi kiểu dữ liệu thành chuỗi|
|7|ma_the_bhyt|VARCHAR||Ghi mã thẻ BHYT của người bệnh do cơ quan BHXH cấp.<br/>**Lưu ý**:<br/>- Khi tiếp đón người bệnh, cơ sở KBCB có trách nhiệm tra cứu trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để kiểm tra thông tin thẻ BHYT. Trường hợp cấp cứu mà người bệnh hoặc thân nhân người bệnh không xuất trình được thẻ BHYT ngay thì cơ sở KBCB tra cứu thông tin thẻ BHYT trước khi người bệnh ra viện.<br/>- Đối với thẻ BHYT của các đối tượng có các mã QN, HC, LS, XK, CY, CA do BHXH Bộ Quốc phòng, BHXH Bộ Công an cấp: Tra cứu để kiểm tra thời hạn sử dụng của thẻ BHYT trong trường hợp các đối tượng này không còn phục vụ trong lực lượng Quân đội, Công an, Cơ yếu.<br/>- Trường hợp trong thời gian điều trị, người bệnh được cấp thẻ BHYT mới có thay đổi thông tin liên quan đến mã thẻ thì ghi tiếp mã thẻ mới (mỗi mã thẻ gồm có 15 ký tự), giữa các mã thẻ cách nhau bằng dấu chấm phẩy “;”;<br/>- Trường hợp người bệnh chưa có thẻ BHYT, cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.<br/>- Trường hợp người bệnh không KBCB BHYT thì để trống trường thông tin này.||`=nghiom.mathe`|
|8|chan_doan_rv|VARCHAR|  X|Ghi đầy đủ chẩn đoán xác định bệnh chính, bệnh kèm theo và/hoặc các triệu chứng hoặc hội chứng, được bác sỹ ghi trong hồ sơ KBCB tại thời điểm kết thúc KBCB đối với người bệnh.<br/>Lưu ý: Đối với việc ghi chẩn đoán ra viện để phục vụ việc tạo lập giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội thì thực hiện theo hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế, trong đó:<br/>- Nội dung chẩn đoán phải mô tả cụ thể về tình trạng sức khỏe hoặc ghi tên bệnh hoặc mã bệnh.<br/>- Trường hợp mắc bệnh cần chữa trị dài ngày thì ghi mã bệnh; trường hợp chưa có mã bệnh thì ghi đầy đủ tên bệnh. Việc ghi mã bệnh và tên bệnh thực hiện theo quy định tại [Thông tư số 46/2016/TT-BYT](https://chinhphu.vn/default.aspx?pageid=27160&docid=189279) ngày 30 tháng 12 năm 2016 của Bộ trưởng Bộ Y tế ban hành danh mục bệnh dài ngày;<br/>- Trường hợp điều trị dưỡng thai: Ghi rõ cụm từ “dưỡng thai”.||`=nghiom.lydo`|
|9|pp_dieutri|VARCHAR| X |Ghi phương pháp điều trị theo đúng hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||-Đối với người bệnh khám ngoại trú: `pp_dieutri = "Ngoại trú"`<br/>-Đối với người bệnh nội trú: `pp_dieutri = dmppdt.diengiai` (tham chiếu thông qua `bnnoitru.mappdt`)|
|10|ma_dinh_chi_thai|NUMERIC(1,0)||Ghi mã "1" là đình chỉ thai nghén, mã "0" là không đình chỉ thai nghén.<br/>Trường hợp đình chỉ thai nghén bắt buộc nhập thông tin vào trường thông tin tuổi thai (TUOI_THAI) và trường thông tin nguyên nhân đình chỉ thai nghén (NGUYENNHAN_DINHCHI).|||
|11|nguyennhan_dinhchi|VARCHAR|Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI là mã "1". |Ghi nguyên nhân đình chỉ thai nghén.<br/>**Lưu ý**: Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI là mã "1".|||
|12|tuoi_thai|NUMERIC(2,0)| Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI là mã "1". |Ghi tuổi thai thực tế (theo tuần), trong đó tuổi thai luôn luôn lớn hơn hoặc bằng 1 và nhỏ hơn hoặc bằng tuổi 42 tuần tuổi.<br/>**Lưu ý**: Bắt buộc ghi trường thông tin này khi MA_DINH_CHI_THAI = 1.|||
|13|so_ngay_nghi|NUMERIC(3,0)|  X |Ghi số ngày nghỉ căn cứ vào tình trạng sức khỏe của người bệnh.<br/>**Lưu ý**: Việc quyết định số ngày nghỉ phải căn cứ vào tình trạng sức khỏe của người bệnh nhưng tối đa không quá 30 ngày cho một lần cấp giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội. Riêng trường hợp người bệnh điều trị bệnh lao theo chương trình chống lao quốc gia thì thời gian nghỉ tối đa không quá 180 ngày cho một lần cấp giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội. <br/>Trường hợp người lao động bị sẩy thai, phá thai, nạo, hút thai, thai chết lưu mà tuổi thai từ 13 tuần tuổi trở lên thì thời gian nghỉ tối đa theo quy định của Luật bảo hiểm xã hội nhưng không quá 50 ngày cho một lần cấp giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội.||`=nghiom.lydo`|
|14|tu_ngay|VARCHAR(8)|  X |Ghi ngày bắt đầu hưởng chế độ, theo định dạng yyyymmdd và phải trùng khớp với ngày người bệnh đến khám.||`=nghiom.tungay`|
|15|den_ngay|VARCHAR(8)|  X |Ghi ngày kết thúc hưởng chế độ, theo định dạng yyyymmdd||`=nghiom.denngay`|
|16|ho_ten_cha|VARCHAR(255)||Ghi họ và tên cha (bố) của người bệnh (nếu có) trong trường hợp người bệnh là trẻ em dưới 07 tuổi theo quy định tại Phụ lục 7 [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế. Trường hợp không có cha (bố) thì để trống trường thông tin này.|||
|17|ho_ten_me|VARCHAR(255)||Ghi họ và tên mẹ của người bệnh (nếu có) trong trường hợp người bệnh là trẻ em dưới 07 tuổi theo quy định tại Phụ lục 7 [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế. Trường hợp không có mẹ thì để trống trường thông tin này.|||
|18|ma_ttdv|VARCHAR(10)|  X|Ghi mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được người đứng đầu cơ sở KBCB ủy quyền được ký và đóng dấu của cơ sở KBCB đó.||Được lấy từ `tham số ma_ttdv`<br/><br/>Đổi kiểu dữ liệu từ số thành chuỗi|
|19|ma_bs|VARCHAR(200)| X  |Ghi mã số định danh y tế (mã số BHXH) của Trưởng khoa hoặc Trưởng phòng hoặc Phó trưởng khoa hoặc Phó trưởng phòng hoặc Bác sỹ hành nghề KBCB ký tên theo quy định của Thủ trưởng cơ sở KBCB.||`= dmnhanvien.sobhxh`[^2024-07-26]<br/>Trong đó tham chiếu: `nghiom.madv = dmdonvi.madv AND dmdonvi.manv_truongkhoa = dmnhanvien.manv`|
|20|ngay_ct|VARCHAR(8)|  X |Ghi ngày cấp chứng từ (Giấy chứng nhận nghỉ việc hưởng BHXH), theo định dạng yyyymmdd và phải trùng với ngày người lao động đến khám bệnh. Trường hợp đợt khám bệnh kéo dài từ 2 ngày trở lên thì ngày, tháng, năm cấp phải trùng với ngày cuối cùng của đợt người lao động đến khám bệnh và cần được chỉ định nghỉ ngoại trú.||`=nghiom.ngaylap`|
|21|ma_the_tam|VARCHAR(15)||Ghi mã thẻ BHYT tạm thời của trẻ em sinh ra hoặc của người hiến tạng nhưng chưa được cơ quan BHXH cấp thẻ BHYT. Cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.||- Khám ngoại trú xét, nếu `psdangky.thetam = 1` thì: `ma_the_tam =  psdangky.mathe`<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: `bnnoitru.thetam = 1` thì: `ma_the_tam = bnnoitru.mathe (đối với thẻ 1)` hoặc `ttcon.thetam = 1` thì: `ma_the_tam = ttcon.mathe (đối với thẻ 2)`|
|22|mau_so|NUMERIC(5,0)||Các cơ sở KBCB sử dụng chuỗi CT07 để xác định đây là Giấy nghỉ việc hưởng bảo hiểm xã hội. Mẫu số mặc định để trống không điền thì hệ thống tự điền CT07.||`=nghiom.quyen`|
|23|du_phong|VARCHAR||Bổ sung trường mới: Trường dữ liệu dự phòng khi cần thiết.|||
||makb|VARCHAR(20)|X|bnnoitru.makb|X||
||mabn|VARCHAR(20)|X|bnnoitru.mabn|X||

[^2024-07-26]: Thay đổi ngày 26/07/2024: Thay đổi điều kiện xuất dữ liệu cột `ma_bs`.
[^2024-06-30-01]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-30-02]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu chi tiết cho các cột.
