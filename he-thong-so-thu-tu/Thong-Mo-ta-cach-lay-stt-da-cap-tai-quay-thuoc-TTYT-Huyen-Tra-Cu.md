<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ CÁCH LẤY STT ĐÃ CẤP TẠI QUẦY THUỐC - TTYT HUYỆN TRÀ CÚ

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **21/06/2024**

###### :eight_spoked_asterisk: Khách hàng: **TTYT HUYỆN TRÀ CÚ**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Hướng dẫn lấy STT:** 
- Sau khi cấp số thứ tự xong, STT của bệnh nhân được lưu vào bảng `current.monitor` cùng với mabn, makb và phân khu.
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/110148171/bc6b1518-bcbd-431b-9882-2beb10f21ad4)
- các module khác có thể dựa vào `makb` để lấy STT bệnh nhân trong bảng `current.monitor`

