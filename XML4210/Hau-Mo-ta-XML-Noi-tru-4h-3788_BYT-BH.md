<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÃ HÓA HÌNH THỨC KHÁM BỆNH, CHỮA BỆNH ĐỐI VỚI BỆNH NHÂN ĐIỀU TRỊ NỘI TRÚ 4h TRỞ XUỐNG

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **29/10/2022**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **02/11/2022**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh:

-  Thực hiện theo công văn: [3788_BYT_Mã hoa hinh thuc KCB.pdf](https://github.com/dh-hos/dhg.hospitalservices/files/9865043/3788_BYT_Ma.hoa.hinh.thuc.KCB.pdf)
-  Ghi nhận thay đổi XML gửi BHXH đối với trường hợp bệnh nhân điều trị nội trú dưới 4h

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Module Treatment - Kiểm soát chi phí tiền giường**

-  Thực hiện cảnh báo người dùng biết khi chỉ định chi phí giường bệnh nếu **[Giờ chỉ định] - [Vào viện] <= 4h**.
-  Khi xuất viện thực hiện cảnh báo chi phí bệnh nhân có tiền giường để người dùng xử lý lại phần chi phí này trường hợp **[Ra viện] - [Vào viện] <= 4h**.

:white_check_mark: **Module Chức năng xuất XML theo 4210**: Xử lý XML1 khi hồ sơ có **[Ra viện] - [Vào viện] <= 4h**

-  Dữ liệu MA_LOAI_KCB: `MA_LOAI_KCB = 9`
-  Dữ liệu NGAY_VAO_NOI_TRU: thêm trường NGAY_VAO_NOI_TRU vào XML1 theo điều kiện tham số hệ thống xml4210.NGAY_VAO_NOI_TRU = 1, ngược lại (không tồn tại tham số này hoặc giá trị khác 1) thì không thêm. Và giá trị của trường này ghi nhận như sau `NGAY_VAO_NOI_TRU = Ngày giờ vào viện xử lý với định dạng ngày giờ qui định theo 4210`.

:white_check_mark: Duyệt: Ok thực hiện theo mô tả trên nha (ngày 07/11/2022 hoàn thành)
