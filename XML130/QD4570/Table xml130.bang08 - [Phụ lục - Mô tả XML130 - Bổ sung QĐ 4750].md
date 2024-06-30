<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang8: Chỉ tiêu dữ liệu tóm tắt hồ sơ bệnh án.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Khi giá trị cột `MA_LOAI_KCB` ở [xml130.bang1](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang01%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md) `IN ('02','03','09')` [^2024-06-30-01]

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X|Theo 4210|
|2|ma_loai_kcb|VARCHAR(2)|X|Ghi mã hình thức KBCB, trong đó:<br/>- Mã "02": Điều trị ngoại trú; <br/>- Mã "03": Điều trị nội trú; <br/>- Mã "04": Điều trị nội trú ban ngày; ||Đổi kiểu dữ liệu từ số thành chuỗi|
|3|ho_ten_cha|VARCHAR(255)||Ghi họ và tên cha (bố) theo hồ sơ bệnh án của người bệnh (nếu có).||Xét `psdangky.loaiqh` có chứa các từ `“cha”, “ba”` thì `ho_ten_cha = psdangky.hotenqh`|
|4|ho_ten_me|VARCHAR(255)||Ghi họ và tên mẹ theo hồ sơ bệnh án của người bệnh (nếu có).||Xét `psdangky.loaiqh` có chứa các từ `“mẹ”, “má”` thì `ho_ten_me = psdangky.hotenqh`|
|5|nguoi_giam_ho|VARCHAR(255)||Ghi họ và tên người giám hộ theo hồ sơ bệnh án của người bệnh (nếu có).||`= psdangky.hotenqh` [^2024-06-30-02]|
|6|don_vi|VARCHAR(1024)||Ghi tên đơn vị của người hưởng.<br/>**Lưu ý**:<br/>- Ghi rõ đơn vị nơi người bệnh làm việc và đóng bảo hiểm xã hội theo thông tin do người đến khám bệnh cung cấp;<br/>- Trường hợp con ốm thì ghi tên đơn vị mà người cha (bố) hoặc mẹ đang làm việc và đóng bảo hiểm xã hội theo thông tin do người đến khám bệnh cung cấp. Thực hiện việc ghi giấy chứng nhận nghỉ việc hưởng BHXH theo hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||`= dmbenhnhan.noict`|
|7|ngay_vao|VARCHAR(12)|X|Ghi thời điểm người bệnh đến KBCB, gồm 12 ký tự, theo định dạng yyyymmddHHMM.<br/>Ví dụ: người bệnh đến KBCB lúc 15 giờ 20 phút ngày 31/03/2017 được hiển thị là: 201703311520.||`= psdangky.ngaydk` [^2024-06-30-03]|
|8|ngay_ra|VARCHAR(12)|X|Ghi thời điểm người bệnh kết thúc điều trị nội trú, kết thúc điều trị nội trú ban ngày, kết thúc điều trị ngoại trú hoặc kết thúc khám bệnh, gồm 12 ký tự theo định dạng yyyymmddHHMM.<br/>Ví dụ: Thời điểm người bệnh kết thúc điều trị lúc 09 giờ 20 phút ngày 05/04/2022, khi đó được hiển thị là: 202204050920. <br/>**Lưu ý**:<br/>- Trường hợp khám bệnh (MA_LOAI_KCB = 01) thì ghi thời điểm kết thúc lần khám bệnh;<br/>- Trường hợp điều trị ngoại trú (MA_LOAI_KCB = 02), điều trị ngoại trú các bệnh mạn tính dài ngày liên tục trong năm (MA_LOAI_KCB = 05), nhận thuốc theo hẹn (không khám bệnh) (MA_LOAI_KCB = 07): Ghi ngày kết thúc của đợt KBCB (là ngày cuối cùng sử dụng thuốc hoặc dịch vụ theo chỉ định của bác sỹ), gồm 02 ký tự giờ + 02 ký tự phút và mặc định là 2359 (Thời điểm cuối cùng của ngày kết thúc đợt KBCB); <br/>- Trường hợp điều trị ngoại trú các bệnh mạn tính dài ngày liên tục trong năm (MA_LOAI_KCB = 08): Ghi thời điểm kết thúc của đợt KBCB (Ví dụ: Trường hợp chạy thận nhân tạo thì ghi ngày cuối cùng của đợt chạy thận nhân tạo);<br/>- Trường hợp người bệnh được chuyển tuyến đến cơ sở KBCB khác thì thời điểm người bệnh ra viện bằng thời điểm người bệnh được chuyển tuyến.||`= bnnoitru.ngayrv` [^2024-06-30-04]|
|9|chan_doan_vao|VARCHAR| X|Ghi chẩn đoán của cơ sở KBCB ở thời điểm tiếp nhận người bệnh (Chẩn đoán sơ bộ).||`= psdangky.cdoantd`|
|10|chan_doan_rv|VARCHAR|  X|Ghi đầy đủ chẩn đoán xác định bệnh chính, bệnh kèm theo và/hoặc các triệu chứng hoặc hội chứng, được bác sỹ ghi trong hồ sơ KBCB tại thời điểm kết thúc KBCB đối với người bệnh.<br/>**Lưu ý**: Đối với việc ghi chẩn đoán ra viện để phục vụ việc tạo lập giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội thì thực hiện theo hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế, trong đó:<br/>- Nội dung chẩn đoán phải mô tả cụ thể về tình trạng sức khỏe hoặc ghi tên bệnh hoặc mã bệnh.<br/>- Trường hợp mắc bệnh cần chữa trị dài ngày thì ghi mã bệnh; trường hợp chưa có mã bệnh thì ghi đầy đủ tên bệnh. Việc ghi mã bệnh và tên bệnh thực hiện theo quy định tại [Thông tư số 46/2016/TT-BYT](https://chinhphu.vn/default.aspx?pageid=27160&docid=189279) ngày 30 tháng 12 năm 2016 của Bộ trưởng Bộ Y tế ban hành danh mục bệnh dài ngày;<br/>- Trường hợp điều trị dưỡng thai: Ghi rõ cụm từ “dưỡng thai”||`= bnnoitru.kqcdoan + ‘;’ + bnnoitru.kqcdoanp` [^2024-06-30-05]|
|11|qt_benhly|VARCHAR|  X|Ghi quá trình bệnh lý và diễn biến lâm sàng.||`= bnnoitru.dienbien`|
|12|tomtat_kq|VARCHAR|  X|Ghi tóm tắt kết quả xét nghiệm cận lâm sàng có giá trị chẩn đoán.||`= bnnoitru.tomtat_kq` [^2024-06-30-06]|
|13|pp_dieutri|VARCHAR|  X|Ghi phương pháp điều trị theo đúng hướng dẫn tại [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.||- Đối với khám bệnh ngoại trú/toa nội trú xuất viện ghi: `pp_dieu_tri = "Ngoại khoa"`<br/><br/>- Đối với người bệnh nội trú/BA ngoại trú quyết toán cuối đợt: `pp_dieu_tri = dmppdt.diengiai` (tham chiếu thông qua `bnnoitru.mappdt`) [^2024-06-30-07]|
|14|ngay_sinhcon|VARCHAR(8)||Trường hợp con chết sau khi sinh thì nhập ngày, tháng, năm sinh của con, theo định dạng yyyymmdd|||
|15|ngay_conchet|VARCHAR(8)||Trường hợp con chết sau khi sinh thì nhập ngày, tháng, năm con chết, theo định dạng yyyymmdd|||
|16|so_conchet|NUMERIC(2,0)||Trường hợp con chết sau khi sinh thì nhập số con bị chết.|||
|17|ket_qua_dtri|NUMERIC(1,0)|X |Ghi mã kết quả điều trị, trong đó:<br/>- Mã "1": Khỏi; <br/>- Mã "2": Đỡ; <br/>- Mã "3": Không thay đổi; <br/>- Mã "4": Nặng hơn; <br/>- Mã "5": Tử vong; <br/>- Mã "6": Tiên lượng nặng xin về; <br/>- Mã "7": Chưa xác định (không thuộc một trong các mã kết quả điều trị nêu trên).<br/>- Mã "8": Tử vong ngoại viện.||Dựa vào giá trị cột `bnnoitru.makq`, xét: [^2024-06-30-08]<br/><table border="1" cellspacing="0" cellpadding="0" width = 100%>  <tr>    <td width=20% valign="top"><p align="center"><strong>bnnoitru.makq</strong></p></td>    <td width=20% valign="top"><p align="center"><strong>ket_qua_dtri</strong></p></td>  <td width=60% valign="top"><p align="center"><strong>Diễn giải</strong></p></td></tr>  <tr>    <td valign="top">01</td>    <td valign="top">1</td><td valign="top"><p>Khỏi</p></td>  </tr><tr>    <td valign="top">02</td>    <td valign="top">2</td><td valign="top"><p>Đỡ</p></td></tr><tr>    <td valign="top">03</td>    <td valign="top">3</td><td valign="top"><p>Không thay đổi</p></td></tr><tr>    <td valign="top">04</td>    <td valign="top">4</td><td valign="top"><p>Nặng hơn</p></td></tr><tr>    <td valign="top">05</td>    <td valign="top">5</td><td valign="top"><p>Tử vong</p></td>  </tr></table>|
|18|ghi_chu|VARCHAR(n)||Trường thông tin này chỉ áp dụng đối với trường hợp người mất hoặc bị hạn chế năng lực hành vi dân sự hoặc trẻ em dưới 16 tuổi phải ghi đầy đủ họ, tên của cha (bố) hoặc của mẹ hoặc người giám hộ của người bệnh theo quy định tại Phụ lục 4 ban hành kèm theo [Thông tư số 18/2022/TT-BYT](https://vanban.chinhphu.vn/?pageid=27160&docid=207234) của Bộ trưởng Bộ Y tế.|||
|19|ma_ttdv|VARCHAR(10)|X  |Ghi mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được người đứng đầu cơ sở KBCB ủy quyền được ký và đóng dấu của cơ sở KBCB đó.||Được lấy từ tham số `ma_ttdv`<br/><br/>Đổi kiểu dữ liệu từ số thành chuỗi|
|20|ngay_ct|VARCHAR(8)| X  |Ghi ngày chứng từ (Tóm tắt hồ sơ bệnh án), theo định dạng yyyymmdd, là ngày Trưởng khoa hoặc Trưởng phòng hoặc Phó trưởng khoa hoặc Phó trưởng phòng cấp tóm tắt hồ sơ bệnh án.||`= ngay_ra`|
|21|ma_the_tam|VARCHAR(15)||Ghi mã thẻ BHYT tạm thời của trẻ em sinh ra hoặc của người hiến tạng nhưng chưa được cơ quan BHXH cấp thẻ BHYT. Cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.||Nếu `bnnoitru.thetam = 1` thì: `ma_the_tam = bnnoitru.mathe (đối với thẻ 1)` hoặc `ttcon.thetam = 1` thì: `ma_the_tam = ttcon.mathe (đối với thẻ 2)` [^2024-06-30-09]|
|22|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần thiết.|||
||mabn|VARCHAR(20)|X|psdangky.mabn|X||
||makb|VARCHAR(20)|X|psdangky.makb|X||

[^2024-06-30-01]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-30-02]: Thay đổi ngày 30/06/2024: Thay đổi điều kiện cột `nguoi_giam_ho`.
[^2024-06-30-03]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện cột `ngay_vao`.
[^2024-06-30-04]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện cột `ngay_ra`.
[^2024-06-30-05]: Thay đổi ngày 30/06/2024: Thay đổi điều kiện cột `chan_doan_rv`.
[^2024-06-30-06]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện cột `tomtat_kq`.
[^2024-06-30-07]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu cột `pp_dieutri`.
[^2024-06-30-08]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện cột `ket_qua_dtri`.
[^2024-06-30-09]: Thay đổi ngày 30/06/2024: Thay đổi điều kiện cột `ma_the_tam`.
