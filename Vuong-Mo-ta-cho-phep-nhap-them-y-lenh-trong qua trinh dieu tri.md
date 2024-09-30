
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: CHO PHÉP NHẬP THÊM Y LỆNH KHI IN QUÁ TRÌNH ĐIỀU TRỊ

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **30/09/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Bổ sung cột ylenh vào bản qtdieutri**
``` sql
ALTER TABLE current.qtdieutri
  ADD COLUMN ylenh VARCHAR;
``` 

:white_check_mark: ****
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|ylenh |VARCHAR|Y lệnh: lưu y lệnh đã được tổng hợp và bổ sung|

:white_check_mark: **Qui trình**
- Khi tổng kết quá trình điều điệu trị:
    - Người dùng có thể điều chỉnh y lệnh theo ID diễn biến (y lệnh được tổng hợp từ chỉ định cls, thuốc) --> Lưu vào cột ylenh bảng qtdieutri.
    - Khi in quá trình điều trị: Y lệnh sẽ lấy từ qtdieutrin.ylenh (nếu có) ngược lại lấy từ chỉ định cls, thuốc

![image](https://github.com/user-attachments/assets/8f027cd0-19b0-4046-a5ad-3499590a0566)

![image](https://github.com/user-attachments/assets/d95848be-dbb5-4bcb-9d7d-510c38371f0f)

- Bổ sung nút in: có cấn trừ thuốc trâ
Lưu ý: y lệnh có thể được điều khi bệnh nhân đã ra viện

