
<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CẬP NHẬT THAM SỐ HỆ THỐNG

</div>

###### :eight_spoked_asterisk: Người lập: [**NGHỊ VĂN BI**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **18/10/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Kiểm tra thông tin sinh hiệu bệnh nhân trước khi khám, thay đổi diễn biến

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

Bi: Thêm tham số sử dụng chung `ktsinhhieu` `Kiểm tra thông tin sinh hiệu trước khi khám (0: không; 1: bắt buộc;)`

:white_check_mark: **Xử lý**
+ Khi ktsinhhieu = 0: không kiểm tra nhập thông tin sinh hiệu
+ Khi ktsinhhieu = 1:
            - Ngoại trú, bệnh án ngoại trú thanh toán ngày: không cho khám khi chưa nhập đủ thông tin sinh hiệu.
            - Nội trú, bệnh án ngoại trú thanh toán đợt: khi thêm và chỉnh diễn biến không cho lưu khi chưa nhập đủ thông tin sinh hiệu.
