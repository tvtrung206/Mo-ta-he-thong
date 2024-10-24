<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ GIẤY CAM KẾT CHUYỂN CƠ SỞ KHÁM BỆNH, CHỮA BỆNH

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **23/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thay đổi cấu trúc dữ liệu

```SQL: Cập nhật cấu trúc bảng current.chuyenvien thêm cột la_nguoi_benh
ALTER TABLE current.chuyenvien
  ADD COLUMN la_nguoi_benh NUMERIC(1,0);

COMMENT ON COLUMN current.chuyenvien.la_nguoi_benh
IS '0: Là người bệnh
1: Là người thân';
```
```SQL: Cập nhật cấu trúc bảng current.psdangky
ALTER TABLE current.psdangky
  ADD COLUMN namsinhqh DATE;
COMMENT ON COLUMN current.psdangky.namsinhqh
IS 'Ngày tháng năm sinh người thân bệnh nhân';

ALTER TABLE current.psdangky
  ADD COLUMN tuoiqh NUMERIC(2,0);
COMMENT ON COLUMN current.psdangky.tuoiqh
IS 'Tuổi người thân bệnh nhân';
```
:white_check_mark: **Treatment**
- Lập phiếu phẫu thuật:
  ![image](https://github.com/user-attachments/assets/dec40ce8-2177-476e-ab62-270c542a0c22)

  - Nếu ekip.pttt = 0: Load tất cả nhân viên
  - Nếu ekip.pttt = 1: Chỉ load nhân viên có chứng chỉ hành nghề
    
:white_check_mark: **Prescription**
- Lập phiếu PT-TT:
  	- Nếu ekip.pttt = 0: Load tất cả nhân viên
  	- Nếu ekip.pttt = 1: Chỉ load nhân viên có chứng chỉ hành nghề
