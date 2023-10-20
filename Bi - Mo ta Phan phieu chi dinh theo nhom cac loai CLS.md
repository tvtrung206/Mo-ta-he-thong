
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CẬP NHẬT THAM SỐ HỆ THỐNG

</div>

###### :eight_spoked_asterisk: Người lập: [**NGHỊ VĂN BI**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **20/10/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Phân nhóm phiếu chỉ định cận lâm sàng theo nhóm loại cận lâm sàng trong cùng kho

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
Bi cập nhật cấu trúc:
- Thêm tham số phieuyc.cauhinh (Thực hiện cấu hình phiếu yêu cầu nhóm theo loại cận lâm sàng (0: không sử dụng; 1: sử dụng)
- Thêm table dmphieuyc:
CREATE TABLE current.dmphieuyc (
  phieuyc NUMERIC(1,0),
  tenphieuyc VARCHAR(1000),
  PRIMARY KEY(phieuyc)
) 
WITH (oids = false);

ALTER TABLE current.dmphieuyc
  ALTER COLUMN phieuyc SET STATISTICS 0;
  
:white_check_mark: **Xử lý**
+ Module Admin:
  Khi tham số phieuyc.cauhinh = 1
  Hỗ trợ người dùng cập nhật danh mục phiếu yêu cầu: current.dmphieuyc.
  Hiển thị và cho phép người dùng chọn Phiếu yêu cầu (giá từ table current.dmphieuyc) tại danh mục Loại cận lâm sàng (giá trị cột dmloaicls.phieuyc) 
+ Module Prescription, Module Treatment:
  Khi tham số phieuyc.cauhinh = 0 thực hiện như hiện tại.
  Khi tham số phieuyc.cauhinh = 1 thực hiện.
  In phiếu chỉ định theo cấu hình phiếu cận lâm sàng: các cận lâm sàng có cùng gía trị dmloaicls.phieuyc lên cùng phiếu chỉ định.
  Thiết kế phiếu chỉ định bằng Xtrareport, bổ sung parameter "tenphieuyc": lấy từ current.dmphieuyc.tenphieuyc tương ứng từng phiếu chỉ định.
  

