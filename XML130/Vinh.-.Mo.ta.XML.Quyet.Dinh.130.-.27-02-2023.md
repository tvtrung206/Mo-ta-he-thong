<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: QUY ĐỊNH CHUẨN VÀ ĐỊNH DẠNG DỮ LIỆU ĐẦU RA PHỤC VỤ VIỆC QUẢN LÝ, GIÁM ĐỊNH, THANH TOÁN CHI PHÍ KHÁM BỆNH, CHỮA BỆNH VÀ GIẢI QUYẾT CÁC CHẾ ĐỘ LIÊN QUAN THEO QUYẾT ĐỊNH 130/QĐ-BYT NGÀY 18/01/2023 CỦA BỘ Y TẾ

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Quản lý các loại chi phí nội bộ (gửi mẫu xét nghiệm,...) theo từng phiếu thu

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Cấu trúc bảng XML**

- [Excel hỗ trợ](/XML130/File-ho-tro/postgres-table.xlsx)

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

:blue_book: Cập nhật cấu trúc, bổ sung cột lưu trữ mã ICD-9 CM Danh mục chuyển đổi giữa danh mục kỹ thuật tương đương và phân loại phẫu thuật, thủ thuật quốc tế ICD-9 CM.

`current.dmcls.maicd9 VARCHAR(20): Mã ICD-9 CM`

Đính kèm: 
- [QD4440-Quyet đinh ban hanh ICD-9 CM thí điểm DRG.signed.pdf](/XML130/File-ho-tro/QD4440-Quyet%20đinh%20ban%20hanh%20ICD-9%20CM%20thí%20điểm%20DRG.signed.pdf) 
- [Phu luc 3 - Danh muc ICD-9 CM Vol3.xlsx](/XML130/File-ho-tro/Phu%20luc%203%20-%20Danh%20muc%20ICD-9%20CM%20Vol3.xlsx)

:blue_book: Cập nhật cấu trúc table psdangky [^2023-12-07]

`current.psdangky.trangthaichuyentuyen NUMERIC(1,0): Ghi nhận trạng thái chuyển tuyến từ tuyến dưới chuyển lên. Giá trị: (null): không có thông tin chuyển tuyến. 1: Chuyển tuyến theo yêu cầu. 2: Chuyển tuyến đúng quy định (vượt khả năng điều trị/ngoài phạm vi chuyên môn của cơ sở KCB). 3: Hẹn tái khám. 4: Chuyển tuyến người bệnh khám và điều trị bệnh lao. 5: Giấy hẹn lãnh thuốc.`

`current.psdangky.giayxacnhancutru NUMERIC(1,0): Ghi nhận trạng thái người bệnh ngoài tỉnh đến khám chữa bệnh có giấy xác nhận (giấy từ chứng minh đang ở tại địa phương khác trong thời gian đi công tác, làm việc lưu động, học tập trung theo các hình thức đào tạo, chương trình đào tạo, tạm trú, ...). Giá trị: (null) hoặc 0: Không có giấy xác nhận. 1: Có giấy xác nhận.`

`current.psdangky.giayluu BYTEA: Lưu trữ Giấy chuyển tuyến/Giấy hẹn tái khám/Giấy xác nhận cư trú (do người dùng scan hoặc chụp).`

:blue_book: Cập nhật cấu trúc table ttcon [^2023-12-07]

`current.ttcon.ngay5nam DATE: Ngày người bệnh tham gia BHYT đủ 05 năm liên tục (thẻ thứ 2).`

:blue_book: Cập nhật cấu trúc table dmthuoc

`current.dmthuoc.ma_pp_chebien VARCHAR(255): Mã phương pháp chế biến vị thuốc cổ truyền. Ghi theo phụ lục 3, Quyết định 824/QĐ-BYT ngày 15/02/2023.`

:blue_book: Bổ sung tham số

`ma_ttdv (Dạng chuỗi - tham số chung): Mã số định danh y tế (mã số BHXH) của người đứng đầu cơ sở KBCB hoặc người được người đứng đầu cơ sở KBCB ủy quyền được ký và đóng dấu của cơ sở KBCB.`

:blue_book: Bổ sung table current.psgiamdinhykhoa
![Alt text](File-ho-tro/current.psgiamdinhykhoa.jpg)

:white_check_mark: **Thực hiện thay đổi**

:blue_book: - Thiết kế DLL: Form Giám định y khoa (tương ứng cập nhật dữ liệu cho current.psgiamdinhykhoa). Tích hợp lên: Prescription và Treatment.

:blue_book: Module Admin

- Bổ sung Control trên Form danh mục CLS cập nhật giá trị cột dmcls.maicd9 (tương ứng cột [Mã ICD-9] phụ lục 3 QĐ 4440). Hỗ trợ script update tự động giá trị cho cột [maicd9] dựa vào cột [Mã tương đương] phụ lục 3 (tương ứng với dmcls.macls_byt).

- Mở rộng chức năng của form [Danh mục kết quả điều trị] cho phép người dùng thêm mới. Sửa nhãn “Mã Medisoft” thành “Mã BYT”
![Alt text](File-ho-tro/admin-00.png)

- Mở rộng form danh mục cận lâm sàng cho phép cập nhật [Mã chỉ số] và [Tên chỉ số] đối với kho: HA (chẩn đoán hình ảnh) và CN (Thăm dò chức năng).
![Alt text](File-ho-tro/admin-01.png)

:blue_book: Module Register/Prescription khi đăng ký tiếp nhận người bệnh: Bổ sung các Control:

-  Bổ sung Control để người tiếp nhận cập nhật trạng thái chuyển tuyến của người bệnh hoặc ghi nhận có giấy hẹn tái khám (tương ứng với cột psdangky.trangthaichuyentuyen). Lưu ý: Cột psdangky.trangthaichuyentuyen chỉ có giá trị khi cột psdangky.manoigt khác rỗng (bắt buộc phải chọn mới cho đăng ký).

-  Bổ sung Control cho phép người dùng xác nhận người bệnh có giấy cư trú (áp dụng cho người bệnh ngoài tỉnh), nếu có xác nhận thì cập nhật tương ứng vào cột psdangky.giayxacnhancutru = 1 và psdangky.tuyen = 0.

- Bổ sung Control cho phép người dùng chọn và lưu tập tin (của giấy chuyển tuyến/giấy hẹn tái khám) khi psdangky.manoigt khác rỗng.

- Bổ sung Control lấy và cập nhật thông tin ngày người bệnh tham gia BHYT đủ 05 năm liên tục tương ứng với cột psdangky.ngay5nam.

:blue_book: Module Prescription:

- Sau khi khám bệnh người bệnh (chuyên khoa đầu tiên, nếu người bệnh có khám nhiều chuyên khoa/phòng) xuất dữ liệu vào xml130.checkin đồng thời gọi API gửi dữ liệu checkin lên cổng giám định BHYT (thời điểm hiện tại BYT chưa công bố chuẩn XML và API cho dữ liệu QĐ130, sẽ bổ sung cập nhật sau khi BYT ban hành).

- Bổ sung Control cho phép người dùng xác nhận kết quả điều trị:
![Alt text](File-ho-tro/prescription-00.png)

Giá trị kết quả điều trị này được lấy từ current.dmketqua và được lưu vào psdangky.ket_qua_dtri (tương ứng với dmketqua.makq) khi được chọn.

- Tại form xuất viện đối với BA ngoại trú thanh toán cuối đợt, khi thao tác lưu thông tin người bệnh được xuất viện hoặc tại form in phiếu 01BV theo QDD6556 đối với người bệnh khám ngoại trú -> Thực hiện thao tác đẩy (lưu) toàn bộ dữ liệu của người bệnh (từ xml130.bang1 đến xml130.bang12).

:blue_book: Bổ sung thêm cho mô tả các trường XML6 (liên quan đến chỉ tiêu khám và điều trị bệnh nhân HIV-ARV)

:blue_book: Bổ sung thêm cho mô tả các trường XML10 (liên quan đến Chỉ tiêu dữ liệu giấy chứng nhận nghỉ dưỡng thai).

:blue_book: Bổ sung thêm cho mô tả các trường XML11 (liên quan đến Chỉ tiêu dữ liệu giấy chứng nhận nghỉ việc hưởng bảo hiểm xã hội).

:blue_book: Module Medicine: Bổ sung Control cập nhật “Mã phương pháp chế biến” tương ứng cột dmthuoc.ma_pp_chebien trên danh mục chế phẩm YHCT.

:blue_book: Module Treatment:

- Bổ sung Control lấy và cập nhật thông tin ngày người bệnh tham gia BHYT đủ 05 năm liên tục tương ứng với cột bnnoitru.ngay5nam đối với thẻ 1 và ttcon.ngay5nam đối với thẻ 2.

- Tại form xuất viện, khi thao tác lưu thông tin người bệnh được xuất viện -> Thực hiện thao tác đẩy (lưu) toàn bộ dữ liệu của người bệnh (từ xml130.bang1 đến xml130.bang12).

:blue_book: Module Printer: Tại form in phiếu 01BV theo QĐ6556 -> Thực hiện thao tác đẩy (lưu) toàn bộ dữ liệu của người bệnh (từ xml130.bang1 đến xml130.bang12)

:blue_book: Module Reports: Thiết kế form cho phép người dùng tra cứu dữ liệu QĐ130 và chức năng xuất dữ liệu ra định dạng XML ra tập tin (hiện tại định dạng này đang chờ BYT/BHXH công bố).

:white_check_mark: **CẤU TRÚC DỮ LIỆU LƯU TRỮ 13 TABLE THEO QĐ130**

1. Table **xml130.checkin: Bảng chỉ tiêu dữ liệu về trạng thái khám bệnh, chữa bệnh (Bảng check-in). Đây là bảng phục vụ thông tuyến thẻ BHYT khi người bệnh đến khám nhiều nơi KCB (nếu có).**

![Alt text](File-ho-tro/xml130.checkin.jpg)

**Giá trị ma_doituong_kcb**

![Alt text](File-ho-tro/ma_doituong_kcb.jpg)

2. Table **xml130.bang1: Chỉ tiêu tổng hợp khám bệnh, chữa bệnh**

![Alt text](File-ho-tro/xml130.bang1-0.jpg)![Alt text](File-ho-tro/xml130.bang1-1.jpg)![Alt text](File-ho-tro/xml130.bang1-2.jpg)![Alt text](File-ho-tro/xml130.bang1-3.jpg)![Alt text](File-ho-tro/xml130.bang1-4.jpg)![Alt text](File-ho-tro/xml130.bang1-5.jpg)
[^2023-12-07]
![Alt text](File-ho-tro/xml130.bang1-6.jpg)

**Giá trị ma_doituong_kcb**

![Alt text](File-ho-tro/ma_doituong_kcb.jpg)
3. Table **xml130.bang2: Chỉ tiêu chi tiết thuốc**

![Alt text](File-ho-tro/xml130.bang2-0.jpg)![Alt text](File-ho-tro/xml130.bang2-1.jpg)![Alt text](File-ho-tro/xml130.bang2-2.jpg)![Alt text](File-ho-tro/xml130.bang2-3.jpg)![Alt text](File-ho-tro/xml130.bang2-4.jpg)![Alt text](File-ho-tro/xml130.bang2-5.jpg)
3. Table **xml130.bang3: Chỉ tiêu chi tiết thuốc**
![Alt text](File-ho-tro/xml130.bang3-0.jpg)![Alt text](File-ho-tro/xml130.bang3-1.jpg)![Alt text](File-ho-tro/xml130.bang3-2.jpg)![Alt text](File-ho-tro/xml130.bang3-3.jpg)![Alt text](File-ho-tro/xml130.bang3-4.jpg)![Alt text](File-ho-tro/xml130.bang3-5.jpg)![Alt text](File-ho-tro/xml130.bang3-6.jpg)
4. Table **xml130.bang4: Chỉ tiêu chi tiết dịch vụ cận lâm sàng**
![Alt text](File-ho-tro/xml130.bang4.jpg)
5. Table **xml130.bang5: Chỉ tiêu chi tiết diễn biến lâm sàng**
![Alt text](File-ho-tro/xml130.bang5.jpg)
6. Table **xml130.bang6: Chỉ tiêu hồ sơ bệnh án chăm sóc và điều trị HIV/AIDS**
![Alt text](File-ho-tro/xml130.bang6-0.jpg)![Alt text](File-ho-tro/xml130.bang6-1.jpg)![Alt text](File-ho-tro/xml130.bang6-2.jpg)![Alt text](File-ho-tro/xml130.bang6-3.jpg)![Alt text](File-ho-tro/xml130.bang6-4.jpg)
7. Table **xml130.bang7: Chỉ tiêu dữ liệu giấy ra viện**
![Alt text](File-ho-tro/xml130.bang7-0.jpg)![Alt text](File-ho-tro/xml130.bang7-1.jpg)![Alt text](File-ho-tro/xml130.bang7-2.jpg)![Alt text](File-ho-tro/xml130.bang7-3.jpg)![Alt text](File-ho-tro/xml130.bang7-4.jpg)
8. Table **xml130.bang8: Chỉ tiêu dữ liệu tóm tắt hồ sơ bệnh án;**
![Alt text](File-ho-tro/xml130.bang8-0.jpg)![Alt text](File-ho-tro/xml130.bang8-1.jpg)![Alt text](File-ho-tro/xml130.bang8-2.jpg)![Alt text](File-ho-tro/xml130.bang8-3.jpg)
9. Table **xml130.bang9: Chỉ tiêu dữ liệu giấy chứng sinh**
![Alt text](File-ho-tro/xml130.bang9-0.jpg)![Alt text](File-ho-tro/xml130.bang9-1.jpg)![Alt text](File-ho-tro/xml130.bang9-2.jpg)![Alt text](File-ho-tro/xml130.bang9-3.jpg)
10. Table **xml130.bang10: Chỉ tiêu dữ liệu giấy chứng nhận nghỉ dưỡng thai**![Alt text](File-ho-tro/xml130.bang10-0.jpg)![Alt text](File-ho-tro/xml130.bang10-1.jpg)
11. Table **xml130.bang11: Chỉ tiêu dữ liệu giấy chứng nhận nghỉ hưởng bảo hiểm xã hội**![Alt text](File-ho-tro/xml130.bang11-0.jpg)![Alt text](File-ho-tro/xml130.bang11-1.jpg)![Alt text](File-ho-tro/xml130.bang11-2.jpg)
12. Table **xml130.bang12: Chỉ tiêu dữ liệu giám định y khoa.**
![Alt text](File-ho-tro/xml130.bang12-0.jpg)![Alt text](File-ho-tro/xml130.bang12-1.jpg)![Alt text](File-ho-tro/xml130.bang12-2.jpg)![Alt text](File-ho-tro/xml130.bang12-3.jpg)![Alt text](File-ho-tro/xml130.bang12-4.jpg)


[^2023-12-07]: Thay đổi ngày 2023-12-07 (sử dụng lại cột `ngay5nam` trong `psdangky` và `bnnoitru`, thay đổi tên cột `ngay55lientuc` bằng `ngay5nam` trong bảng `ttcon`, `xml130.bang1.nam_nam_lien_tuc` lấy dữ liệu từ cột `ngay5nam`).
