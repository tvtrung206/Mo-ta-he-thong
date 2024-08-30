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
- Tiêu chí thời gian thống kê: được chọn từ `xml130.bang1.ngay_ttoan`, `xml130.bang1.thang_qt` và `xml130.bang1.nam_qt`. Các bảng dữ liệu còn lại được load tham chiếu từ cột `ma_lk` của bảng hiện tại tương ứng với `xml1.ma_lk` của bảng 1.
- Tại tab `bảng 1` (XML1): Bổ sung cột `checkbox` cho phép người dùng chọn hồ sơ cần xuất dữ liệu ra file XML. Với các hồ sơ đã chọn, bổ sung các Button xuất: `[XML 1 bệnh nhân 1 file]`, `[XML file tổng hợp]`, `[Excel CV3360 - (Cổng update 27/8/2019)]`.
<p align="center"><img src="https://github.com/user-attachments/assets/94722470-a31b-4e19-ad2e-c6472c8e05a0" width="70%"></p>

- Dữ liệu xuất XML  theo chuẩn và quy định tại Công văn [ 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024).
- Dữ liệu xuất file Excel Công văn [3360/BHXH-CSYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/CONGVAN-YEUCAU/CV%203360_BHXH-CSYT_ngay0492015.pdf), do BHXH Việt Nam ban hành ngày 04 tháng 09 năm 2015: Cập nhật mẫu Excel  từ Cổng giám định BHYT ngày 27/8/2019, cụ thể:

|STT|Chỉ tiêu|Kiểu dữ liệu (theo QĐ4750)|Diễn giải (CV3360)|Ghi chú|
|:-------:|-------|-------|-------|-------|
|1|stt|NUMERIC(10,0)|Số thứ tự bệnh nhân từ 1 đến hết||
|2|ma_bn|VARCHAR(100)|Mã số BN quy định tại CSKCB|`=bang1.ma_bn`|
|3|ho_ten|VARCHAR(255)|Họ tên người bệnh viết bằng chữ thường.|`=bang1.ho_ten`|
|4|ngay_sinh|VARCHAR(12)|Ngày sinh ghi trên thẻ gồm 8 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày (nếu không có ngày sinh thì ghi năm sinh: 4 ký tự)|`=bang1.ngay_sinh`|
|5|gioi_tinh|NUMERIC(1,0)|Giới tính: mã hóa bằng 1 chữ số (Nam = 1 Nữ = 2) |`=bang1.gioi_tinh`|
|6|dia_chi|VARCHAR(1024)|Địa chỉ trên thẻ BHYT đối với trẻ em không có thẻ ghi đầy đủ địa chỉ trên giấy tờ thay thế (tối thiểu phải có địa chỉ về xã huyện tỉnh của trẻ).|`=bang1.dia_chi`|
|7|ma_the|VARCHAR(50)|Mã thẻ BHYT do cơ quan BHXH cấp không thay đổi không thêm bớt các ký tự|`=bang1.ma_the_bhyt`|
|8|ma_dkbd|VARCHAR(50)|Mã cơ sở KCB ban đầu ghi đúng 5 ký tự trên thẻ BHYT|`=bang1.ma_dkbd`|
|9|gt_the_tu|VARCHAR(50)|Thời điểm thẻ có giá trị gồm 8 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày. Ví dụ: ngày 30/04/2015 được hiển thị là 20150430|`=bang1.gt_the_tu`|
|10|gt_the_den|VARCHAR(50)|Thời điểm thẻ hết giá trị gồm 8 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày. Ví dụ: ngày 31/05/2015 được hiển thị là 20150531|`=bang1.gt_the_den`|
|11|ma_benh|VARCHAR(7)|Mã bệnh chính được mã hóa theo ICD X|`=bang1.ma_benh_chinh`|
|12|ma_benhkhac|VARCHAR(100)|Mã bệnh khác mã hóa theo ICD X nếu có nhiều mã ICD thì mỗi mã đuợc phân cách bằng ký tự “;”|`=bang1.ma_benh_kt`|
|13|ma_lydo_vvien|VARCHAR(4)|Mã hóa lý do đến khám bệnh: 1 = đúng tuyến; 2 = cấp cứu; 3 = trái tuyến|`=bang1.ma_doituong_kcb`|
|14|ma_noi_chuyen|VARCHAR(5)|Mã cơ sở KCB chuyển người bệnh đến (Mã do cơ quan BHXH cấp)|`=bang1.ma_noi_di`|
|15|ngay_vao|VARCHAR(12)|Thời gian đến khám hoặc nhập viện theo ngày giờ; gồm 12 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày + 2 ký tự giờ (24 giờ) + 2 ký tự phút. Ví dụ: ngày 30/06/2015 08:20 được hiển thị là 201506300820|`=bang1.ngay_vao`|
|16|ngay_ra|VARCHAR(12)|Ngày giờ ra viện; gồm 12 ký tự; 4 ký tự năm + 2 ký tự tháng + 2 ký tự ngày + 2 ký tự giờ (24 giờ) + 2 ký tự phút. Ví dụ: ngày 31/07/2015 16:20 được hiển thị là 201507311620|`=bang1.ngay_ra`|
|17|so_ngay_dtri|NUMERIC(3,0)|Số ngày điều trị trong đợt KCB ngoại trú hoặc nằm viện nội trú (= ngày ra - ngày vào). Trường hợp điều trị nội trú nhưng có một số ngày không nằm viện thì tính theo ngày nằm viện thực tế|`=bang1.so_ngay_dtri`|
|18|ket_qua_dtri|NUMERIC(1,0)|Kết quả điều trị: Mã hóa (1: Khỏi; 2: Đỡ; 3: Không thay đổi; 4: Nặng hơn; 5: Tử vong)|`=bang1.ket_qua_dtri`|
|19|tinh_trang_rv|NUMERIC(1,0)|Tình trạng ra viện: Mã hóa (1: Ra viện; 2: Chuyển viện; 3: Trốn viện; 4: Xin ra viện)|`=bang1.ma_loai_rv`[^2024-08-30]|
|20|t_tongchi|NUMERIC(15,2)|Tổng chi phí KCB BHYT trong lần/đợt điều trị|`=bang1.t_tongchi_bh`|
|21|t_xn|NUMERIC(15,2)|Tiền xét nghiệm|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 1`|
|22|t_cdha|NUMERIC(15,2)|Tiền chẩn đoán hình ảnh và thăm dò chức năng|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 2`|
|23|t_thuoc|NUMERIC(15,2)|Tiền thuốc và dịch truyền|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 4`|
|24|t_mau|NUMERIC(15,2)|Tiền máu và chế phẩm của máu|`=SUM(bang2.thanh_tien_bh)` đối với `bang2.ma_nhom = 7`|
|25|t_pttt|NUMERIC(15,2)|Tiền phẫu thuật và thủ thuật|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom IN (8,18)`|
|26|t_vtyt|NUMERIC(15,2)|Tiền vật tư y tế|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 10`|
|27|t_dvkt_tyle|NUMERIC(15,2)|Tiền dịch vụ kỹ thuật thanh toán theo tỷ lệ||
|28|t_thuoc_tyle|NUMERIC(15,2)|Tiền thuốc thanh toán theo tỷ lệ||
|29|t_vtyt_tyle|NUMERIC(15,2)|Tiền vật tư y tế thanh toán theo tỷ lệ||
|30|t_kham|NUMERIC(15,2)|Tiền công khám bệnh ngoại trú hoặc tiền giường nội trú|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 13`|
|31|t_vchuyen|NUMERIC(15,2)|Tiền vận chuyển|`=SUM(bang3.thanh_tien_bh)` đối với `bang3.ma_nhom = 12`|
|32|t_bntt|NUMERIC(15,2)|Số tiền người bệnh thanh toán (Ghi số tiền người bệnh chi trả bao gồm cùng chi trả tự trả khi khám bệnh chữa bệnh không đúng tuyến số tiền tự trả đối với các dịch vụ y tế áp dụng tỷ lệ thanh toán)|`=bang1.t_bntt + bang1.t_bncct`|
|33|t_bhtt|NUMERIC(15,2)|Tiền đề nghị cơ quan BHXH thanh toán (gồm cả chi phí ngoài định suất).|`=bang1.t_bhtt`|
|34|t_ngoaids|NUMERIC(15,2)|Tiền thanh toán ngoài định suất (không bao gồm tiền BN cùng chi trả)|`=bang1.t_bhtt_gdv`|
|35|ma_khoa|VARCHAR(50)|Ghi mã khoa theo quy định tại bảng 7 Quyết định số 2348/BYT-BH ngày 10/4/2015 của Bộ Y tế.|`=bang1.ma_khoa`|
|36|nam_qt|NUMERIC(4,0)|Năm đề nghị BHXH thanh toán|`=bang1.nam_qt`|
|37|thang_qt|NUMERIC(2,0)|Tháng đề nghị BHXH thanh toán|`=bang1.thang_qt`|
|38|ma_khuvuc|VARCHAR(2)|Ghi mã nơi sinh sống trên thẻ BHYT “K1/K2/K3” (nếu có)|`=bang1.ma_khuvuc`|
|39|ma_loaikcb|VARCHAR(2)|Mã hóa hình thức KCB: (1: khám bệnh; 2: điều trị ngoại trú; 3: điều trị nội trú)|`=bang1.ma_loai_kcb`|
|40|ma_cskcb|VARCHAR(5)|Mã cơ sở KCB nơi điều trị: Ghi đúng 5 ký tự mã cơ sở KCB do BHXH VN cung cấp|`=bang1.ma_cskcb`|
|41|t_nguonkhac[^2024-08-11]|NUMERIC(15,2)|Ghi tổng số tiền các nguồn khác chi trả ngoài phạm vi chi trả của quỹ BHYT|`=bang1.t_nguonkhac`|


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
|25|16|Số tiền từ nguồn khác của chi phí thanh toán từ nguồn tập trung như thuốc kháng HIV.|`= [1] + [2] + [3]`<br/><br/>Trong đó:<br/>1️⃣ Đối với thuốc/máu:<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh = 0` thì `[1] = SUM(bang2.t_bntt)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh <> 0` thì `[1] = SUM(bang2.t_bncct)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` thì `[1] = 0`.<br/><br/>2️⃣ Đối với VTYT (`bang3.ma_nhom = 10`):<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = SUM(bang3.t_bncct)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = 0`.<br/><br/>3️⃣ Đối với cận lâm sàng (`bang3.ma_nhom <> 10`):<br/>⇒ Nếu `dmcls.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = SUM(bang3.t_bncct)`<br/>⇒ Nếu `dmcls.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = 0`.|
|26|17|Số tiền từ nguồn ngoài khác thanh toán, như chi phí được thanh toán từ các nguồn tài trợ khác (như thuốc Glivec).|`= [1] + [2] + [3]`<br/><br/>Trong đó:<br/>1️⃣ Đối với thuốc/máu:<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh = 0` thì `[1] = SUM(bang2.t_bntt)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` và `bang2.tyle_tt_bh <> 0` thì `[1] = SUM(bang2.t_bncct)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang2.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]` thì `[1] = 0`.<br/><br/>2️⃣ Đối với VTYT (`bang3.ma_nhom = 10`):<br/>⇒ Nếu `dmthuoc.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = SUM(bang3.t_bncct)`.<br/>⇒ Nếu `dmthuoc.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[2] = 0`.<br/><br/>3️⃣ Đối với cận lâm sàng (`bang3.ma_nhom <> 10`):<br/>⇒ Nếu `dmcls.loainguonkhac = 1` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = SUM(bang3.t_bncct)`<br/>⇒ Nếu `dmcls.loainguonkhac = 0` và `bang3.sdnguonkhac = 1` và `[psdangky.sdnguonkhac = 1 hoặc bnnoitru.sdnguonkhac = 1]`thì `[3] = 0`.|
|27|18|Số tiền người bệnh tự chi trả ngoài phạm vi được BHYT||

[^2024-08-30]: Thay đổi ngày 30/08/2024: Điều chỉnh điều kiện cột `tinh_trang_rv` được lấy dữ liệu từ `bang1.ma_loai_rv`.
[^2024-08-16-01]: Thay đổi ngày 16/08/2024: Thay đổi cách tính cột `[11], [12], [16], [17]` từ `pshdxn.sdnguonkhac` thành `bang2.sdnguonkhac` *(đối với thuốc/máu)* và `bang3.sdnguonkhac` *(đối với VTYT)*, từ `chidinhcls.sdnguonkhac` thành `bang3.sdnguonkhac`.
[^2024-08-11]: Thay đổi ngày 11/08/2024: Thay đổi số cột xuất Excel 3360 (Cổng update 27/8/2019) chỉ có 41 cột.
