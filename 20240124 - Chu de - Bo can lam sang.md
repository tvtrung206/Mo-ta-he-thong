
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CHỈ ĐỊNH BỘ CẬN LÂM SÀNG CÓ SỐ LƯỢNG MẶC ĐỊNH

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **24/01/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- [Thực hiện theo Yêu cầu - Bộ CLS mặc định số lượng](https://github.com/dh-hos/To_Lap_Trinh/issues/22)


###### :eight_spoked_asterisk: Xử lý yêu cầu

- Admin: Cấu hình số lượng cận lâm sàng trong bộ Cận lâm sàng
- Prescription, Register, Treatment: Chỉ định bộ cận lâm sàng sẽ lấy số lượng mặc định theo cấu hình

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm cột soluong NUMERIC(3,1) trong bảng current.bocls để lưu số lượng mặc định khi chỉ định theo bộ
- SQL cập nhật cấu trúc: 

```
ALTER TABLE current.bocls ADD COLUMN soluong NUMERIC(3,1);
COMMENT ON COLUMN current.bocls.soluong IS 'Số lượng mặc định khi chọn bộ CLS';
```
  
:white_check_mark: **Xử lý**

- Module Admin: Thêm control cho phép thay đổi số lượng khi lưu bộ cận lâm sàng vào current.bocls.soluong
- Prescription, Register, Treatment: Nếu current.bocls.soluong > 0 thì ghi nhận số lượng theo cấu hình, ngược lại xử lý như hiện tại.
