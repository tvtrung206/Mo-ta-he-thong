
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ GHI NHẬN NGÀY HẸN TÁI KHÁM

</div>

###### :eight_spoked_asterisk: Người lập: [**Lê Quốc Thống**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **20/08/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thay đổi cấu trúc dữ liệu
- Thêm cột mabshk vào bảng current.psdangky:
- Mô tả:
  + mabshk : Mã bác sĩ hẹn tái khám, được lưu khi bác sĩ chọn ngày hẹn tái khám và lưu lại
```sql
ALTER TABLE current.psdangky
ADD mabshk VARCHAR(20);
```

###### :eight_spoked_asterisk: Cách ghi nhận ngày hẹn
- Trường hợp chưa có ngày hẹn : khi bác sĩ chọn ngày hẹn tái khám, lưu ngày hẹn kèm với mabshk.
- Trường hợp đã có ngày hẹn:
  + nếu cùng bác sĩ, cho phép cập nhật lại ngày hẹn khám.
  + nếu khác bác sĩ, cảnh báo đã có giấy hẹn tái khám. Nếu bác sĩ vẫn chọn chỉnh ngày hẹn mới thì lưu nhật ký thay đổi.

###### :eight_spoked_asterisk: Lưu ý.
- Ngày hẹn không phụ thuộc vào toa, việc thay đổi ngày uống của toa hay hạn tái khám không ảnh hưởng đến ngày hẹn.
