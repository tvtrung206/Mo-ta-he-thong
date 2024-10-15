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
:white_check_mark: **Cấu hình ứng dụng quét căn cước công cân**

![](https://i.imgur.com/jtSMbGc.png)

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

