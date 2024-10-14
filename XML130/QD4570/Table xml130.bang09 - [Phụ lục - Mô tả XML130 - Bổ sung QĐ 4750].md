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
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Dữ liệu bảng này phải phát sinh ở table `current.ttcon`. [^2024-06-30]. Bổ sung điều kiện là ***`loaitt=0`*** [^2024-10-04]

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Diễn giải|Ghi chú[^2024-10-14-01]|Kiểu dữ liệu|Bắt buộc|Index|
|:-------:|-------|-------|-------|:-------:|:-------:|:-------:|
|1|ma_lk|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|Các dữ liệu ở table này join vào `current.ttcon` để lấy thông tin của trẻ sơ sinh. Không áp dụng khám ngoại trú và BA ngoại trú quyết toán cuối đợt.|VARCHAR(100)|X|X|
|2|ma_bhxh_nnd|Ghi mã số BHXH người nuôi dưỡng (nếu có).|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ma_bhxh_nnd = psnguoinuoiduong.ma_bhxh_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ma_bhxh_nnd = 10 ký tự cuối bnnoitru.mathe`|VARCHAR(10)|||
|3|ma_the_nnd|Ghi mã thẻ BHYT người nuôi dưỡng (nếu có).|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ma_the_nnd = psnguoinuoiduong.ma_the_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ma_the_nnd = bnnoitru.mathe`|VARCHAR(15)|||
|4|ho_ten_nnd|Ghi họ và tên của mẹ hoặc của người nuôi dưỡng.|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ho_ten_nnd = psnguoinuoiduong.ho_ten_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ho_ten_nnd = dmbenhnhan.holot + “ ” + dmbenhnhan.ten`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn`|VARCHAR(255)|X||
|5|ngaysinh_nnd|Ghi ngày sinh của mẹ hoặc người nuôi dưỡng, định dạng yyyymmdd|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ngaysinh_nnd = to_char(psnguoinuoiduong.ngaysinh_nnd,'yyyyMMdd')` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ngaysinh_nnd = to_char(dmbenhnhan.ngaysinh,'yyyyMMdd')`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn`|VARCHAR(8)|X||
|6|ma_dantoc_nnd|Ghi mã dân tộc của mẹ hoặc người nuôi dưỡng theo Danh mục các dân tộc Việt Nam ban hành kèm theo [Quyết định số 121-TCTK/PPCĐ](http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html) ngày 02 tháng 3 năm 1979 của Tổng cục trưởng Tổng cục Thống kê để điền chi tiết). Tra cứu mã dân tộc tại đường link: http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html |Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ma_dantoc_nnd = psnguoinuoiduong.ma_dantoc_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ma_dantoc_nnd = dmdantoc.ma4750`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn AND dmbenhnhan.madt = dmdantoc.madt`|VARCHAR(2)| X||
|7|so_cccd_nnd|Ghi số chứng minh nhân dân hoặc số căn cước công dân hoặc số hộ chiếu của mẹ hoặc người nuôi dưỡng. |Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`so_cccd_nnd = psnguoinuoiduong.so_cccd_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`so_cccd_nnd = dmbenhnhan.cmnd`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn`|VARCHAR(15)| X||
|8|ngaycap_cccd_nnd|Ghi ngày cấp chứng minh nhân dân hoặc căn cước công dân hoặc hộ chiếu của mẹ hoặc người nuôi dưỡng, định dạng yyyymmdd|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ngaycap_cccd_nnd = to_char(psnguoinuoiduong.ngaycap_cccd_nnd, 'YYYYMMDD')` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ngaycap_cccd_nnd = to_char(dmbenhnhan.ngaycap, 'YYYYMMDD')`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn`|VARCHAR(8)|X ||
|9|noicap_cccd_nnd|Ghi nơi cấp chứng minh nhân dân hoặc căn cước công dân hoặc hộ chiếu của mẹ hoặc người nuôi dưỡng.|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`noicap_cccd_nnd = psnguoinuoiduong.noicap_cccd_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`noicap_cccd_nnd = dmbenhnhan.noicap`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn`|VARCHAR(1024)|X ||
|10|noi_cu_tru_nnd|Ghi địa chỉ nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. <br/>**Lưu ý**: <br/>- Nếu là người Việt Nam: Ghi địa chỉ nơi cư trú theo địa danh 4 cấp: Thôn/bản, xã/phường/thị trấn, quận/huyện/ thành phố thuộc tỉnh, tỉnh/thành phố trực thuộc trung ương;<br/>- Trường hợp người nước ngoài có địa chỉ nơi cư trú tại Việt Nam thì ghi giống như người Việt Nam;<br/>- Trường hợp người nước ngoài không có địa chỉ nơi cư trú tại Việt Nam nhưng sinh đẻ tại cơ sở y tế của Việt Nam thì ghi tên tỉnh/thành phố/bang và quốc gia nơi họ đang sinh sống.|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`noi_cu_tru_nnd = psnguoinuoiduong.noi_cu_tru_nnd` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`noi_cu_tru_nnd = dmbenhnhan.diachi`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn`|VARCHAR(1024)|X ||
|11|ma_quoctich|Ghi mã quốc tịch của mẹ hoặc người nuôi dưỡng theo quy định tại Phụ lục 2 [Thông tư số 07/2016/TT-BCA](https://congan.quangngai.gov.vn/documents/8878324/9231653/0_20200704221919.pdf/fcd11c17-3599-43f0-ae40-0d5e467bb10d) ngày 01 tháng 2 năm 2016 của Bộ trưởng Bộ Công an.|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`ma_quoctich = psnguoinuoiduong.ma_quoctich` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`)<br/><br/>Ngược lại:<br/>`ma_quoctich = dmquocgia.ma4750`<br/>Trong đó tham chiếu `bnnoitru.mabn = dmbenhnhan.mabn AND dmbenhnhan.maqg = dmquocgia.maqg`|VARCHAR(3)| X||
|12|matinh_cu_tru|Mã đơn vị hành chính cấp tỉnh nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. Ghi theo 02 ký tự cuối của mã đơn vị hành chính của tỉnh, thành phố trực thuộc Trung ương nơi người bệnh cư trú (Quy định tại Phụ lục 1 [Thông tư số 07/2016/TT-BCA](https://congan.quangngai.gov.vn/documents/8878324/9231653/0_20200704221919.pdf/fcd11c17-3599-43f0-ae40-0d5e467bb10d) ngày 01 tháng 2 năm 2016 của Bộ trưởng Bộ Công an).|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`matinh_cu_tru = dmxa4750.matinh` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`). Trong đó, tham chiếu: `psnguoinuoiduong.id_cu_tru_nnd = dmxa4750.id`<br/><br/>Ngược lại:<br/>`matinh_cu_tru = dmxa4750.matinh`. Trong đó, tham chiếu: `bnnoitru.maxa = dmxa4750.id`|VARCHAR(3)| X||
|13|mahuyen_cu_tru|Mã đơn vị hành chính cấp huyện nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. Ghi mã đơn vị hành chính cấp huyện theo [Quyết định số 124/2004/QĐ-TTg](https://vanban.chinhphu.vn/default.aspx?pageid=27160&docid=14081) ngày 08/7/2004 của Thủ tướng Chính phủ ban hành danh mục mã đơn vị hành chính.|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`mahuyen_cu_tru = dmxa4750.mahuyen` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`). Trong đó, tham chiếu: `psnguoinuoiduong.id_cu_tru_nnd = dmxa4750.id`<br/><br/>Ngược lại:<br/>`mahuyen_cu_tru = dmxa4750.mahuyen`. Trong đó, tham chiếu: `bnnoitru.maxa = dmxa4750.id`|NUMERIC(3,0)| X||
|14|maxa_cu_tru|Mã đơn vị hành chính cấp xã nơi cư trú hiện tại của mẹ hoặc người nuôi dưỡng. Ghi mã đơn vị hành chính cấp xã theo [Quyết định số 124/2004/QĐ-TTg](https://vanban.chinhphu.vn/default.aspx?pageid=27160&docid=14081) ngày 08/7/2004 của Thủ tướng Chính phủ ban hành danh mục mã đơn vị hành chính.|Nếu `psnguoinuoiduong.ho_ten_nnd` khác rỗng:<br/>`maxa_cu_tru = dmxa4750.maxa` (thông qua điều kiện: `ttcon.maba = psnguoinuoiduong.maba AND ttcon.mabame = psnguoinuoiduong.mabame`). Trong đó, tham chiếu: `psnguoinuoiduong.id_cu_tru_nnd = dmxa4750.id`<br/><br/>Ngược lại:<br/>`maxa_cu_tru = dmxa4750.maxa`. Trong đó, tham chiếu: `bnnoitru.maxa = dmxa4750.id`|VARCHAR(5)|X ||
|15|ho_ten_cha|Ghi họ và tên cha (bố) của trẻ được cấp giấy chứng sinh.|`=ttcon.hotencha`|VARCHAR(255)|||
|16|ma_the_tam|Ghi mã thẻ BHYT tạm thời của người con. Cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.|Nếu `ttcon.thetam = 1` thì: `ma_the_tam = ttcon.mathe`|VARCHAR(15)|||
|17|ho_ten_con|Ghi họ và tên dự định đặt cho con (nếu có).|`= ttcon.tendudinh`|VARCHAR(255)|||
|18|gioi_tinh_con|Ghi giới tính con, trong đó:<br/>- Mã "1": Nam; <br/>- Mã "2": Nữ; <br/>- Mã "3": Chưa xác định.|`= ttcon.gioitinh`|NUMERIC(1,0)|X||
|19|so_con|Ghi số lượng con trong lần sinh này.|`= ttcon.socon`|NUMERIC(2,0)| X||
|20|lan_sinh|Ghi số lần sinh con (tính cả lần sinh này).|`= ttcon.lan_sinh` [^2024-07-24-07]|NUMERIC(2,0)| X||
|21|so_con_song|Ghi số con hiện đang sống (tính cả trẻ sinh ra lần này).|`= ttcon.soconsong` [^2024-07-24-08]|NUMERIC(2,0)|X ||
|22|can_nang_con|Ghi số cân nặng của con, tính theo gram (ký hiệu là: g) (ví dụ: 3.6 kg = 3600g).|`= ttcon.cannang`|NUMERIC(10,0)|X ||
|23|ngay_sinh_con|Ghi ngày sinh con theo định dạng yyyymmddHHMM.|`= to_char(ttcon.ngaysinh, 'yyyyMMddHH24:mi')`|VARCHAR(12)| X||
|24|noi_sinh_con|Ghi địa chỉ nơi con được sinh ra. <br/>**Lưu ý**:<br/>- Trường hợp trẻ em được sinh ra tại bệnh viện, thì ghi tên bệnh viện và địa danh hành chính nơi trẻ em được sinh ra. Ví dụ: bệnh viện đa khoa tỉnh Nam Định);<br/>- Trường hợp trẻ em được sinh tại cơ sở y tế khác thì ghi tên cơ sở y tế và địa danh hành chính 3 cấp nơi trẻ em sinh ra (Ví dụ: Trạm y tế xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định);<br/>- Trường hợp trẻ em được sinh tại nhà thì ghi địa chỉ nhà và địa danh 3 cấp: cấp xã/phường, quận/huyện, tỉnh/thành phố trực thuộc trung ương <br/>Ví dụ: sinh tại nhà ở xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định;<br/>- Trường hợp trẻ em được sinh ra tại nơi khác, ngoài cơ sở KBCB thì cũng ghi nơi trẻ em được sinh ra và địa danh 3 cấp hành chính.<br/>Ví dụ: đẻ trên đường đi, tại xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định.<br/>- Trường hợp trẻ em bị bỏ rơi thì ghi rõ trẻ bị bỏ rơi và nơi tìm thấy trẻ, với địa danh 3 cấp hành chính.<br/>Ví dụ: trẻ bị bỏ rơi tại xã Liên Bảo, huyện Vụ Bản, tỉnh Nam Định.|`= tham số [tenbv]`|VARCHAR(1024)|  X||
|25|tinh_trang_con|Ghi rõ tình trạng của trẻ tại thời điểm làm Giấy chứng sinh: khỏe mạnh, yếu, dị tật hoặc các biểu hiện liên quan đến sức khỏe khác (nếu có).<br/>**Lưu ý**: Nếu trẻ bị dị dạng, dị tật, ghi cụ thể loại dị dạng, dị tật, kể cả khuyết tật về hình thái của trẻ nếu phát hiện được.|`= ttcon.suckhoe`|VARCHAR|  X||
|26|sinhcon_phauthuat|Ghi:<br/>- Mã "1": sinh con phải phẫu thuật;<br/>- Mã "0": sinh con không phải phẫu thuật.|`= ttcon.sinhcon_phauthuat` [^2024-07-24-09]|NUMERIC(1,0)|  X||
|27|sinhcon_duoi32tuan|Ghi:<br/>- Mã "1": sinh con dưới 32 tuần tuổi;<br/>- Mã "0" là không sinh con dưới 32 tuần tuổi.|`= ttcon.sinhcon_duoi32tuan` [^2024-07-24-10]|NUMERIC(1,0)|  X||
|28|ghi_chu|Trường hợp sinh con phải phẫu thuật hoặc sinh con dưới 32 tuần tuổi hoặc vừa sinh con dưới 32 tuần tuổi lại vừa phải phẫu thuật thì trong phần ghi chú phải ghi rõ một trong các nội dung sau "Sinh con phải phẫu thuật" hoặc "Sinh con dưới 32 tuần tuổi" hoặc "Phẫu thuật, sinh con dưới 32 tuần tuổi".|Nếu:[^2024-07-24-11]<br/>1️⃣  `sinhcon_phauthuat = 1 AND sinhcon_duoi32tuan = 0` thì `ghi_chu = "Sinh con phải phẫu thuật"`.<br/>2️⃣  `sinhcon_phauthuat = 0 AND sinhcon_duoi32tuan = 1` thì `ghi_chu = "Sinh con dưới 32 tuần tuổi"`.<br/>3️⃣  `sinhcon_phauthuat = 1 AND sinhcon_duoi32tuan = 1` thì `ghi_chu = "Sinh con phải phẫu thuật; Sinh con dưới 32 tuần tuổi"`.|VARCHAR|  X||
|29|nguoi_do_de|Ghi họ và tên người đỡ đẻ.|`= dmnhanvien.holot + “ ” + dmnhanvien.ten`<br/><br/>Trong đó, tham chiếu `ttcon.nguoidd = dmnhanvien.manv`|VARCHAR(255)|  X||
|30|nguoi_ghi_phieu|Ghi họ và tên người ghi phiếu.|`= dmnhanvien.holot + “ ” + dmnhanvien.ten`<br/><br/>Trong đó, tham chiếu `ttcon.taikhoan = dmnhanvien.taikhoan`|VARCHAR(255)|  X||
|31|ngay_ct|Ghi ngày cấp chứng từ (Giấy chứng sinh), định dạng yyyymmdd, ghi theo ngày dương lịch.|`= to_char(ttcon.ngaychinh, 'yyyyMMdd')`|VARCHAR(8)| X ||
|32|so|Ghi số của chứng từ (Giấy chứng sinh) tại cơ sở KBCB.|`= ttcon.so`|VARCHAR(200)| X ||
|33|quyen_so|Ghi quyển số của chứng từ (Giấy chứng sinh) tại cơ sở KBCB.|`= ttcon.quyen`|VARCHAR(200)|  X||
|34|ma_ttdv|Ghi mã số định danh y tế (mã số BHXH) của Thủ trưởng cơ sở KBCB cấp giấy chứng sinh.|Được lấy từ `tham số ma_ttdv`|VARCHAR(10)|  X||
|35|du_phong|Bổ sung trường mới: Trường dữ liệu dự phòng khi cần thiết.||VARCHAR|||
||makb|bnnoitru.makb||VARCHAR(20)|X|X|
||mabn|bnnoitru.mabn||VARCHAR(20)|X|X|

[^2024-10-14-01]: Thay đổi ngày 14/10/2024: Cập nhật cách ghi nhận giá trị cho các cột `ma_bhxh_nnd`, `ma_the_nnd`, `ho_ten_nnd`, `ngaysinh_nnd`, `ma_dantoc_nnd`, `so_cccd_nnd`, `ngaycap_cccd_nnd`, `noicap_cccd_nnd`, `noi_cu_tru_nnd`, `ma_quoctich`, `matinh_cu_tru`, `mahuyen_cu_tru`, `maxa_cu_tru` theo [Mô tả Người nuôi dưỡng cho thông tin con](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20Ng%C6%B0%E1%BB%9Di%20nu%C3%B4i%20d%C6%B0%E1%BB%A1ng%20cho%20th%C3%B4ng%20tin%20con.md). Chi tiết theo yêu cầu [#694](https://github.com/dh-hos/To_Lap_Trinh/issues/694).
[^2024-07-24-11]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `ghi_chu`.
[^2024-07-24-10]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `sinhcon_duoi32tuan`.
[^2024-07-24-09]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `sinhcon_phauthuat`.
[^2024-07-24-08]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `so_con_song`.
[^2024-07-24-07]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `lan_sinh`.
[^2024-07-24-06]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `ma_quoctich`.
[^2024-07-24-05]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `noi_cu_tru_nnd`.
[^2024-07-24-04]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `noicap_cccd_nnd`.
[^2024-07-24-03]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `ngaycap_cccd_nnd`.
[^2024-07-24-02]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `so_cccd_nnd`.
[^2024-07-24-01]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `ma_dantoc_nnd`.
[^2024-07-24-12]: Thay đổi ngày 24/07/2024: Bổ sung cách ghi nhận giá trị cho cột `ma_the_nnd`.
[^2024-06-30]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-12]: Thay đổi ngày 12/06/2024: bổ sung cách ghi nhận giá trị cho `matinh_cu_tru`, `mahuyen_cu_tru`, `maxa_cu_tru` theo yêu cầu [#393](https://github.com/dh-hos/To_Lap_Trinh/issues/393)
[^2024-10-04]: Thay đổi ngày 04/10/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
