![image](https://github.com/user-attachments/assets/bbc6d1d3-d9f2-465b-a76d-cd0a4bb9a36a)<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: HƯỚNG DẨN CÀI ĐẶT SERVICES CTS

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **30/06/2024**

###### :eight_spoked_asterisk: HƯỚNG DẪN CÀI ĐẶT SERVICE
1. Đảm bảo server cài đặt service có cài đặt NODE.JS (version: v18.20.2).
2. Tải file cài đặt: [Tại đây](https://gofile.me/78TQg/TF2dIoH9L)
3. Giải nén file vừa tải về, mở file app.js và cấu hình port và csdl.
   ![image](https://github.com/user-attachments/assets/969af120-3131-4463-94da-30bd67d1e01f)
4. Tại thư mục vừa giải nén file, mở cmd chạy câu lệnh `myapp.exe install` để cài đặt và `myapp.exe start` để chạy service.
   ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/110148171/5759a7ac-10e5-4372-bf22-89825dd2cd28)
5. Mở port: Truy cập vào Windows Defender Firewall -> Advanced settings. Tại cửa sổ Windows Defender Firewall with Advanced security tiến hành mở port.
   ![](https://i.imgur.com/3TTgzgF.png)
   ![](https://i.imgur.com/Uh0HD8K.png)
   ![](https://i.imgur.com/Yd49M13.png)
   ![](https://i.imgur.com/gAzhm4e.png)
   ![](https://i.imgur.com/Cj2EI3W.png)

###### :eight_spoked_asterisk: MAP CTS VÀO TÀI KHOẢN TRÊN HIS
- sử dụng postman thực hiện request sau :
  + URL: http://IP:PORT/create_user_softdream (IP: địa chỉ IP của bệnh viện, PORT: mã port đã thiết lập ở phần cài đặt service)
  + METHOD: POST
  + BODY:
    ```cshap
    {
    "username":"api-dh",
    "password":"pjjb2r0d19rfd5r2",
    "serial":"5401100065302B84D97D23C04E8746EF",
    "pin":"018852",
    "manv":"001"
    }
    ```

 ###### :eight_spoked_asterisk: CẤU HÌNH SỬ DỤNG TRÊN HIS

 



