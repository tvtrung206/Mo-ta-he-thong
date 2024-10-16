<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: TÍCH HỢP THIẾT BỊ ĐỌC CĂN CƯỚC GẮN CHIP HN212 - JTH

</div>

###### :eight_spoked_asterisk: Người lập: [Lê Quốc Thống](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập:

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Tài liệu hỗ trợ

- [Tài liệu hướng dẫn cài đặt (md)](Tich-hop-doc-the-cccd-gan-chip-HN212-jth-api.md)

- [Tích hợp API (md)](Tich-hop-doc-the-cccd-gan-chip-HN212-jth.md)

- [Tài liệu hướng dẫn cài đặt (pdf)](Tich-hop-doc-the-cccd-gan-chip-HN212-jth.pdf)

- [Tích hợp API (pdf)](Tich-hop-doc-the-cccd-gan-chip-HN212-jth-api.pdf)

- JTHeID.Setup.exe: `NAS: To Code/SOFTS/JTHeID.Setup.exe`

- [JTHeID.Setup.exe] (https://gofile.me/78TQg/ZnOfo1tdX)

- [.NET 6.0 Desktop Runtime (v6.0.35) - Windows x64 Installer](https://download.visualstudio.microsoft.com/download/pr/0bfb4b48-9221-491f-8157-eed2307f13e6/3d7890b36ae32759d141633afd43787e/windowsdesktop-runtime-6.0.35-win-x64.exe)

###### :eight_spoked_asterisk: Yêu cầu phát sinh

###### :eight_spoked_asterisk: Xử lý yêu cầu
:white_check_mark: **Xử lý nghiệp vụ tại Admin và Register**

- Sử dụng DLL `DH.GoiBenh.dll`.
- Khởi tạo `WebhookCCCD` :
  ```csharp
    private WebhookCCCD _webhookListener;
  ```

- Khởi động WebhookListener và lắng nghe trên http://localhost:8050/ đã cấu hình.
  ```csharp
    _webhookListener = new WebhookCCCD();
    _webhookListener.OnDataReceived += WebhookListener_OnDataReceived; //Khi dữ liệu được nhận, sự kiện này sẽ được kích hoạt, xữ lý dữ liệu nhận được trong hàm này.
    _webhookListener.Start("http://localhost:8050/");
  ```

- Nhận giá trị từ máy quét và xử lý.
  ```csharp
    private void WebhookListener_OnDataReceived(string data)
    {
              // Data nhận được là một chuỗi dạng json.
              // Ví dụ :
                JObject jsonObject = JObject.Parse(data);
    
                // Cập nhật giá trị vào TextBox từ luồng chính (UI thread)
                this.Invoke((Action)(() =>
                {
                    txtQR.Text = jsonObject["id_card"]?.ToString(); // Lấy giá trị "id_card"
                }));
    }
  ```
- Dừng WebhookListener khi không sử dụng.
  ```csharp
    _webhookListener.Stop();
  ```

###### :eight_spoked_asterisk: Thực hiện kết nối
- Kết nối máy quét CCCD gắn chip HN-212 với máy chạy ứng dụng HIS thông qua cổng USB.

  ![](https://i.imgur.com/E6HvhBw.png)
  
- Mở ứng dụng JTH hỗ trợ quét CCCD và đăng nhập bằng tài khoản được cấp.

  ![](https://i.imgur.com/ku2tAM0.png)

###### :eight_spoked_asterisk: Nhận dữ liệu.
- Sau khi quét CCCD bằng máy quét gắn chip HN-212. Thông tin CCCD được hiển thị trên ứng dụng JTH.

  ![](https://i.imgur.com/94uv7OS.png)
  
- Ứng dụng JTH sẽ tự động gửi dữ liệu đến HIS thông qua API đã cấu hình bao gồm các trường như sau:
  + `id_card` : Số CCCD.
  + `full_name` : Họ và tên.
  + `date_of_birth` : Ngày sinh.
  + `gender` : Giới tính.
  + `nationality` : Quốc tịch.
  + `race` : Dân tộc.
  + `religion` : Tôn giáo.
  + `place_of_origin` : Quê quán.
  + `place_of_residence` : Địa chỉ thường trú.
  + `personal_identification` : Đặc điểm nhận dạng.
  + `date_of_issue` : Ngày cấp CCCD.
  + `date_of_expiry` : Ngày hết hạn CCCD.
  + `father_name` : Họ tên cha.
  + `mother_name` : Họ tên mẹ.
  + `wife_name` : Tên Vợ/Chồng.
  + `old_id_card` : Số CMND.
  + `id_img` : Hình ảnh.

- Phần mềm HIS sẽ phân tích dữ liệu nhận được và điền vào các ô cần thiết.

###### :eight_spoked_asterisk: Cách sử dụng.
- Mở ứng dụng JTH và đăng nhập bằng tài khoản được cấp.
- Mở ứng dụng HIS đã tích hợp chức năng quét CCCD bằng thiết bị gắn chip HN-212.
- Tại ứng dụng HIS, mở form cần lấy thông tin CCCD sau đó đặt thẻ CCCD vào thiết bị gắn chin HN-212.
  ![](https://i.imgur.com/GriJSHQ.png).

 - **Sử dụng chức năng trên Register**
   + Bước 1: Mở ứng dụng JTH và đăng nhập.
   + Bước 2: Mở giao diện `Đăng ký KCB` trên Register
   + Bước 3: Ấn vào nút đăng ký và đặt thẻ CCCD vào máy HN-212
     ![](https://i.imgur.com/yuRH81g.gif)

###### :eight_spoked_asterisk: Triển khai.
- Cài đặt ứng dụng JTH.
- Cấu hình ứng dụng JTH.
  
  ![](https://i.imgur.com/jtSMbGc.png)
  
- Cài đặt `.NET 6.0 Desktop Runtime (v6.0.35)`.
- Cập nhật ứng dụng HIS đã tích hợp chức năng quét CCCD bằng thiết bị gắn chin HN-212.


###### :eight_spoked_asterisk: Các điều kiện cần thiết.
- Có thiết bị xác thực CCCD gắn chip HN-212.
- Cài đặt đầy đủ các ứng dụng JTH, HIS và `.NET 6.0 Desktop Runtime (v6.0.35)`.
- Cấu hình đúng WebHook URL để nhận dữ liệu được gửi từ ứng dụng JTH đến HIS.




