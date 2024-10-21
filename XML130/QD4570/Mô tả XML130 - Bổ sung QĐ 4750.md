<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: Quy định chuẩn và định dạng dữ liệu đầu ra phục vụ việc quản lý, giám định, thanh toán chi phí khám bệnh, chữa bệnh và giải quyết các chế độ liên quan theo [Quyết định 130/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/130Q%20.signed.pdf) ngày 18/01/2023 của Bộ Y tế

#### Bổ sung theo [Quyết định 4750/QD-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/4750.pdf) của Bộ Y tế ngày 29/12/2023

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)

###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Cấu trúc các bảng theo quy định của QĐ 4750 và theo dõi cập nhật thông tin chi tiết tại:** [Excel 4750](https://docs.google.com/spreadsheets/d/1H8Y8rsTMqs0QIflxjpDAHQ882tNGMTHl/edit#gid=255000288)

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

:blue_book: Cập nhật cấu trúc, bổ sung hỗ trợ lưu trữ dữ liệu XML theo [Quyết định 130/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/130Q%20.signed.pdf) (Cập nhật theo [Quyết định 4750/QD-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/4750.pdf)).

- Script tạo schema: `CREATE SCHEMA xml130`
- Tạo 17 table tương ứng với: 1 bảng lưu trữ thông tin chung, 1 bảng check-in và 15 bảng theo các chỉ tiêu. <= Chi tiết tại Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750 (Click vào từng table để xem chi tiết phụ lục)

1. [Table psxml](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.psxml%20-%20[Ph%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750].md): Bảng lưu thông tin chung, ghi nhận thông tin sau khi dữ liệu XML đã được xuất (đã được lưu trữ từ bảng 1 đến bảng 15) hoặc cập nhật các trạng thái có liên quan đến hồ sơ.
2. [Table checkin](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang00checkin%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Bảng chỉ tiêu dữ liệu về trạng thái khám bệnh, chữa bệnh (Bảng check-in);
3. [Table bang1](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang01%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu tổng hợp khám bệnh, chữa bệnh;
4. [Table bang2](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang02%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu chi tiết thuốc;
5. [Table bang3](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang03%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu chi tiết dịch vụ kỹ thuật và vật tư y tế;
6. [Table bang4](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang04%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu chi tiết dịch vụ cận lâm sàng;
7. [Table bang5](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang05%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu chi tiết diễn biến lâm sàng;
8. [Table bang6](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang06%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu hồ sơ bệnh án chăm sóc và điều trị HIV/AIDS;
9. [Table bang7](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang07%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giấy ra viện;
10. [Table bang8](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang08%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu tóm tắt hồ sơ bệnh án;
11. [Table bang9](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang09%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giấy chứng sinh;
12. [Table bang10](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang10%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giấy chứng nhận nghỉ dưỡng thai;
13. [Table bang11](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang11%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giấy chứng nhận nghỉ hưởng bảo hiểm xã hội;
14. [Table bang12](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang12%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giám định y khoa;
15. [Table bang13](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang13%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giấy chuyển tuyến khám bệnh, chữa bệnh bảo hiểm y tế;
16. [Table bang14](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang14%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu dữ liệu giấy hẹn khám lại;
17. [Table bang15](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang15%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md): Chỉ tiêu thông tin quản lý điều trị bệnh lao;

:blue_book: Cập nhật cấu trúc, bổ sung cột lưu trữ mã [ICD-9 CM](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/CONGVAN-YEUCAU/QD4440-Quyet%20%C4%91inh%20ban%20hanh%20ICD-9%20CM%20th%C3%AD%20%C4%91i%E1%BB%83m%20DRG.signed.pdf). Danh mục chuyển đổi giữa danh mục kỹ thuật tương đương và phân loại phẫu thuật, thủ thuật quốc tế ICD-9 CM. Bổ sung các cột vào table **dmcls**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
| 1 | maicd9 | VARCHAR(20) | Mã ICD-9 CM |
| 2 | don_vi_do | VARCHAR(50) | Ghi đơn vị đo của chỉ số xét nghiệm, chẩn đoán hình ảnh, thăm dò chức năng theo Phụ lục 11 ban hành kèm theo [Quyết định số 7603/QĐ-BYT](https://syt.binhdinh.gov.vn/index.php/vi/van-ban-chi-dao-dieu-hanh/detail/Quyet-dinh-ve-viec-ban-hanh-bo-ma-danh-muc-dung-chung-ap-dung-trong-quan-ly-kham-benh-chua-benh-va-thanh-toan-bao-hiem-y-te-Phien-ban-so-6-261/) ngày 25 tháng 12 năm 2018 của Bộ trưởng Bộ Y tế. Đối với các chỉ số không có đơn vị đo thì để trống trường thông tin này. |
|3|ma_xang_dau [^2024-07-04-02]| VARCHAR(20) |Ghi mã loại xăng, dầu để tính chi phí vận chuyển người bệnh, ghi theo Bộ mã DMDC do Bộ trưởng Bộ Y tế ban hành. *Áp dụng cho các cận lâm sàng chuyển viện.*|

:blue_book: Cập nhật cấu trúc table **psdangky**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
| 1 | trangthaichuyentuyen | NUMERIC(1,0) | Ghi nhận trạng thái chuyển tuyến từ tuyến dưới chuyển lên. Giá trị:<br/>- (null): không có thông tin chuyển tuyến.<br/>- 1: Chuyển tuyến theo yêu cầu.<br/>- 2: Chuyển tuyến đúng quy định (vượt khả năng điều trị/ngoài phạm vi chuyên môn của cơ sở KCB).<br/>- 3: Hẹn tái khám.<br/>- 4: Chuyển tuyến người bệnh khám và điều trị bệnh lao.<br/>- 5: Giấy hẹn lãnh thuốc.<br/>- 6: Giấy hẹn lãnh thuốc (lao).[^2024-09-12-01]|
|2|giayxacnhancutru|NUMERIC(1,0)|Ghi nhận trạng thái người bệnh ngoài tỉnh đến khám chữa bệnh có giấy xác nhận (giấy tờ chứng minh đang ở tại địa phương khác trong thời gian đi công tác, làm việc lưu động, học tập trung theo các hình thức đào tạo, chương trình đào tạo, tạm trú, …). Giá trị:<br/>- (null) hoặc 0: Không có giấy xác nhận.<br/>- 1: Có giấy xác nhận.|
|3|giayluu|BYTEA|Lưu trữ: Giấy xác nhận cư trú (do người dùng scan hoặc chụp).|
|4|giayluuchuyentuyen|BYTEA|Lưu trữ: Giấy chuyển tuyến/Giấy hẹn tái khám|

:blue_book: Cập nhật cấu trúc table **dmbenhnhan**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|nhom_mau|VARCHAR(5)|Ghi nhóm máu của người bệnh trong trường hợp có thông tin. Giá trị gồm: A; A+; A-; B; B+; B-; AB; AB+; AB-; O; O+; O-; Rh; Rh+; Rh-|

:blue_book: Cập nhật cấu trúc table **dmthuoc**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|ma_pp_chebien|VARCHAR(255)|Ghi mã phương pháp chế biến vị thuốc cổ truyền theo Bộ mã DMDC do Bộ trưởng Bộ Y tế ban hành (Phương pháp chế biến vị thuốc cổ truyền theo quy định tại [Thông tư số 30/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=135619) của Bộ trưởng Bộ Y tế).|
|2|ma_cskcb_thuoc|VARCHAR(10)|- Trường hợp do thiên tai, dịch bệnh phải chuyển thuốc đến cơ sở KBCB khác để điều trị cho người bệnh thì ghi C.XXXXX (XXXXX là mã cơ sở KBCB nơi chuyển thuốc đi).<br/>- Trường hợp thuốc thanh toán ngoài giá dịch vụ cận lâm sàng chuyển thực hiện tại cơ sở KBCB khác thì ghi K.XXXXX (XXXXX là mã cơ sở KBCB nơi thực hiện dịch vụ cận lâm sàng).<br/>- Trường hợp chế phẩm máu có sử dụng bộ dụng cụ gạn tách (kít tách tiểu cầu, bạch cầu…) hoặc xét nghiệm được thanh toán ngoài giá đơn vị máu, chế phẩm máu quy định tại tiết d khoản 10 Điều 3 [Thông tư số 17/2020/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=147191) ngày 12/11/2020 của Bộ Y tế thì ghi M.XXXXX (trong đó XXXXX là mã cơ sở KBCB của đơn vị cung cấp máu).<br/>- Trường hợp cơ sở KCB sử dụng thuốc của hạng bệnh hạng cao hơn được kê đơn, chỉ định bằng hình thức hội chẩn từ xa theo quy định tại [Thông tư số 20/2022/TT-BYT](https://danang.baohiemxahoi.gov.vn/vanban/Pages/default.aspx?ItemID=8665) thì ghi HC.XXXXX (trong đó XXXXX là mã cơ sở KCB nơi thực hiện kê đơn, chỉ định thuốc)|
|3|tt_thau4750[^2024-06-25-91]|VARCHAR|Ghi nhận thông tin thầu theo 4750.|

:blue_book: Cập nhật cấu trúc table **pshdxn**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|lieu_dung|VARCHAR(1024)|Ghi liều dùng thuốc cho người bệnh, cụ thể:<br/>- Đối với ngoại trú, được thể hiện bằng: số lượng thuốc dùng trong một lần sử dụng * số lần trong ngày _ số ngày sử dụng [tổng số thuốc/ngày].<br/>Ví dụ: liều dùng của thuốc A: 2 viên/lần, 2 lần/ngày, sử dụng trong 5 ngày thì được ghi như sau: 2 viên/lần _ 2 lần/ngày _ 5 ngày [4 viên/ngày].<br/>- Đối với nội trú, được thể hiện bằng: số lượng thuốc dùng trong một lần sử dụng _ số lần trong ngày \_ 01 ngày [tổng số thuốc/ngày].<br/>**Lưu ý**:<br/>- Trường hợp liều thuốc thay đổi trong ngày theo từng lần sử dụng thì ghi chi tiết.<br/>Ví dụ: liều dùng của thuốc A, sáng: 3 viên, chiều: 2 viên, tối: 1 viên. Như vậy, sẽ ghi như sau: Sáng: 3 viên, Chiều: 2 viên, Tối: 1 viên [6 viên/ngày].|

:blue_book: Cập nhật cấu trúc table **qtdieutri**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|giai_doan_benh|VARCHAR|Ghi giai đoạn bệnh trong trường hợp người bệnh đã được cơ sở KBCB xác định giai đoạn bệnh.|

:blue_book: Cập nhật cấu trúc table **ttcon**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|lan_sinh [^2024-07-24-02]|NUMERIC(2,0)|Ghi số lần sinh con (tính cả lần sinh này).|
|2|sinhcon_phauthuat [^2024-07-24-03]|NUMERIC(1,0)|Ghi:<br/>- Mã "1": sinh con phải phẫu thuật;<br/>- Mã "0": sinh con không phải phẫu thuật.|
|3|sinhcon_duoi32tuan [^2024-07-24-04]|NUMERIC(1,0)|Ghi:<br/>- Mã "1": sinh con dưới 32 tuần tuổi;<br/>- Mã "0" là không sinh con dưới 32 tuần tuổi.|

:blue_book: Cập nhật cấu trúc: **bổ sung tham số**
| STT | TÊN THAM SỐ | KIỂU |PHÂN HỆ| DIỄN GIẢI |
|:-------:|-------|:-------:|-------|-------|
|1|ma_ttdv|Chuỗi|Tham số chung|Mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được người đứng đầu cơ sở KBCB ủy quyền được ký và đóng dấu của cơ sở KBCB|
|2|ma_xang_dau [^2024-07-04-01]|Chuỗi|Tham số chung|Mã xăng dầu mặc định (sử dụng cho trường hợp mã xăng dầu của cận lâm sàng chuyển viện trong danh mục chưa cấu hình). Ghi mã loại xăng, dầu để tính chi phí vận chuyển người bệnh, ghi theo Bộ mã DMDC do Bộ trưởng Bộ Y tế ban hành.|
|3|ma_benh_kt.soluong [^2024-07-12-01]|Số|Tham số chung|Số lượng mã bệnh ICD10 phụ tối đa cho 1 lần khám, chữa bệnh.|
|4|ma_loai_kcb.ba_ngoai_ngay [^2024-07-24-01]|Số|Tham số chung|Hỗ trợ xuất XML130 (QĐ4750) cho cột [ma_loai_kcb](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/ma_loai_kcb.md) bảng `checkin` và bảng `XML1` đối với người bệnh bệnh án ngoại trú quyết toán ngày. Giá trị:<br/>- `0`: Không áp dụng tham số này, giá trị cột `ma_loai_kcb` sẽ áp dụng theo mô tả tại [ma_loai_kcb](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/ma_loai_kcb.md)[^2024-10-09-01].<br/>- `1`: `ma_loai_kcb = 01` (Khám ngoại trú).<br/>- `2`: `ma_loai_kcb = 02` (bệnh án ngoại trú).|

:blue_book: Cập nhật cấu trúc: bổ sung table **current.psgiamdinhykhoa**
| STT | TÊN CỘT | KIỂU | DIỄN GIẢI | INDEX |
|:-------:|-------|:-------:|-------|:-------:|
|1|mabn|VARCHAR(20)|Mã bệnh nhân|X|
|2|makb|VARCHAR(20)|Mã khám bệnh|X|
|3|maba|VARCHAR(20)|Mã bệnh án||
|4|noitru|NUMERIC(1,0)|0: ngoại trú; 1: nội trú||
|5|nguoi_chu_tri|VARCHAR(255)|Họ và tên người chủ trì trong danh mục người chủ trì hội đồng giám định y khoa đã nhập trên Cổng tiếp nhận của cơ quan BHXH||
|6|chuc_vu|NUMERIC(1,0)|Chức vụ của người chủ trì, trong đó: mã “1”: Chủ tịch; mã “2”: Người ký thay chủ tịch.||
|7|ngay_hop|TIMESTAMP|Ngày họp hội đồng giám định y khoa||
|8|ma_doi_tuong|VARCHAR(20)|Mã đối tượng giám định (BB: Bệnh binh; BHXH1L: Hưởng BHXH 1 lần; BNN: Bệnh nghề nghiệp; CĐHH: Chất độc hóa học; KNLĐH: Nghỉ hưu trước tuổi; KNLĐT: Tuất; NKT: Người khuyết tật; NVQS: Khám tuyển nghĩa vụ quân sự; TB: Thương binh; TH: Giám định tổng hợp; TNLĐ: Tai nạn lao động).<br/>Ghi chú: Trường hợp một đối tượng mà có từ hai mã đối tượng trở lên thì liệt kê các mã đối tượng, giữa các mã đối tượng cách nhau bằng dấu chấm phẩy “;”.||
|9|kham_giam_dinh|NUMERIC(1,0)|Mã khám giám định, trong đó:<br/>- Mã “1”: Khám giám định lần đầu;<br/>- Mã “2”: Khám giám định lại;<br/>- Mã “3”: Khám giám định tái phát;<br/>- Mã “4”: Khám phúc quyết (vượt khả năng chuyên môn, hoặc đối tượng không đồng ý, hoặc theo đề nghị của Cục Quản lý KCB/Cục Người có công/BHXH);<br/>- Mã “5”: Khám phúc quyết lần cuối;<br/>- Mã “6”: Khám bổ sung;<br/>- Mã “7”: Khám vết thương còn sót;<br/>- Mã “8”: Giám định tổng hợp.||
|10|so_bien_ban|VARCHAR(200)|Số thứ tự trong biên bản họp hội đồng giám định y khoa.||
|11|tyle_ttct_cu|NUMERIC(3,0)|Tỷ lệ (%) tổn thương cơ thể do thương tật, bệnh tật, bệnh nghề nghiệp của lần giám định trước (lần gần nhất) theo kết luận của Hội đồng giám định y khoa.<br/>Ghi chú: Trường thông tin này để trống nếu không có tỷ lệ tổn thương cơ thể của lần giám định trước (lần gần nhất).||
|12|dang_huong_che_do|NUMERIC(3,0)|Mã chế độ đang hưởng, trong đó:<br/>- Mã “1”: Thương binh;<br/>- Mã “2”: Bệnh, tật;<br/>- Mã “3”: Bệnh nghề nghiệp;<br/>- Mã “4”: Tai nạn lao động;<br/>- Mã “5”: Chất độc hoá học;<br/>- Mã “6”: Bệnh binh;<br/>- Mã “7”: Khác (không thuộc một trong các đối tượng quy định từ mã “1” đến mã “6” của trường thông tin này).<br/>Ghi chú: <br/>- Trường hợp đang được hưởng cùng lúc nhiều chế độ khác nhau thì ghi mã các chế độ đang được hưởng, phân cách bằng dấu chấm phẩy “;”;<br/>- Trường thông tin này để trống nếu không thuộc một trong các chế độ nêu trên.||
|13|ngay_chung_tu|TIMESTAMP|Ngày chứng từ (ngày họp Hội đồng giám định y khoa)||
|14|so_giay_gioi_thieu|VARCHAR(200)|Số giấy giới thiệu||
|15|ngay_de_nghi|TIMESTAMP|Ngày đề nghị||
|16|ma_donvi|VARCHAR(200)|Mã cơ quan, đơn vị quản lý hoặc cơ quan, đơn vị giới thiệu đối tượng khám giám định y khoa.||
|17|gioi_thieu_cua|VARCHAR(1024)|Tên đầy đủ của cơ quan, đơn vị quản lý hoặc cơ quan, đơn vị giới thiệu đối tượng khám giám định y khoa.||
|18|ket_qua_kham|VARCHAR|Kết quả khám của Hội đồng Giám định y khoa (được thể hiện trong Biên bản giám định y khoa).||
|19|so_van_ban_can_cu|VARCHAR(200)|Số văn bản (Ghi đầy đủ số và ký tự của văn bản) làm căn cứ khám giám định y khoa phù hợp với đối tượng giám định (Ví dụ: Thông tư 34/2012/TTLT-BYT-BLĐTBXH; Thông tư 28/2013/TTLT-BYT-BLDTBXH; Thông tư 20/2016/TTLT-BYT-BLĐTBXH; Thông tư 52/2017/TT-BYT; [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005); [Thông tư số 01/2019/TT-BLĐTBXH](https://vanban.chinhphu.vn/?pageid=27160&docid=196549); Thông tư 45/2014/TTLT-BYT-BLĐTBXH; Nghị định 28/2012/NĐ-CP;…).<br/>Nếu có nhiều văn bản làm căn cứ giám định, kết luận thì ghi đầy đủ các số hiệu văn bản, giữa các số hiệu văn bản phân cách bằng dấu chấm phẩy “;”.||
|20|tyle_ttct_moi|NUMERIC(3,0)|Tỷ lệ (%) tổn thương cơ thể do thương tật, bệnh tật, bệnh nghề nghiệp của lần giám định này theo kết luận của Hội đồng giám định y khoa.||
|21|tong_tyle_ttct|NUMERIC(3,0)|Tổng tỷ lệ tổn thương cơ thể, do thương tật, bệnh tật, bệnh nghề nghiệp (nếu có) theo kết luận của Hội đồng giám định y khoa.<br/>Lưu ý: chỉ ghi trường thông tin này trong trường hợp khám giám định tổng hợp, khám bổ sung, khám vết thương còn sót.||
|22|dang_khuyettat|NUMERIC(1,0)|Mã dạng khuyết tật theo quy định về dạng khuyết tật tại Mẫu số 01 ban hành kèm theo [Thông tư số 01/2019/TT-BLĐTBXH](https://vanban.chinhphu.vn/?pageid=27160&docid=196549) ngày 02/01/2019 của Bộ Lao động – Thương binh – Xã hội, trong đó:<br/>- Mã “1”: Khuyết tật vận động;<br/>- Mã “2”: Khuyết tật nghe, nói;<br/>- Mã “3”: Khuyết tật nhìn;<br/>- Mã “4”: Khuyết tật thần kinh, tâm thần;<br/>- Mã “5”: Khuyết tật trí tuệ;<br/>- Mã “6”: Khuyết tật khác.<br/>Trường thông tin này chỉ ghi trong trường hợp khám giám định người khuyết tật.||
|23|muc_do_khuyettat|NUMERIC(1,0)|Mã mức độ khuyết tật theo quy định về mức độ khuyết tật tại Mẫu số 01 ban hành kèm theo [Thông tư số 01/2019/TT-BLĐTBXH](https://vanban.chinhphu.vn/?pageid=27160&docid=196549) ngày 02/01/2019 của Bộ Lao động – Thương Binh – Xã hội, trong đó:<br/>- Mã “1”: Thực hiện được;<br/>- Mã “2”: Thực hiện được nhưng cần trợ giúp;<br/>- Mã “3”: Không thực hiện được;<br/>- Mã “4: Không xác định được.<br/>Trường thông tin này chỉ ghi trong trường hợp khám giám định người khuyết tật.||
|24|de_nghi|VARCHAR|Nội dung đề nghị.||
|25|duoc_xacdinh|VARCHAR|Ghi chú được xác định, ghi đầy đủ nội dung theo quy định tại khoản 2 Điều 4 [Thông tư số 56/2017/TT-BYT](https://vbpl.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=129005): Đối với các trường hợp không tự kiểm soát hoặc không tự thực hiện được các hoạt động đi lại, mặc quần áo, vệ sinh cá nhân và những việc khác phục vụ nhu cầu sinh hoạt cá nhân hằng ngày mà cần có người theo dõi, trợ giúp, chăm sóc hoàn toàn.||

:blue_book: Cập nhật cấu trúc: bổ sung table `current.dmxa4750`, dữ liệu được lấy dữ liệu từ [danh mục đơn vị hành chính](https://danhmuchanhchinh.gso.gov.vn/Default.aspx) của Tổng Cục Thống Kê [^2024-06-12-01]
| STT | TÊN CỘT | KIỂU |BẮT BUỘC| DIỄN GIẢI | INDEX |
|:-------:|-------|:-------:|:-------:|-------|:-------:|
|1|id|VARCHAR(20)|X|Giá trị: `matinh + mahuyen + maxa`|X|
|2|maxa|VARCHAR(20)|X|Mã xã (5 ký tự)||
|3|tenxa|VARCHAR(255)||Tên xã||
|4|tentienganh|VARCHAR(255)||Tên xã (tiếng Anh)||
|5|cap|VARCHAR(50)||Cấp: Huyện/Phường/Thị trấn/Xã||
|6|mahuyen|VARCHAR(20)|X|Mã huyện (3 ký tự)||
|7|tenhuyen|VARCHAR(255)|X|Tên huyện||
|8|matinh|VARCHAR(20)|X|Mã tỉnh (2 ký tự)||
|9|tentinh|VARCHAR(255)|X|Tên tỉnh||
|10|viettat|VARCHAR(50)||Mã viết tắt||

:blue_book: Cập nhật cấu trúc table **bnnoitru**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|tomtat_kq [^2024-06-28-01]|VARCHAR|Ghi tóm tắt kết quả xét nghiệm cận lâm sàng có giá trị chẩn đoán.|

:blue_book: Cập nhật cấu trúc table **current.phauthuat**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|mamay  [^2024-07-02-01]|VARCHAR(20)|Mã máy (tham chiếu từ cột `dmmamay.mamay`.|

:blue_book: Cập nhật cấu trúc table **current.dmnhanvien**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|thuchien [^2024-07-25-01]|NUMERIC(1,0)|Trạng thái cho phép nhân viên thực hiện cận lâm sàng có `kho IN ('HA','CN','XN')`. Giá trị:<br/>- 0: Không được phép thực hiện.<br/>- 1: Được phép thực hiện.|

:blue_book: Cập nhật cấu trúc table **current.chidinhcls**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|nguoi_thuc_hien [^2024-07-25-03]|VARCHAR(255)|Ghi mã nhân viên y tế thực hiện dịch vụ kỹ thuật (mã hóa theo số Chứng chỉ hành nghề).|

:blue_book: Cập nhật cấu trúc table **current.lichtruc_diagnose**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|duockham [^2024-07-25-06]|NUMERIC(1,0)|Ghi nhận trạng thái được đọc kết quả chẩn đoán hình ảnh/thăm dò chức năng trong lịch trực.|
|2|thuchien [^2024-07-25-07]|NUMERIC(1,0)|Ghi nhận trạng thái được thực hiện chẩn đoán hình ảnh/thăm dò chức năng trong lịch trực.|

:blue_book: Cập nhật cấu trúc table **current.lichtruc_laboratory**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|duockham [^2024-07-25-08]|NUMERIC(1,0)|Ghi nhận trạng thái được đọc kết quả xét nghiệm trong lịch trực.|
|2|thuchien [^2024-07-25-09]|NUMERIC(1,0)|Ghi nhận trạng thái được thực hiện xét nghiệm trong lịch trực.|

:blue_book: Cập nhật cấu trúc table **current.pskhamxn**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|manv_nguoithuchien [^2024-07-28-01]|VARCHAR(20)|Ghi nhận mã nhân viên của người thực hiện xét nghiệm.|

:blue_book: Cập nhật cấu trúc table **current.pstebaotucung**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|manv_nguoithuchien [^2024-07-28-02]|VARCHAR(20)|Ghi nhận mã nhân viên của người thực hiện xét nghiệm tế bào cổ tử cung.|

:blue_book: Cập nhật cấu trúc table **current.pssinhthiet**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|manv_nguoithuchien [^2024-07-28-03]|VARCHAR(20)|Ghi nhận mã nhân viên của người thực hiện xét nghiệm sinh thiết.|

:blue_book: Cập nhật cấu trúc table **current.psdom**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|manv_nguoithuchien [^2024-07-28-04]|VARCHAR(20)|Ghi nhận mã nhân viên của người thực hiện xét nghiệm đờm.|

:blue_book: Cập nhật cấu trúc table **current.pscovid19**: 
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|manv_nguoithuchien [^2024-07-28-05]|VARCHAR(20)|Ghi nhận mã nhân viên của người thực hiện xét nghiệm Covid-19.|

:white_check_mark: **Quy trình áp dụng:**

:blue_book: Thiết kế DLL: **Form Giám định y khoa** (tương ứng cập nhật dữ liệu cho `current.psgiamdinhykhoa`). Tích hợp lên: `Prescription` và `Treatment`.

:blue_book: Module Admin
- Tại form hiệu chỉnh thông tin bệnh nhân, trước khi lưu dữ liệu thông tin bệnh nhân kiểm tra ô `[CMND]` phải đúng định dạng như sau: Định dạng CCCD phải có 9,12 ký tự số hoặc hộ chiếu 8 ký tự bắt đầu là chữ in hoa và 7 ký tự số ở sau.

- Tại tab `[Cấu hình tên chỉ số, mã chỉ số theo Xml (4210)]` của form `[Danh mục cận lâm sàng]`, bổ sung thêm ô text cho phép người dùng nhập/cập nhật `[Đơn vị đo]`, cập nhật tương ứng với cột `dmcls.don_vi_do`. Mở rộng chức năng cấu hình mã chỉ số, tên chỉ số cho kho: `HA (chẩn đoán hình ảnh) và CN (Thăm dò chức năng)`.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/admin-donvido.jpg" width="70%"></p>

- Bổ sung Control trên **Form danh mục CLS** cập nhật giá trị cột `dmcls.maicd9` (tương ứng cột [Mã ICD-9] [phụ lục 3 QĐ 4440](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/CONGVAN-YEUCAU/Phu%20luc%203%20-%20Danh%20muc%20ICD-9%20CM%20Vol3%2019-10-2020.xlsx)). Hỗ trợ script update tự động giá trị cho cột `[maicd9]` dựa vào cột `[Mã tương đương]` phụ lục 3 (tương ứng với `dmcls.macls_byt`).

- Mở rộng chức năng của form `[Danh mục kết quả điều trị]` cho phép người dùng thêm mới. Sửa nhãn `“Mã Medisoft”` thành `“Mã BYT”`.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/admin-00.png"></p>

- Form `[Danh sách nhân viên]`, bổ sung Textbox `[Số BHXH]` cho phép người dùng cập nhật thông tin số BHXH cho nhân viên, dữ liệu tương ứng cột `dmnhanvien.sobhxh`.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/admin_sobhxh.jpg" width="70%"></p>

- Bổ sung thêm menu `[Địa phương (theo QĐ 4750)]`, thiết kế form thể hiện dữ liệu danh mục tương ứng với table `current.dmxa4750`. Thiết kế chức năng cho phép import dữ liệu từ tập tin Excel, cấu trúc và dữ liệu mẫu từ [Danh sách cấp tỉnh kèm theo quận/huyện phường/xã - 11/06/2024.xlsx](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/Danh_sach_cap_tinh_kem_theo_quan_huyen_phuong_xa_11_06_2024.xlsx) (Nguồn: [Tổng Cục Thống Kê](https://danhmuchanhchinh.gso.gov.vn/Default.aspx)). **Lưu ý**: danh mục này chỉ cho phép người dùng cập nhật giá trị cột **[Viết tắt]** (`current.dmxa4750.viettat`), **KHÔNG** được phép thao tác **[Thêm/Xóa]**. [^2024-06-12-02]
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/admin_dmxa_viettat.jpg" width="70%"></p>

- Tại form `[Hiệu chỉnh thông tin bệnh nhân]`: thay đổi cách lấy dữ liệu địa phương từ table `current.dmxa` sang table `current.dmxa4750`, cụ thể: cập nhật giá trị cho `dmbenhnhan.maxa = dmxa4750.id` thay cho cột `dmxa.maxa`.

- Tại form quản lý `[Danh mục mã máy thực hiện CLS]`, bổ sung thêm giá trị cho `[Kho CLS]` là `TT (thủ thuật)` và `PT (phẫu thuật)`. [^2024-07-02-02]
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/b5e3fcc8-935c-42be-9a04-5f69f60f6a83" width="70%"></p>

- Tại form quản lý `[Danh mục Cận lâm sàng]`, bổ sung `Texbox` cho phép người dùng nhập/điều chỉnh `[Mã xăng dầu]`, dữ liệu được lưu trữ tương ứng vào cột `dmcls.ma_xang_dau`. [^2024-07-04-03]

- Cập nhật: [^2024-07-01]<br/>
➡️ Trên form danh mục nhân viên bổ sung chức năng cho phép nhập họ lót nhân viên không có chức danh để thực gửi hồ sơ XML, và kiểm tra thông tuyến.<br/>
➡️ Ưu tiên lấy họ lót không chức danh => họ lót hiện tại. (`current.dmnhanvien: holot_thuan => holot`) khi lấy họ tên bác sĩ hoặc nhân viên khi xuất XML hoặc tra cứu thông tuyến.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/image.png" width="70%"></p>

- Tại form **[Danh mục nhân viên]**, bổ sung CheckBox cho phép cập nhật trạng thái `[Được thực hiện cận lâm sàng]`. Giá trị `checkbox = true` tương ứng với cột `dmnhanvien.thuchien = 1`, ngược lại `dmnhanvien.thuchien = 0`.[^2024-07-25-02]

- Cập nhật: **Form Hiệu chỉnh thông tin bệnh nhân ngoại trú**, Bổ sung Control cập nhật `[Trạng thái chuyển tuyến]` tương ứng với `psdangky.trangthaichuyentuyen`. [^2024-08-03-04]<br/>
1️⃣ Điều kiện ràng buộc khi tham số `tuyenbv <= 2` *(CSKCB tuyến huyện trở xuống)*: <br/>
➡️ Nếu `psdangky.mabvdk = psdangky.mabvkb` thì `psdangky.tuyen = 0`.<br/>
➡️ Nếu `psdangky.mabvdk <> psdangky.mabvkb`, xét người bệnh trong tỉnh hoặc ngoài tỉnh (dựa vào tham số `thetrongtinh`):<br/>
⇒ Người bệnh trong tỉnh: `psdangky.tuyen = 0`  và `psdangky.tuyenxml = 0`.<br/>
⇒ Người bệnh ngoài tỉnh: Nếu `psdangky.giayxacnhancutru = 1` thì  `[psdangky.tuyen = 0 và psdangky.tuyenxml = 0]`, ngược lại `[psdangky.tuyen = 0 và psdangky.tuyenxml = 1]` `(theo Công văn 627, người bệnh trái tuyến được hưởng như đúng tuyến)`.<br/><br/>
2️⃣ Điều kiện ràng buộc khi tham số `tuyenbv = 3` *(CSKCB tuyến tỉnh)*: <br/>
➡️ Nếu `[psdangky.manoigt khác rỗng]` và `psdangky.trangthaichuyentuyen IN (2,3,4,5)` thì `psdangky.tuyen = 0`. *⚠️ Lưu ý:* đối với trường hợp này **KHÔNG** hiển thị message xác nhận có giấy chuyển tuyến, áp dụng cho tất cả các giá trị tham số `tuyenbv` (tương ứng như hình: đã có chọn `mã nơi giới thiệu` và chọn `trạng thái` ở tab *[Chuyển tuyến]*).<br/><p align="center"><img src="https://github.com/user-attachments/assets/e8665eaf-2cd5-46b1-998d-229002cc23c7" width="70%"></p>
➡️ Nếu `[psdangky.manoigt là rỗng]` hoặc [`psdangky.manoigt khác rỗng` và `psdangky.trangthaichuyentuyen = 1`] thì `psdangky.tuyen = 1` *(người bệnh trái tuyến)*.<br/>
➡️ Nếu `[psdangky.manoigt khác rỗng]` *(có giấy chuyển tuyến tuyến dưới)*: cập nhật giá trị mặc định `psdangky.trangthaichuyentuyen = 2`: Chuyển tuyến đúng quy định (vượt khả năng điều trị/ngoài phạm vi chuyên môn của cơ sở KCB).<br/>
➡️ Nếu `psdangky.manoigt` khác rỗng thì bắt buộc cột `psdangky.trangthaichuyentuyen` phải có giá trị  **(bắt buộc phải chọn mới cho hiệu chỉnh)**

- Cập nhật: [^2024-10-11-01]<br/>
➡️ Chức năng `hiệu chỉnh thông tin ngoại trú` và `hiệu chỉnh thông tin nội trú`: tại ô `CMND/CCCD/Hộ chiếu` khi lưu phải kiểm tra điều kiện HỢP LỆ tại ô này như sau (điều kiện tuần tự từ trên xuống):<br/>🔹9 hoặc 12 ký tự đều là chữ số (CMND/CCCD).<br/>🔹8 ký tự (Hộ chiếu): với ký tự đầu tiên phải là ký tự chữ cái IN HOA và 7 ký tự còn lại là chữ số.<br/>🔹9 ký tự (Hộ chiếu): với 2 ký tự đầu là chữ cái (IN HOA hoặc thường) và 7 ký tự còn lại là chữ số.<br/>🔹Các trường hợp còn lại là KHÔNG HỢP LỆ.

:blue_book: Module Register/Prescription khi đăng ký tiếp nhận người bệnh: Bổ sung các Control:

- Bổ sung Control để người tiếp nhận cập nhật trạng thái chuyển tuyến của người bệnh hoặc ghi nhận có giấy hẹn tái khám (tương ứng với cột `psdangky.trangthaichuyentuyen`). **Lưu ý**: <br/>
⇒ Cột `psdangky.trangthaichuyentuyen` chỉ có giá trị khi cột `psdangky.manoigt` khác rỗng **(bắt buộc phải chọn mới cho đăng ký)**.<br/>
⇒ Đối với `psdangky.trangthaichuyentuyen = 5 (Giấy hẹn lãnh thuốc)`[^2024-10-15-01], khi đăng ký khám bệnh chỉ ràng buộc *mã nơi giới thiệu*, các thông tin khác tại `tab chuyển tuyến` là **không bắt buộc**[^2024-09-12-02].<br/>
⇒ Riêng **đối với người bệnh khám lao** (*xem ảnh*) có giấy hẹn lãnh thuốc: khi chọn `psdangky.trangthaichuyentuyen = 6` (Giấy hẹn lãnh thuốc người bệnh lao) thì hỗ trợ check chọn mặc định `[Bệnh nhân khám lao] = true` tại  `tab  [Khám lao]`, đồng thời không bắt buộc phải chọn mã bệnh viện nơi giới thiệu (`psdangky.manoigt`). [^2024-09-13-01]<br/>
⇒ Riêng **đối với người bệnh khám lao** có giấy chuyển tuyến: `psdangky.trangthaichuyentuyen = 4` và `psdangky.manoigt <> ''` *(Chuyển tuyến người bệnh khám và điều trị bệnh lao)* thì hỗ trợ check chọn mặc định `[Bệnh nhân khám lao] = true` tại  `tab  [Khám lao]` và `psdangky.mabv_dieutri_lao = psdangky.manoigt`.[^2024-09-12-03]
<p align="center"><img src="https://github.com/user-attachments/assets/df2e7750-6181-4126-8317-a0cfca8e4d94" width="70%"></p>
- Bổ sung Control cho phép người dùng xác nhận người bệnh có giấy cư trú (áp dụng cho người bệnh ngoài tỉnh), nếu có xác nhận thì cập nhật tương ứng vào cột `psdangky.giayxacnhancutru = 1` và `psdangky.tuyen = 0`.

- Bổ sung Control cho phép người dùng chọn và lưu tập tin (của giấy chuyển tuyến/giấy hẹn tái khám) khi `psdangky.manoigt` khác rỗng. Dữ liệu lưu trữ tập tin vào cột `psdangky.giayluuchuyentuyen`.

- Bổ sung Control cho phép người dùng chọn và lưu tập tin của giấy lưu trú khi `psdangky.giayxacnhancutru = 1`. Dữ liệu lưu trữ tập tin vào cột `psdangky.giayluu`.

- Tại form nhập và hiệu chỉnh thông tin bệnh nhân, trước khi lưu dữ liệu thông tin bệnh nhân kiểm tra ô `[CMND]` phải đúng định dạng như sau: Định dạng CCCD phải có 9,12 ký tự số hoặc hộ chiếu 8 ký tự bắt đầu là chữ in hoa và 7 ký tự số ở sau.

- Đối với `Register`: Tại form **nhập và hiệu chỉnh thông tin bệnh nhân**, bổ sung ComboBox cho phép chọn/cập nhật thông tin `[Nhóm máu]`, dữ liệu được cập nhật tương ứng với cột `dmbenhnhan.nhom_mau`. **Lưu ý**: thiết kế ô nhập `[Nhóm máu]` chung với các thông tin chỉ số sinh hiệu.

- Đối với `Prescription`: Tại form **nhập và hiệu chỉnh thông tin bệnh nhân**, bổ sung ô text cho phép nhập/cập nhật thông tin `[Nhóm máu]`, dữ liệu được cập nhật tương ứng với cột `dmbenhnhan.nhom_mau`. **Lưu ý**: thiết kế ô nhập `[Nhóm máu]` chung với các thông tin chỉ số sinh hiệu.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/dmbenhnhan_nhom_mau.jpg"></p>

- Tại form **nhập/cập nhật thông tin bệnh nhân**: thay đổi cách lấy dữ liệu địa phương từ table `current.dmxa` sang table `current.dmxa4750`, cụ thể: cập nhật giá trị cho `dmbenhnhan.maxa = dmxa4750.id` thay cho cột `dmxa.maxa`.

- Cập nhật: **Form tiếp nhận bệnh (`Register`) và Hiệu chỉnh thông tin bệnh nhân (`Presctiption`)**: [^2024-08-03-01]<br/>
1️⃣ Điều kiện ràng buộc khi tham số `tuyenbv <= 2` *(CSKCB tuyến huyện trở xuống)*: <br/>
➡️ Nếu `psdangky.mabvdk = psdangky.mabvkb` thì `psdangky.tuyen = 0`.<br/>
➡️ Nếu `psdangky.mabvdk <> psdangky.mabvkb`, xét người bệnh trong tỉnh hoặc ngoài tỉnh (dựa vào tham số `thetrongtinh`):<br/>
⇒ Người bệnh trong tỉnh: `psdangky.tuyen = 0`  và `psdangky.tuyenxml = 0`.<br/>
⇒ Người bệnh ngoài tỉnh: Nếu `psdangky.giayxacnhancutru = 1` thì  `[psdangky.tuyen = 0 và psdangky.tuyenxml = 0]`, ngược lại `[psdangky.tuyen = 0 và psdangky.tuyenxml = 1]` `(theo Công văn 627, người bệnh trái tuyến được hưởng như đúng tuyến)`.<br/><br/>
2️⃣ Điều kiện ràng buộc khi tham số `tuyenbv = 3` *(CSKCB tuyến tỉnh)*: <br/>
➡️ Nếu `[psdangky.manoigt khác rỗng]` và `psdangky.trangthaichuyentuyen IN (2,3,4,5)` thì `psdangky.tuyen = 0`.  *⚠️ Lưu ý:* đối với trường hợp này **KHÔNG** hiển thị message xác nhận có giấy chuyển tuyến, áp dụng cho tất cả các giá trị tham số `tuyenbv`.[^2024-10-21-01] (tương ứng như hình: đã có chọn `mã nơi giới thiệu` và chọn `trạng thái` ở tab *[Chuyển tuyến]*).<br/><p align="center"><img src="https://github.com/user-attachments/assets/e8665eaf-2cd5-46b1-998d-229002cc23c7" width="70%"></p>
➡️ Nếu `[psdangky.manoigt là rỗng]` hoặc [`psdangky.manoigt khác rỗng` và `psdangky.trangthaichuyentuyen = 1`] thì `psdangky.tuyen = 1` *(người bệnh trái tuyến)*.<br/>
➡️ Nếu `[psdangky.manoigt khác rỗng]` *(có giấy chuyển tuyến tuyến dưới)*: cập nhật giá trị mặc định `psdangky.trangthaichuyentuyen = 2`: Chuyển tuyến đúng quy định (vượt khả năng điều trị/ngoài phạm vi chuyên môn của cơ sở KCB).<br/>
➡️ Nếu `psdangky.manoigt` khác rỗng thì bắt buộc cột `psdangky.trangthaichuyentuyen` phải có giá trị  **(bắt buộc phải chọn mới cho hiệu chỉnh)**<br/>
<p align="center"><img src="https://github.com/user-attachments/assets/1c7afd86-854c-4f43-a425-fce7a06d03d6" width="70%"></p>

:blue_book: Module Prescription:
|Khám ngoại trú|Bệnh án ngoại trú|
|-------|-------|
|➡️ Khi phát sinh chẩn đoán bệnh đầu tiên (có phát sinh 1 công khám đầu tiên trong table `current.chidinhcls`): Nếu `psdangky.mabn = xml130.psxml.mabn AND psdangky.makb = xml130.psxml.makb AND xml130.psxml.loaihosokcb = ‘NGOAI_TRU’ AND  xml130.psxml.checkin_cls != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_cls = 1`. `(1)`<br/>➡️ Khi phát sinh toa thuốc đầu tiên (có 1 thuốc đầu tiên trong table `current.pshdxn`): Nếu `psdangky.mabn = xml130.psxml.mabn AND psdangky.makb = xml130.psxml.makb AND xml130.psxml.loaihosokcb = ‘NGOAI_TRU’ AND xml130.psxml.checkin_thuoc != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_thuoc = 1`. `(2)`<br/>➡️ Khi phát sinh toa VTYT đầu tiên (có 1 VTYT đầu tiên trong table `current.pshdxn`): Nếu `psdangky.mabn = xml130.psxml.mabn AND psdangky.makb = xml130.psxml.makb AND xml130.psxml.loaihosokcb = ‘NGOAI_TRU’ AND xml130.psxml.checkin_vtyt != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_vtyt = 1`. `(3)`|➡️ Khi phát sinh chỉ định cận lâm sàng đầu tiên (có phát sinh cận lâm sàng đầu tiên trong table `current.chidinhcls`): Nếu `bnnoitru.mabn = xml130.psxml.mabn AND bnnoitru.makb = xml130.psxml.makb AND bnnoitru.maba =  xml130.psxml.maba AND xml130.psxml.loaihosokcb = ‘BA_NGOAI_TRU’ AND xml130.psxml.checkin_cls != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_cls = 1`. `(4)`<br/>➡️ Khi phát sinh toa thuốc đầu tiên (có 1 thuốc đầu tiên trong table `current.pshdxn`): Nếu `bnnoitru.mabn = xml130.psxml.mabn AND bnnoitru.makb = xml130.psxml.makb AND bnnoitru.maba =  xml130.psxml.maba AND xml130.psxml.loaihosokcb = ‘BA_NGOAI_TRU’ AND xml130.psxml.checkin_thuoc != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_thuoc = 1`. `(5)`<br/>➡️ Khi phát sinh toa VTYT đầu tiên (có 1 VTYT đầu tiên trong table `current.pshdxn`): Nếu `bnnoitru.mabn = xml130.psxml.mabn AND bnnoitru.makb = xml130.psxml.makb AND bnnoitru.maba =  xml130.psxml.maba AND xml130.psxml.loaihosokcb = ‘BA_NGOAI_TRU’ AND xml130.psxml.checkin_vtyt != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_vtyt = 1`. `(6)`|

**⚠️ Lưu ý:** các trường hợp `(1), (2), (3), (4), (5) và (6)`: sau khi thực hiện xong, kiểm tra table `xml130.psxml` nếu chưa phát sinh dòng dữ liệu cho trường hợp đang thực hiện thì khởi tạo dữ liệu vào table này.

- Tại form **ra toa thuốc**: bổ sung chức năng cập nhật giá trị cho cột `pshdxn.lieu_dung` theo quy tắc như sau:
  > Ghi liều dùng thuốc cho người bệnh, cụ thể:
  > - Đối với ngoại trú, được thể hiện bằng: số lượng thuốc dùng trong một lần sử dụng _ số lần trong ngày _ số ngày sử dụng [tổng số thuốc/ngày].
  >   Ví dụ: liều dùng của thuốc A: 2 viên/lần, 2 lần/ngày, sử dụng trong 5 ngày thì được ghi như sau: 2 viên/lần _ 2 lần/ngày _ 5 ngày [4 viên/ngày].
  > - Đối với bệnh án ngoại trú, được thể hiện bằng: số lượng thuốc dùng trong một lần sử dụng _ số lần trong ngày _ 01 ngày [tổng số thuốc/ngày].
  >   Lưu ý:
  > - Trường hợp liều thuốc thay đổi trong ngày theo từng lần sử dụng thì ghi chi tiết.
  >   Ví dụ: liều dùng của thuốc A, sáng: 3 viên, chiều: 2 viên, tối: 1 viên. Như vậy, sẽ ghi như sau: Sáng: 3 viên, Chiều: 2 viên, Tối: 1 viên [6 viên/ngày].

- Bổ sung Control cho phép người dùng xác nhận kết quả điều trị: Giá trị kết quả điều trị này được lấy từ `current.dmketqua` và được lưu vào `psdangky.ket_qua_dtri` (tương ứng với `dmketqua.ma_medisoft` [^2024-07-10-01]) khi được chọn.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/prescription-00.png"></p>
 
- Tại form **xuất viện đối với BA ngoại trú thanh toán cuối đợt**, khi thao tác lưu thông tin người bệnh được xuất viện hoặc tại form in phiếu 01BV theo [QĐ 6556](https://ytehagiang.org.vn/van-ban/6556-qd-byt.doc) đối với người bệnh khám ngoại trú => Thực hiện thao tác đẩy (lưu) toàn bộ dữ liệu của người bệnh (từ `xml130.bang1` đến `xml130.bang15`).

- Tại form lập phiếu `Thủ thuật/Phẫu thuật`: Bổ sung cụm `[Mã máy]` *(như hình, tương ứng cột dmmamay.mamay và dmmamay.tenmay)*, cho phép người dùng chọn mã máy (dữ liệu được load từ `current.dmmamay`, điều kiện theo cột `dmmamay.khocls`). Dữ liệu được lưu trữ tương ứng từ `dmmamay.mamay` vào cột `phauthuat.mamay`. **Lưu ý:** *Không bắt buộc phải có giá trị cột này.* [^2024-07-02-03]
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/b3050e50-f970-40ec-8afd-78b9dcb13fb8"></p>

- Tại form **[Khám bệnh]**: khi điều chỉnh chẩn đoán bệnh, sử dụng tham số `ma_benh_kt.soluong`. Xét: nếu `ma_benh_kt.soluong` > 0, khi lưu chẩn đoán bệnh kiểm tra **`[Tổng số lượng mã bệnh ICD10 (chính + phụ)]`** *(đếm số lượng các mã ICD từ `khambenh.maicd` và `khambenh.maicdp`)* **`<=`** **`[ma_benh_kt.soluong + 1]`**, ngược lại: **KHÔNG** cho lưu chẩn đoán bệnh. [^2024-07-12-02]
<p align="center"><img src="https://github.com/user-attachments/assets/a3eb2985-538e-461a-80dc-97ee0bbc74d0"  width="70%"><br/>Áp dụng tương tự đối với Bệnh án ngoại trú:<img src="https://github.com/user-attachments/assets/afbd88df-af98-40b4-a2e0-31c7a8b6a474" width="70%"></p>

- Cập nhật: **Tại Form Hiệu chỉnh thông tin bệnh nhân bệnh án ngoại trú (`Presctiption`)**: Bổ sung Control cập nhật `[Trạng thái chuyển tuyến]` tương ứng với `psdangky.trangthaichuyentuyen`. [^2024-08-03-02]<br/>
1️⃣ Điều kiện ràng buộc khi tham số `tuyenbv <= 2` *(CSKCB tuyến huyện trở xuống)*: <br/>
➡️ Nếu `bnnoitru.mabvdk = bnnoitru.mabvkb` thì `bnnoitru.tuyen = 0`.<br/>
➡️ Nếu `bnnoitru.mabvdk <> bnnoitru.mabvkb`, xét người bệnh trong tỉnh hoặc ngoài tỉnh (dựa vào tham số `thetrongtinh`):<br/>
⇒ Người bệnh trong tỉnh: `bnnoitru.tuyen = 0`  và `bnnoitru.tuyenxml = 0`.<br/>
⇒ Người bệnh ngoài tỉnh: Nếu `psdangky.giayxacnhancutru = 1` thì  `[bnnoitru.tuyen = 0 và bnnoitru.tuyenxml = 0]`, ngược lại `[bnnoitru.tuyen = 0 và bnnoitru.tuyenxml = 1]` `(theo Công văn 627, người bệnh trái tuyến được hưởng như đúng tuyến)`.<br/><br/>
2️⃣ Điều kiện ràng buộc khi tham số `tuyenbv = 3` *(CSKCB tuyến tỉnh)*: <br/>
➡️ Nếu `[bnnoitru.manoigt khác rỗng]` và `psdangky.trangthaichuyentuyen IN (2,3,4,5)` thì `bnnoitru.tuyen = 0`.  *⚠️ Lưu ý:* đối với trường hợp này **KHÔNG** hiển thị message xác nhận có giấy chuyển tuyến, áp dụng cho tất cả các giá trị tham số `tuyenbv`. (tương ứng như hình: đã có chọn `mã nơi giới thiệu` và chọn `trạng thái` ở tab *[Chuyển tuyến]*).<br/><p align="center"><img src="https://github.com/user-attachments/assets/e8665eaf-2cd5-46b1-998d-229002cc23c7" width="70%"></p>
➡️ Nếu `[bnnoitru.manoigt là rỗng]` hoặc [`bnnoitru.manoigt khác rỗng` và `psdangky.trangthaichuyentuyen = 1`] thì `bnnoitru.tuyen = 1` *(người bệnh trái tuyến)*.<br/>
➡️ Nếu `[bnnoitru.manoigt khác rỗng]` *(có giấy chuyển tuyến tuyến dưới)*: cập nhật giá trị mặc định `psdangky.trangthaichuyentuyen = 2`: Chuyển tuyến đúng quy định (vượt khả năng điều trị/ngoài phạm vi chuyên môn của cơ sở KCB).<br/>
➡️ Nếu `bnnoitru.manoigt` khác rỗng thì bắt buộc cột `psdangky.trangthaichuyentuyen` phải có giá trị  **(bắt buộc phải chọn mới cho hiệu chỉnh)**
- Cập nhật: [^2024-10-11-02]<br/>
➡️ Chức năng `Tiếp nhận bệnh/Đăng ký KSK/Hiệu chỉnh thông tin bệnh nhân/Hiệu chỉnh thông tin bệnh nhân BA ngoại trú`: tại ô `CMND/CCCD/Hộ chiếu` khi lưu phải kiểm tra điều kiện HỢP LỆ tại ô này như sau (điều kiện tuần tự từ trên xuống):<br/>🔹9 hoặc 12 ký tự đều là chữ số (CMND/CCCD).<br/>🔹8 ký tự (Hộ chiếu): với ký tự đầu tiên phải là ký tự chữ cái IN HOA và 7 ký tự còn lại là chữ số.<br/>🔹9 ký tự (Hộ chiếu): với 2 ký tự đầu là chữ cái (IN HOA hoặc thường) và 7 ký tự còn lại là chữ số.<br/>🔹Các trường hợp còn lại là KHÔNG HỢP LỆ.

:blue_book: Module Medicine:

- Bổ sung Control cập nhật `“Mã phương pháp chế biến”` tương ứng cột `dmthuoc.ma_pp_chebien` trên danh mục chế phẩm YHCT.

- Bổ sung Control cập nhật `“Mã CSKCB thuốc”` tương ứng cột `dmthuoc.ma_cskcb_thuoc` trên danh mục thuốc.

:blue_book: Module Treatment:

- Khi phát sinh chỉ định cận lâm sàng đầu tiên (có phát sinh cận lâm sàng đầu tiên trong table `current.chidinhcls`): Nếu `bnnoitru.mabn = xml130.psxml.mabn AND bnnoitru.makb = xml130.psxml.makb AND bnnoitru.maba =  xml130.psxml.maba AND xml130.psxml.loaihosokcb = ‘BA_NOI_TRU’ AND xml130.psxml.checkin_cls != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_cls = 1`. `(7)`

- Khi phát sinh toa thuốc đầu tiên (có 1 thuốc đầu tiên trong table `current.pshdxn`): Nếu `bnnoitru.mabn = xml130.psxml.mabn AND bnnoitru.makb = xml130.psxml.makb AND bnnoitru.maba =  xml130.psxml.maba AND xml130.psxml.loaihosokcb = ‘BA_NOI_TRU’ AND xml130.psxml.checkin_thuoc != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_thuoc = 1`. `(8)`

- Khi phát sinh toa VTYT đầu tiên (có 1 VTYT đầu tiên trong table `current.pshdxn`): Nếu `bnnoitru.mabn = xml130.psxml.mabn AND bnnoitru.makb = xml130.psxml.makb AND bnnoitru.maba =  xml130.psxml.maba AND xml130.psxml.loaihosokcb = ‘BA_NOI_TRU’ AND xml130.psxml.checkin_vtyt != 1`, thực hiện xuất dữ liệu vào table `xml130.checkin` đồng thời gọi API gửi dữ liệu check-in lên cổng giám định BHYT (Chuẩn dữ liệu và gọi hàm API tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024), thực hiện gửi check-in xong cập nhật `xml130.psxml.checkin_vtyt = 1`. `(9)`

**⚠️ Lưu ý**: các trường hợp `(7), (8) và (9)`: sau khi thực hiện xong, kiểm tra table `xml130.psxml` nếu chưa phát sinh dòng dữ liệu cho trường hợp đang thực hiện thì khởi tạo dữ liệu vào table này.

- Tại form ra toa thuốc: bổ sung chức năng cập nhật giá trị cho cột `pshdxn.lieu_dung` theo quy tắc như sau:
  > Ghi liều dùng thuốc cho người bệnh, cụ thể:
  > - Được thể hiện bằng: số lượng thuốc dùng trong một lần sử dụng _ số lần trong ngày _ 01 ngày [tổng số thuốc/ngày]. Lưu ý:
  > - Trường hợp liều thuốc thay đổi trong ngày theo từng lần sử dụng thì ghi chi tiết. Ví dụ: liều dùng của thuốc A, sáng: 3 viên, chiều: 2
  >   viên, tối: 1 viên. Như vậy, sẽ ghi như sau: Sáng: 3 viên, Chiều: 2
  >   viên, Tối: 1 viên [6 viên/ngày].

- Tại form **nhập/hiệu chỉnh thông tin bệnh nhân**, trước khi lưu dữ liệu thông tin bệnh nhân kiểm tra ô `[CMND]` phải đúng định dạng như sau: Định dạng CCCD phải có 9,12 ký tự số hoặc hộ chiếu 8 ký tự bắt đầu là chữ in hoa và 7 ký tự số ở sau.

- Tại form **theo dõi diễn biến quá trình điều trị** (thông tin thêm và thay đổi diễn biến bệnh): bổ sung thêm ô text cho phép nhập/cập nhật `[Giai đoạn bệnh]`, tương ứng với cột dữ liệu `qtdieutri.giai_doan_benh`. Thêm ComboBox cho phép chọn/cập nhật thông tin `[Nhóm máu]`, dữ liệu được cập nhật tương ứng với cột `dmbenhnhan.nhom_mau`. **Lưu ý**: thiết kế ô nhập `[Nhóm máu]` chung với các thông tin chỉ số sinh hiệu.
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/File-ho-tro/dmbenhnhan_nhom_mau.jpg"></p>

- Tại form **xuất viện**, khi thao tác lưu thông tin người bệnh được xuất viện => Thực hiện thao tác đẩy (lưu) toàn bộ dữ liệu của người bệnh (từ `xml130.bang1` đến `xml130.bang15`).

- Tại form **xuất viện**: bổ sung Control cho phép người dùng nhập nội dung `[Tóm tắt kết quả xét nghiệm cận lâm sàng]`, tương ứng với dữ liệu cột `bnnoitru.tomtat_kq`. **Lưu ý: Bắt buộc phải có dữ liệu `tomtat_kq` mới cho xuất viện**. [^2024-06-28-02]

- Tại form lập phiếu `Thủ thuật/Phẫu thuật`: Bổ sung cụm `[Mã máy]` *(như hình, tương ứng cột dmmamay.mamay và dmmamay.tenmay)*, cho phép người dùng chọn mã máy (dữ liệu được load từ `current.dmmamay`, điều kiện theo cột `dmmamay.khocls`). Dữ liệu được lưu trữ tương ứng từ `dmmamay.mamay` vào cột `phauthuat.mamay`. **Lưu ý:** *Không bắt buộc phải có giá trị cột này.* [^2024-07-02-03]
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/b3050e50-f970-40ec-8afd-78b9dcb13fb8"></p>

- Tại form **[Khám và điều trị bệnh]**: khi thay đổi diễn biến bệnh và điều chỉnh chẩn đoán bệnh, sử dụng tham số `ma_benh_kt.soluong`. Xét: nếu `ma_benh_kt.soluong` > 0, khi lưu chẩn đoán bệnh (diễn biến) kiểm tra **`[Tổng số lượng mã bệnh ICD10 (chính + phụ)]`** *(đếm số lượng các mã ICD từ `qtdieutri.maicd` và `qtdieutri.maicdp`)* **`<=`** **`[ma_benh_kt.soluong + 1]`**, ngược lại: **KHÔNG** cho lưu diễn biến bệnh. [^2024-07-12-03]
<p align="center"><img src="https://github.com/user-attachments/assets/47ea188c-64c4-4639-a739-e02381559c79" width="70%"></p>

- Tại form **[Thông tin con sản phụ]** [^2024-07-24-05]<br/>
➡️ Sửa nhãn **[Số con/lần sinh]** thành **[Số con]** và giá trị ô text tương ứng với cột `ttcon.socon`.<br/>
➡️ Bổ sung Control ứng với nhãn **[Lần sinh]** và giá trị ô text tương ứng với cột `ttcon.lan_sinh`.<br/>
➡️ Bổ sung CheckBox **[Sinh con phải phẫu thuật]** và giá trị tương ứng khi giá trị checkbox = true thì `ttcon.sinhcon_phauthuat = 1`, ngược lại `ttcon.sinhcon_phauthuat = 0`.<br/>
➡️ Bổ sung CheckBox **[Sinh con dưới 32 tuần tuổi]** và giá trị tương ứng khi giá trị checkbox = true thì `ttcon.sinhcon_duoi32tuan = 1`, ngược lại `ttcon.sinhcon_duoi32tuan = 0`.<br/>
<p align="center"><img src="https://github.com/user-attachments/assets/be067256-6525-421d-bdb7-9d08bdc8ba38" width="70%"></p>

- Cập nhật: **Tại Form Hiệu chỉnh thông tin bệnh nhân**, Bổ sung Control cập nhật `[Trạng thái chuyển tuyến]` tương ứng với `psdangky.trangthaichuyentuyen`. [^2024-08-03-03]<br/>
1️⃣ Điều kiện ràng buộc khi tham số `tuyenbv <= 2` *(CSKCB tuyến huyện trở xuống)*: <br/>
➡️ Nếu `bnnoitru.mabvdk = bnnoitru.mabvkb` thì `bnnoitru.tuyen = 0`.<br/>
➡️ Nếu `bnnoitru.mabvdk <> bnnoitru.mabvkb`, xét người bệnh trong tỉnh hoặc ngoài tỉnh (dựa vào tham số `thetrongtinh`):<br/>
⇒ Người bệnh trong tỉnh: `bnnoitru.tuyen = 0`  và `bnnoitru.tuyenxml = 0`.<br/>
⇒ Người bệnh ngoài tỉnh: Nếu `psdangky.giayxacnhancutru = 1` thì  `[bnnoitru.tuyen = 0 và bnnoitru.tuyenxml = 0]`, ngược lại `[bnnoitru.tuyen = 0 và bnnoitru.tuyenxml = 1]` `(theo Công văn 627, người bệnh trái tuyến được hưởng như đúng tuyến)`.<br/><br/>
2️⃣ Điều kiện ràng buộc khi tham số `tuyenbv = 3` *(CSKCB tuyến tỉnh)*: <br/>
➡️ Cập nhật `bnnoitru.tuyen = 0`.<br/>
➡️ Nếu `[bnnoitru.manoigt khác rỗng]` *(có giấy chuyển tuyến tuyến dưới)*: cập nhật giá trị mặc định `psdangky.trangthaichuyentuyen = 2`: Chuyển tuyến đúng quy định (vượt khả năng điều trị/ngoài phạm vi chuyên môn của cơ sở KCB).<br/>
➡️ Nếu `bnnoitru.manoigt` khác rỗng thì bắt buộc cột `psdangky.trangthaichuyentuyen` phải có giá trị  **(bắt buộc phải chọn mới cho hiệu chỉnh)**.
- Cập nhật: [^2024-10-11-03]<br/>
➡️ Chức năng `Hiệu chỉnh thông tin bệnh nhân nội trú`: tại ô `CMND/CCCD/Hộ chiếu` khi lưu phải kiểm tra điều kiện HỢP LỆ tại ô này như sau (điều kiện tuần tự từ trên xuống):<br/>🔹9 hoặc 12 ký tự đều là chữ số (CMND/CCCD).<br/>🔹8 ký tự (Hộ chiếu): với ký tự đầu tiên phải là ký tự chữ cái IN HOA và 7 ký tự còn lại là chữ số.<br/>🔹9 ký tự (Hộ chiếu): với 2 ký tự đầu là chữ cái (IN HOA hoặc thường) và 7 ký tự còn lại là chữ số.<br/>🔹Các trường hợp còn lại là KHÔNG HỢP LỆ.

:blue_book: Module Printer:

- Tại form in **phiếu 01BV** theo [QĐ6556](https://ytehagiang.org.vn/van-ban/6556-qd-byt.doc) => Thực hiện thao tác đẩy (lưu) toàn bộ dữ liệu của người bệnh (từ `xml130.bang1` đến `xml130.bang15`).

:blue_book: Module Reports:

- Thiết kế form cho phép người dùng tra cứu và xuất dữ liệu QĐ130 (bổ sung QĐ 4750) ra định dạng XML ra tập tin XML (Chuẩn dữ liệu XML tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024).

- Tại form xuất dữ liệu `xml4210.xml1` của `XML4210`, bổ sung các cột số liệu so sánh với dữ liệu `XML130`. Cụ thể:
<p align="center">
<table border="1" cellspacing="0" cellpadding="0" width=100%>
  <tr>
    <td width=12%><p align="center">1</p></td>
    <td width=12%><p align="center">27</p></td>
    <td width=12%><p align="center">28</p></td>
    <td width=12%><p align="center">29</p></td>
    <td width=12%><p align="center">30</p></td>
    <td width=40% colspan="4"><p align="center">XML130</p></td>
  </tr>
  <tr>
    <td><p align="center">MA_LK</p></td>
    <td><p align="center">TONG_CHI</p></td>
    <td><p align="center">T_BNTT</p></td>
    <td><p align="center">T_BNCCT</p></td>
    <td><p align="center">T_BHTT</p></td>
    <td><p align="center">T_TONGCHI_BH</p></td>
    <td><p align="center">T_BNTT</p></td>
    <td><p align="center">T_BNCCT</p></td>
    <td><p align="center">T_BHTT</p></td>
  </tr>
</table>
</p>

- Các báo cáo liên quan danh mục địa phương: Kết hợp dữ liệu giữa `current.dmxa` và `current.dmxa4750`.

:blue_book: Module Services:

- Thiết kế form/Cập nhật form đẩy dữ liệu theo QĐ130 lên cổng giám định BHYT thông qua API (Chuẩn dữ liệu tham khảo chi tiết [công văn 1245/BHXH-CNTT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/1245-BHXH-CNTT_c%C3%A1c_t%E1%BB%89nh_N%C3%A2ng_c%E1%BA%A5p_h%E1%BB%87_th%E1%BB%91ng_theo_Quy%E1%BA%BFt_%C4%91%E1%BB%8Bnh_s%E1%BB%91_4750_Q%C4%90_BYT_fn.pdf) do BHXH Việt Nam ban hành ngày 03/05/2024).

:blue_book: Module Diagnose: 

- Tại các form trả kết quả của `Chẩn đoán hình ảnh (HA)/Thăm dò chức năng (CN)`, bổ sung control ghi nhận `[Ngày thực hiện y lệnh]`. Thời gian này được lấy mặc định từ khi mở form thực hiện (cho phép người dùng tùy chỉnh, điều kiện phải nhỏ hơn hoặc bằng thời gian Ngày thực hiện). Dữ liệu được cập nhật tương ứng cột: `chidinhcls.giolaymau`.[^2024-06-29]
<p align="center"><img src="https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/9cf79ca2-d2bd-4fb3-9011-094dbe77e0bf" width="70%"></p>

- Cập nhật: [^2024-07-25-04]<br/>
➡️ Tại form **[Danh sách bác sĩ trực]**, cho phép cấu hình chọn (không giới hạn) nhân viên `[Được phép thực hiện cận lâm sàng]`.<br/>
➡️ Tại form **[Danh sách thực hiện]**, **không** cho phép thực hiện nếu chưa cấu hình chọn `[Bác sĩ trực]` và `[Nhân viên thực hiện]`.<br/>
➡️ Tại các form **trả kết quả (thực hiện)**: Bổ sung ComboBox load danh sách nhân viên thực hiện (đã chọn), dữ liệu khi lưu tương ứng với cột `chidinhcls.nguoi_thuc_hien = dmnhanvien.macc_hanhnghe_cv2348`, tham chiếu từ `dmnhanvien.manv` của nhân viên thực hiện.

:blue_book: Module Laboratory: 

- Cập nhật: [^2024-07-25-05]<br/>
➡️ Tại form **[Danh sách bác sĩ trực]**, cho phép cấu hình chọn (không giới hạn) nhân viên `[Được phép thực hiện cận lâm sàng]`.<br/>
➡️ Tại form **[Danh sách thực hiện]**, **không** cho phép thực hiện nếu chưa cấu hình chọn `[Bác sĩ trực]` và `[Nhân viên thực hiện]`.<br/>
➡️ Tại các form **trả kết quả (thực hiện)**: Bổ sung ComboBox load danh sách nhân viên thực hiện (đã chọn), dữ liệu khi lưu tương ứng với cột `chidinhcls.nguoi_thuc_hien = dmnhanvien.macc_hanhnghe_cv2348`, tham chiếu từ `dmnhanvien.manv` của nhân viên thực hiện.

:blue_book: Kết nối HIS-LIS: [^2024-08-16-01]
1. Đối với kết nối sử dụng Function:
- Cập nhật hàm `current.sp_lis_result`: bổ sung truyền tham số `manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm khi LIS đổ kết quả về HIS.
<p align="center"><img src="https://github.com/user-attachments/assets/091e1f6f-944d-4835-93b5-21617a983279" width="50%"></p>

- Gửi tài liệu cập nhật cho các đơn vị đối tác LIS. Chi tiết: [DH - HIS-LIS Connection (Function) - 16-08-2024.pdf](https://github.com/user-attachments/files/16632149/DH.-.HIS-LIS.Connection.Function.-.16-08-2024.pdf)

2. Đối với kết nối API:[^2024-08-22-01]
- Đối với hàm `SP_LIS_Order`: trả về các xét nghiệm chưa có kết quả (có trạng thái `chidinhcls.dath != 1`).
- Cập nhật hàm `SP_LIS_Result, AddSinhThiet, AddTeBaoCoTuCung`: bổ sung truyền tham số `manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm khi LIS đổ kết quả về HIS.
- Cập nhật hàm `SP_LIS_Result`: Từ chối nhận kết quả đối với các xét nghiệm chưa lấy mẫu hoặc không tồn tại trong dữ liệu chỉ định.
- Gửi tài liệu cập nhật cho các đơn vị đối tác LIS. Chi tiết: [DH - Tai lieu API HIS-LIS - Token - 22-08-2024.pdf](https://github.com/user-attachments/files/16702957/DH.-.Tai.lieu.API.HIS-LIS.-.Token.-.22-08-2024.pdf)

[^2024-10-21-01]: Thay đổi ngày 21/10/2024: Bổ sung ràng buộc khi `[psdangky.manoigt khác rỗng]` và `psdangky.trangthaichuyentuyen IN (2,3,4,5)` thì `psdangky.tuyen = 0` (áp dụng khi tiếp nhận bệnh hoặc hiệu chỉnh thông tin bệnh nhân). Chi tiết yêu cầu [#706](https://github.com/dh-hos/To_Lap_Trinh/issues/706)
[^2024-10-15-01]: Thay đổi ngày 15/10/2024: Sửa câu `Đối với psdangky.trangthaichuyentuyen = 5 hoặc 6 (Giấy hẹn lãnh thuốc)` thành `Đối với psdangky.trangthaichuyentuyen = 5 (Giấy hẹn lãnh thuốc)`. Vì, mô tả cho giấy hẹn lãnh thuốc bệnh nhân lao được mô tả ở dòng phía đó. Chi tiết yêu cầu [#699](https://github.com/dh-hos/To_Lap_Trinh/issues/699)
[^2024-10-11-03]: Thay đổi ngày 11/10/2024: Điều kiện ràng buộc khi hiệu chỉnh thông tin bệnh nhân tại `module Treatment` đối với  `CCCD/CMND/Hộ chiếu`. Chi tiết yêu cầu [#693](https://github.com/dh-hos/To_Lap_Trinh/issues/693)
[^2024-10-11-02]: Thay đổi ngày 11/10/2024: Điều kiện ràng buộc khi hiệu chỉnh thông tin bệnh nhân tại `module Register/Prescription` đối với  `CCCD/CMND/Hộ chiếu`. Chi tiết yêu cầu [#693](https://github.com/dh-hos/To_Lap_Trinh/issues/693)
[^2024-10-11-01]: Thay đổi ngày 11/10/2024: Điều kiện ràng buộc khi hiệu chỉnh thông tin bệnh nhân tại `module Admin` đối với  `CCCD/CMND/Hộ chiếu`. Chi tiết yêu cầu [#693](https://github.com/dh-hos/To_Lap_Trinh/issues/693)
[^2024-10-09-01]: Thay đổi ngày 09/10/2024: Thay đổi diễn giải giá trị đối với tham số  `ma_loai_kcb.ba_ngoai_ngay`.
[^2024-09-12-03]: Thay đổi ngày 12/09/2024: Bổ sung mô tả thông tin chuyển tuyến người bệnh lao khi tiếp nhận bệnh tại module Register, đối với `psdangky.trangthaichuyentuyen = 4 (Chuyển tuyến người bệnh khám và điều trị bệnh lao)` . Thay đổi theo yêu cầu [tại đây](https://github.com/dh-hos/THEO-DOI-THUC-HIEN/issues/127).
[^2024-09-12-02]: Thay đổi ngày 12/09/2024: Bổ sung mô tả ràng buộc khi tiếp nhận bệnh tại module Register, đối với `psdangky.trangthaichuyentuyen = 5 hoặc 6 (Giấy hẹn lãnh thuốc)` . Thay đổi theo yêu cầu [tại đây](https://github.com/dh-hos/THEO-DOI-THUC-HIEN/issues/127).
[^2024-09-12-01]: Thay đổi ngày 12/09/2024: Bổ sung giá trị cho cột `psdangky.trangthaichuyentuyen = 6`: Giấy hẹn lãnh thuốc. Thay đổi theo yêu cầu [tại đây](https://github.com/dh-hos/THEO-DOI-THUC-HIEN/issues/127).
[^2024-08-22-01]: Thay đổi ngày 22/08/2024: Thay đổi điều kiện kết nối API (HIS-LIS) đối ới các hàm: `SP_LIS_Order`, `SP_LIS_Result`.
[^2024-08-16-01]: Thay đổi ngày 16/08/2024: Bổ sung mô tả ghi nhận người thực hiện (áp dụng cho `bang3.nguoi_thuc_hien`) đối với kết nối HIS-LIS.
[^2024-09-13-01]: Thay đổi ngày 14/08/2024: Bổ sung điều kiện ràng buộc cột `psdangky.trangthaichuyentuyen` đối với người bệnh khám lao khi tiếp nhận bệnh.
[^2024-08-03-04]: Thay đổi ngày 03/08/2024: Cập nhật: Form Hiệu chỉnh thông tin bệnh nhân ngoại trú (`Admin`) với các ràng buộc xác định tuyến người bệnh.
[^2024-08-03-03]: Thay đổi ngày 03/08/2024: Cập nhật: Tại Form Hiệu chỉnh thông tin bệnh nhân (`Treatment`) với các ràng buộc xác định tuyến người bệnh.
[^2024-08-03-02]: Thay đổi ngày 03/08/2024: Cập nhật: Tại Form Hiệu chỉnh thông tin bệnh nhân bệnh án ngoại trú (`Presctiption`) với các ràng buộc xác định tuyến người bệnh.
[^2024-08-03-01]: Thay đổi ngày 03/08/2024: Cập nhật: Form tiếp nhận bệnh (`Register`) và Hiệu chỉnh thông tin bệnh nhân (`Presctiption`) với các ràng buộc xác định tuyến người bệnh.
[^2024-07-28-05]: Thay đổi ngày 28/07/2024: Bổ sung cột `pscovid19.manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm Covid-19 module `Laboratory`.
[^2024-07-28-04]: Thay đổi ngày 28/07/2024: Bổ sung cột `psdom.manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm đờm module `Laboratory`.
[^2024-07-28-03]: Thay đổi ngày 28/07/2024: Bổ sung cột `pssinhthiet.manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm sinh thiết module `Laboratory`.
[^2024-07-28-02]: Thay đổi ngày 28/07/2024: Bổ sung cột `pstebaotucung.manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm tế bào cổ tử cung module `Laboratory`.
[^2024-07-28-01]: Thay đổi ngày 28/07/2024: Bổ sung cột `pskhamxn.manv_nguoithuchien`, ghi nhận người thực hiện xét nghiệm module `Laboratory`.
[^2024-07-25-09]: Thay đổi ngày 25/07/2024: Bổ sung cột `lichtruc_laboratory.thuchien`, xác định trạng thái thực hiện xét nghiệm trong lịch trực module `Laboratory`.
[^2024-07-25-08]: Thay đổi ngày 25/07/2024: Bổ sung cột `lichtruc_laboratory.duockham`, xác định trạng thái đọc kết quả xét nghiệm trong lịch trực module `Laboratory`.
[^2024-07-25-07]: Thay đổi ngày 25/07/2024: Bổ sung cột `lichtruc_diagnose.thuchien`, xác định trạng thái thực hiện CĐHA/TDCN trong lịch trực module `Diagnose`.
[^2024-07-25-06]: Thay đổi ngày 25/07/2024: Bổ sung cột `lichtruc_diagnose.duockham`, xác định trạng thái đọc kết quả CĐHA/TDCN trong lịch trực module `Diagnose`.
[^2024-07-25-05]: Thay đổi ngày 25/07/2024: Module `Laboratory`, cấu hình nhân viên `[Được thực hiện cận lâm sàng]` và ghi nhận giá trị `chidinhcls.nguoi_thuc_hien` khi thực hiện.
[^2024-07-25-04]: Thay đổi ngày 25/07/2024: Module `Diagnose`, cấu hình nhân viên `[Được thực hiện cận lâm sàng]` và ghi nhận giá trị `chidinhcls.nguoi_thuc_hien` khi thực hiện.
[^2024-07-25-03]: Thay đổi ngày 25/07/2024: Bổ sung cột `chidinhcls.nguoi_thuc_hien`,  ghi nhận mã Chứng chỉ hành nghề nhân viên thực hiện cận lâm sàng.
[^2024-07-25-02]: Thay đổi ngày 25/07/2024: Module `Admin`, form `[Danh mục nhân viên]`, bổ sung checkbox `[Được thực hiện cận lâm sàng]`.
[^2024-07-25-01]: Thay đổi ngày 25/07/2024: Bổ sung cột `dmnhanvien.thuchien`, xác định trạng thái được phép thực hiện cận lâm sàng `kho IN ('HA','CN','XN')`.
[^2024-07-24-05]: Thay đổi ngày 24/07/2024: Cập nhật form `[Thông tin con sản phụ]` module `Treatment`, bổ sung các control cập nhật giá trị tương ứng cho các cột `ttcon.lan_sinh`, `ttcon.sinhcon_phauthuat`, `ttcon.sinhcon_duoi32tuan`, hỗ trợ dữ liệu [xml130.bang9](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang09%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md).
[^2024-07-24-04]: Thay đổi ngày 24/07/2024: Bổ sung cột `sinhcon_duoi32tuan` table `ttcon`, hỗ trợ dữ liệu [xml130.bang9](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang09%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md).
[^2024-07-24-03]: Thay đổi ngày 24/07/2024: Bổ sung cột `sinhcon_phauthuat` table `ttcon`, hỗ trợ dữ liệu [xml130.bang9](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang09%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md).
[^2024-07-24-02]: Thay đổi ngày 24/07/2024: Bổ sung cột `lan_sinh` table `ttcon`, hỗ trợ dữ liệu [xml130.bang9](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang09%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md).
[^2024-07-24-01]: Thay đổi ngày 24/07/2024: Bổ sung tham số `ma_loai_kcb.ba_ngoai_ngay` áp dụng cho cột `ma_loai_kcb` bảng [xml130.checkin](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang00checkin%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md) và [xml130.bang1](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang01%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md).
[^2024-07-12-03]: Thay đổi ngày 12/07/2024: Bổ sung quy trình áp dụng đối với module `Treatment` ⇒ Kiểm tra số lượng mã ICD10 khi sử dụng tham số `ma_benh_kt.soluong` để thay đổi diễn biến bệnh.
[^2024-07-12-02]: Thay đổi ngày 12/07/2024: Bổ sung quy trình áp dụng đối với module `Prescription` ⇒ Kiểm tra số lượng mã ICD10 khi sử dụng tham số `ma_benh_kt.soluong` để khám bệnh.
[^2024-07-12-01]: Thay đổi ngày 12/07/2024: Bổ sung tham số `ma_benh_kt.soluong`.
[^2024-07-10-01]: Thay đổi ngày 10/07/2024: Thay đổi cách ghi nhận giá trị cột `psdangky.ket_qua_dtri` từ`dmketqua.ma_medisoft`.
[^2024-07-04-03]: Thay đổi ngày 04/07/2024: Bổ sung quy trình áp dụng cho `Module Admin` ⇒ `Danh mục cận lâm sàng` ==> Bổ sung Control áp dữ liệu cho cột `dmcls.ma_xang_dau`.
[^2024-07-04-02]: Thay đổi ngày 04/07/2024: Bổ sung cột `dmcls.ma_xang_dau`.
[^2024-07-04-01]: Thay đổi ngày 04/07/2024: Bổ sung tham số `ma_xang_dau`.
[^2024-07-02-04]: Thay đổi ngày 02/07/2024: Hướng dẫn bổ sung quy trình thực hiện cho `Module Treatment` ⇒ Form thực hiện `Thủ thuật/Phẫu thuật`.
[^2024-07-02-03]: Thay đổi ngày 02/07/2024: Hướng dẫn bổ sung quy trình thực hiện cho `Module Prescription` ⇒ Form thực hiện `Thủ thuật/Phẫu thuật`.
[^2024-07-02-02]: Thay đổi ngày 02/07/2024: Hướng dẫn bổ sung quy trình thực hiện cho `Module Admin` ⇒ Form `[Danh mục mã máy thực hiện CLS]`.
[^2024-07-02-01]: Thay đổi ngày 02/07/2024: Bổ sung cấu trúc, cột `phauthuat.mamay`.
[^2024-07-01]: Thay đổi ngày 01/07/2024: Họ lót không chức danh.
[^2024-06-29]: Thay đổi ngày 29/06/2024: Bổ sung control ghi nhận Ngày thực hiện y lệnh đối với `Chẩn đoán hình ảnh/Thăm dò chức năng` khi thực hiện trả kết quả.
[^2024-06-12-01]: Thay đổi ngày 12/06/2024: Bổ sung cấu trúc bảng theo yêu cầu tại: [#393](https://github.com/dh-hos/To_Lap_Trinh/issues/393)
[^2024-06-12-02]: Thay đổi ngày 12/06/2024: Bổ sung mô tả quy trình thực hiện theo yêu cầu tại: [#393](https://github.com/dh-hos/To_Lap_Trinh/issues/393)
[^2024-06-25-91]: Thay đổi ngày 25/06/2024: Bổ sung TT_THAU theo QĐ 130, 4750: [#415](https://github.com/dh-hos/To_Lap_Trinh/issues/415)
[^2024-06-28-01]: Thay đổi ngày 28/06/2024: Bổ sung cột `tomtat_kq` phục vụ dữ liệu [xml130.bang8](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang08%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md)
[^2024-06-28-02]: Thay đổi ngày 28/06/2024: Bổ sung quy trình áp dụng ghi nhận `tomtat_kq` cho phân hệ `Treatment`.
