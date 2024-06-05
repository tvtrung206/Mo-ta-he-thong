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
- Hàm gọi bệnh nhận vào một giá trị enum có cấu trúc như sau:
```csharp
enum GoiBenhEnum 
{ 
    sott, // số thứ tự
    sophong, // số phòng
    loaphat, // loa phát
    module, //tên module 
    tuso, // số dùng để gọi nhìu bệnh nhân tusu -> sott, 
    tiento, // tên file âm thanh đầu. Ví du tiento = “MBNCSTT” -> Loa sẽ đọc : Mời bệnh nhân có số thứ tự + sott + hauto + sophong
    hauto // tên file âm thanh cuối. Ví dụ hauto = “VQS” -> Loa sẽ đọc : tiento + sott + “Vào quầy số” + sophong
}
// *nếu
// tuso = null -> xử lý gọi bệnh theo sott.
// tuso < sott -> xử lý gọi bệnh từ tuso đến sott.
```

- Gán giá trị cho enum
```csharp
EnumGoiBenh _enum = new EnumGoiBenh
            {
                Sott = 1,
                Sophong = 1,
                Loaphat = 91,
                Module = "register",
                Tuso = 1,
                Tiento = "MBNCSTT",
                Hauto = "VQ"
            };
```

- Gọi hàm gọi bệnh và truyền giá trị để sử dụng
```csharp
DHGoiBenh.GoiBenh(_enum, LibraryApp.ClsConnection.conn);
```

:white_check_mark: **Hướng dẫn xóa Monitor**
```csharp
DHGoiBenh.DelMonitor(mabn, makb, phankhu, DHGoiBenh.Module.Register, LibraryApp.ClsConnection.conn);
```
//phankhu: mặc định = 96 đối với quầy phát thuốc


