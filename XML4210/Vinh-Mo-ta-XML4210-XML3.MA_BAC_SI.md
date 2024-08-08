<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CÁCH GHI NHẬN GIÁ TRỊ CỘT XML3.[MA_BAC_SI] (cột 25, bảng 3 - XML4210)

</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)

###### :eight_spoked_asterisk: Ngày lập: **09/11/2022**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - Mô tả chi tiết cột 25 [MA_BAC_SI] khi xuất XML 4210](https://github.com/dh-hos/Mo-ta-he-thong/issues/19)
- Thực hiện theo Quyết định: [4210/QĐ-BYT - ngày 20/09/2017 của Bộ Y tế](https://github.com/dh-hos/Mo-ta-he-thong/files/9967120/QD-2017-4210_20170920.pdf)

###### :eight_spoked_asterisk: Xử lý yêu cầu: Các phân hệ xuất dữ liệu theo 4210

:white_check_mark: **Đối với Vật tư y tế**: `XML3.MA_BAC_SI = macc_hanhnghe_cv2348` từ `dmnhanvien` thông qua `chungtu.manv = dmnhanvien.manv` của toa Vật tư y tế.

:white_check_mark: **Đối với Cận lâm sàng**: `XML3.MA_BAC_SI` => ghép các `macc_hanhnghe_cv2348` cách nhau bởi dấu `;` thông qua `dmnhanvien.manv` theo quy tắc: `chidinhcls.manv;pskhamha.manv;psmotaxn.manv;pssinhthiet.manvtraketqua;pstebaotucung.manv_th;psdom.manv_th;ekippt.manv`. Trong đó:
- `chidinhcls.manv`: `macc_hanhnghe_cv2348` của bác sĩ chỉ định.
- `pskhamha.manv`: `macc_hanhnghe_cv2348` của nhân viên/bác sĩ đọc kết quả[^2024-08-08] Chẩn đoán hình ảnh/Thăm dò chức năng. Được tham chiếu chi tiết: `chidinhcls.mabn = pskhamha.mabn AND chidinhcls.makb = pskhamha.makb AND chidinhcls.macls = pskhamha.macls AND chidinhcls.ngaykcb = pskhamha.ngaykcb`.
- `psmotaxn.manv`: `macc_hanhnghe_cv2348` của nhân viên thực hiện trả kết quả Xét nghiệm cơ bản (Huyết học; Sinh hóa; Nước tiểu; Miễn dịch; Vi sinh; ...). Được tham chiếu chi tiết: `chidinhcls.mabn = psmotaxn.mabn AND chidinhcls.makb = psmotaxn.makb AND chidinhcls.macls = psmotaxn.macls AND chidinhcls.ngaykcb = psmotaxn.ngaykcb`.
- `pssinhthiet.manvtraketqua`: `macc_hanhnghe_cv2348` của nhân viên thực hiện trả kết quả Xét nghiệm Sinh thiết. Được tham chiếu chi tiết: `chidinhcls.mabn = pssinhthiet.mabn AND chidinhcls.makb = pssinhthiet.makb AND chidinhcls.macls = pssinhthiet.macls AND chidinhcls.ngaykcb = pssinhthiet.ngaykcb AND COALESCE(pssinhthiet.manvtraketqua,'') != ''`.
- `pstebaotucung.manv_th`: `macc_hanhnghe_cv2348` của nhân viên thực hiện trả kết quả Xét nghiệm Tế bào cổ tử cung. Được tham chiếu chi tiết: `chidinhcls.mabn = pstebaotucung.mabn AND chidinhcls.makb = pstebaotucung.makb AND chidinhcls.macls = pstebaotucung.macls AND chidinhcls.ngaykcb = pstebaotucung.ngaykcb`.
- `psdom.manv_th`: `macc_hanhnghe_cv2348` của nhân viên thực hiện trả kết quả Xét nghiệm Đờm. Được tham chiếu chi tiết: `chidinhcls.mabn = psdom.mabn AND chidinhcls.makb = psdom.makb AND chidinhcls.macls = psdom.macls AND chidinhcls.ngaykcb = psdom.ngaykcb`.
- `ekippt.manv`: Gom tất cả các `macc_hanhnghe_cv2348` của nhân viên trong ekip thực hiện Thủ thuật/Phẫu thuật. Được tham chiếu chi tiết: `chidinhcls.mabn = ekippt.mabn AND chidinhcls.makb = ekippt.makb AND chidinhcls.id = ekippt.id`.

[^2024-08-08]: Thay đổi ngày 08/08/2024: Điều chỉnh từ `"nhân viên thực hiện trả kết quả"` ⇒ `"nhân viên/bác sĩ đọc kết quả"` đối với `pskhamha.manv`.
