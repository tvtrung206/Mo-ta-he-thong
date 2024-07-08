<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ THỰC HIỆN THỦ THUẬT/PHẪU THUẬT ĐỐI VỚI CẬN LÂM SÀNG
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **08/07/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - PK Medic Miền Đông: Không cấu hình loại PT trên danh mục CLS vẫn lập được phiếu PT-TT  #435](https://github.com/dh-hos/To_Lap_Trinh/issues/435)

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Quy trình áp dụng:** 

:blue_book: DHG.Hospital Admin: 
- Tại form `[Danh mục Cận lâm sàng]`: Cho phép cập nhật `[Loại PT]` *(như hình)*, tại control này dữ liệu được load từ `current.dmloaipt`. Dữ liệu được lấy từ cột `dmloaipt.maloai` và lưu trữ tương ứng vào cột `dmcls.maloaipt`. **Lưu ý:** áp dụng cho tất cả cận lâm sàng. 
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/1f34e8a6-bcbf-4c79-9015-80a3ad7d4a37)

:blue_book: Các phân hệ có thực hiện Thủ thuật/Phẫu thuật: `Prescription, Treatment`. 
- Tại form thực hiện Phẫu thuật/Thủ thuật: cho phép thực hiện cận lâm sàng có cấu hình cột `dmcls.maloaipt` khác rỗng. 
