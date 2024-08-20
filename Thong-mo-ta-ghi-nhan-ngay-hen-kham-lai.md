
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
:white_check_mark: **Trên Form khám bệnh**
- Trường hợp chưa có ngày hẹn : bác sĩ chọn ngày hẹn và lưu lại.
- Trường hợp đã có ngày hẹn:
  + nếu cùng bác sĩ -> bác sĩ có thể chọn ngày hẹn khác và lưu lại.
  + nếu khác bác sĩ -> khi bác sĩ chọn ngày hẹn khác và lưu lại thì cảnh báo đã có giấy hẹn tái khám. Nếu bác sĩ vẫn chọn chỉnh ngày hẹn mới thì lưu nhật ký thay đổi.

:white_check_mark: **Trên Form ra toa**

XÉT THAM SỐ hentaikham :
  1. hentaikham = 0 :
- Trường hợp chưa có ngày hẹn : bác sĩ chọn `ngày hẹn` và lưu lại.
- Trường hợp đã có ngày hẹn:
     + nếu cùng bác sĩ -> bác sĩ có thể chọn `ngày hẹn` khác và lưu lại.
     + nếu khác bác sĩ -> khi bác sĩ chọn `ngày hẹn` khác và lưu lại thì cảnh báo đã có giấy hẹn tái khám. Nếu bác sĩ vẫn chọn chỉnh `ngày hẹn` mới thì lưu nhật ký thay đổi.

=> `Ngày hẹn` không phụ thuộc vào toa, việc thay đổi `ngày uống` của toa hay `hạn tái khám` không ảnh hưởng đến `ngày hẹn`.

2. hentaikham = 1 :
- Trường hợp chưa có ngày hẹn : bác sĩ nhập số ngày uống, phần mềm tự động tính và điền `hạn tái khám` và `ngày hẹn` và lưu lại.
- Trường hợp đã có ngày hẹn:
     + nếu cùng bác sĩ -> bác sĩ nhập số ngày uống, phần mềm tự động tính và điền `hạn tái khám` và `ngày hẹn` và lưu lại.
     + nếu khác bác sĩ -> bác sĩ nhập số ngày uống, phần mềm tự động tính và điền `hạn tái khám` và `ngày hẹn`. Khi lưu lại thì cảnh báo đã có giấy hẹn tái khám. Nếu bác sĩ vẫn chọn chỉnh `ngày hẹn` mới thì lưu nhật ký thay đổi.
  
=> Load `ngày hẹn` theo số `ngày uống` trên toa thuốc. Khi chỉnh `hạn tái khám`, tự động điều chỉnh `ngày hẹn` cho phù hợp.
