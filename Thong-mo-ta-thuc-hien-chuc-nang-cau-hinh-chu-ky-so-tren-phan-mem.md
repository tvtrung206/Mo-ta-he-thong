<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN CHỨC NĂNG CẤU HÌNH CHỮ KÝ SỐ TRÊN PHẦN MỀM.

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **14/07/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **15/07/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
- Thêm table current.dmcts để thực hiện lưu thông tin chứng thư số.
```csharp
CREATE TABLE current.dmcts (
  taikhoan VARCHAR(255) NOT NULL,
  matkhau VARCHAR(255) NOT NULL,
  serial VARCHAR(50) NOT NULL,
  pin VARCHAR(50),
  manv VARCHAR(10),
  ngaybd TIMESTAMP(0) WITHOUT TIME ZONE,
  ngaykt TIMESTAMP(0) WITHOUT TIME ZONE
) 
WITH (oids = false);
```

:white_check_mark: **Xây dựng form Thông Tin CTS**
- Tại dll `DH.ChuKySo.dll` xây dựng form Thông Tin CTS để người dùng có thể nhập thông tin của CTS và map chữ ký.
- Tại dll `DH.ChuKySo.dll` thay đổi hàm CallAPI, lấy các thông tin CTS dựa vào manv được các module khác truyền vào khi gọi đến và truyền đến services CTS.
- Hướng dẫn sử dụng DLL `DH.ChuKySo.dll` : 
+ Gọi đến Form Thông Tin CTS
```csharp
  FrmThongTinCTS frm = new FrmThongTinCTS(LibraryApp.ClsConnection.conn);
  frm.ShowDialog();
```

:white_check_mark: **Cập nhật lại service ký số**
- Cập nhật lại service ký số : nhận các thông tin CTS được truyền đến để thực hiện ký số và trả kết quả. 
