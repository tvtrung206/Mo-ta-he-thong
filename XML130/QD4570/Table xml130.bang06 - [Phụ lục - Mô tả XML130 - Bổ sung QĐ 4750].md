<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang6: Chỉ tiêu hồ sơ bệnh án chăm sóc và điều trị HIV/AIDS.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Điều kiện xuất dữ liệu XML130:** Dữ liệu bảng này phải tồn tại trong **`Schemas: fhi`** [^2024-06-30]

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)**

|TT QĐ 4750|Tên cột|Diễn giải|Ghi chú[^2024-10-16-01]|Kiểu dữ liệu|Bắt buộc|Index|
|:-------:|-------|-------|-------|:-------:|:-------:|:-------:|
|1|ma_lk|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|`= bang1.ma_lk`|VARCHAR(100)|X|X|
|2|ma_the_bhyt|Ghi mã thẻ BHYT của người bệnh do cơ quan BHXH cấp.<br/>**Lưu ý**:<br/>- Khi tiếp đón người bệnh, cơ sở KBCB có trách nhiệm tra cứu trên Cổng tiếp nhận dữ liệu Hệ thống thông tin giám định BHYT của BHXH Việt Nam để kiểm tra thông tin thẻ BHYT. Trường hợp cấp cứu mà người bệnh hoặc thân nhân người bệnh không xuất trình được thẻ BHYT ngay thì cơ sở KBCB tra cứu thông tin thẻ BHYT trước khi người bệnh ra viện.<br/>- Đối với thẻ BHYT của các đối tượng có các mã QN, HC, LS, XK, CY, CA do BHXH Bộ Quốc phòng, BHXH Bộ Công an cấp: Tra cứu để kiểm tra thời hạn sử dụng của thẻ BHYT trong trường hợp các đối tượng này không còn phục vụ trong lực lượng Quân đội, Công an, Cơ yếu.<br/>- Trường hợp trong thời gian điều trị, người bệnh được cấp thẻ BHYT mới có thay đổi thông tin liên quan đến mã thẻ thì ghi tiếp mã thẻ mới (mỗi mã thẻ gồm có 15 ký tự), giữa các mã thẻ cách nhau bằng dấu chấm phẩy “;”.<br/>- Trường hợp người bệnh chưa có thẻ BHYT, cơ sở KBCB sử dụng chức năng “Thông tuyến khám chữa bệnh\Tra cứu thẻ tạm của trẻ em hoặc của người hiến tạng” trên Cổng tiếp nhận dữ liệu của BHXH Việt Nam để tra cứu mã thẻ BHYT tạm thời.<br/>- Trường hợp người bệnh không KBCB BHYT thì để trống trường thông tin này.||VARCHAR|X|X|
|3|so_cccd|Ghi số căn cước công dân hoặc số chứng minh thư nhân dân hoặc số hộ chiếu của người bệnh.<br/>Trường hợp không có số căn cước công dân hoặc số chứng minh thư nhân dân hoặc số hộ chiếu thì sử dụng mã tài khoản định danh điện tử.|Đổi kiểu dữ liệu từ số thành chuỗi|VARCHAR(15)|||
|4|ngay_sinh|Sử dụng thông tin tại trường NGAY_SINH trong Bảng 1 ban hành kèm theo Quyết định này||VARCHAR(12)|||
|5|gioi_tinh|Sử dụng thông tin tại trường GIOI_TINH trong Bảng 1 ban hành kèm theo Quyết định này||NUMERIC(1,0)|||
|6|dia_chi|Sử dụng thông tin tại trường DIA_CHI trong Bảng 1 ban hành kèm theo Quyết định này||VARCHAR(1024)|||
|7|matinh_cu_tru|Sử dụng thông tin tại trường MATINH_CU_TRU trong Bảng 1 ban hành kèm theo Quyết định này|`=current.dmxa4750.matinh` [^2024-06-12]|VARCHAR(3)|||
|8|mahuyen_cu_tru|Sử dụng thông tin tại trường MAHUYEN_CU_TRU trong Bảng 1 ban hành kèm theo Quyết định này|`=current.dmxa4750.mahuyen`|VARCHAR(3)|||
|9|maxa_cu_tru|Sử dụng thông tin tại trường MAXA_CU_TRU trong Bảng 1 ban hành kèm theo Quyết định này|`=current.dmxa4750.maxa`|VARCHAR(5)|||
|10|ngaykd_hiv|Ghi thời điểm khẳng định HIV của người nhiễm HIV, định dạng yyyymmdd.<br/>Trường hợp điều trị phơi nhiễm thì để trống trường thông tin này.||VARCHAR(8)|||
|11|noi_lay_mau_xn|Ghi mã cơ sở KBCB nơi lấy mẫu máu xét nghiệm HIV do cơ quan có thẩm quyền cấp.||VARCHAR(5)|X||
|12|noi_xn_kd|Ghi mã cơ sở KBCB nơi người bệnh làm xét nghiệm khẳng định HIV do cơ quan có thẩm quyền cấp.||VARCHAR(5)|X||
|13|noi_bddt_arv|Ghi mã cơ sở KBCB đầu tiên nơi người bệnh nhận thuốc ARV trong chương trình chăm sóc và điều trị được ghi trong hồ sơ bệnh án của người bệnh do cơ quan có thẩm quyền cấp.||VARCHAR(5)|X||
|14|bddt_arv|Ghi thời điểm đầu tiên người bệnh nhận thuốc ARV trong chương trình chăm sóc và điều trị được ghi trong hồ sơ bệnh án của người bệnh; định dạng yyyymmdd.||VARCHAR(8)|||
|15|ma_phac_do_dieu_tri_bd|Ghi mã phác đồ điều trị HIV/AIDS khi bắt đầu điều trị ARV theo danh mục mã phác đồ điều trị HIV/AIDS tại Phụ lục 10 ban hành kèm theo [Quyết định số 5937/QĐ-BYT](https://ttytphumy.com/laws/detail/v-v-bo-sung-danh-muc-ma-dung-chung-lien-quan-bhyt-28/) ngày 30/12/2021 của Bộ trưởng Bộ Y tế.||VARCHAR(200)|||
|16|ma_bac_phac_do_bd|Ghi mã bậc của phác đồ khi bắt đầu điều trị ARV sử dụng phác đồ điều trị là "Khác", trong đó:<br/>- Mã "1": Phác đồ bậc 1;<br/>- Mã "2": Phác đồ bậc 2;<br/>- Mã "3": Phác đồ bậc 3.||NUMERIC(1,0)|||
|17|ma_lydo_dtri|Ghi mã lý do bệnh nhân đăng ký giai đoạn điều trị tại cơ sở KBCB, trong đó:<br/>- Mã "1": Bệnh nhân HIV mới đăng ký lần đầu;<br/>- Mã "2": Bệnh nhân HIV chưa điều trị ARV chuyển tới;<br/>- Mã "3": Bệnh nhân HIV đã điều trị ARV chuyển tới;<br/>- Mã "4": Bệnh nhân HIV đã điều trị ARV nay điều trị lại;<br/>- Mã "5": Bệnh nhân HIV chưa điều trị ARV đăng ký lại.||NUMERIC(1,0)|X||
|18|loai_dtri_lao|Ghi mã loại điều trị lao, trong đó:<br/>- Mã "0": Không điều trị lao; <br/>- Mã "1": Điều trị lao tiềm ẩn; <br/>- Mã "2": Điều trị lao;<br/>- Mã "3": Điều trị lao kháng thuốc.||NUMERIC(1,0)|X ||
|19|sang_loc_lao|Mã các phương pháp sàng lọc lao được thực hiện, trong đó:<br/>- Mã "1": Không sàng lọc;<br/>- Mã "2": Sàng lọc triệu chứng;<br/>- Mã "3": Chụp X-quang phổi;<br/>- Mã "4": Xét nghiệm Protein phản ứng C||NUMERIC(1,0)|X||
|20|phacdo_dtri_lao|- Ghi mã phác đồ điều trị bệnh lao ở người nhiễm HIV, trong đó:<br/>+ Mã "1": Phác đồ 2RHZE/4RHE; <br/>+ Mã "2": Phác đồ 2RHZE/4RH; <br/>+ Mã "3": Phác đồ 2RHZE/10RHE; <br/>+ Mã "4": Phác đồ 2RHZE/10RH; <br/>+ Mã "5": Phác đồ khác.<br/>- Ghi mã phác đồ điều trị đối với bệnh nhân lao tiềm ẩn, trong đó:<br/>+ Mã "6": Phác đồ INH; <br/>+ Mã "7": Phác đồ 3HP; <br/>+ Mã "8: Phác đồ 1HP; <br/>+ Mã "9": Phác đồ 3HR; <br/>+ Mã "10": Phác đồ 4R; <br/>+ Mã "11": Phác đồ 6L; <br/>+ Mã "12": Phác đồ khác.<br/><br/>Ghi mã phác đồ điều trị lao nhạy cảm thuốc, điều trị lao kháng thuốc ở người nhiễm HIV; điều trị lao tiềm ẩn theo bộ mã DMDC do Bộ Y tế quy định.||NUMERIC(2,0)|||
|21|ngaybd_dtri_lao|Ghi thời điểm bắt đầu điều trị bệnh lao hoặc lao tiềm ẩn tại cơ sở KBCB, định dạng yyyymmdd.||VARCHAR(8)|||
|22|ngaykt_dtri_lao|Ghi thời điểm kết thúc điều trị bệnh lao hoặc lao tiềm ẩn tại cơ sở KBCB, định dạng yyyymmdd. <br/>Trường hợp chưa kết thúc điều trị thì để trống trường thông tin này.||VARCHAR(8)|||
|23|kq_dtri_lao|Ghi mã kết quả điều trị lao, điều trị lao tiềm ẩn, trong đó:<br/>- Mã "1": Đang điều trị;<br/>- Mã "2": Hoàn thành;<br/>- Mã "3": Thất bại;<br/>- Mã "4": Tử vong;<br/>- Mã "5": Bỏ điều trị;<br/>- Mã "6": Ngừng điều trị (ghi rõ lý do);<br/>- Mã "7": Không đánh giá.||NUMERIC(1,0)|X||
|24|ma_lydo_xntl_vr|Ghi mã lý do chỉ định xét nghiệm đo tải lượng vi rút ở người bệnh đang điều trị ARV, trong đó:<br/>- Mã "1": Thường quy; <br/>- Mã "2": Nghi ngờ thất bại điều trị; <br/>- Mã "3": Khác.||NUMERIC(1,0)|||
|25|ngay_xn_tlvr|Ghi thời điểm lấy mẫu làm xét nghiệm tải lượng virus, gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Thời điểm lấy mẫu làm xét nghiệm tải lượng virus là ngày 31/03/2017, khi đó trường thông tin này được hiển thị là: 20170331||VARCHAR(8)|||
|26|kq_xntl_vr|Ghi mã kết quả xét nghiệm tải lượng vi rút HIV, là số lượng bản sao vi rút HIV trên 1 ml máu, trong đó:<br/>- Mã "1": Không phát hiện; <br/>- Mã "2": Dưới 50 bản sao/ml; <br/>- Mã "3": Từ 50 đến dưới 200 bản sao/ml; <br/>- Mã "4": Từ 200 đến 1000 bản sao/ml; <br/>- Mã "5: Trên 1000 bản sao/ml.||NUMERIC(1,0)|||
|27|ngay_kq_xn_tlvr|Ghi thời điểm có kết quả xét nghiệm tải lượng virus, gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày có kết quả xét nghiệm tải lượng virus là ngày 31/03/2017, khi đó trường thông tin này được được hiển thị là: 20170331||VARCHAR(8)|||
|28|ma_loai_bn|Ghi mã đối tượng đến khám, trong đó:<br/>- Mã "1": Người nhiễm HIV; <br/>- Mã "2": Trẻ phơi nhiễm với HIV; <br/>- Mã "3": Điều trị dự phòng trước phơi nhiễm; <br/>- Mã "4": Điều trị dự phòng sau phơi nhiễm; <br/>- Mã "5": Khác.||NUMERIC(1,0)|||
|29|giai_doan_lam_sang|Ghi mã giai đoạn lâm sàng, trong đó:<br/>- Mã "1": Giai đoạn I;<br/>- Mã "2": Giai đoạn II;<br/>- Mã "3": Giai đoạn III;<br/>- Mã "4": Giai đoạn IV;||NUMERIC(1,0)|X||
|30|nhom_doi_tuong|Ghi mã nhóm đối tượng, trong đó:<br/>- Mã "0": Người sử dụng ma tuý;<br/>- Mã "1": Người bán dâm;<br/>- Mã "2": Người có quan hệ tình dục đồng giới;<br/>- Mã "3": Người chuyển đổi giới tính;<br/>- Mã "4": Vợ, chồng và thành viên khác trong gia đình cùng sống chung với người nhiễm HIV; vợ, chồng của đối tượng quy định tại các mã 0, 1, 2 và mã 3 nêu trên;<br/>- Mã "5": Người có quan hệ tình dục với người nhiễm HIV;<br/>- Mã "6": Người mắc các bệnh lây truyền qua đường tình dục;<br/>- Mã "7": Người di biến động;<br/>- Mã "8": Người mắc bệnh lao;<br/>- Mã "9": Người có triệu chứng lâm sàng nghi ngờ nhiễm HIV;<br/>- Mã "10": Phạm nhân, người bị tạm giam, trại viên cơ sở giáo dục bắt buộc, học sinh trường giáo dưỡng, học viên cơ sở cai nghiện ma túy;<br/>- Mã "11": Các đối tượng khác.||NUMERIC(2,0)|X||
|31|ma_tinh_trang_dk|Ghi mã tình trạng của đối tượng đến khám, trong đó:<br/>- Mã "1": Trẻ dưới 18 tháng sinh ra từ mẹ nhiễm HIV;<br/>- Mã "2": Phơi nhiễm;<br/>- Mã "3": Đang điều trị lao;<br/>- Mã "4": Có bầu;<br/>- Mã "5": Chuyển dạ;<br/>- Mã "6": Sau sinh;<br/>- Mã "7": Viêm gan;<br/>- Mã "8": Nghiện chích ma túy;<br/>- Mã "9": Khác.<br/>Trường hợp đối tượng khám có 2 tình trạng trở lên thì các Mã cách nhau bởi dấu chấm phẩy “;”. Ví dụ: 1;2;3 ||VARCHAR(18)| X||
|32|lan_xn_pcr|Ghi mã lần thực hiện xét nghiệm PCR, trong đó:<br/>- Mã "1": lần 1; <br/>- Mã "2": lần 2; <br/>- Mã "3": lần 3 (chỉ áp dụng trong lần 1 âm tính và lần 2 dương tính). <br/>Trường thông tin này chỉ áp dụng cho trẻ dưới 18 tháng tuổi bị phơi nhiễm với HIV.||NUMERIC(1,0)| bắt buộc nếu MA_TINH_TRANG_DK =1||
|33|ngay_xn_pcr|Ghi ngày mà người bệnh thực hiện xét nghiệm PCR, gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày mà người bệnh thực hiện xét nghiệm PCR là ngày 31/03/2017, khi đó, trường thông tin này được hiển thị là: 20170331<br/>Trường thông tin này chỉ áp dụng cho trẻ dưới 18 tháng tuổi bị phơi nhiễm với HIV.||VARCHAR(8)|bắt buộc nếu MA_TINH_TRANG_DK =1 ||
|34|ngay_kq_xn_pcr|Ghi ngày mà người bệnh có kết quả xét nghiệm PCR1, gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày mà người bệnh có kết quả xét nghiệm PCR1 là ngày 31/03/2017, khi đó, trường thông tin này được hiển thị là: 20170331<br/>Trường thông tin này chỉ áp dụng cho trẻ dưới 18 tháng tuổi bị phơi nhiễm với HIV||VARCHAR(8)| bắt buộc nếu MA_TINH_TRANG_DK =1||
|35|ma_kq_xn_pcr|Ghi mã kết quả xét nghiệm PCR1, trong đó:<br/>- Mã "0": Âm tính; <br/>- Mã "1": Dương tính.<br/>Trường thông tin này chỉ áp dụng cho trẻ dưới 18 tháng tuổi bị phơi nhiễm với HIV.||NUMERIC(1,0)|bắt buộc nếu MA_TINH_TRANG_DK =1 ||
|36|ngay_nhan_tt_mang_thai|Ghi thời điểm nhận thông tin mang thai, gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày nhận thông tin mang thai là ngày 31/03/2017, khi đó, trường thông tin này được hiển thị là: 20170331||VARCHAR(8)|||
|37|ngay_bat_dau_dt_ctx|Ghi thời điểm bắt đầu điều trị Cotrimoxazol (CTX), gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày bắt đầu điều trị Cotrimoxazol (CTX) là ngày 31/03/2017, khi đó, trường thông tin này được hiển thị là: 20170331||VARCHAR(8)|||
|38|ma_xu_tri|Ghi mã xử trí của cơ sở y tế, trong đó:<br/>- Mã "1": Điều trị ARV;<br/>- Mã "2": Điều trị lao;<br/>- Mã "3": Dự phòng lao;<br/>- Mã "4": Cotrimoxazol;<br/>- Mã "5": PLTMC;<br/>- Mã "6": Điều trị viêm gan B<br/>- Mã "7": Điều trị viêm gan C<br/>- Mã "8": Khác<br/>Trường hợp có nhiều xử trí thì ghi các mã xử trí, giữa các mã xử trí phân cách bằng dấu chấm phẩy “;”.|Đổi kiểu dữ liệu từ số thành chuỗi. Tăng kích thước tối đa lên 10 ký tự|VARCHAR(10)|X ||
|39|ngay_bat_dau_xu_tri|Ghi ngày bắt đầu xử trí của đợt điều trị ARV (áp dụng đối với trường hợp có mã xử trí (MA_XU_TRI) là "1"), gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày bắt đầu xử trí của đợt điều trị ARV là ngày 31/03/2017, khi đó, trường thông tin này được hiển thị là: 20170331||VARCHAR(8)| bắt buộc khi MA_XU_TRI = 1||
|40|ngay_ket_thuc_xu_tri|Ghi ngày kết thúc xử trí của đợt điều trị ARV (áp dụng đối với trường hợp có mã xử trí (MA_XU_TRI) là "1"), gồm 08 ký tự theo định dạng yyyymmdd.<br/>Ví dụ: Ngày kết thúc xử trí của đợt điều trị ARV là ngày 31/03/2017, khi đó, trường thông tin này được hiển thị là: 20170331||VARCHAR(8)|bắt buộc khi MA_XU_TRI = 1 ||
|41|ma_phac_do_dieu_tri|Ghi mã phác đồ điều trị HIV/AIDS của đợt điều trị (Tham chiếu danh mục mã phác đồ điều trị HIV/AIDS tại Phụ lục 10 ban hành kèm theo [Quyết định số 5937/QĐ-BYT](https://ttytphumy.com/laws/detail/v-v-bo-sung-danh-muc-ma-dung-chung-lien-quan-bhyt-28/) ngày 30/12/2021 của Bộ trưởng Bộ Y tế).||VARCHAR(200)| X||
|42|ma_bac_phac_do|Ghi mã bậc phác đồ của đợt điều trị khi phác đồ điều trị là "Khác", trong đó:<br/>- Mã "1": Phác đồ bậc 1;<br/>- Mã "2": Phác đồ bậc 2;<br/>- Mã "3": Phác đồ bậc 3.||NUMERIC(1,0)|bắt buộc trong trường hợp MA_PHAC_DO_DIEU_TRI = KHAC ||
|43|so_ngay_cap_thuoc_arv|Ghi số ngày thuốc ARV được cấp (nhỏ hơn hoặc bằng với ngày trong trường thông tin NGAY_KET_THUC_XU_TRI trừ đi (-) ngày trong trường thông tin NGAY_BAT_DAU_XU_TRI)||NUMERIC(3,0)| bắt buộc khi MA_XU_TRI = 1||
|44|ngay_chuyen_phac_do|Ghi ngày chuyển phác đồ điều trị, gồm 08 ký tự theo định dạng yyyymmdd||VARCHAR(8)|X||
|45|ly_do_chuyen_phac_do|Ghi mã lý do chuyển phác đồ, trong đó:<br/>- Mã "1": Thiếu thuốc;<br/>- Mã "2": Tác dụng phụ;<br/>- Mã "3": Thất bại điều trị;<br/>- Mã "4": Tối ưu hoá phác đồ;<br/>- Mã "5": Phác đồ mới theo hướng dẫn quốc gia;<br/>- Mã "6": Khác.||NUMERIC(1,0)|X||
|46|ma_cskcb|Ghi mã cơ sở KBCB nơi người bệnh đến khám bệnh, điều trị HIV/AIDS, do cơ quan có thẩm quyền cấp.||VARCHAR(5)|||
|47|du_phong|Trường dữ liệu dự phòng khi cần||VARCHAR|||
||mabn|psdangky.mabn||VARCHAR(20)|X|X|
||makb|psdangky.makb||VARCHAR(20)|X|X|
||[^2024-07-12]ngay_tai_kham| Bổ sung theo dự án HIV ||VARCHAR(20)|X|X|
||ma_benh_kt| Bổ sung theo dự án HIV ||VARCHAR(200)|X|X|
||ly_do_ket_thuc_dieu_tri| Bổ sung theo dự án HIV ||VARCHAR(200)|X|X|
||kq_sang_loc_lao| Bổ sung theo dự án HIV ||VARCHAR(200)|X|X|
||mabenhan| Bổ sung theo dự án HIV ||VARCHAR(20)|X|X|

[^2024-10-16-01]: Thay đổi ngày 16/10/2024: Bổ sung mô tả giá trị các cột `ma_lk`. Chi tiết theo yêu cầu [#684](https://github.com/dh-hos/To_Lap_Trinh/issues/684).
[^2024-07-12]: Thay đổi ngày 07/12/2024: Bổ sung các cột riêng theo yêu cầu của dự án HIV
[^2024-06-30]: Thay đổi ngày 30/06/2024: Bổ sung điều kiện xuất dữ liệu trong bảng này.
[^2024-06-12]: Thay đổi ngày 12/06/2024: bổ sung cách ghi nhận giá trị cho `matinh_cu_tru`, `mahuyen_cu_tru`, `maxa_cu_tru` theo yêu cầu [#393](https://github.com/dh-hos/To_Lap_Trinh/issues/393)
