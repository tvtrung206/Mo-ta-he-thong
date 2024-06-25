
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: XÂY DỰNG DLL CẤP SỐ THỨ TỰ

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)


###### :eight_spoked_asterisk: Ngày lập: **25/06/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **26/06/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Thay đổi cấu trúc:
- Bổ sung cấu trúc:
```csharp
  ALTER TABLE current.cauhinhmay ADD COLUMN phankhu NUMERIC(2,0);
```
###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Chức năng cấp STT mới**
 - Xây dựng hàm cấp số thứ tự nhận vào các giá trị truyền vào gồm `mabn`, `makb`, `phankhu`, `module`. Xử lý lưu thông tin nhận vào và STT mới vào bảng `current.monitor`.
   
:white_check_mark: **Chức năng lấy số thứ tự** 
- Xây dựng hàm lấy số thứ tự. Dựa vào `mabn`, `makb` và `phankhu` để lấy STT hiện tại của bệnh nhân tại phân khu đó.

###### :eight_spoked_asterisk: **Hướng dẫn sử dụng dll [**DH.SoThuTu.dll**]()**
:white_check_mark: **Hàm cấp STT** 
- Gọi hàm CapSoMoi và truyền giá trị như sau:
```csharp
  STT.CapSoMoi(mabn, makb, phankhu, modole, conn);
//Ví dụ: int stt = STT.CapSoMoi("2024001360", "2401003971", "96", "Ordinal", LibraryApp.ClsConnection.conn);
```

:white_check_mark: **Hàm lấy STT hiện tại của bệnh nhân** 
- Gọi hàm getSTT và truyền giá trị như sau:
```csharp
  STT.getSTT(mabn, makb, phankhu, LibraryApp.ClsConnection.conn);
//Ví dụ: int stt = STT.getSTT("2024001360", "2401003971", "96", LibraryApp.ClsConnection.conn);
```

