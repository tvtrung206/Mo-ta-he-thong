<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang9: Chỉ tiêu dữ liệu giấy chứng sinh.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Ngày cập nhật: **12/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X|Các dữ liệu ở table này join vào current.ttcon để lấy thông tin của trẻ sơ sinh. Không áp dụng khám ngoại trú và BA ngoại trú quyết toán cuối đợt.|
|2|ma_bhxh_nnd|VARCHAR(10)||Ghi mã số BHXH người nuôi dưỡng (nếu có).||Đổi kiểu dữ liệu từ số thành chuỗi<br/><br/>10 ký tự cuối bnnoitru.mathe|
|3|ma_the_nnd|VARCHAR(15)||Ghi mã thẻ BHYT người nuôi dưỡng (nếu có).|||
|4|ho_ten_nnd|VARCHAR(255)| X|Ghi họ và tên của mẹ hoặc của người nuôi dưỡng.||ho_ten_nnd = dmbenhnhan.holot + “ ” + dmbenhnhan.ten<br/><br/>Trong đó tham chiếu bnnoitru.mabn = dmbenhnhan.mabn|
|5|ngaysinh_nnd|VARCHAR(8)| X|Ghi ngày sinh của mẹ hoặc người nuôi dưỡng, định dạng yyyymmdd||ngaysinh_nnd = to_char(dmbenhnhan.ngaysinh,'yyyyMMdd')<br/><br/>Trong đó tham chiếu bnnoitru.mabn = dmbenhnhan.mabn|
|6|ma_dantoc_nnd|VARCHAR(2)| X|Ghi mã dân tộc của mẹ hoặc người nuôi dưỡng theo Danh mục các dân tộc Việt Nam ban hành kèm theo [Quyết định số 121-TCTK/PPCĐ](http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html) ngày 02 tháng 3 năm 1979 của Tổng cục trưởng Tổng cục Thống kê để điền chi tiết). Tra cứu mã dân tộc tại đường link: http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html ||Đổi kiểu dữ liệu từ số thành chuỗi|
|7|so_cccd_nnd|VARCHAR(15)| X|Ghi số chứng minh nhân dân hoặc số căn cước công dân hoặc số hộ chiếu của mẹ hoặc người nuôi dưỡng. ||Đổi kiểu dữ liệu từ số thành chuỗi|
|8|ngaycap_cccd_nnd|VARCHAR(8)|X |Ghi ngày cấp chứng minh nhân dân hoặc căn cước công dân hoặc hộ chiếu của mẹ hoặc người nuôi dưỡng, định dạng yyyymmdd|||
|9|noicap_cccd_nnd|VARCHAR(1024)|X |Ghi nơi cấp chứng minh nhân dân hoặc căn cước công dân hoặc hộ chiếu của mẹ hoặc người nuôi dưỡng.|||
|10|noi_cu_tru_nnd|VARCHAR(1024)|X |Ghi địa chỉ nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. <br/>**Lưu ý**: <br/>- Nếu là người Việt Nam: Ghi địa chỉ nơi cư trú theo địa danh 4 cấp: Thôn/bản, xã/phường/thị trấn, quận/huyện/ thành phố thuộc tỉnh, tỉnh/thành phố trực thuộc trung ương;<br/>- Trường hợp người nước ngoài có địa chỉ nơi cư trú tại Việt Nam thì ghi giống như người Việt Nam;<br/>- Trường hợp người nước ngoài không có địa chỉ nơi cư trú tại Việt Nam nhưng sinh đẻ tại cơ sở y tế của Việt Nam thì ghi tên tỉnh/thành phố/bang và quốc gia nơi họ đang sinh sống.|||
|11|ma_quoctich|VARCHAR(3)| X|Ghi mã quốc tịch của mẹ hoặc người nuôi dưỡng theo quy định tại Phụ lục 2 [Thông tư số 07/2016/TT-BCA](https://congan.quangngai.gov.vn/documents/8878324/9231653/0_20200704221919.pdf/fcd11c17-3599-43f0-ae40-0d5e467bb10d) ngày 01 tháng 2 năm 2016 của Bộ trưởng Bộ Công an.||Đổi kiểu dữ liệu từ số thành chuỗi|
|12|matinh_cu_tru|VARCHAR(3)| X|Mã đơn vị hành chính cấp tỉnh nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. Ghi theo 02 ký tự cuối của mã đơn vị hành chính của tỉnh, thành phố trực thuộc Trung ương nơi người bệnh cư trú (Quy định tại Phụ lục 1 [Thông tư số 07/2016/TT-BCA](https://congan.quangngai.gov.vn/documents/8878324/9231653/0_20200704221919.pdf/fcd11c17-3599-43f0-ae40-0d5e467bb10d) ngày 01 tháng 2 năm 2016 của Bộ trưởng Bộ Công an).||`=current.dmxa4750.matinh`|
|13|mahuyen_cu_tru|NUMERIC(3,0)| X|Mã đơn vị hành chính cấp huyện nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. Ghi mã đơn vị hành chính cấp huyện theo [Quyết định số 124/2004/QĐ-TTg](https://vanban.chinhphu.vn/default.aspx?pageid=27160&docid=14081) ngày 08/7/2004 của Thủ tướng Chính phủ ban hành danh mục mã đơn vị hành chính.||`=current.dmxa4750.mahuyen`|
|14|maxa_cu_tru|VARCHAR(5)|X |Mã đơn vị hành chính cấp xã nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. Ghi mã đơn vị hành chính cấp xã theo [Quyết định số 124/2004/QĐ-TTg](https://vanban.chinhphu.vn/default.aspx?pageid=27160&docid=14081) ngày 08/7/2004 của Thủ tướng Chính phủ ban hành danh mục mã đơn vị hành chính.||`=current.dmxa4750.maxa`|
|15|ho_ten_cha|VARCHAR(255)||Ghi họ và tên cha (bố) của trẻ được cấp giấy chứng sinh.||ho_ten_cha = ttcon.hotencha|
|16|ma_the_tam|VARCHAR(15)||Ghi mã thẻ BHYT tạm thời của người con. Cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.||- Khám ngoại trú xét, nếu psdangky.thetam = 1 thì: ma_the_tam =  psdangky.mathe<br/>- Nội trú/BA ngoại trú thanh toán cuối đợt: bnnoitru.thetam = 1 thì: ma_the_tam = bnnoitru.mathe (đối với thẻ 1) hoặc ttcon.thetam = 1 thì: ma_the_tam = ttcon.mathe (đối với thẻ 2)|
|17|ho_ten_con|VARCHAR(255)||Ghi họ và tên dự định đặt cho con (nếu có).||ho_ten_con = ttcon.tendudinh|
|18|gioi_tinh_con|NUMERIC(1,0)|X|Ghi giới tính con, trong đó:<br/>- Mã "1": Nam; <br/>- Mã "2": Nữ; <br/>- Mã "3": Chưa xác định.||gioi_tinh_con = ttcon.gioitinh|
|19|so_con|NUMERIC(2,0)| X|Ghi số lượng con trong lần sinh này.||so_con = ttcon.socon|
|20|lan_sinh|NUMERIC(2,0)| X|Ghi số lần sinh con (tính cả lần sinh này).|||
|21|so_con_song|NUMERIC(2,0)|X |Ghi số con hiện đang sống (tính cả trẻ sinh ra lần này).|||
|22|can_nang_con|NUMERIC(10,0)|X |Ghi số cân nặng của con, tính theo gram (ký hiệu là: g) (ví dụ: 3.6 kg = 3600g).||can_nang_con = ttcon.cannang|
|23|ngay_sinh_con|VARCHAR(12)| X|Ghi ngày sinh con theo định dạng yyyymmddHHMM.||ngay_sinh_con = to_char(ttcon.ngaysinh, 'yyyyMMddHH24:mi')|
|24|noi_sinh_con|VARCHAR(1024)|  X|Ghi địa chỉ nơi con được sinh ra. <br/>**Lưu ý**:<br/>- Trường hợp trẻ em được sinh ra tại bệnh viện, thì ghi tên bệnh viện và địa danh hành chính nơi trẻ em được sinh ra. Ví dụ: bệnh viện đa khoa tỉnh Nam Định);<br/>- Trường hợp trẻ em được sinh tại cơ sở y tế khác thì ghi tên cơ sở y tế và địa danh hành chính 3 cấp nơi trẻ em sinh ra (Ví dụ: Trạm y tế xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định);<br/>- Trường hợp trẻ em được sinh tại nhà thì ghi địa chỉ nhà và địa danh 3 cấp: cấp xã/phường, quận/huyện, tỉnh/thành phố trực thuộc trung ương <br/>Ví dụ: sinh tại nhà ở xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định;<br/>- Trường hợp trẻ em được sinh ra tại nơi khác, ngoài cơ sở KBCB thì cũng ghi nơi trẻ em được sinh ra và địa danh 3 cấp hành chính.<br/>Ví dụ: đẻ trên đường đi, tại xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định.<br/>- Trường hợp trẻ em bị bỏ rơi thì ghi rõ trẻ bị bỏ rơi và nơi tìm thấy trẻ, với địa danh 3 cấp hành chính.<br/>Ví dụ: trẻ bị bỏ rơi tại xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định.||noi_sinh_con = tham số [tenbv]|
|25|tinh_trang_con|VARCHAR|  X|Ghi rõ tình trạng của trẻ tại thời điểm làm Giấy chứng sinh: khỏe mạnh, yếu, dị tật hoặc các biểu hiện liên quan đến sức khỏe khác (nếu có).<br/>**Lưu ý**: Nếu trẻ bị dị dạng, dị tật, ghi cụ thể loại dị dạng, dị tật, kể cả khuyết tật về hình thái của trẻ nếu phát hiện được.||tinh_trang_con = ttcon.suckhoe|
|26|sinhcon_phauthuat|NUMERIC(1,0)|  X|Ghi:<br/>- Mã "1": sinh con phải phẫu thuật;<br/>- Mã "0": sinh con không phải phẫu thuật.|||
|27|sinhcon_duoi32tuan|NUMERIC(1,0)|  X|Ghi:<br/>- Mã "1": sinh con dưới 32 tuần tuổi;<br/>- Mã "0" là không sinh con dưới 32 tuần tuổi.|||
|28|ghi_chu|VARCHAR|  X|Trường hợp sinh con phải phẫu thuật hoặc sinh con dưới 32 tuần tuổi hoặc vừa sinh con dưới 32 tuần tuổi lại vừa phải phẫu thuật thì trong phần ghi chú phải ghi rõ một trong các nội dung sau "Sinh con phải phẫu thuật" hoặc "Sinh con dưới 32 tuần tuổi" hoặc "Phẫu thuật, sinh con dưới 32 tuần tuổi".|||
|29|nguoi_do_de|VARCHAR(255)|  X|Ghi họ và tên người đỡ đẻ.||nguoi_do_de = dmnhanvien.holot + “ ” + dmnhanvien.ten<br/><br/>Trong đó, tham chiếu ttcon.nguoidd = dmnhanvien.manv|
|30|nguoi_ghi_phieu|VARCHAR(255)|  X|Ghi họ và tên người ghi phiếu.||nguoi_do_de = dmnhanvien.holot + “ ” + dmnhanvien.ten<br/><br/>Trong đó, tham chiếu ttcon.taikhoan = dmnhanvien.taikhoan|
|31|ngay_ct|VARCHAR(8)| X |Ghi ngày cấp chứng từ (Giấy chứng sinh), định dạng yyyymmdd, ghi theo ngày dương lịch.||ngay_ct = to_char(ttcon.ngaychinh, 'yyyyMMdd')|
|32|so|VARCHAR(200)| X |Ghi số của chứng từ (Giấy chứng sinh) tại cơ sở KBCB.||so = ttcon.so|
|33|quyen_so|VARCHAR(200)|  X|Ghi quyển số của chứng từ (Giấy chứng sinh) tại cơ sở KBCB.||quyen_so = ttcon.quyen|
|34|ma_ttdv|VARCHAR(10)|  X|Ghi mã số định danh y tế (mã số BHXH) của Thủ trưởng cơ sở KBCB cấp giấy chứng sinh.||Được lấy từ tham số ma_ttdv<br/><br/>Đổi kiểu dữ liệu từ số thành chuỗi|
|35|du_phong|VARCHAR||Bổ sung trường mới: Trường dữ liệu dự phòng khi cần thiết.|||
||makb|VARCHAR(20)|X|bnnoitru.makb|X||
||mabn|VARCHAR(20)|X|bnnoitru.mabn|X||
