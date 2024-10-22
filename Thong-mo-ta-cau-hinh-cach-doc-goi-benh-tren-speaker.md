<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ CÁCH THỨC CẤU HÌNH CÁCH ĐỌC KHI GỌI BỆNH TRÊN MODULE SPEAKER

</div>

:white_check_mark: **Người lập: LÊ QUỐC THỐNG**

:white_check_mark: **Ngày lập: 21/10/2024**

:white_check_mark: **Ngày dự hoàn thành: 21/10/2024**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Chi tiết cách cấu hình**
1. Chép hai file giọng đọc `tiento`(.Wav) và `hauto`(.Wav) vào thư mục cài đặt của module Speaker.
   -  tiento: Âm thanh được đọc phía trước số thứ tự bệnh nhân.
   -  hauto: Âm thanh được đọc phía sau số thứ tự bệnh nhân và trước số phòng hoặc số quầy
    Ví dụ: tiento + 2 + hauto + 1 =>> "mời bệnh nhân có số thứ tự" 2 "Vào quầy" 1

![image](https://i.imgur.com/HnPhjZj.png)
2. Cách thức đặt tên file.

   - Đối với hình thức cấu hình theo module.
     + tên file tiento = Tên module cấu hình + "_tiento".
     + tên file hauto = Tên module cấu hình + "_hauto".
![](https://i.imgur.com/X9QeZIV.png)

*Ví dụ* Khi cấu hình Speaker theo module -> Phân hệ Register.

![](https://i.imgur.com/4h3ZGcq.png)

=>> Tên file tiền tố = 'Register' + "_tiento" (kết quả: Register_tiento) và tên file hậu tố = 'Register' + "_hauto" (kết quả: Register_hauto).

   - Đối với hình thức cấu hình theo loa phát
     + tên file tiento = Tên loa phát + "_tiento".
     + ten file hauto = Tên loa phát + "_hauto".

![image](https://i.imgur.com/VgP2mQK.png).

*Ví dụ* Khi cấu hình Speaker theo loa phát.

![](https://i.imgur.com/gVUINwv.png)

=>> Tên file tiền tố  = '91' + chuỗi "_tiento" (Kết quả: 91_tiento) và tên file hậu tố = '91' + "_hauto" (kết quả: 91_hauto).
     
**LƯU Ý** =>> Trường hợp không tìm thấy 2 file cấu hình trên, phầm mềm sẽ tự đọc theo mặc định có sẳn.


