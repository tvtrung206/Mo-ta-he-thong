
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

:white_check_mark: **Xử lý**
+ Module Admin:
- Hiển thị và cho phép người dùng cập nhật giá trị dmloaicls.phieuyc (numeric (1,0)) hỗ trợ cấu hình nhóm loại cận lâm sàng cần in cùng phiếu chỉ định;
+ Module Prescription:
  Khi tham số phieuycchuan = 2 thực hiện
- Trong từng kho tiến hành gom các loại cận lâm sàng có cấu hình dmloaicls.phieuyc giống nhau in cùng phiếu.
- Thiết kế phiếu chỉ định bằng Xtrareport.
+ Module Treatment:
  Khi tham số nt.phieuycchuan = 2 thực hiện
- Trong từng kho tiến hành gom các loại cận lâm sàng có cấu hình dmloaicls.phieuyc giống nhau in cùng phiếu.
- Thiết kế phiếu chỉ định bằng Xtrareport.
