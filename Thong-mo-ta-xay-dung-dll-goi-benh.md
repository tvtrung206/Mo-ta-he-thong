<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: XÂY DỰNG DLL GỌI BỆNH

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)


###### :eight_spoked_asterisk: Ngày lập: **02/06/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **02/06/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
 - Thêm 2 cột tiento, hauto vào bảng current.goibenh
 - Script : `ALTER TABLE current.goibenh 
             ADD COLUMN tiento VARCHAR(10), 
             ADD COLUMN hauto VARCHAR(10); `

:white_check_mark: **Hướng dẫn sử dụng dll [**DH.GoiBenh.dll**]()**
- Gọi hàm DHGoiBenh.GoiBenh(enum, LibraryApp.ClsConnection.conn);
- Hàm nhận vào một emum có cấu trúc như sau:
