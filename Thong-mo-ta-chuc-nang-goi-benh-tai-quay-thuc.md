<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THÊM CHỨC NĂNG GỌI BỆNH TẠI QUẦY THUỐC

</div>

:white_check_mark: **Người lập: LÊ QUỐC THỐNG**

:white_check_mark: **Ngày lập: 06/6/2024**

:white_check_mark: **Ngày dự hoàn thành: 07/6/2024**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Xử lý yêu cầu**
1. Trên Ordinal, thêm giao diện bắt số thứ tự tại quầy thuốc bao gồm ô quét mabn, phân khu và quầy. Bệnh nhân quét mã trên toa thuốc để lấy số thứ tự -> Monitor hiển thị lên danh sách chờ
2. Trên giao diện bắt số thứ tự tại quầy thuốc. Thêm checkbox gọi bệnh. Khi người dùng check vào checkbox gọi bệnh và thực hiện quét toa thuốc, module sẽ tiến hành gọi dll DH.GoiBenh.dll thêm thông tin vào bảng current.goibenh -> Speaker tiến hành gọi bệnh -> Monitor hiển thị lên danh sách phục vụ. 
3. Sau khi gọi bệnh nhân tiếp theo, xữ lý xóa bệnh nhân trước đó ra khỏi danh sách phục vụ trên Monitor
