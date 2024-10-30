<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: Module Reports xuất dữ liệu XML130 theo [Quyết định 4750/QD-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/4750.pdf) và Mẫu C79-HD ([Thông tư 102/2018/TT-BTC](https://chinhphu.vn/default.aspx?pageid=27160&docid=196269)) lấy dữ liệu từ XML4750.
</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)

###### :eight_spoked_asterisk: Ngày lập: **07/08/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Module Reports bổ sung menu và form xuất dữ liệu XML130 (Theo Quyết định 4750). Form xuất XML130 gồm 2 tab:**

:blue_book: Tab 1 xuất `XML4750`:

- Bổ sung đầy đủ các tab con từ `XML1` đến `XML15`. Mỗi bảng tương ứng 1 tab: bổ sung đầy đủ các cột theo quy định từ QĐ 4750.
- Dữ liệu được load từ `SCHEMA xml130`.
- Tiêu chí thời gian thống kê: được chọn từ `xml130.bang1.ngay_ttoan`, `xml130.bang1.thang_qt` và `xml130.bang1.nam_qt`. Các bảng dữ liệu còn lại được load tham chiếu từ cột `ma_lk` của bảng hiện tại tương ứng với `xml1.ma_lk` của bảng 1. Điều kiện ràng buộc khi load dữ liệu: `bang1.t_tongchi_bh > 0`[^2024-09-09-01].
- Tại tab `bảng 1` (XML1): Bổ sung cột `checkbox` cho phép người dùng chọn hồ sơ cần xuất dữ liệu ra file XML. Với các hồ sơ đã chọn, bổ sung các Button xuất: `[XML 1 bệnh nhân 1 file]`, `[XML file tổng hợp]`, `[Excel CV3360 - (Cổng update 27/8/2019)]`.
<p align="center"><img src="https://github.com/user-attachments/assets/94722470-a31b-4e19-ad2e-c6472c8e05a0" width="70%"></p>

- Dữ liệu xuất XML  theo chuẩn và quy định tại Công văn [ 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024).
- Dữ liệu xuất file Excel Công văn [3360/BHXH-CSYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/CONGVAN-YEUCAU/CV%203360_BHXH-CSYT_ngay0492015.pdf), do BHXH Việt Nam ban hành ngày 04 tháng 09 năm 2015: Cập nhật mẫu Excel  từ Cổng giám định BHYT ngày 27/8/2019, cụ thể:

|STT|Chỉ tiêu|Xuất 4210|Xuất 4750[^2024-09-14]|Kiểu dữ liệu (theo QĐ4750)|Diễn giải (CV3360)|
|:-------:|-------|-------|-------|-------|-------|
|1|stt|||NUMERIC(10,0)|Số thứ tự bệnh nhân từ 1 đến hết|
|2|ma_bn|`=bang1.ma_bn`|`=bang1.ma_bn`|VARCHAR(100)|Mã số BN quy định tại CSKCB|
|3|ho_ten|`=bang1.ho_ten`|`=bang1.ho_ten`|VARCHAR(255)|Họ tên người bệnh viết bằng chữ thường.|
|4|ngay_sinh|`ngay_sinh=LEFT(bang1.ngay_sinh,8)`[^2024-09-06-01]. Riêng đối với người bệnh chỉ có năm sinh `ngay_sinh=LEFT(bang1.ngay_sinh,4)`[^2024-09-13-01]|`=bang1.ngay_sinh`|VARCHAR(12)|Ngày sinh ghi trên thẻ gồm 8 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày (nếu không có ngày sinh thì ghi năm sinh: 4 ký tự)|
|5|gioi_tinh|`=bang1.gioi_tinh`|`=bang1.gioi_tinh`|NUMERIC(1,0)|Giới tính: mã hóa bằng 1 chữ số (Nam = 1 Nữ = 2) |
|6|dia_chi|`=bang1.dia_chi`|`=bang1.dia_chi`|VARCHAR(1024)|Địa chỉ trên thẻ BHYT đối với trẻ em không có thẻ ghi đầy đủ địa chỉ trên giấy tờ thay thế (tối thiểu phải có địa chỉ về xã huyện tỉnh của trẻ).|
|7|ma_the|`=bang1.ma_the_bhyt`|`=bang1.ma_the_bhyt`|VARCHAR(50)|Mã thẻ BHYT do cơ quan BHXH cấp không thay đổi không thêm bớt các ký tự|
|8|ma_dkbd|`=bang1.ma_dkbd`|`=bang1.ma_dkbd`|VARCHAR(50)|Mã cơ sở KCB ban đầu ghi đúng 5 ký tự trên thẻ BHYT|
|9|gt_the_tu|`=bang1.gt_the_tu`|`=bang1.gt_the_tu`|VARCHAR(50)|Thời điểm thẻ có giá trị gồm 8 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày. Ví dụ: ngày 30/04/2015 được hiển thị là 20150430|
|10|gt_the_den|`=bang1.gt_the_den`|`=bang1.gt_the_den`|VARCHAR(50)|Thời điểm thẻ hết giá trị gồm 8 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày. Ví dụ: ngày 31/05/2015 được hiển thị là 20150531|
|11|ma_benh|`=bang1.ma_benh_chinh`|`=bang1.ma_benh_chinh`|VARCHAR(7)|Mã bệnh chính được mã hóa theo ICD X|
|12|ma_benhkhac|`=bang1.ma_benh_kt`|`=bang1.ma_benh_kt`|VARCHAR(100)|Mã bệnh khác mã hóa theo ICD X nếu có nhiều mã ICD thì mỗi mã đuợc phân cách bằng ký tự “;”|
|13|ma_lydo_vvien|Xét giá trị cột:`bang1.ma_doituong_kcb`[^2024-09-13-04]<br/>➡️`('2')`: `ma_lydo_vvien = '2'`<br/>➡️`('7.1','1.8','1.1','1.4','1.7','1.5','1.3','3.6','3.2')`: `ma_lydo_vvien = '1'`<br/>➡️`('3.3','3.5')`: `ket_qua_dtri = '3'`<br/>➡️`('1.2')`: `ma_lydo_vvien = '4'`<br/>➡️`('1.9','1.10')`: Nếu `bang1.ma_dkbd = bang1.ma_cskcb` thì `ma_lydo_vvien = '1'`, ngược lại `ma_lydo_vvien = '3'`|`=bang1.ma_doituong_kcb`|VARCHAR(4)|Mã hóa lý do đến khám bệnh: 1 = đúng tuyến; 2 = cấp cứu; 3 = trái tuyến|
|14|ma_noi_chuyen|`=bang1.ma_noi_di`|`=bang1.ma_noi_di`|VARCHAR(5)|Mã cơ sở KCB chuyển người bệnh đến (Mã do cơ quan BHXH cấp)|
|15|ngay_vao|`=bang1.ngay_vao`|`=bang1.ngay_vao`|VARCHAR(12)|Thời gian đến khám hoặc nhập viện theo ngày giờ; gồm 12 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày + 2 ký tự giờ (24 giờ) + 2 ký tự phút. Ví dụ: ngày 30/06/2015 08:20 được hiển thị là 201506300820|
|16|ngay_ra|`=bang1.ngay_ra`|`=bang1.ngay_ra`|VARCHAR(12)|Ngày giờ ra viện; gồm 12 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày + 2 ký tự giờ (24 giờ) + 2 ký tự phút. Ví dụ: ngày 31/07/2015 16:20 được hiển thị là 201507311620|
|17|so_ngay_dtri|`=bang1.so_ngay_dtri`|`=bang1.so_ngay_dtri`|NUMERIC(3,0)|Số ngày điều trị trong đợt KCB ngoại trú hoặc nằm viện nội trú (= ngày ra - ngày vào). Trường hợp điều trị nội trú nhưng có một số ngày không nằm viện thì tính theo ngày nằm viện thực tế|
|18|ket_qua_dtri|Xét giá trị cột:`bang1.ket_qua_dtri`[^2024-09-13-03]<br/>➡️`(1)`: `ket_qua_dtri = 1`<br/>➡️`(2)`: `ket_qua_dtri = 2`<br/>➡️`(3, 7)`: `ket_qua_dtri = 3`<br/>➡️`(4, 6)`: `ket_qua_dtri = 4`<br/>➡️`(5, 8)`: `ket_qua_dtri = 5`|`=bang1.ket_qua_dtri`|NUMERIC(1,0)|Kết quả điều trị: Mã hóa (1: Khỏi; 2: Đỡ; 3: Không thay đổi; 4: Nặng hơn; 5: Tử vong)|
|19|tinh_trang_rv|`=bang1.ma_loai_rv`[^2024-08-30]|`=bang1.ma_loai_rv`|NUMERIC(1,0)|Tình trạng ra viện: Mã hóa (1: Ra viện; 2: Chuyển viện; 3: Trốn viện; 4: Xin ra viện)|
|20|t_tongchi|`=bang1.t_tongchi_bh`|`=bang1.t_tongchi_bh`|NUMERIC(15,2)|Tổng chi phí KCB BHYT trong lần/đợt điều trị|
|21|t_xn|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 1`|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 1`|NUMERIC(15,2)|Tiền xét nghiệm|
|22|t_cdha[^2024-10-04-01]|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (2,3)`|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (2,3)`|NUMERIC(15,2)|Tiền chẩn đoán hình ảnh và thăm dò chức năng|
|23|t_thuoc|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 4`|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 4`|NUMERIC(15,2)|Tiền thuốc và dịch truyền|
|24|t_mau|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 7`|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 7`|NUMERIC(15,2)|Tiền máu và chế phẩm của máu|
|25|t_pttt|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (8,18)`|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (8,18)`|NUMERIC(15,2)|Tiền phẫu thuật và thủ thuật|
|26|t_vtyt|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 10`|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 10`|NUMERIC(15,2)|Tiền vật tư y tế|
|27|t_dvkt_tyle|||NUMERIC(15,2)|Tiền dịch vụ kỹ thuật thanh toán theo tỷ lệ|
|28|t_thuoc_tyle|||NUMERIC(15,2)|Tiền thuốc thanh toán theo tỷ lệ|
|29|t_vtyt_tyle|||NUMERIC(15,2)|Tiền vật tư y tế thanh toán theo tỷ lệ|
|30|t_kham|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 13`|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 13`|NUMERIC(15,2)|Tiền công khám bệnh ngoại trú hoặc tiền giường nội trú|
|31|t_vchuyen|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 12`|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 12`|NUMERIC(15,2)|Tiền vận chuyển|
|32|t_bntt[^2024-10-30-01]|`=bang1.t_tongchi_bh - bang1.t_bhtt`|`=bang1.t_tongchi_bh - bang1.t_bhtt`|NUMERIC(15,2)|Số tiền người bệnh thanh toán (Ghi số tiền người bệnh chi trả bao gồm cùng chi trả tự trả khi khám bệnh chữa bệnh không đúng tuyến số tiền tự trả đối với các dịch vụ y tế áp dụng tỷ lệ thanh toán)|
|33|t_bhtt|`=bang1.t_bhtt`|`=bang1.t_bhtt`|NUMERIC(15,2)|Tiền đề nghị cơ quan BHXH thanh toán (gồm cả chi phí ngoài định suất).|
|34|t_ngoaids|`=bang1.t_bhtt_gdv`|`=bang1.t_bhtt_gdv`|NUMERIC(15,2)|Tiền thanh toán ngoài định suất (không bao gồm tiền BN cùng chi trả)|
|35|ma_khoa|`=bang1.ma_khoa`|`=bang1.ma_khoa`|VARCHAR(50)|Ghi mã khoa theo quy định tại bảng 7 Quyết định số 2348/BYT-BH ngày 10/4/2015 của Bộ Y tế.|
|36|nam_qt|`=bang1.nam_qt`|`=bang1.nam_qt`|NUMERIC(4,0)|Năm đề nghị BHXH thanh toán|
|37|thang_qt|`=bang1.thang_qt`|`=bang1.thang_qt`|NUMERIC(2,0)|Tháng đề nghị BHXH thanh toán|
|38|ma_khuvuc|`=bang1.ma_khuvuc`|`=bang1.ma_khuvuc`|VARCHAR(2)|Ghi mã nơi sinh sống trên thẻ BHYT “K1/K2/K3” (nếu có)|
|39|ma_loaikcb|Xét giá trị cột:`bang1.ma_loai_kcb`[^2024-09-13-02]<br/>➡️`('01','05','07','08')`: `ma_loaikcb = '1'`<br/>➡️`('02')`: `ma_loaikcb = '2'`<br/>➡️`('03','04','09')`[^2024-10-16-01]: `ma_loaikcb = '3'`|`=bang1.ma_loai_kcb`|VARCHAR(2)|Mã hóa hình thức KCB: (1: khám bệnh; 2: điều trị ngoại trú; 3: điều trị nội trú)|
|40|ma_cskcb|`=bang1.ma_cskcb`|`=bang1.ma_cskcb`|VARCHAR(5)|Mã cơ sở KCB nơi điều trị: Ghi đúng 5 ký tự mã cơ sở KCB do BHXH VN cung cấp|
|41|t_nguonkhac[^2024-08-11]|`=bang1.t_nguonkhac`|`=bang1.t_nguonkhac`|NUMERIC(15,2)|Ghi tổng số tiền các nguồn khác chi trả ngoài phạm vi chi trả của quỹ BHYT|

🆕 Cập nhật cấu trúc: Bổ sung table `current.cauhinh3360_4750`[^2024-10-25-01]
| STT | TÊN CỘT | KIỂU |KHÓA | DIỄN GIẢI | INDEX |
|:-------:|-------|:-------:|:-------:|-------|:-------:|
|1|thamso|VARCHAR(50)|Chính|Tên tham số (cấu hình)|X|
|2|giatri|VARCHAR(255)||Giá trị cấu hình||
- Tại chức năng `[Excel CV3360 - (Cổng update 27/8/2019)]`, bổ sung menu `[Cấu hình]` và `form cấu hình` tương ứng để người dùng cấu hình và tùy chọn phương thức xuất Excel 3360 cho các cột (Thêm 4 dòng dữ liệu vào table `current.cauhinh3360_4750` tương ứng 4 cấu hình):
<p align="center"><img src="https://github.com/user-attachments/assets/d023f7b0-8f52-4469-ab0d-16e00032bd5d" width="70%"></p>

|STT|Tên cột|Tên cấu hình (dữ liệu cột `cauhinh3360_4750.thamso`)|Giá trị (dữ liệu cột `cauhinh3360_4750.giatri`)[^2024-10-29-01]|
|:-------:|-------|-------|-------|
|1|ngay_sinh|ngay_sinh|0️⃣: Theo QĐ4210<br/>*Ngày sinh ghi trên thẻ gồm 8 ký tự theo định dạng yyyymmdd; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày (nếu không có ngày sinh thì ghi năm sinh: 4 ký tự)*<br/>1️⃣: Theo QĐ4750<br/>*Ghi ngày, tháng, năm sinh ghi trên thẻ BHYT của người bệnh, gồm 12 ký tự theo định dạng yyyymmddHHMM. Lưu ý:<br/>- Trường hợp không có thông tin giờ, phút sinh thì ký tự giờ và phút được mặc định là 0000;<br/>- Trường hợp không có thông tin ngày sinh, tháng sinh thì ký tự ngày sinh, tháng sinh được mặc định là 0000;*|
|2|ma_lydo_vvien[^2024-10-28-02]|ma_lydo_vvien|0️⃣: Theo QĐ4210<br/>*Mã hóa lý do đến khám bệnh: 1 = đúng tuyến; 2 = cấp cứu; 3 = trái tuyến*<br/>1️⃣: Theo QĐ4750 (Chi tiết theo ma_doituong_kcb)<br/>*Các giá trị chi tiết theo* [Quyết định số 824/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/80dfedaffd557024c054fd720545a11becd0b537/XML130/Q%C4%90%20824-B%E1%BB%95%20sung%20m%C3%A3%20d%C3%B9ng%20chung.pdf) *ngày 15 tháng 02 năm 2023 của Bộ trưởng Bộ Y tế. Cụ thể xem chi tiết tại* [ma_doituong_kcb](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/ma_doituong_kcb.md)<br/>2️⃣: Theo QĐ4750 (Theo MÃ NHÓM của ma_doituong_kcb)<br/>*Các giá trị theo nhóm của* [Quyết định số 824/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/80dfedaffd557024c054fd720545a11becd0b537/XML130/Q%C4%90%20824-B%E1%BB%95%20sung%20m%C3%A3%20d%C3%B9ng%20chung.pdf) *ngày 15 tháng 02 năm 2023 của Bộ trưởng Bộ Y tế. Cụ thể:<br/>- 1: Đúng tuyến<br/>- 2: Cấp cứu<br/>- 3: Trái tuyến<br/>- 7: Lĩnh thuốc theo giấy hẹn trong trường hợp dịch bệnh hoặc bất khả kháng hoặc do bất kỳ nguyên nhân nào<br/>- 9: Khám chữa, bệnh dịch vụ*|
|3|ket_qua_dtri|ket_qua_dtri|0️⃣: Theo QĐ4210<br/>*Kết quả điều trị: Mã hóa (1: Khỏi; 2: Đỡ; 3: Không thay đổi; 4: Nặng hơn; 5: Tử vong)*<br/>1️⃣: Theo QĐ4750<br/>*Ghi mã kết quả điều trị, trong đó:<br/>- “1”: Khỏi;<br/>- “2”: Đỡ;<br/>- “3”: Không thay đổi;<br/>- “4”: Nặng hơn;<br/>- “5”: Tử vong;<br/>- “6”: Tiên lượng nặng xin về;<br/>- “7”: Chưa xác định (không thuộc một trong các mã kết quả điều trị nêu trên).<br/>- “8”: Tử vong ngoại viện*|
|4|ma_loaikcb|ma_loaikcb|0️⃣: Theo QĐ4210<br/>*Mã hóa hình thức KCB: (1: khám bệnh; 2: điều trị ngoại trú; 3: điều trị nội trú)*<br/>1️⃣: Theo QĐ4750<br/>*Ghi mã hình thức KBCB theo Bộ mã DMDC do Bộ trưởng Bộ Y tế ban hành. Chi tiết xem tại Phụ lục 1 (Danh mục mã loại hình khám bệnh, chữa bệnh) –* [Quyết định 824/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/80dfedaffd557024c054fd720545a11becd0b537/XML130/Q%C4%90%20824-B%E1%BB%95%20sung%20m%C3%A3%20d%C3%B9ng%20chung.pdf) *ngày 15/02/2023.*|
- Khi xuất dữ liệu `[Excel CV3360 - (Cổng update 27/8/2019)]` tại form XML4750: dựa vào cấu hình trên để lấy dữ liệu theo chuẩn tương ứng đã cấu hình.

:blue_book: Tab 2 xuất dữ liệu mẫu `C79-HD`:

<p align="center"><img src="https://github.com/user-attachments/assets/745791e6-f1dc-4105-ba70-34838c0a1bff" width="70%"></p>

- Dữ liệu từ `XML4750`, xuất lên form đầy đủ theo mẫu `C79-HD: TỔNG HỢP CHI PHÍ KHÁM BỆNH, CHỮA BỆNH CỦA NGƯỜI THAM GIA BẢO HIỂM Y TẾ`.
<p align="center"><img src="https://github.com/user-attachments/assets/4749b265-b83f-4d4f-ba87-854876afc20e" width="70%"><img src="https://github.com/user-attachments/assets/e3a8752e-6ab7-401f-ab33-2bcac1c225a6" width="70%"></p>

- Cấu trúc dữ liệu mẫu `C79-HD`:[^2024-08-16-01]

|STT|TT Cột|Tên cột|Ghi chú|
|:-------:|:-------:|-------|-------|
|1|A|STT|Thứ tự tăng dần|
|2|B|Họ và tên|`=bang1.ho_ten`|
|3|C|Năm sinh|`=LEFT(bang1.ngay_sinh,4)`|
|4|D|Giới tính|Xét: `bang1.gioi_tinh`:<br/>- 1: Nam<br/>- 2: Nữ<br/>- 3: Chưa xác định|
|5|E|Mã thẻ BHYT|`=bang1.ma_the_bhyt`|
|6|G|Mã bệnh|`=bang1.ma_benh_chinh`|
|7|H|Ngày vào|`=bang1.ngay_vao`|
|8|I|Ngày ra|`=bang1.ngay_ra`|
|9|K|Số ngày điều trị thực tế|`=bang1.so_ngay_dtri`|
|10|1|Tổng số tiền chi KCB BHYT thuộc phạm vi hưởng BHYT|`=bang1.t_tongchi_bh`|
|11|2|Tiền khám bệnh|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 13`|
|12|3|Tiền giường|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (14,15,16)`|
|13|4|Tiền xét nghiệm|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 1`|
|14|5|Tiền Chẩn đoán hình ảnh/Thăm dò chức năng|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (2,3)`|
|15|6|Tiền Thủ thuật/phẫu thuật|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (8,18)`|
|16|7|Tiền máu|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 7`|
|17|8|Tiền thuốc|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 4`|
|18|9|Tiền Vật tư y tế|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 10`|
|19|10|Tiền vận chuyển|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 12`|
|20|11|Tổng số tiền đề nghị thanh toán từ quỹ BHYT chuyển cho BHXH tỉnh để thanh toán cơ sở KCB được thanh toán|`= [1] + [2] + [3]`<br/><br/>Trong đó:<br/>1️⃣ Đối với thuốc/máu:<br/>Nếu `dmthuoc.loainguonbhyt = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[1] = 0`, ngược lại `[1] = SUM(bang2.t_bhtt)`<br/><br/>2️⃣ Đối với VTYT (`bang3.ma_nhom = 10`):<br/>Nếu `dmthuoc.loainguonbhyt = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = 0`, ngược lại `[2] = SUM(bang3.t_bhtt)`.<br/><br/>3️⃣ Đối với cận lâm sàng (`bang3.ma_nhom <> 10`):<br/>Nếu `dmcls.loainguonbhyt = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = 0`, ngược lại `[3] = SUM(bang3.t_bhtt)`.|
|21|12|Tổng số tiền đề nghị thanh toán từ quỹ BHYT, được thanh toán từ nguồn tập trung của BHXH Việt Nam. Từ năm 2019 đó là chi phí thuốc kháng HIV thanh toán từ quỹ BHYT|`= [1] + [2] + [3]`<br/><br/>Trong đó:<br/>1️⃣ Đối với thuốc/máu:<br/>Nếu `dmthuoc.loainguonbhyt = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[1] = SUM(bang2.t_bhtt)`, ngược lại `[1] = 0`.<br/><br/>2️⃣ Đối với VTYT (`bang3.ma_nhom = 10`):<br/>Nếu `dmthuoc.loainguonbhyt = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = SUM(bang3.t_bhtt)` ngược lại `[2] = 0`.<br/><br/>3️⃣ Đối với cận lâm sàng (`bang3.ma_nhom <> 10`):<br/>Nếu `dmcls.loainguonbhyt = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = SUM(bang3.t_bhtt)` ngược lại `[3] = 0`.|
|22|13|Tiền chi thuốc, hóa chất, vật tư y tế được cấp phép lưu hành tại Việt Nam và các dịch vụ kỹ thuật y tế được cấp có thẩm quyền phê duyệt trong quyền lợi được hưởng theo quy định tại Khoản 2, Điều 10 Nghị định số 70/2015/NĐ-CP của đối tượng quân nhân, công an, cơ yếu||
|23|14|Số tiền người bệnh cùng chi trả|`=bang1.t_bncct`|
|24|15|Số tiền trong phạm vi BHYT do người bệnh tự trả|`=bang1.t_bntt`|
|25|16|Số tiền từ nguồn khác của chi phí thanh toán từ nguồn tập trung như thuốc kháng HIV.|`= [1] + [2] + [3]`[^2024-10-28-01]<br/><br/>Trong đó:<br/>1️⃣ Đối với thuốc/máu:<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh = 0` thì `[1] = SUM(bang2.t_bntt)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh <> 0` thì `[1] = SUM(bang2.t_nguonkhac)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` thì `[1] = 0`.<br/><br/>2️⃣ Đối với VTYT (`bang3.ma_nhom = 10`):<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = SUM(bang3.t_nguonkhac)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = 0`.<br/><br/>3️⃣ Đối với cận lâm sàng (`bang3.ma_nhom <> 10`):<br/>⇒ Nếu `dmcls.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = SUM(bang3.t_nguonkhac)`<br/>⇒ Nếu `dmcls.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = 0`.|
|26|17|Số tiền từ nguồn ngoài khác thanh toán, như chi phí được thanh toán từ các nguồn tài trợ khác (như thuốc Glivec).|`= [1] + [2] + [3]`<br/><br/>Trong đó:<br/>1️⃣ Đối với thuốc/máu:<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh = 0` thì `[1] = SUM(bang2.t_bntt)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh <> 0` thì `[1] = SUM(bang2.t_bncct)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` thì `[1] = 0`.<br/><br/>2️⃣ Đối với VTYT (`bang3.ma_nhom = 10`):<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = SUM(bang3.t_bncct)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = 0`.<br/><br/>3️⃣ Đối với cận lâm sàng (`bang3.ma_nhom <> 10`):<br/>⇒ Nếu `dmcls.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = SUM(bang3.t_bncct)`<br/>⇒ Nếu `dmcls.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = 0`.|
|27|18|Số tiền người bệnh tự chi trả ngoài phạm vi được BHYT||

[^2024-10-30-01]: Thay đổi ngày 30/10/2024: Thay đổi cách tính cột: `t_bntt` khi xuất `Excel3360`. Chi tiết yêu cầu [#7](https://github.com/dh-his/Phieu_Yeu_Cau/issues/7)
[^2024-10-29-01]: Thay đổi ngày 29/10/2024: Diễn giải chi tiết giá trị các cột: `ngay_sinh`,  `ma_lydo_vvien`, `ket_qua_dtri`, `ma_loaikcb` khi cấu hình để xuất `Excel3360`. Chi tiết yêu cầu [#5](https://github.com/dh-his/Phieu_Yeu_Cau/issues/5)
[^2024-10-28-02]: Thay đổi ngày 28/10/2024: Bổ sung diễn giải cho cột `ma_lydo_vvien` khi cấu hình để xuất `Excel3360`. Chi tiết yêu cầu [#5](https://github.com/dh-his/Phieu_Yeu_Cau/issues/5)
[^2024-10-28-01]: Thay đổi ngày 28/10/2024: Điều chỉnh `Số tiền từ nguồn khác của chi phí thanh toán từ nguồn tập trung như thuốc kháng HIV.` của mẫu `C79-HD` cột 16 (thay đổi từ `t_bncct` sang `t_nguonkhac`). Chi tiết lỗi [#5](https://github.com/dh-his/Ghi_Nhan_Loi/issues/5#event-14860577861)
[^2024-10-16-01]: Thay đổi ngày 16/10/2024: Bổ sung điều kiện xuất `Excel3360` đối với cột `ma_loaikcb` đối với `ma_loai_kcb = '04'`. Chi tiết lỗi [#701](https://github.com/dh-hos/To_Lap_Trinh/issues/701)
[^2024-10-25-01]: Thay đổi ngày 25/10/2024: Bổ sung chức năng cấu hình xuất `Excel3360` cho các cột: `ngay_sinh`, `ma_lydo_vvien`, `ket_qua_dtri` và `ma_loaikcb`. Chi tiết lỗi [#364](https://github.com/dh-hos/Yeu_cau_ho_tro/issues/364)
[^2024-10-16-01]: Thay đổi ngày 16/10/2024: Bổ sung điều kiện xuất `Excel3360` đối với cột `ma_loaikcb` đối với `ma_loai_kcb = '04'`. Chi tiết lỗi [#701](https://github.com/dh-hos/To_Lap_Trinh/issues/701)
[^2024-10-04-01]: Thay đổi ngày 04/10/2024: Thay đổi điều kiện xuất `Excel3360` đối với cột `t_cdha` gồm `ma_nhom IN (2,3)`. Chi tiết lỗi [#134](https://github.com/dh-hos/dhg.hospitalreports/issues/134)
[^2024-09-14]: Thay đổi ngày 14/09/2024: Bổ sung điều kiện xuất Excel3360 theo 4750 và 4210. Chi tiết yêu cầu [#95](https://github.com/dh-hos/To_Ho_Tro/issues/95)
[^2024-09-13-04]: Thay đổi ngày 13/09/2024: Bổ sung điều kiện cột `ma_lydo_vvien` khi xuất dữ liệu `Excel 3360`. Chi tiết yêu cầu [#95](https://github.com/dh-hos/To_Ho_Tro/issues/95)
[^2024-09-13-03]: Thay đổi ngày 13/09/2024: Bổ sung điều kiện cột `ket_qua_dtri` khi xuất dữ liệu `Excel 3360`. Chi tiết yêu cầu [#95](https://github.com/dh-hos/To_Ho_Tro/issues/95)
[^2024-09-13-02]: Thay đổi ngày 13/09/2024: Bổ sung điều kiện cột `ma_loaikcb` khi xuất dữ liệu `Excel 3360`. Chi tiết yêu cầu [#95](https://github.com/dh-hos/To_Ho_Tro/issues/95)
[^2024-09-13-01]: Thay đổi ngày 13/09/2024: Bổ sung điều kiện cột `ngay_sinh` khi xuất dữ liệu `Excel 3360`, chỉ lấy 4 ký tự bên trái cột `bang1.ngay_sinh` đối với người bệnh chỉ có năm sinh. Chi tiết yêu cầu [#126](https://github.com/dh-hos/dhg.hospitalreports/issues/126)
[^2024-09-09-01]: Thay đổi ngày 09/09/2024: Bổ sung điều kiện ràng buộc khi load dữ liệu: `bang1.t_tongchi_bh > 0`. Chi tiết yêu cầu [#123](https://github.com/dh-hos/THEO-DOI-THUC-HIEN/issues/123)
[^2024-09-06-01]: Thay đổi ngày 06/09/2024: Điều chỉnh điều kiện cột `ngay_sinh` khi xuất dữ liệu `Excel 3360`, chỉ lấy 8 ký tự bên trái cột `bang1.ngay_sinh`. Chi tiết yêu cầu [#126](https://github.com/dh-hos/dhg.hospitalreports/issues/126)
[^2024-08-30]: Thay đổi ngày 30/08/2024: Điều chỉnh điều kiện cột `tinh_trang_rv` được lấy dữ liệu từ `bang1.ma_loai_rv`.
[^2024-08-16-01]: Thay đổi ngày 16/08/2024: Thay đổi cách tính cột `[11], [12], [16], [17]` từ `pshdxn.sdnguonkhac` thành `bang2.sdnguonkhac` *(đối với thuốc/máu)* và `bang3.sdnguonkhac` *(đối với VTYT)*, từ `chidinhcls.sdnguonkhac` thành `bang3.sdnguonkhac`.
[^2024-08-11]: Thay đổi ngày 11/08/2024: Thay đổi số cột xuất Excel 3360 (Cổng update 27/8/2019) chỉ có 41 cột.
