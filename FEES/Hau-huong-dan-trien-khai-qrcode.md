<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>HƯỚNG DẪN SỬ DỤNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CÀI ĐẶT  WEBSERVICES CHO HỆ THỐNG TÍCH HỢP THANH TOÁN QRCODE

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **21/03/2024**

###### :eight_spoked_asterisk: Khách hàng tích hợp thanh toán QRCode

###### :eight_spoked_asterisk: Yêu cầu máy tính để chạy webservice

- Máy tính có kết nối Internet, cài window 64bit
- Nên cài đặt window server (hỗ trợ tối đa kết nối đến webservice)
- Cài đặt Git mới nhất tại [git-scm.com](https://git-scm.com/downloads) (Phải khởi động lại sau khi cài đặt)

###### :eight_spoked_asterisk: Bước 1: Cài đặt github-action-runner

- Mục đích: Lấy code trên github.com về máy hiện tại chạy webservice (Việc tạo repo và upcode sẽ do nhóm code thực hiện)
- Hướng dẫn dưới đây lấy ví dụ là cho Bệnh viện Quận 12 - kết nối BIDV
![alt text](File-ho-tro/QRCode/action-runner/b1-chon-repo.png)
![alt text](File-ho-tro/QRCode/action-runner/b2-actions.png)
![alt text](File-ho-tro/QRCode/action-runner/b3-new-runner.png)
![alt text](File-ho-tro/QRCode/action-runner/b4-download-token.png)
![alt text](File-ho-tro/QRCode/action-runner/b5-giai-nen.png)
![alt text](File-ho-tro/QRCode/action-runner/b6-phan-quyen-script.png)

```Set-ExecutionPolicy -ExecutionPolicy RemoteSigned```

Tạo tập tin register-action.bat để thực hiện đăng ký, thay các tham số tương ứng
--url, --token, --labels vào trong thư mục giải nén phía trên.

```
for %%I in (.) do set CurrDirName=%%~nxI
echo %CurrDirName%
config.cmd --unattended --url https://github.com/dh-hos/79029-qrcode-bidv --token BFFENVBV2KEDNDAW7WZQPRDF7PT2I --runasservice --labels 79029-qrcode-bidv
```

![alt text](File-ho-tro/QRCode/action-runner/b7-chay-register.png)
![alt text](File-ho-tro/QRCode/action-runner/b8-dang-ky-thanh-cong.png)
![alt text](File-ho-tro/QRCode/action-runner/b9-tao-action.png)
![alt text](File-ho-tro/QRCode/action-runner/b10-copy-noi-dung.png)
![alt text](File-ho-tro/QRCode/action-runner/b11-them-yml.png)
![alt text](File-ho-tro/QRCode/action-runner/b13-run-action.png)
![alt text](File-ho-tro/QRCode/action-runner/b14-chay-thanh-cong.png)

###### :eight_spoked_asterisk: Bước 2: Cài đặt webservices

- Khởi chạy dịch vụ webservice để nhận dữ liệu phía ngân hàng báo có về HIS
![alt text](File-ho-tro/QRCode/webservices/b0-cau-hinh-firewall.png)
![alt text](File-ho-tro/QRCode/webservices/b1-cai-webservice.png)
![alt text](File-ho-tro/QRCode/webservices/b2-start.png)
![alt text](File-ho-tro/QRCode/webservices/b3-cau-hinh-csdl.png)

###### :eight_spoked_asterisk: Lưu ý: Cài đặt webservices

- Khi thay đổi các tập tin trên github.com, muốn thay đổi tới bệnh viện thì phải thực hiện chạy lại các workflow
![alt text](File-ho-tro/QRCode/action-runner/b13-run-action.png)

#### KẾT THÚC CHÚC THÀNH CÔNG